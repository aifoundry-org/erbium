# QSPI Datasheet

<div class="multicols" markdown="1">

The Quad SPI is an improved version of SPI with multiple IO lines i.e. QSPI supports dual as well as Quad IO lines support. (Better performance compared to legacy SPI). The QSPI also comes with the Execute in Place option which avoids copying the code to the On chip memory and executing. The core can directly read from flash and execute. i.e. the QSPI flash chips can act like normal RAM to the core.

The QSPI implementation also has programmable address size, data size, dummy cycle, instruction size, etc. The IO lines as well as the QSPI clock are all software configurable.

## Features

* Supports Single/dual/Quad SPI mode.
* Single / Double Data rate support.
* Supports 3 modes
    * Indirect mode (All operations are performed using QSPI registers).
    * Automatic status polling mode (flash status register is periodically read and interrupt is generated on flag setting).
    * Memory mapped mode (XiP mode): flash memory is mapped into device address space and seen as internal memory.
* Programmable for Single SPI (Legacy SPI), Dual IO mode & Quad IO mode.
* Programmable widths for Address, data, dummy cycles, instruction, alternative mode, etc.
* Common 32 byte FIFO is shared across both transmit & receive.
* Status register & interrupt enable registers.
* Programmable flash size.
* Mode 0 and mode 3 support.

</div>
## Ports

| Port Name | Direction | Description                                                                                                       |
| --------- | --------- | ----------------------------------------------------------------------------------------------------------------- |
| CLK       | O         | Serial clock for QSPI communication.                                                                              |
| CS        | O         | Chip select signal for QSPI applications.                                                                         |
| IO[3:0]   | IO        | Quad data lines. Output when configured to send commands and acts as input when configured to receive data (response). |

## QSPI registers

The original register IP sizes are variable for the Shakti use cases, and the data duplicates it across for the access size. Although logically 32-bit or less on the IP side, they are accessible as 64-bit values on the system bus.

| Register name         | Offset address | IP Side Size | Accessible Size | Description                                                    |
| --------------------- | -------------- | ------------ | --------------- | -------------------------------------------------------------- |
| CONTROL_REG           | 0x00           | 32 bits      | 32 bits         | Device Control Register (Read and Write)                       |
| DEVICE_CONFIG_REG     | 0x08           | 32 bits      | 32 bits         | Device Configuration Register (Read and Write)                 |
| STATUS_REG            | 0x10           | 16 bits      | 32 bits         | Device Status Register (Read Only)                             |
| FLAG_CLEAR_REG        | 0x18           | 8 bits       | 32 bits         | Flag Clear Register (Write and Read)                           |
| DATA_LENGTH_REG       | 0x20           | 32 bits      | 32 bits         | Data Length Register (Read and Write)                          |
| COMMN_CONFIG_REG      | 0x28           | 32 bits      | 32 bits         | Communication Configuration Register (Read and Write)          |
| ADDRESS_REG           | 0x30           | 32 bits      | 32 bits         | QSPI Flash Address Register (Read and Write)                   |
| ALTERNATE_BYTE_REG    | 0x38           | 32 bits      | 32 bits         | Alternate Byte Register (Read and Write)                       |
| DATA_REG              | 0x40           | 32 bits      | 32 bits         | Data Register (Read and Write)                                 |
| POLL_STS_MASK_REG     | 0x48           | 32 bits      | 32 bits         | Polling Status Mask Register (Read and Write)                  |
| POLL_STS_MATCH_REG    | 0x50           | 32 bits      | 32 bits         | Polling Status Match Register (Read and Write)                 |
| POLL_INTERVAL_REG     | 0x58           | 32 bits      | 32 bits         | Polling Interval Register (Read and Write)                     |
| LOW_POWER_TIMEOUT_REG | 0x60           | 32 bits      | 32 bits         | Low Power Timeout Register (Read and Write)                    |

## Register Descriptions

### CONTROL Register
Address offset: 0x00
Reset value: 0x0000 0x0000

| Bits   | Identifier      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| ------ | --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 31:24  | PRESCALER[7:0]  | **Clock prescaler**: This bitfield defines the scalar factor for generating CLK based on the AHB clock (value+1).<br>0: FCLK = FAHB, AHB clock used directly as QUADSPI CLK (prescaler bypassed)<br>1: FCLK = FAHB/2<br>2: FCLK = FAHB/3<br>...<br>255: FCLK = FAHB/256<br>Note: This bitfield can be modified only when BUSY = 0                                                                                                                                                                                                                                                                                                                       |
| 23     | PMM             | **Polling match mode**: This bit indicates which method must be used for determining a "match" during automatic status-polling mode.<br>0: AND match mode. SMF is set if all the unmasked bits received from the flash memory match the corresponding bits in the match register.<br>1: OR match mode. SMF is set if any one of the unmasked bits received from the flash memory matches its corresponding bit in the match register.<br>Note: This bit can be modified only when BUSY = 0.                                                                                                                                                              |
| 22     | APMS            | **Automatic status-polling mode stop**: This bit determines if automatic status-polling is stopped after a match.<br>0: Automatic status-polling mode is stopped only by abort or by disabling the QUADSPI.<br>1: Automatic status-polling mode stops as soon as there is a match.<br>Note: This bit can be modified only when BUSY = 0.                                                                                                                                                                                                                                                                                                               |
| 21     | Reserved        | Must be kept at reset value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| 20     | TOIE            | **Timeout interrupt enable**: This bit enables the timeout interrupt.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| 19     | SMIE            | **Status match interrupt enable**: This bit enables the status match interrupt.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| 18     | FTIE            | **FIFO threshold interrupt enable**: This bit enables the FIFO threshold interrupt.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| 17     | TCIE            | **Transfer complete interrupt enable**: This bit enables the transfer complete interrupt.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| 16     | TEIE            | **Transfer error interrupt enable**: This bit enables the transfer error interrupt.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| 15:13  | Reserved        | Must be kept at reset value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| 12:8   | FTHRES[4:0]     | **FIFO threshold level**: This bitfield defines, in indirect mode, the threshold number of bytes in the FIFO that causes the FIFO threshold flag (bit FTF in register STATUS_REG) to be set.                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| 7      | FSEL            | **Flash memory selection**: This bit selects the flash memory to be addressed in single-flash mode (when DFM = 0).<br>0: FLASH 1 selected<br>1: FLASH 2 selected<br>Note: This bit can be modified only when BUSY = 0. This bit is ignored when DFM = 1.                                                                                                                                                                                                                                                                                                                                                                                               |
| 6      | DFM             | **Dual-flash mode**: This bit activates dual-flash mode, where two external flash memories are used simultaneously to double throughput and capacity.<br>0: Dual-flash mode disabled<br>1: Dual-flash mode enabled<br>Note: This bit can be modified only when BUSY = 0.                                                                                                                                                                                                                                                                                                                                                                              |
| 5      | Reserved        | Must be kept at reset value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| 4      | SSHIFT          | **Sample shift**: By default, when SSHIFT = 0, the QUADSPI samples data on the following CLK edge after the data is driven by flash memory.<br>When SSHIFT = 1, an additional data sampling delay is introduced.<br>Note: This bitfield can only be modified when BUSY = 0.                                                                                                                                                                                                                                                                                                                                                                             |
| 3      | TCEN            | **Timeout counter enable**: This bit is valid only when memory-mapped mode (FMODE = 11) is selected. Activating this bit causes the NCS to be released if there has not been an access after a certain amount of time.                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| 2      | DMAEN           | **DMA enable**: This bit enables DMA for the corresponding channel.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| 1      | ABORT           | **Abort request**: Writing 1 to this bit aborts the current transfer.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| 0      | QSPI_ENABLE     | **QSPI Enable**: This bit enables the QUADSPI.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |

### DEVICE_CONFIG_REG (DCR)
Address offset: 0x08
Reset value: 0x0000 0x0000

| Bits  | Identifier | Description                                                                                                                                                        |
| ----- | ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 20:16 | FSIZE      | **Flash memory size**: This bitfield defines the size of the external memory. (Size in bytes = 2^(FSIZE+1)).                                                        |
| 10:8  | CSHT       | **Chip select high time**: This bitfield defines the minimum number of clock cycles where the chip select (NCS) must remain high between two consecutive accesses. |
| 0     | CKMODE     | **Clock mode**: Selects the clock mode.<br>0: Mode 0 (CLK is 0 when idle)<br>1: Mode 3 (CLK is 1 when idle)                                                         |

### STATUS_REG (SR)
Address offset: 0x10

| Bits  | Identifier | Description                                                                                                                                                     |
| ----- | ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 13:8  | FLEVEL     | **FIFO level**: Indicates the number of bytes currently available in the FIFO.                                                                                  |
| 5     | BUSY       | **Busy flag**: This bit is set when the QUADSPI is performing an operation.                                                                                     |
| 4     | TOF        | **Timeout flag**: Set when the timeout counter reaches 0 in memory-mapped mode.                                                                                 |
| 3     | SMF        | **Status match flag**: Set in automatic status-polling mode when the received status matches the match register.                                                |
| 2     | FTF        | **FIFO threshold flag**: Set when the FIFO level crosses the threshold defined in FTHRES.                                                                       |
| 1     | TCF        | **Transfer complete flag**: Set when the programmed number of data has been transferred.                                                                        |
| 0     | TEF        | **Transfer error flag**: This bit is set in indirect mode when an invalid address is being accessed in indirect mode. It is cleared by writing 1 to CTEF. |

### FLAG_CLEAR_REG (FCR)
Address offset: 0x18
Reset value: 0x0000 0x0000

| Bits  | Identifier | Description                                                       |
| ----- | ---------- | ----------------------------------------------------------------- |
| 4     | CTOF       | **Clear timeout flag**: Writing 1 clears the TOF flag in STATUS_REG. |
| 3     | CSMF       | **Clear status match flag**: Writing 1 clears the SMF flag in STATUS_REG. |
| 1     | CTCF       | **Clear transfer complete flag**: Writing 1 clears the TCF flag in STATUS_REG. |
| 0     | CTEF       | **Clear transfer error flag**: Writing 1 clears the TEF flag in STATUS_REG. |

### DATA_LENGTH_REG (DLR)
Address offset: 0x20
Reset value: 0x0000 0x0000

| Bits | Identifier | Description                                                               |
| ---- | ---------- | ------------------------------------------------------------------------- |
| 31:0 | DL[31:0]   | **Data length**: Number of bytes to transfer (programmed value + 1).      |

### COMMN_CONFIG_REG (CCR)
Address offset: 0x28
Reset value: 0x0000 0x0000

| Bits   | Identifier       | Description                                                                                                                                                                                                                                                                                                                                          |
| ------ | ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 31     | DDRM             | **Double data rate mode**: This bit sets the DDR mode for the address, alternate byte and data phase:<br>0: DDR mode disabled<br>1: DDR mode enabled<br>Note: This bit can be written only when BUSY = 0.                                                                                                                                            |
| 30     | DHHC             | **DDR hold**: This bit delays the data output by 1/4 of the QUADSPI output clock cycle in DDR mode:<br>0: Data output delayed using analog delay<br>1: Data output delayed by 1/4 of a QUADSPI output clock cycle<br>This feature is only active in DDR mode.<br>Note: This bit can be written only when BUSY = 0. PRESCALER > 0 is mandatory when DHHC = 1. |
| 28     | SIOO             | **Send instruction only once mode**: This bit has no effect when IMODE = 00.<br>0: Instruction sent on every transaction<br>1: Instruction sent only for the first command<br>Note: This bit can be written only when BUSY = 0.                                                                                                                     |
| 27:26  | FMODE[1:0]       | **Functional mode**: This bitfield defines the QUADSPI functional mode of operation.<br>00: Indirect-write mode<br>01: Indirect-read mode<br>10: Automatic status-polling mode<br>11: Memory-mapped mode<br>Note: This bitfield can be written only when BUSY = 0.                                                                                    |
| 25:24  | DMODE[1:0]       | **Data mode**: This bitfield defines the data phase mode of operation:<br>00: No data<br>01: Data on a single line<br>10: Data on two lines<br>11: Data on four lines<br>Note: This bitfield can be written only when BUSY = 0.                                                                                                                       |
| 23     | D_CONF           | **Programming Dummy confirmation bit**: needed by Micron model to trigger XIP mode                                                                                                                                                                                                                                                                  |
| 22:18  | DCYC[4:0]        | **Number of dummy cycles enable**: This bitfield defines the duration of the dummy phase. In both SDR and DDR modes, it specifies a number of CLK cycles (0-31).<br>Note: This bitfield can be written only when BUSY = 0.                                                                                                                          |
| 17:16  | ABSIZE[1:0]      | **Alternate-byte size**: This bit defines the size of alternate bytes.<br>00: 8-bit alternate byte<br>01: 16-bit alternate bytes<br>10: 24-bit alternate bytes<br>11: 32-bit alternate bytes<br>Note: This bitfield can be written only when BUSY = 0.                                                                                             |
| 15:14  | ABMODE[1:0]      | **Alternate byte mode**: This bitfield defines the alternate-byte phase mode of operation.<br>00: No alternate bytes<br>01: Alternate bytes on a single line<br>10: Alternate bytes on two lines<br>11: Alternate bytes on four lines<br>Note: This bitfield can be written only when BUSY = 0.                                                     |
| 13:12  | ADSIZE[1:0]      | **Address size**: This bit defines address size:<br>00: 8-bit address<br>01: 16-bit address<br>10: 24-bit address<br>11: 32-bit address<br>Note: This bitfield can be written only when BUSY = 0.                                                                                                                                                    |
| 11:10  | ADMODE[1:0]      | **Address mode**: This bitfield defines the address phase mode of operation.<br>00: No address<br>01: Address on a single line<br>10: Address on two lines<br>11: Address on four lines<br>Note: This bitfield can be written only when BUSY = 0.                                                                                                     |
| 9:8    | IMODE[1:0]       | **Instruction mode**: This bitfield defines the instruction phase mode of operation.<br>00: No instruction<br>01: Instruction on a single line<br>10: Instruction on two lines<br>11: Instruction on four lines<br>Note: This bitfield can be written only when BUSY = 0.                                                                             |
| 7:0    | INSTR[7:0]       | **Instruction**: Instruction opcode to be sent to the external SPI device.<br>Note: This bitfield can be written only when BUSY = 0.                                                                                                                                                                                                                 |

### ADDRESS_REG (AR)
Address offset: 0x30
Reset value: 0x0000 0x0000

| Bits | Identifier | Description                                                                                              |
| ---- | ---------- | -------------------------------------------------------------------------------------------------------- |
| 31:0 | ADDRESS    | **Address**: This bitfield contains the address to be sent to the external flash memory.                 |

### ALTERNATE_BYTE_REG (ABR)
Address offset: 0x38
Reset value: 0x0000 0x0000

| Bits | Identifier | Description                                                                                                   |
| ---- | ---------- | ------------------------------------------------------------------------------------------------------------- |
| 31:0 | ALTERNATE  | **Alternate bytes**: Optional data to be sent to the external SPI device right after the address.<br>Note: This bitfield can be written only when BUSY = 0. |

### DATA_REG (DR)
Address offset: 0x40
Reset value: 0x0000 0x0000

| Bits | Identifier | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| ---- | ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 31:0 | DATA[31:0] | **Data**: Data to be sent/received to/from the external SPI device.<br>In indirect write mode, data written to this register is stored on the FIFO before it is sent to the flash memory during the data phase. If the FIFO is too full, a write operation is stalled until the FIFO has enough space to accept the amount of data being written.<br>In indirect read mode, reading this register gives (via the FIFO) the data which was received from the flash memory. If the FIFO does not have as many bytes as requested by the read operation and if BUSY=1, the read operation is stalled until enough data is present or until the transfer is complete, whichever happens first.<br>In automatic status-polling mode, this register contains the last data read from the flash memory (without masking).<br>Word, halfword, and byte accesses to this register are supported. In indirect write mode, a byte write adds 1 byte to the FIFO, a halfword write 2, and a word write 4. Similarly, in indirect read mode, a byte read removes 1 byte from the FIFO, a halfword read 2, and a word read 4.<br>Accesses in indirect mode must be aligned to the bottom of this register: a byte read must read DATA[7:0] and a halfword read must read DATA[15:0]. |

### POLL_STS_MASK_REG (PSMKR)
Address offset: 0x48
Reset value: 0x0000 0x0000

| Bits | Identifier | Description                                                                                                                                                                                                                                                        |
| ---- | ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 31:0 | MASK[31:0] | **Status mask**: Mask to be applied to the status bytes received in automatic status-polling mode.<br>Note: This bitfield can be written only when BUSY = 0.                                                                                                       |

### POLL_STS_MATCH_REG (PSMAR)
Address offset: 0x50
Reset value: 0x0000 0x0000

| Bits | Identifier  | Description                                                                                                                                    |
| ---- | ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| 31:0 | MATCH[31:0] | **Status match**: Value to be compared with the masked status register to get a match.<br>Note: This bitfield can be written only when BUSY = 0. |

### POLL_INTERVAL_REG (PIR)
Address offset: 0x58
Reset value: 0x0000 0x0000

| Bits | Identifier      | Description                                                                                                                         |
| ---- | --------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| 31:0 | INTERVAL[31:0]  | **Polling interval**: Number of CLK cycles between two reads during automatic status-polling phases.<br>Note: This bitfield can be written only when BUSY = 0. |

### LOW_POWER_TIMEOUT_REG (LPTR)
Address offset: 0x60
Reset value: 0x0000 0x0000

| Bits | Identifier     | Description                                                                                                                                                                                                         |
| ---- | -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 31:0 | TIMEOUT[31:0]  | **Timeout period**: Number of CLK cycles the QUADSPI waits after the FIFO becomes full until it raises NCS in memory-mapped mode.<br>Note: This bitfield can be written only when BUSY = 0.                          |

## Features Tested

\Begin{multicols}{2}
* Single/Quad SPI mode.
* indirect mode (All operations are performed using QSPI registers).
\End{multicols}

## Program Flow

### Initialization
1.  **Enable Peripheral**: Write to the `SystemConfig` register in the System Control block to enable the QSPI clock and interface (`qspi_enable = 1`).
2.  **Configure Flash Parameters (optional)**: Write to the `DEVICE_CONFIG_REG (DCR)` to set the flash memory size (`FSIZE`) and clock mode (`CKMODE`).
3.  **Enable Controller**: Write to `CONTROL_REG (CR)` to set the clock prescaler and enable the controller (`QSPI_ENABLE = 1`).

### Indirect Write Transaction
1.  **Set Data Length**: Write the number of bytes to be transferred to the `DATA_LENGTH_REG (DLR)`.
2.  **Configure Transaction**: Write to the `COMMN_CONFIG_REG (CCR)` to specify the instruction, address mode, data mode, and dummy cycles. Set `FMODE = 00` (Indirect Write).
3.  **Set Address**: Write the target flash address to the `ADDRESS_REG (AR)`. This prepares the controller for the start of the transaction.
4.  **Provide Data**: Write the data to be transmitted into the `DATA_REG (DR)`. For multiple words, ensure the FIFO has space by checking `FLEVEL` in `STATUS_REG`. For write transcation to start the fifo must be filled with minimum of 4 bytes of data.
5.  **Wait for Completion**: Monitor `STATUS_REG[1]` (`TCF` - Transfer Complete Flag). Once set, the transaction is finished.
6.  **Clear Flags**: Write `1` to `FLAG_CLEAR_REG[1]` (`CTCF`) to clear the transfer complete flag for the next operation.

**Example: Quad Page Program (Instruction 0x32)**
*   Target: Write 4 bytes to address `0x000000`.
*   `DLR = 0x00000003` (4 bytes).
*   `CCR = 0x03002532` (imode=1, admode=1, adsize=2, dmode=3, fmode=0, instr=0x32).
*   `AR = 0x00000000`.
*   `DR = 0xDEADBEEF`.

### Indirect Read Transaction
1.  **Set Data Length**: Write the number of bytes to be read to the `DATA_LENGTH_REG (DLR)`.
2.  **Configure Transaction**: Write to the `COMMN_CONFIG_REG (CCR)` with `FMODE = 01` (Indirect Read) and relevant phase modes.
3.  **Trigger Transaction**: Write the source flash address to the `ADDRESS_REG (AR)`. The controller will automatically start fetching data.
4.  **Read Data**: Monitor `STATUS_REG[13:8]` (`FLEVEL`) or `STATUS_REG[2]` (`FTF`). Read the received data from the `DATA_REG (DR)`.
5.  **Wrap Up**: Wait for `TCF` to be set, then clear the flag via `FLAG_CLEAR_REG`.

**Example: Quad Fast Read (Instruction 0xEB)**
*   Target: Read 4 bytes from address `0x001000`.
*   `DLR = 0x00000003` (4 bytes).
*   `CCR = 0x07182CEB` (imode=1, admode=3, adsize=2, dmode=3, fmode=1, dcyc=6, instr=0xEB).
*   `AR = 0x00001000`.
*   Read `DR` once `FTF` or `TCF` is set.
