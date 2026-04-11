# I2C Controller Datasheet


* I2C Master-Only Controller
	* 7-bit slave addressing
	* Configurable clock via prescale register
* AXI-Stream FIFO interface (CMD / TX / RX FIFOs)
* Single byte and multi-byte (burst) write transfers
* Repeated START for combined write+read sequences
* NACK detection via `missed_ack` status bit
* Automatic STOP generation (`stop_on_idle` mode)



## Memory Map

The I2C register block is accessible at base address **0x40002000**.

| Offset | Identifier   | Name             | Access | Reset |Accessible Size
|--------|--------------|------------------|--------|-------|----------------
| 0x00   | Commands     | Command Registers| RW     | 0x0   |32 bits
| 0x08   | Status       | Status Register  | R      | 0x0   |32 bits
| 0x10   | Cfg          | Configuration    | RW     | 0x0   |32 bits
| 0x18   | Wdata        | Write Data FIFO  | W      | 0x0   |32 bits
| 0x20   | Rdata        | Read Data FIFO   | R      | 0x0   |32 bits

> **Note:** The I2C peripheral must be enabled 


## Registers

### Commands Register (0x40002000)

Used to enqueue a command into the CMD FIFO. Write to this register to initiate
or describe an I2C transaction. The `enq` bit [5] is a **singlepulse** —
it self-clears one cycle after being written; hardware copies the command into
the FIFO on the rising edge.

| Bits  | Identifier     | Access | Reset | Description                                              |
|-------|----------------|--------|-------|----------------------------------------------------------|
| 0     | start          | RW     | 0x0   | Issue START condition at beginning of transaction        |
| 1     | read           | RW     | 0x0   | Perform a read transaction (slave → master)              |
| 2     | write          | RW     | 0x0   | Perform a single-byte write transaction                  |
| 3     | write_multiple | RW     | 0x0   | Perform a multi-byte write (uses wlast to end burst)     |
| 4     | stop           | RW     | 0x0   | Issue STOP condition at end of transaction               |
| 5     | enq            | RW     | 0x0   | Enqueue the command (singlepulse — self-clears)          |
| 14:8  | address        | RW     | 0x0   | 7-bit slave address                                      |

---

### Status Register (0x40002008)

Read-only register reflecting the current state of the I2C controller and FIFOs.
All bits reset to 0 except FIFO not-full flags which are hardware-driven.

| Bits | Identifier     | Access | Reset | Description                                                      |
|------|----------------|--------|-------|------------------------------------------------------------------|
| 0    | busy           | RO     | 0x0   | High while a transaction is in progress                          |
| 1    | bus_control    | RO     | 0x0   | Master holds bus (has issued START, no STOP yet)                 |
| 2    | bus_active     | RO     | 0x0   | SCL/SDA bus activity detected                                    |
| 3    | missed_ack     | RO     | 0x0   | Slave did not ACK the address (NACK detected)                    |
| 4    | cmd_ff_n_full  | RO     | —     | **1** = CMD FIFO has space; **0** = CMD FIFO full                |
| 5    | tx_ff_n_full   | RO     | —     | **1** = TX FIFO has space; **0** = TX FIFO full                  |
| 6    | rx_ff_n_full   | RO     | —     | **1** = RX FIFO has data; **0** = RX FIFO empty                  |
| 7    | rx_overflow    | RO     | —     | RX FIFO overflow — data was received when FIFO was full          |

**Polling guidance:**

| Goal                          | Poll condition              |
|-------------------------------|-----------------------------|
| Wait for transaction to end   | `busy == 0`                 |
| Wait for TX space (write)     | `tx_ff_n_full == 1`         |
| Wait for RX data (read)       | `rx_ff_n_full == 1`         |
| Check for addressing error    | `missed_ack == 1`           |
| Check for CMD FIFO space      | `cmd_ff_n_full == 1`        |

---

### Cfg Register (0x40002010)

Configuration register for clock prescaling and bus-idle behaviour.

| Bits  | Identifier   | Access | Reset | Description                                      |
|-------|--------------|--------|-------|--------------------------------------------------|
| 15:0  | prescale     | RW     | 0x0   | SCL clock divider: `prescale = Fclk / (FI2C × 4)` |
| 16    | stop_on_idle | RW     | 0x0   | When set, auto-issue STOP when CMD FIFO empties  |

---

### Wdata Register (0x40002018)

Write-only register used to push one byte into the TX FIFO per write.
Only valid bits are `[8:0]`; upper bits are ignored.

| Bits | Identifier | Access | Reset | Description                                          |
|------|------------|--------|-------|------------------------------------------------------|
| 7:0  | wdata      | WO     | 0x0   | Data byte to transmit                                |
| 8    | wlast      | WO     | 0x0   | Set to 1 on the **last** byte of a burst write       |

> **Important:** For `write_multiple` transfers, the controller waits in `STATE_WRITE_1`
> for each successive byte. Set `wlast = 1` on the final byte to signal end of burst
> and allow the STOP condition to be issued.

---

### Rdata Register (0x40002020)

Read-only register used to pop one byte from the RX FIFO per read access.
Poll `Status.rx_ff_n_full` before reading to confirm data is available.

| Bits | Identifier | Access | Reset | Description                                                    |
|------|------------|--------|-------|----------------------------------------------------------------|
| 7:0  | rdata      | RO     | 0x0   | Received data byte                                             |
| 8    | rlast      | RO     | 0x0   | Set to 1 when this is the **last** byte in a read burst        |

> Each read of this register pops one byte from the RX FIFO.
> Do **not** read more bytes than available — use `rx_ff_n_full` to gate reads.


## Enabling the I2C Peripheral

The I2C controller is **disabled by default** at reset. 


Full `SystemConfig` register at `0x40000008`:

| Bit | Field               | Reset | Description                   |
|-----|---------------------|-------|-------------------------------|
| 3   | i2c_enable          | 0     | **I2C peripheral enable**     |



## Program Flow

### Write Transfer


1.  **Enable Peripheral**: Write to the `SystemConfig` register in the System Control block to enable the I2C clock and interface (`i2c_enable = 1`).
2.  **Set Clock Frequency**: Write to the `CFG_REG (CFGR)` to configure the SCL clock frequency using the `prescale` field. `prescale = Fclk / (FI2C × 4)`.
3.  **Enqueue Command**: Write to the `COMMAND_REG (CMD)` to initiate the transaction. Set the appropriate flags for a write operation (e.g., `start`, `write`, `stop`, `enq`, `address`).
4.  **Provide Data**: Write the data to be transmitted into the `DATA_REG (DR)`. For multiple words, ensure the FIFO has space by checking `FLEVEL` in `STATUS_REG`. For write transcation to start the fifo must be filled with minimum 4 bytes of data.
5.  **Wait for Completion**: Monitor `STATUS_REG[1]` (`TCF` - Transfer Complete Flag). Once set, the transaction is finished.

- For **write multiple bytes** set `wlast = 1` on the last byte to signal end of burst and allow the STOP condition to be issued. Set `Commands = start|write_multiple|stop|enq|(addr<<8)`

### Read Transfer

1.  **Enable Peripheral**: Write to the `SystemConfig` register in the System Control block to enable the I2C clock and interface (`i2c_enable = 1`).
2.  **Set Clock Frequency**: Write to the `CFG_REG (CFGR)` to configure the SCL clock frequency using the `prescale` field. `prescale = Fclk / (FI2C × 4)`.
3.  **Enqueue Command**: Write to the `COMMAND_REG (CMD)` to initiate the transaction. Set the appropriate flags for a read operation (e.g., `start`, `read`, `stop`, `enq`, `address`).
4.  **Wait for Completion**: Monitor `STATUS_REG[1]` (`TCF` - Transfer Complete Flag). Once set, the transaction is finished.


### Repeated START (Combined Write + Read)

Used for register-addressed reads (write register address, repeated START, read data).

```
1. Enable I2C and set prescale
2. Push register address byte: Wdata = reg_addr | (1<<8)
3. Enqueue WRITE without STOP:
      Commands = start|write|enq|(addr<<8)     # stop=0
4. Poll: while (Status.busy == 1): wait
5. Enqueue READ with START (repeated START):
      Commands = start|read|stop|enq|(addr<<8)
6. Collect RX bytes as in the Read Transfer flow above
```

## Error Handling

### NACK on Address

If the addressed slave does not ACK:

1. `Status.missed_ack` is set **for one clock cycle** during the ACK phase.
2. The controller terminates the transaction and returns to IDLE.
3. `Status.busy` clears normally.


