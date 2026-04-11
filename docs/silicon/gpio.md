# GPIO Datasheet

The GPIO module provides 11 general-purpose bidirectional digital I/O pins (GPIO[10:0]). Each pin can be individually configured as an input or output via software registers. Pins designated as inputs can optionally generate an interrupt on a rising edge transition. All GPIO pins are shared through a hardware multiplexer with the on-chip peripherals (SPI, QSPI, I2C, UART) and are reclaimed by the respective peripheral when that peripheral is enabled.

## GPIO Registers

The GPIO registers are part of the System Registers block at base address **0x40000000**.

| Register name       | Offset address | Accessible Size | Description                                        |
| ------------------- | -------------- | --------------- | -------------------------------------------------- |
| GPIO_OE             | 0x78           | 32 bits         | GPIO Output Enable Register (Read and Write)       |
| GPIO_I              | 0x80           | 32 bits         | GPIO Input Register (Read Only)                    |
| GPIO_O              | 0x88           | 32 bits         | GPIO Output Register (Read and Write)              |
| GPIO_Interrupt_Enable | 0x90         | 32 bits         | GPIO Interrupt Enable Register (Read and Write)    |

## Register Descriptions

### GPIO_OE
Address offset: 0x78
Reset value: 0x000

| Bits | Identifier | Description                                                                  |
| ---- | ---------- | ---------------------------------------------------------------------------- |
| 10:0 | gpio_oe    | **Output Enable**: Write `1` to configure the corresponding pin as an output. Write `0` to configure as an input. One bit per GPIO pin. |

### GPIO_I
Address offset: 0x80
Reset value: 0x000

| Bits | Identifier | Description                                                                              |
| ---- | ---------- | ---------------------------------------------------------------------------------------- |
| 10:0 | gpio_i     | **Input Value**: For each pin configured as an input, reflects the current logic level on the pad. Read-only. |

### GPIO_O
Address offset: 0x88
Reset value: 0x000

| Bits | Identifier | Description                                                                                     |
| ---- | ---------- | ----------------------------------------------------------------------------------------------- |
| 10:0 | gpio_o     | **Output Value**: For each pin configured as an output, the value written here is driven onto the pad. |

### GPIO_Interrupt_Enable
Address offset: 0x90
Reset value: 0x000

| Bits | Identifier       | Description                                                                                                   |
| ---- | ---------------- | ------------------------------------------------------------------------------------------------------------- |
| 10:0 | gpio_interrupt_en | **Interrupt Enable**: For each input-mode pin, setting the corresponding bit to `1` enables an interrupt on a rising edge. The interrupt is aggregated into a single `gpio_interrupt` signal. |

## Pin Multiplexer

All 11 GPIO pins are shared with on-chip peripherals. When a peripheral is enabled in `SystemConfig`, the corresponding pins are claimed by the peripheral and are isolated from the GPIO registers (reads of `GPIO_I` will not capture values on those pins, and `GPIO_O` will not drive them).

| GPIO Pin(s) | Peripheral | Enable bit in SystemConfig |
| ----------- | ---------- | -------------------------- |
| GPIO[0]     | OSC_CLK_OUT| `TestMode` HW pin (hardware-controlled) |
| GPIO[1:2]   | I2C (SCL, SDA) | `i2c_enable` (bit 3)   |
| GPIO[3:6]   | SPI (CS, CLK, DQ[1:0]) | `spi_enable` (bit 4) |
| GPIO[7:8]   | QSPI (DQ[3:2]) | `qspi_enable` (bit 5)  |
| GPIO[9:10]  | UART (TX, RX) | `uart_enable` (bit 6)   |

> **Note:** SPI is enabled by default at reset (`spi_enable = 1`). To use GPIO[3:6] as general-purpose I/O, clear `spi_enable` in `SystemConfig` first. Write `SystemConfig = 0x0` to disable all peripherals and gain full GPIO access to all 11 pins.

## Program Flow

### Configure GPIO as Output

1. **Disable Peripheral Mux** (if needed): Write to `SystemConfig` to clear any peripheral enable bits that claim the target pins.
2. **Set Output Enable**: Write `1` to the corresponding bit(s) in `GPIO_OE` to configure the pins as outputs.
3. **Drive Output Value**: Write the desired value to `GPIO_O`. The value is immediately reflected on the pad.
4. **Verify**: Read back `GPIO_O` to confirm the written value.

### Configure GPIO as Input

1. **Disable Peripheral Mux** (if needed): Write to `SystemConfig` to clear any peripheral enable bits that claim the target pins.
2. **Set Input Mode**: Write `0` to the corresponding bit(s) in `GPIO_OE` to configure the pins as inputs (reset default).
3. **Read Input Value**: Read `GPIO_I`. The value at each bit reflects the current logic level on the corresponding pad.

### Enable GPIO Interrupt

1. **Configure as Input**: Ensure the target pin(s) have their `GPIO_OE` bit cleared (input mode).
2. **Enable Interrupt**: Write `1` to the corresponding bit(s) in `GPIO_Interrupt_Enable`.
3. **Detect Interrupt**: Monitor the `gpio_interrupt` signal (aggregated from all enabled pins). A rising edge on any enabled input pin asserts `gpio_interrupt`.
4. **Clear / Disable**: Write `0` to the corresponding bit in `GPIO_Interrupt_Enable` to disable further interrupts for that pin.

