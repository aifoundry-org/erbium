# Datasheet

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

## Errata:
There are errors in the JEDC 251C Specification. 
* The Profile2 Hyberbus bit map assigns A31:A3 to a 24 bit field instead of a 29 bit field. The upper 5 bits are marked as reserved. We follow the Cypress Hyperbus bitfield here and use the upper 5 bits to form the required 29 bit address address.
* In 251C-1 the Specification for QuadSPI defines a format for Quad SPI but does not use it. We are ignoring the format.
* 
# Overview.
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
| setRate                                 | 52h  | 0.G      | 1.A      | 1.A             |
| OTPRead                                 | 4Bh  |          |          |                 |
| OTPWrite                                | 42h  |          |          |                 |


SetRate command writes a tuple of 3 bytes, each byte specifies the rate for cmd, addr, data. the encoding is
 
S1=0, D1=1, S2=not Implemented, D2 =NotImplemented, S4=4, D4=5, S8=6, D8=7, HB=8

For Hyperbus mode all 3 bytes should be HB.


* SPI Memory access uses 4B addressing.
* SPI Register access uses 3B addressing.
* Some commands Commands marked 1.A  do not require an address field. e.g. Enter Pd, Exit PD, Reset Device.
* Hyperbus uses 5bAddressing + cmd
** Note **

* The 1.X commands follow the pattern of CMD-Ext, 4B Address, X cycles of latency, Data
* The 0.X commands do not have Ext, Spec allows #b or 4B address, we implement only 4B address.
* For Register Transaction the Data is 32 bit.
* For Memory Transaction Data is 64 bit.
* JEDEC has messed up the Quad Standard.
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
* Modes in SFDP Document
	* 1s-1s-4s
	* 1s-4s-4s
	* 1s-2s-2s
	* 1s-1s-2s
	* 1s-8s-8s
	* 1s-8d-8d
	* 4s-4s-4s
	* 4s-4d-4d
	* 1s-4d-4d
	* 1s-2d-2d
	* 1s-1d-1d
	* 2s-2s-2s
	* 8s-8s-8s
	* 8d-8d-8d
	* 0-4-4 (xip)
	* 0-8-8 (xip)


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

