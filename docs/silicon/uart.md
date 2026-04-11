# UART Datasheet

The UART module provides a two-wire asynchronous serial non-return-to-zero (NRZ) communication with RS-232 (RS-422/485) interface. Each UART module has transmit and receive buffers that can hold up to 16 entries. Data transfer rate can be modified by providing appropriate value to the UARTBAUD register.

**Required data rate = Internal clock frequency / (UARTBAUD * 16)**

The data transmission and reception starts with a start bit followed by data words whose length can be varied through UARTCHARSIZE in UARTCONTROL register which is followed by optional parity bit and stop bits. The parity can be Odd or Even and the parity can also be disabled through UARTPARITY bits in the UARTCONTROL register. The number of stop bits can also be varied through UARTSTOPBITS in the UARTCONTROL register. Delayed Transmit control is done by providing the required delay in the UARTTXDELAY register.

The value to be transmitted is written into the UARTTXDATA register and the value received is read from the UARTRXDATA register. UARTSTATUS register holds the UART status & UARTINTERRUPTEN register holds the interrupt enable for the various interrupt events. UARTRXTH register holds the receiver FIFO threshold value, when the RX FIFO level increases beyond the threshold, corresponding status bit will be set and when interrupt is enabled, interrupt will be raised. UART can be operated in full-duplex or half-duplex mode. The inputs to UART receiver and transmitter are double-buffered and each has its own separate enable and interrupt bits.

UART has three external pins - Transmitter data pin, Receiver data pin and Transmitter output enable pin.

## UART Registers

The original register IP sizes are variable for the Shakti use cases, and the data duplicates it across for the access size. Although logically 32-bit or less on the IP side, they are accessible as 64-bit values on the system bus.

| Register name | Offset address | IP Side Size | Accessible Size | Description                                          |
| ------------- | -------------- | ------------ | --------------- | ---------------------------------------------------- |
| BaudReg       | 0x00           | 16 bits      | 32 bits         | UART Baud Rate Register (Read and write)             |
| TxReg         | 0x08           | 32 bits      | 32 bits         | UART Transmitter Data Register (Write only)          |
| RxReg         | 0x10           | 32 bits      | 32 bits         | UART Receiver Data Register (Read Only)              |
| StatusReg     | 0x18           | 16 bits      | 32 bits         | UART Status Register (Read only)                     |
| DelayReg      | 0x20           | 16 bits      | 32 bits         | UART Transmitter Delay Register (Read and write)     |
| ControlReg    | 0x28           | 16 bits      | 32 bits         | UART Control Register (Read and write)               |
| InterruptEn   | 0x30           | 16 bits      | 32 bits         | UART Interrupt Enable Register (Read and write)      |
| IQC           | 0x38           | 8 bits       | 32 bits         | Input Qualification Control Register (Read and write)|
| Rx_Threshold  | 0x40           | 8 bits       | 32 bits         | UART Receiver Threshold Register (Read and write)    |

## Register Descriptions

### BaudReg
Address offset: 0x00
Reset value: 0x05

| Bits  | Identifier | Description                                                               |
| ----- | ---------- | ------------------------------------------------------------------------- |
| 15:0  | baud_value | **Baud Rate**: Calculated by Baud_value = (Clock Frequency) / (16 * Baudrate) |

### TxReg
Address offset: 0x08

| Bits  | Identifier | Description                                                                      |
| ----- | ---------- | -------------------------------------------------------------------------------- |
| 31:0  | data       | **TX Data**: The value to be transmitted is written into this register. |

### RxReg
Address offset: 0x10

| Bits  | Identifier | Description                                                            |
| ----- | ---------- | ---------------------------------------------------------------------- |
| 31:0  | data       | **RX Data**: The received value can be read from this register. |

### StatusReg
Address offset: 0x18

| Bits | Identifier         | Comments                                                                                            |
| ---- | ------------------ | --------------------------------------------------------------------------------------------------- |
| 8    | rx_fifo_threshold  | **RX FIFO Threshold**: Set if RX FIFO reaches the value set in the Rx_Threshold register.           |
| 7    | break_error        | **Break Error**: Set when the data and stop bits are both zero.                                     |
| 6    | frame_error        | **Frame Error**: Set when the stop bit is zero.                                                     |
| 5    | overrun_error      | **Overrun Error**: Set when additional data arrives while the RX FIFO is full.                      |
| 4    | parity_error       | **Parity Error**: Set when the receive character has incorrect parity.                              |
| 3    | rx_full            | **Receiver Full**: Set when the Receive Buffer is Full.                                             |
| 2    | rx_notEmpty        | **Receiver Not Empty**: Set when there is some data in the Receive Buffer.                          |
| 1    | tx_full            | **Transmitter Full**: Set when the transmit Buffer is full.                                         |
| 0    | tx_empty           | **Transmitter Empty**: Set when the Transmit Buffer is empty.                                       |

### DelayReg
Address offset: 0x20
Reset value: 0x0

| Bits  | Identifier    | Description                                                               |
| ----- | ------------- | ------------------------------------------------------------------------- |
| 15:0  | delay_control | **Transmit Delay Count**: Delayed Transmit control delay cycles.          |

### ControlReg
Address offset: 0x28

| Bits  | Identifier   | Comments                                                                                           |
| ----- | ------------ | -------------------------------------------------------------------------------------------------- |
| 10:5  | charsize     | **Character size**: Character size of data (max 32). Default is 8.                                 |
| 4:3   | parity       | **Parity selection**: 0 -> no parity, 1 -> odd parity, 2 -> even parity                            |
| 2:1   | stopbits     | **Stop bits**: 00 -> 1 stop bit, 01 -> 1.5 stop bits, 10 -> 2 stop bits                            |

### InterruptEn
Address offset: 0x30

| Bits | Identifier             | Comments                                   |
| ---- | ---------------------- | ------------------------------------------ |
| 8    | rx_fifo_threshold_en   | RX FIFO ~80% Full Interrupt Enable         |
| 7    | break_error_en         | Break Error Interrupt Enable               |
| 6    | frame_error_en         | Frame Error Interrupt Enable               |
| 5    | overrun_error_en       | Overrun Interrupt Enable                   |
| 4    | parity_error_en        | Parity Error Interrupt Enable              |
| 3    | rx_not_empty_en        | Receiver Not Empty Interrupt Enable        |
| 2    | rx_not_full_en         | Receiver Not Full Interrupt Enable         |
| 1    | tx_not_full_en         | Transmitter Not Full Interrupt Enable      |
| 0    | tx_done_en             | Transmission Done Interrupt Enable         |

### IQC
Address offset: 0x38

| Bits  | Identifier   | Description                                           |
| ----- | ------------ | ----------------------------------------------------- |
| 7:0   | qual_cycles  | **Input Qualification Cycles**: Filter cycles for IQC. |

### Rx_Threshold
Address offset: 0x40

| Bits  | Identifier | Description                                                                                                                                                                 |
| ----- | ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 7:0   | rx_level   | **RX Threshold Level**: Holds the receiver FIFO threshold value. When the RX FIFO level increases beyond the threshold, the corresponding status bit will be set.             |

## Program Flow

### Initialization
1.  **Global Enable**: Enable the UART peripheral in the `SystemConfig` register (set `uart_enable = 1`).
2.  **Baud Rate**: Set the `BaudReg` with the calculated divisor for the desired baud rate.
3.  **Line Coding**: Configure `ControlReg` for the required character size (e.g., 8-bit), parity (None/Odd/Even), and stop bits (1, 1.5, or 2).

### Data Transmission
1.  **Check Status**: Read `StatusReg` and verify that `tx_full` (bit 1) is `0` or `tx_empty` (bit 0) is `1`.
2.  **Write Data**: Write the 8-bit or 32-bit data word to the `TxReg`.
3.  **Wait for Done**: (Optional) Poll `StatusReg[0]` to ensure the transmitter has finished sending all bits if consecutive high-speed writes are not being used.

### Data Reception
1.  **Monitor Status**: Poll `StatusReg[2]` (`rx_notEmpty`) to check if data has been received and stored in the RX FIFO.
2.  **Read Data**: Read the received word from the `RxReg`.
3.  **Error Checking**: After reading, check `StatusReg` bits [7:4] for any `break_error`, `frame_error`, `overrun_error`, or `parity_error` that might have occurred during the reception.
