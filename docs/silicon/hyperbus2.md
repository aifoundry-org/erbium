---
title: Erbium Technical Reference manual.
overview: Introduction to the chip
author: Vijayvithal
header-includes: |
  \usepackage{longtable,booktabs}
  \usepackage{adjustbox}
  \let\origtabular\tabular
  \let\endorigtabular\endtabular
  \renewenvironment{tabular}[1]{\adjustbox{max width=\textwidth}\origtabular{#1}}{\endorigtabular}
---
# xSPI Datasheet

\Begin{multicols}{2}

* xSPI bus interface supporting
	* 1S-1S-1S (SPI)
	* 4S-4D-4D
	* 4D-4D-4D
	* 8D-8D-8D (Octal profile 2)
	* 8D-8D-8D (Hyperbus)
* While other combinations are possible, only the above configurations are tested during verification. e.g.
	* 1S-4S-4S (Quad)
	* 4S-4S-4S (Quad)
* Boot configuration SPI, Quad, Octal, Hyperbus.
* Hardware Reset.
* Deep Powerdown mode
* Based on JESD251C, JESD215C-1, JESD216H

\End{multicols}

## Overview.
## Commands
### Hyperbus Mode

* 8D-8D-8D mode.

### SPI, Quad SPI, Octal SPI Mode

| Commands                                | Code | 1S-1S-1S | 4S-4D-4D | 8D-8D-8D(Octal) |
| ---                                     | ---  | ---      | ---      | ---             |
| Read SFDP                               | 5Ah  | 0.E      | 1.B      | 1.B             |
| Read (0L)                               | NA   | NA       | NA       | NA              |
| Read Register                           | 65   | 0.D      | 1.B      | 1.B             |
| Write Register                          | 71   | 0.K      | 1.D      | 1.D             |
| Enter Power Down                        | B9h  | 0.A      | 1.A      | 1.A             |
| Exit Power Down                         | ABh  | 0.A      | 1.A      | 1.A             |
| Reset Device and Enter default mode(1S) | 99h  | 0.A      | 1.A      | 1.A             |
| Read Memory                             | 0Bh  | 0.F      | 1.B      | 1.B             |
| Write Memory                            | 02h  | 0.K      | 1.D      | 1.D             |


**Note**

* The 1.X commands follow the pattern of CMD-Ext, 4B Address, X cycles of latency, Data
* The 0.X commands do not have Ext, Spec allows #b or 4B address, we implement only 4B address.
* For Register Transaction the Data is 32 bit.
* For Memory Transaction Data is 64 bit.
* JEDEC has messed up the QuadSPI Standard.
	* Section 4 specifies 1.X format and Section 5 Specifies 3.X format which is similar to 0.X formats.
	* We will go with 1.X format specified in Section 4.
* for 1S mode we will use the equivalent 0.X format,
* All address formats use 4B address.
* We will not implement read zero latency as that will not work with our pipeline. 
* Supported(Tested) Modes are (ref 6.10.18 of SFDP)
	* 1S-1S-1S
	* 8D-8D-8D
	* 8S-8S-8S
	* 4S-4D-4D
	* 4S-4S-4S
* Other Modes are possible, e.g. 4S-1S-4D (Why?) but not tested. If there is interest in an SPI mode other than the 3 listed above, please discuss.


## Not supported in Phase 1

| Mode                      | Plan          |
| ---                       | ---           |
| Wrapped bursts            | (Phase 2)     |
| XIP                       | (Phase 2)     |
| Write Enable              | Not Supported |
| Page/Sector Erase/Program | Not Supported |

## Octal Mode

We have a requirement of supporting the following devices in the production chip

1. SPI
2. QuadSPI
3. OctalSPI
4. Hyperbus

