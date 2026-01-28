---
title: Erbium Pinout Description
overview: Pinout and Pinmuxing
author: Vijayvithal
copyright: Veevx Inc
---
# Signals

## Test Signals
| Signal      | Direction | Note                                                                    |
| ----        | :----:    | --------                                                                |
| ANATEST0    | INOUT     | Analog Test Pins                                                        |
| ANATEST1    | INOUT     | Analog Test Pins                                                        |
| TestMode    | INPUT     | Digital Testmode Enable. For internal use only. Tie to 0 in production. |
| OSC_CLK_OUT | OUTPUT    | Oscillator clk div N                                                    |



## xSPI Target Interface

| Port                       | Direction | Note                    |
| -----                      | :---:     | ------                  |
| XSPI_CS                    | INPUT     | Chip Select             |
| XSPI_DQ,                   | INPUT     | Data, Bidirectional     |
| XSPI_RWDS,                 | INOUT     | Data Strobe             |

## UART Target Interface

| Port   | Direction | Note         |
| ----   | :----:    | --------   |
| Tx     | OUTPUT    | Transmit Pin |
| Rx   | INPUT     | Receive Pin  |

## I2C Controller Interface
 Port | Direction | Note   |
| --- | :---:  | ----------                  |
| SCL | OUTPUT | Clock                       |
| SDA | INOUT  | Data. Needs external pullup |

## QSPI Controller Interface
| Port    | Direction | Note        |
| ---     | :---:     | --------- |
| CLK     | OUTPUT    | Clock       |
| DQ[3:0] | INOUT     | Data        |
| CS      | OUTPUT    | Chip select |

## GPIO Interface.

| Port       | Direction | Note                                             |
| -----      | :---:     | -------                                          |
| GPIO[10:0] | INOUT     | All GPIO Pins are muxed with other IO protocols. |

## JTAG Signals

| Port     | Direction | Note                               |
| ------   | :---:     | ------                             |
| TCK,     | INPUT     | Clock. Shared with xSPI            |
| TRSTn    | INPUT     | Reset. Active Low Shared with xSPI |
| JTAG_TDI | INPUT     |                                    |
| JTAG_TDO | OUTPUT    |                                    |
| JTAG_TMS | INPUT     |                                    |

## Pin Muxing

| A Port      | B Port    | A_SEL                                    |
| ------      | :---:     | ------                                   |
| OSC_CLK_OUT | GPIO[0]   | TestMode PIN                             |
| SCL         | GPIO[1]   | system_register.SystemConfig.i2c_enable  |
| SDA         | GPIO[2]   | system_register.SystemConfig.i2c_enable  |
| SPI_CS      | GPIO[3]   | system_register.SystemConfig.spi_enable  |
| SPI_CLK     | GPIO[4]   | system_register.SystemConfig.spi_enable  |
| SPI_DQ[1:0] | GPIO[6:5] | system_register.SystemConfig.spi_enable  |
| SPI_DQ[3:2] | GPIO[8:7] | system_register.SystemConfig.qspi_enable |
| UART_TX     | GPIO[9]   | system_register.SystemConfig.uart_enable |
| UART_RX     | GPIO[10]  | system_register.SystemConfig.uart_enable |

*Note* At boot SPI_enable=1 I2C_enable=0, QSPI_enable=0;
