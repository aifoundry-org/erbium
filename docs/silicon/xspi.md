# XSPI Datasheet
\Begin{multicols}{2}

* xSPI bus interface supporting
	* 1S-1S-1S (SPI)
	* 4S-4D-4D
	* 4D-4D-4D
	* 8D-8D-8D (Octal profile 1)
	* 8D-8D-8D (Hyperbus Octal Profile 2)
* Boot configuration SPI, Quad, Octal Profile 1, Hyperbus.
* Hardware Reset.
* Deep Powerdown mode
* Based on JESD251C, JESD215C-1, JESD216H

\End{multicols}

 
## Commands

### SPI, Quad SPI, Octal SPI Mode

| Commands                                | Code | 1S-1S-1S | 4S-4D-4D | 8D-8D-8D(Octal) |
| ---                                     | ---  | ---      | ---      | ---             |
| Read SFDP                               | 5Ah  | 0.E      | 1.B      | 1.B             |
| Read (0L)                               | NA   | NA       | NA       | NA              |
| Read Register                           | 65   | 0.F      | 1.B      | 1.B             |
| Write Register                          | 71   | 0.K      | 1.D      | 1.D             |
| Reset Device and Enter default mode(1S) | 99h  | 0.A      | 1.A      | 1.A             |
| Read Memory                             | 0Bh  | 0.F      | 1.B      | 1.B             |
| Write Memory                            | 02h  | 0.K      | 1.D      | 1.D             |
| setRate                                 | 52h  | 0.G      | 1.A      | 1.A             |

SetRate command writes a tuple of 3 bytes, each byte specifies the rate for cmd, addr, data. The encoding is
 
* S1=0,
* D1=1,
* S2=not Implemented,
* D2 =NotImplemented,
* S4=4,
* D4=5,
* S8=6,
* D8=7,
* HB=8

### Format 1S-1S-1S

The following formats are applicable to 1S-1S-1S mode of operation.

| Format | Ext            | Address Bytes  | Latency        | Read Txn       | Write Txn      | Note      |
| ---    | ---            | ---            | ---            | ---            | ---            | ---       |
| 0.A    | \faIcon{xmark} | \faIcon{xmark} | \faIcon{xmark} | \faIcon{xmark} | \faIcon{xmark} | CMD Only  |
| 0.E    | \faIcon{xmark} | 3              | \faIcon{check} | \faIcon{check} | \faIcon{xmark} | Read Reg  |
| 0.F    | \faIcon{xmark} | 4              | \faIcon{check} | \faIcon{check} | \faIcon{xmark} | Read Mem  |
| 0.G    | \faIcon{xmark} | \faIcon{xmark} | \faIcon{xmark} | \faIcon{xmark} | \faIcon{check} | setRate   |
| 0.J    | \faIcon{xmark} | 3              | \faIcon{xmark} | \faIcon{xmark} | \faIcon{check} | Write Reg |
| 0.K    | \faIcon{xmark} | 4              | \faIcon{xmark} | \faIcon{xmark} | \faIcon{check} | Write Mem |

### Format Other rates

* The following formats are applicable to 4S/4D/8S/8D  modes of operation.
* These modes require Ext and address is always 4.

| Format | Ext            | Address Bytes  | Latency        | Read Txn       | Write Txn      | Note          |
| ---    | ---            | ---            | ---            | ---            | ---            | ---           |
| 1.A    | \faIcon{check} | \faIcon{xmark} | \faIcon{xmark} | \faIcon{xmark} | \faIcon{xmark} | CMD Only      |
| 1.B    | \faIcon{check} | 4              | \faIcon{check} | \faIcon{check} | \faIcon{xmark} | Read Reg/Mem  |
| 1.D    | \faIcon{check} | 4              | \faIcon{xmark} | \faIcon{xmark} | \faIcon{check} | Write Reg/Mem |
| 1.G    | \faIcon{check} | \faIcon{xmark} | \faIcon{xmark} | \faIcon{xmark} | \faIcon{check} | setRate       |



## Default Mode.

The standard allows the datarate at reset to be something other than SPI(1S-1S-1S).
This can be controlled via the `default_mode` pin.

| Default Mode | Default Rate |
| ---          | ---          |
| 00           | Hyperbus     |
| 01           | Octal SPI    |
| 10           | Quad SPI     |
| 11           | SPI          |


For Hyperbus mode all 3 data bytes of setrate should be HB.


* SPI Memory access uses 4B addressing.
* SPI Register access uses 3B addressing.
* Some commands marked 1.A  do not require an address field. e.g. Enter Pd, Exit PD, Reset Device.

**Note**

* 1.G is a non standard format for set rate
* All writes have zero latency
* All Reads have latency cycles.
* 1s can have 3 or 4 byte address, use 3 byte for xspi-register and 4 byte for memory transactions
* non 1S only support 4 byte address.
* The 1.X commands follow the pattern of CMD-Ext, 4B Address, X cycles of latency, Data
* The 0.X commands do not have Ext
* For Register Transaction the Data is 32 bit.
* For Memory Transaction Data is multiple of 64 bit.
* Behavior when data width is not multiple of 64 (for mem) or 32 for reg is not defined.
* We will not implement read zero latency as that will not work with our pipeline. 
* Supported(Tested) Modes are (ref 6.10.18 of SFDP)
	
        * 1S-1S-1S
        * 8D-8D-8D
        * 8S-8S-8S
        * 4S-4D-4D
        * 4D-4D-4D
        * 4S-4S-4S


## Not supported in Phase 1

| Mode                      | Plan          |
| ---                       | ---           |
| Wrapped bursts            | (Phase 2)     |
| XIP                       | (Phase 2)     |
| Write Enable              | Not Supported |
| Page/Sector Erase/Program | Not Supported |


## Verification Requirement.

* Verify all supported mode.
* For spi, quadspi, octalspi  do a cross coverage of command, rates, latency, burst length, mem/reg, read/write
* Verify SFPD.
* Verify contents and behavior of register space.
* Ensure register space is accessible from both minion and xspi.
* verify hyperbus ensure cross coverage for latenxy and burst 
* Ensure all functionality is implemented.

## Booting.

* The device requires a few cycles of xspi clock to complete the reset process.
* Whenever the XSPI IP is resetted e.g. por, soft_reset etc. Run TCK for 8 cycles.
* If the xspi controller is not capable of running TCK without a transaction, issue a transaction with cmd=0 

## Error handling.

Errors are generated in cases where 

1. Host tries to access invalid memory space.
2. Host transfer does not complete due to network congestion.

`sccr.interrupt_status` register should be checked after each transaction for errors. The fields are as follows.

* `axi_resp`: The last known Error from the interconnect.

*  `axi_read_underflow`: Set when a read transaction is issued and read data is not available before end of latency period or the next word of a burst is not available at the time when the last bit of current burst is sent on wire.

* `axi_write_overflow`: Set when  the host issues a write burst transaction and the next word is presented before the current word is consumed by the interconnect.

Once set these bits remain set and can be cleared by reading the interrupt register.

If the `sccr.xspi_control.interrupt_enable` bit is set, a non zero value in the interrupt_status register can generate an interrupt to the minion. It is recommended to keep the interrupt disabled and let the host manage the exception. Only in case where the host cannot manage exceptions should minion step in.

Recommended host flow.

1. For write operations, Poll `sccr.xsip_status.wip` until the bit is cleared.
2. Check the value of `sccr.interrupt_status` if it is non zero initiate error recovery (e.g. retry the transaction at a lower data rate, increase latency, reduce burst size, reduce clock frequency, check the destination address etc.)
3. If it is zero, write to the mailbox to inform the minion the transaction is over and it can take control of the buffer.

## Errata:
There are errors in the JEDC 251C Specification. 

* The Profile2 Hyberbus bit map assigns A31:A3 to a 24 bit field instead of a 29 bit field. The upper 5 bits are marked as reserved. We follow the Cypress Hyperbus bitfield here and use the upper 5 bits to form the required 29 bit address address.
* In 251C-1 the Specification for QuadSPI defines a format for Quad SPI but does not use it. We are ignoring the format and using 1.X format for Quad mode.

## RWDS Behavior
| State            | DQ     | RWDS | RWDS_Val |
| ---              | ---    | ---  | ---      |
| Idle             | In     | Out  | 0        |
| Cmd              | In     | Out  | 0        |
| Ext              | In     | Out  | 0        |
| Latency          | In/Out | Out  | 0        |
| Latency to Read  | out    | out  | o        |
| Read             | out    | ou   | toggle   |
| Latency to Write | In     | In   | 0        |
| Write            | In     | In   | toggle   |
|                  |        |      |          |
| HB-CMD           | In     | Out  | 0        |
| HB-Address       | In     | Out  | 0        |
| HB-Latency-Write | In     | In   | 0        |
| HB-Latency-Read  | Out    | Out  | 0        |
| HB-Write         | In     | In   | Toggle   |
| HB-Read          | Out    | Out  | Toggle   |

