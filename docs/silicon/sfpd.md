<!---
Markdown description for SystemRDL register map.

Don't override. Generated from: SFDP_Reg
  - ../../ip/xspi/systemrdl/sfdp.rdl
-->

## SFDP_Reg address map

- Absolute Address: 0x0
- Base Offset: 0x0
- Size: 0xB3C

|Offset| Identifier|Name|
|------|-----------|----|
| 0x000|  reg6_2_1 |  — |
| 0x004|  reg6_2_2 |  — |
| 0x008| reg6_4__1 |  — |
| 0x00C| reg6_4__2 |  — |
| 0x010| reg6_7__1 |  — |
| 0x014| reg6_7__2 |  — |
| 0x018| reg6_9__1 |  — |
| 0x01C| reg6_9__2 |  — |
| 0x020| reg6_10__1|  — |
| 0x024| reg6_10__2|  — |
| 0x028| reg6_11__1|  — |
| 0x02C| reg6_11__2|  — |
| 0x030| reg6_17__1|  — |
| 0x034| reg6_17__2|  — |
| 0x400| reg_6_4_4 |  — |
| 0x404| reg_6_4_5 |  — |
| 0x408|  reg6_4_6 |  — |
| 0x40C|  reg6_4_7 |  — |
| 0x410|  reg6_4_8 |  — |
| 0x414|  reg6_4_9 |  — |
| 0x418| reg6_4_10 |  — |
| 0x41C| reg6_4_11 |  — |
| 0x420| reg6_4_12 |  — |
| 0x424| reg6_4_13 |  — |
| 0x428| reg6_4_14 |  — |
| 0x42C| reg6_4_15 |  — |
| 0x430| reg6_4_16 |  — |
| 0x434| reg6_4_17 |  — |
| 0x438| reg6_4_18 |  — |
| 0x43C| reg_6_4_19|  — |
| 0x440| reg_6_4_20|  — |
| 0x444| reg_6_4_21|  — |
| 0x448| reg_6_4_22|  — |
| 0x44C| reg_6_4_23|  — |
| 0x450| reg_6_4_24|  — |
| 0x454| reg_6_4_25|  — |
| 0x458| reg_6_4_26|  — |
| 0x700| reg_6_7_3 |  — |
| 0x704| reg_6_7_4 |  — |
| 0x900| reg_6_9_3 |  — |
| 0x904| reg_6_9_4 |  — |
| 0x908| reg_6_9_5 |  — |
| 0xA00| reg_6_10_3|  — |
| 0xA04| reg_6_10_4|  — |
| 0xA08| reg_6_10_5|  — |
| 0xA0C| reg_6_10_6|  — |
| 0xA10| reg_6_10_7|  — |
| 0xA14| reg_6_10_8|  — |
| 0xA18| reg_6_10_9|  — |
| 0xA1C|reg_6_10_10|  — |
| 0xA20|reg_6_10_11|  — |
| 0xA24|reg_6_10_12|  — |
| 0xA28|reg_6_10_13|  — |
| 0xA2C|reg_6_10_14|  — |
| 0xA30|reg_6_10_15|  — |
| 0xA34|reg_6_10_16|  — |
| 0xA38|reg_6_10_17|  — |
| 0xA3C|reg_6_10_18|  — |
| 0xA40|reg_6_10_19|  — |
| 0xA44|reg_6_10_20|  — |
| 0xA48|reg_6_10_21|  — |
| 0xA4C|reg_6_10_22|  — |
| 0xA50|reg_6_10_23|  — |
| 0xA54|reg_6_10_24|  — |
| 0xA58|reg_6_10_25|  — |
| 0xA5C|reg_6_10_26|  — |
| 0xA60|reg_6_10_27|  — |
| 0xA64|reg_6_10_28|  — |
| 0xA68|reg_6_10_29|  — |
| 0xA6C| reg_6_11_3|  — |
| 0xA70| reg_6_11_4|  — |
| 0xB00| reg_6_11_5|  — |
| 0xB04| reg_6_11_6|  — |
| 0xB08| reg_6_11_7|  — |
| 0xB0C| reg_6_11_8|  — |
| 0xB10| reg_6_11_9|  — |
| 0xB14|reg_6_11_10|  — |
| 0xB18|reg_6_11_11|  — |
| 0xB1C|reg_6_11_12|  — |
| 0xB20|reg_6_11_13|  — |
| 0xB24|reg_6_11_14|  — |
| 0xB28|reg_6_11_15|  — |
| 0xB2C| reg_6_17_3|  — |
| 0xB30| reg_6_17_4|  — |
| 0xB34| reg_6_17_5|  — |
| 0xB38| reg_6_17_6|  — |

### reg6_2_1 register

- Absolute Address: 0x0
- Base Offset: 0x0
- Size: 0x4

|Bits|Identifier|Access|   Reset  |Name|
|----|----------|------|----------|----|
|31:0| signature|   r  |0x50444653|  — |

#### signature field

<p>SFDP Signature</p>

### reg6_2_2 register

- Absolute Address: 0x4
- Base Offset: 0x4
- Size: 0x4

| Bits|   Identifier  |Access|Reset|Name|
|-----|---------------|------|-----|----|
| 7:0 |     minor     |   r  | 0xC |  — |
| 15:8|     major     |   r  | 0x1 |  — |
|23:16|     numHdr    |   r  | 0x6 |  — |
|31:24|access_protocol|   r  | 0xFA|  — |

#### minor field

<p>SFDP Version Minor</p>

#### major field

<p>SFDP Version Major</p>

#### numHdr field

<p>Num Parameter Header TBD</p>

#### access_protocol field

<p>TBD SFDP Access protocol</p>

### reg6_4__1 register

- Absolute Address: 0x8
- Base Offset: 0x8
- Size: 0x4

| Bits|Identifier|Access|Reset|Name|
|-----|----------|------|-----|----|
| 7:0 |    id    |   r  | 0x0 |  — |
| 15:8| minor_rev|   r  | 0x9 |  — |
|23:16| major_rev|   r  | 0x1 |  — |
|31:24|  tbl_len |   r  | 0x17|  — |

#### id field

<p>parameter id lsb</p>

#### minor_rev field

<p>minor rev</p>

#### major_rev field

<p>major_rev</p>

#### tbl_len field

<p>Tbl Len</p>

### reg6_4__2 register

- Absolute Address: 0xC
- Base Offset: 0xC
- Size: 0x4

| Bits|  Identifier |Access|Reset|Name|
|-----|-------------|------|-----|----|
| 23:0|param_tbl_ptr|   r  |0x400|  — |
|31:24| param_id_msb|   r  | 0xFF|  — |

#### param_tbl_ptr field

<p>Parameter Table Pointer TBD</p>

#### param_id_msb field

<p>Parameter Table ID MSB</p>

### reg6_7__1 register

- Absolute Address: 0x10
- Base Offset: 0x10
- Size: 0x4

| Bits|Identifier|Access|Reset|Name|
|-----|----------|------|-----|----|
| 7:0 |    id    |   r  | 0x84|  — |
| 15:8| minor_rev|   r  | 0x1 |  — |
|23:16| major_rev|   r  | 0x1 |  — |
|31:24|  tbl_len |   r  | 0x2 |  — |

#### id field

<p>parameter id lsb</p>

#### minor_rev field

<p>minor rev</p>

#### major_rev field

<p>major_rev</p>

#### tbl_len field

<p>Tbl Len</p>

### reg6_7__2 register

- Absolute Address: 0x14
- Base Offset: 0x14
- Size: 0x4

| Bits|  Identifier |Access|Reset|Name|
|-----|-------------|------|-----|----|
| 23:0|param_tbl_ptr|   r  |0x700|  — |
|31:24| param_id_msb|   r  | 0xFF|  — |

#### param_tbl_ptr field

<p>Parameter Table Pointer TBD</p>

#### param_id_msb field

<p>Parameter Table ID MSB</p>

### reg6_9__1 register

- Absolute Address: 0x18
- Base Offset: 0x18
- Size: 0x4

| Bits|Identifier|Access|Reset|Name|
|-----|----------|------|-----|----|
| 7:0 |    id    |   r  | 0x6 |  — |
| 15:8| minor_rev|   r  | 0x0 |  — |
|23:16| major_rev|   r  | 0x1 |  — |
|31:24|  tbl_len |   r  | 0x3 |  — |

#### id field

<p>parameter id lsb</p>

#### minor_rev field

<p>minor rev</p>

#### major_rev field

<p>major_rev</p>

#### tbl_len field

<p>Tbl Len</p>

### reg6_9__2 register

- Absolute Address: 0x1C
- Base Offset: 0x1C
- Size: 0x4

| Bits|  Identifier |Access|Reset|Name|
|-----|-------------|------|-----|----|
| 23:0|param_tbl_ptr|   r  |0x900|  — |
|31:24| param_id_msb|   r  | 0xFF|  — |

#### param_tbl_ptr field

<p>Parameter Table Pointer TBD</p>

#### param_id_msb field

<p>Parameter Table ID MSB</p>

### reg6_10__1 register

- Absolute Address: 0x20
- Base Offset: 0x20
- Size: 0x4

| Bits|Identifier|Access|Reset|Name|
|-----|----------|------|-----|----|
| 7:0 |    id    |   r  | 0x87|  — |
| 15:8| minor_rev|   r  | 0x1 |  — |
|23:16| major_rev|   r  | 0x1 |  — |
|31:24|  tbl_len |   r  | 0x1C|  — |

#### id field

<p>parameter id lsb</p>

#### minor_rev field

<p>minor rev</p>

#### major_rev field

<p>major_rev</p>

#### tbl_len field

<p>Tbl Len</p>

### reg6_10__2 register

- Absolute Address: 0x24
- Base Offset: 0x24
- Size: 0x4

| Bits|  Identifier |Access|Reset|Name|
|-----|-------------|------|-----|----|
| 23:0|param_tbl_ptr|   r  |0xA00|  — |
|31:24| param_id_msb|   r  | 0xFF|  — |

#### param_tbl_ptr field

<p>Parameter Table Pointer TBD</p>

#### param_id_msb field

<p>Parameter Table ID MSB</p>

### reg6_11__1 register

- Absolute Address: 0x28
- Base Offset: 0x28
- Size: 0x4

| Bits|Identifier|Access|Reset|Name|
|-----|----------|------|-----|----|
| 7:0 |    id    |   r  | 0x9 |  — |
| 15:8| minor_rev|   r  | 0x0 |  — |
|23:16| major_rev|   r  | 0x1 |  — |
|31:24|  tbl_len |   r  | 0xD |  — |

#### id field

<p>parameter id lsb</p>

#### minor_rev field

<p>minor rev</p>

#### major_rev field

<p>major_rev</p>

#### tbl_len field

<p>Tbl Len</p>

### reg6_11__2 register

- Absolute Address: 0x2C
- Base Offset: 0x2C
- Size: 0x4

| Bits|  Identifier |Access|Reset|Name|
|-----|-------------|------|-----|----|
| 23:0|param_tbl_ptr|   r  |0xB00|  — |
|31:24| param_id_msb|   r  | 0xFF|  — |

#### param_tbl_ptr field

<p>Parameter Table Pointer TBD</p>

#### param_id_msb field

<p>Parameter Table ID MSB</p>

### reg6_17__1 register

- Absolute Address: 0x30
- Base Offset: 0x30
- Size: 0x4

| Bits|Identifier|Access|Reset|Name|
|-----|----------|------|-----|----|
| 7:0 |    id    |   r  | 0xF |  — |
| 15:8| minor_rev|   r  | 0x1 |  — |
|23:16| major_rev|   r  | 0x1 |  — |
|31:24|  tbl_len |   r  | 0xA |  — |

#### id field

<p>parameter id lsb</p>

#### minor_rev field

<p>minor rev</p>

#### major_rev field

<p>major_rev</p>

#### tbl_len field

<p>Tbl Len</p>

### reg6_17__2 register

- Absolute Address: 0x34
- Base Offset: 0x34
- Size: 0x4

| Bits|  Identifier |Access| Reset|Name|
|-----|-------------|------|------|----|
| 23:0|param_tbl_ptr|   r  |0x1100|  — |
|31:24| param_id_msb|   r  | 0xFF |  — |

#### param_tbl_ptr field

<p>Parameter Table Pointer TBD</p>

#### param_id_msb field

<p>Parameter Table ID MSB</p>

### reg_6_4_4 register

- Absolute Address: 0x400
- Base Offset: 0x400
- Size: 0x4

| Bits|     Identifier    |Access|Reset|Name|
|-----|-------------------|------|-----|----|
| 1:0 |     erase_size    |   r  | 0x3 |  — |
|  2  | write_granularity |   r  | 0x0 |  — |
|  3  |always_volatile_csr|   r  | 0x1 |  — |
|  4  |   we_instruction  |   r  | 0x1 |  — |
| 7:5 |      unused1      |   r  | 0x7 |  — |
| 15:8|     erase_4kb     |   r  | 0xFF|  — |
|  16 |     fs_1s1s2s     |   r  | 0x0 |  — |
|18:17|     addrBytes     |   r  | 0x2 |  — |
|  19 |      dtr_mode     |   r  | 0x1 |  — |
|  20 |     fs_1s2s2s     |   r  | 0x0 |  — |
|  21 |     fs_1s4s4s     |   r  | 0x0 |  — |
|  22 |     fs_1s1s1s     |   r  | 0x0 |  — |
|31:23|      unused0      |   r  | 0xFF|  — |

#### erase_size field

<p>Block/Sector Erase size.</p>

#### write_granularity field

<p>Write Granularity (1byte).</p>

#### always_volatile_csr field

<p>Volatile Status Register Block Protect.</p>

#### we_instruction field

<p>Write Enable Instruction select for writing to volatile status reg.</p>

#### unused1 field

<p>Unused</p>

#### erase_4kb field

<p>Does not support 4KB Erase</p>

#### fs_1s1s2s field

<p>Does not support 1S-1S-2S Fast Read</p>

#### addrBytes field

<p>Address Bytes (4-Byte Only Addressing)</p>

#### dtr_mode field

<p>Supports DTR mode</p>

#### fs_1s2s2s field

<p>Does not support 1S-2S-2S Fast Read</p>

#### fs_1s4s4s field

<p>Does not support 1S-4S-4S Fast Read</p>

#### fs_1s1s1s field

<p>Does not support 1S-1S-4S Fast Read</p>

#### unused0 field

<p>Unused</p>

### reg_6_4_5 register

- Absolute Address: 0x404
- Base Offset: 0x404
- Size: 0x4

|Bits| Identifier|Access|  Reset |Name|
|----|-----------|------|--------|----|
|31:0|mem_density|   r  |0xFFFFFF|  — |

#### mem_density field

<p>memory Density(in bits)</p>

### reg6_4_6 register

- Absolute Address: 0x408
- Base Offset: 0x408
- Size: 0x4

| Bits|   Identifier   |Access|Reset|Name|
|-----|----------------|------|-----|----|
| 4:0 |waitstate_1s4s4s|   r  | 0x2 |  — |
| 7:5 |   mode_1s4s4s  |   r  | 0x0 |  — |
| 15:8| fr_inst_1s4s4s |   r  | 0xAB|  — |
|20:16|waitstate_1s1s4s|   r  | 0x2 |  — |
|23:21|   mode_1s1s4s  |   r  | 0x0 |  — |
|31:24| fr_inst_1s1s4s |   r  | 0xAA|  — |

#### waitstate_1s4s4s field

<p>1s-4s-4s fast read wait states</p>

#### mode_1s4s4s field

<p>1s-4s-4s fast read num mode clocks</p>

#### fr_inst_1s4s4s field

<p>1s-4s-4s fast read wait states</p>

#### waitstate_1s1s4s field

<p>1s-1s-4s fast read wait states</p>

#### mode_1s1s4s field

<p>1s-1s-4s fast read num mode clocks</p>

#### fr_inst_1s1s4s field

<p>1s-1s-4s fast read instruction</p>

### reg6_4_7 register

- Absolute Address: 0x40C
- Base Offset: 0x40C
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0| reserved |   r  | 0x0 |  — |

#### reserved field

<p>2S mode is not suppported. Reserved</p>

### reg6_4_8 register

- Absolute Address: 0x410
- Base Offset: 0x410
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 |  mode_2s |   r  | 0x0 |  — |
|  4 |  mode_4s |   r  | 0x1 |  — |

#### mode_2s field

<p>Supports 2S-2S-2S fast read mode(not supported)</p>

#### mode_4s field

<p>Supports 4S-4S-4S fast read mode</p>

### reg6_4_9 register

- Absolute Address: 0x414
- Base Offset: 0x414
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0| reserved |   r  | 0x0 |  — |

#### reserved field

<p>2S mode is not suppported. Reserved</p>

### reg6_4_10 register

- Absolute Address: 0x418
- Base Offset: 0x418
- Size: 0x4

| Bits|   Identifier   |Access|Reset|Name|
|-----|----------------|------|-----|----|
|20:16|waitstate_4s4s4s|   r  | 0x2 |  — |
|23:21|   mode_4s4s4s  |   r  | 0x0 |  — |
|31:24| fr_inst_4s4s4s |   r  | 0xAC|  — |

#### waitstate_4s4s4s field

<p>4s-4s-4s fast read wait states</p>

#### mode_4s4s4s field

<p>4s-4s-4s fast read num mode clocks</p>

#### fr_inst_4s4s4s field

<p>4s-4s-4s fast read instruction</p>

### reg6_4_11 register

- Absolute Address: 0x41C
- Base Offset: 0x41C
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0| reserved |   r  | 0x0 |  — |

#### reserved field

<p>Erase instruction 2,1 is not suppported. Reserved</p>

### reg6_4_12 register

- Absolute Address: 0x420
- Base Offset: 0x420
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0| reserved |   r  | 0x0 |  — |

#### reserved field

<p>Erase instruction 4,3 is not suppported. Reserved</p>

### reg6_4_13 register

- Absolute Address: 0x424
- Base Offset: 0x424
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0| reserved |   r  | 0x0 |  — |

#### reserved field

<p>Erase instruction is not suppported. Reserved</p>

### reg6_4_14 register

- Absolute Address: 0x428
- Base Offset: 0x428
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0| reserved |   r  | 0x0 |  — |

#### reserved field

<p>Erase/Program instruction is not suppported. Reserved</p>

### reg6_4_15 register

- Absolute Address: 0x42C
- Base Offset: 0x42C
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0| reserved |   r  | 0x0 |  — |

#### reserved field

<p>Suspend/Resume for Erase/Program instruction is not suppported. Reserved</p>

### reg6_4_16 register

- Absolute Address: 0x430
- Base Offset: 0x430
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0| reserved |   r  | 0x0 |  — |

#### reserved field

<p>Suspend/Resume for Erase/Program instruction is not suppported. Reserved</p>

### reg6_4_17 register

- Absolute Address: 0x434
- Base Offset: 0x434
- Size: 0x4

| Bits|        Identifier        |Access|Reset|Name|
|-----|--------------------------|------|-----|----|
| 1:0 |         reserved         |   r  | 0x0 |  — |
| 7:2 |       dev_busy_poll      |   r  | 0x0 |  — |
| 12:8|     exit_delay_count     |   r  | 0x2 |  — |
|14:13|     exit_delay_units     |   r  | 0x3 |  — |
|22:15| inst_deep_power_down_exit|   r  | 0xAE|  — |
|30:23|inst_deep_power_down_enter|   r  | 0xAD|  — |
|  31 |      deep_power_down     |   r  | 0x1 |  — |

#### reserved field

<p>Reserved</p>

#### dev_busy_poll field

<p>device busy poll (not supported)</p>

#### exit_delay_count field

<p>Exit Deep powerdown delay count</p>

#### exit_delay_units field

<p>Exit Deep powerdown delay units 64us</p>

#### inst_deep_power_down_exit field

<p>Exit Deep powerdown Instruction</p>

#### inst_deep_power_down_enter field

<p>Enter Deep powerdown Instruction</p>

#### deep_power_down field

<p>Deep powerdown is supported</p>

### reg6_4_18 register

- Absolute Address: 0x438
- Base Offset: 0x438
- Size: 0x4

| Bits|    Identifier   |Access|Reset|Name|
|-----|-----------------|------|-----|----|
| 3:0 | mode_disable444 |   r  | 0x0 |  — |
| 8:4 |  mode_enable444 |   r  | 0x0 |  — |
|  9  |xip_supported_044|   r  | 0x1 |  — |
|15:10|   mode_exit044  |   r  | 0x0 |  — |
|19:16|  mode_entry044  |   r  | 0x0 |  — |
|22:20|   quad_enable   |   r  | 0x0 |  — |
|  23 | hold_rst_support|   r  | 0x0 |  — |

#### mode_disable444 field

<p>4-4-4 Mode disable sequence TBD</p>

#### mode_enable444 field

<p>4-4-4 Mode enable sequence TBD</p>

#### xip_supported_044 field

<p>0-4-4 Mode supported (XIP)</p>

#### mode_exit044 field

<p>0-4-4 Mode exit method TBD</p>

#### mode_entry044 field

<p>0-4-4 Mode entry method TBD</p>

#### quad_enable field

<p>quad enable requirement</p>

#### hold_rst_support field

<p>hold/reset disable (not supported)</p>

### reg_6_4_19 register

- Absolute Address: 0x43C
- Base Offset: 0x43C
- Size: 0x4

| Bits|      Identifier     |Access|Reset|Name|
|-----|---------------------|------|-----|----|
| 6:0 |volatile_status_reg_1|   r  | 0x2 |  — |
| 13:8|  soft_reset_support |   r  | 0x0 |  — |
|23:14|  exit_4B_addressing |   r  | 0x0 |  — |
|31:24| enter_4B_addressing |   r  | 0x40|  — |

#### volatile_status_reg_1 field

<p>volatile register status1</p>

#### soft_reset_support field

<p>Soft reset instruction support (not supported)</p>

#### exit_4B_addressing field

<p>Exit 4 byte addressing TBD</p>

#### enter_4B_addressing field

<p>Enter 4 byte addressing;Always in $B mode</p>

### reg_6_4_20 register

- Absolute Address: 0x440
- Base Offset: 0x440
- Size: 0x4

| Bits|   Identifier   |Access|Reset|Name|
|-----|----------------|------|-----|----|
| 4:0 |waitstate_1s8s8s|   r  | 0x2 |  — |
| 7:5 |   mode_1s8s8s  |   r  | 0x0 |  — |
| 15:8| fr_inst_1s8s8s |   r  | 0xAB|  — |
|20:16|waitstate_1s1s8s|   r  | 0x2 |  — |
|23:21|   mode_1s1s8s  |   r  | 0x0 |  — |
|31:24| fr_inst_1s1s8s |   r  | 0xAF|  — |

#### waitstate_1s8s8s field

<p>1s-8s-8s fast read wait states</p>

#### mode_1s8s8s field

<p>1s-8s-8s fast read num mode clocks</p>

#### fr_inst_1s8s8s field

<p>1s-8s-8s fast read wait states</p>

#### waitstate_1s1s8s field

<p>1s-1s-8s fast read wait states</p>

#### mode_1s1s8s field

<p>1s-1s-8s fast read num mode clocks</p>

#### fr_inst_1s1s8s field

<p>1s-1s-8s fast read instruction</p>

### reg_6_4_21 register

- Absolute Address: 0x444
- Base Offset: 0x444
- Size: 0x4

| Bits|        Identifier        |Access|Reset|Name|
|-----|--------------------------|------|-----|----|
|22:18|      drive_strength      |   r  | 0x1 |  — |
|  23 |        jedec_reset       |   r  | 0x0 |  — |
|25:24| data_strobe_str_waveform |   r  | 0x0 |  — |
|  26 |data_strobe_support_4s4S4S|   r  | 0x0 |  — |
|  27 |data_strobe_support_4s4d4d|   r  | 0x0 |  — |
|30:29|          cmd_ext         |   r  | 0x0 |  — |
|  31 |       byte_order_8D      |   r  | 0x0 |  — |

#### drive_strength field

<p>Drive Strength TBD</p>

#### jedec_reset field

<p>JEDEC reset(not supported)</p>

#### data_strobe_str_waveform field

<p>Data strobe STR Waveform TBD</p>

#### data_strobe_support_4s4S4S field

<p>Data strobe support in QPI 4S-4S-4S</p>

#### data_strobe_support_4s4d4d field

<p>Data strobe support in QPI 4S-4D-4D</p>

#### cmd_ext field

<p>Octal DTR Command/Extension</p>

#### byte_order_8D field

<p>Byte order in 8D-8D-8D mode same as 1S-1S-1S mode</p>

### reg_6_4_22 register

- Absolute Address: 0x448
- Base Offset: 0x448
- Size: 0x4

| Bits|    Identifier    |Access|Reset|Name|
|-----|------------------|------|-----|----|
| 3:0 |disable_seq_8s8s8s|   r  | 0x1 |  — |
| 8:4 | enable_seq_8s8s8s|   r  | 0x2 |  — |
|  9  | xip_supported_088|   r  | 0x1 |  — |
|15:10|   xip_exit_088   |   r  | 0x4 |  — |
|19:16|   xip_entry_088  |   r  | 0x1 |  — |
|22:20| octal_enable_req |   r  | 0x1 |  — |

#### disable_seq_8s8s8s field

<p>8s8s8s mode disable seq</p>

#### enable_seq_8s8s8s field

<p>8s8s8s mode enable seq</p>

#### xip_supported_088 field

<p>0-8-8 XIP supported</p>

#### xip_exit_088 field

<p>0-8-8 Mode Exit method TBD</p>

#### xip_entry_088 field

<p>0-8-8 Mode Entry method</p>

#### octal_enable_req field

<p>octal_enable req</p>

### reg_6_4_23 register

- Absolute Address: 0x44C
- Base Offset: 0x44C
- Size: 0x4

| Bits|       Identifier      |Access|Reset|Name|
|-----|-----------------------|------|-----|----|
| 3:0 |max_4S_speed_without_ds|   r  | 0x8 |  — |
| 7:4 |  max_4S_speed_with_ds |   r  | 0x7 |  — |
| 11:8|max_4D_speed_without_ds|   r  | 0x8 |  — |
|15:12|  max_4D_speed_with_ds |   r  | 0x8 |  — |
|19:16|max_8S_speed_without_ds|   r  | 0x8 |  — |
|23:20|  max_8S_speed_with_ds |   r  | 0x8 |  — |
|27:24|max_8D_speed_without_ds|   r  | 0x8 |  — |
|31:28|  max_8D_speed_with_ds |   r  | 0x8 |  — |

#### max_4S_speed_without_ds field

<p>max 4S-4S-4S speed not using DS 200 Mhz</p>

#### max_4S_speed_with_ds field

<p>max 4S-4S-4S speed using DS 166Mhz</p>

#### max_4D_speed_without_ds field

<p>max 4S-4D-4D speed not using DS</p>

#### max_4D_speed_with_ds field

<p>max 4S-4D-4D speed using DS</p>

#### max_8S_speed_without_ds field

<p>max 8S speed not using DS</p>

#### max_8S_speed_with_ds field

<p>max 8S speed using DS 200Mhz</p>

#### max_8D_speed_without_ds field

<p>max 8D speed not using DS</p>

#### max_8D_speed_with_ds field

<p>max 8D speed using DS 200Mhz</p>

### reg_6_4_24 register

- Absolute Address: 0x450
- Base Offset: 0x450
- Size: 0x4

|Bits|   Identifier  |Access|Reset|Name|
|----|---------------|------|-----|----|
| 2:0|supports_4s4d4d|   r  | 0x1 |  — |
| 4:3|supports_1s4d4d|   r  | 0x1 |  — |
|  5 |supports_1s2d2d|   r  | 0x0 |  — |
|  6 |supports_1s1d1d|   r  | 0x0 |  — |

#### supports_4s4d4d field

<p>supports 4S-4D-4D Fast Read</p>

#### supports_1s4d4d field

<p>supports 1S-4D-4D Fast Read</p>

#### supports_1s2d2d field

<p>supports 1S-2D-2D Fast Read</p>

#### supports_1s1d1d field

<p>supports 1S-1D-1D Fast Read</p>

### reg_6_4_25 register

- Absolute Address: 0x454
- Base Offset: 0x454
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0| reserved |   r  | 0x0 |  — |

#### reserved field

<p>1S2D2D and 1S1D1D not supported</p>

### reg_6_4_26 register

- Absolute Address: 0x458
- Base Offset: 0x458
- Size: 0x4

| Bits|   Identifier   |Access|Reset|Name|
|-----|----------------|------|-----|----|
| 4:0 |waitstate_1s4d4d|   r  | 0x2 |  — |
| 7:5 |   mode_1s4d4d  |   r  | 0x0 |  — |
| 15:8| fr_inst_1s4d4d |   r  | 0xB1|  — |
|20:16|waitstate_4s4d4d|   r  | 0x2 |  — |
|23:21|   mode_4s4d4d  |   r  | 0x0 |  — |
|31:24| fr_inst_4s4d4d |   r  | 0xB0|  — |

#### waitstate_1s4d4d field

<p>1s-4d-4d fast read wait states</p>

#### mode_1s4d4d field

<p>1s-4d-4d fast read num mode clocks</p>

#### fr_inst_1s4d4d field

<p>1s-4d-4d fast read wait states</p>

#### waitstate_4s4d4d field

<p>4s-4d-4d fast read wait states</p>

#### mode_4s4d4d field

<p>4s-4d-4d fast read num mode clocks</p>

#### fr_inst_4s4d4d field

<p>4s-4d-4d fast read instruction</p>

### reg_6_7_3 register

- Absolute Address: 0x700
- Base Offset: 0x700
- Size: 0x4

| Bits|         Identifier        |Access|Reset|Name|
|-----|---------------------------|------|-----|----|
|  0  |       r_inst_1s1s1s       |   r  | 0x1 |  — |
|  1  |       fr_inst_1s1s1s      |   r  | 0x1 |  — |
| 3:2 |        reserved_2s        |   r  | 0x0 |  — |
|  4  |       fr_inst_1s1s4s      |   r  | 0x1 |  — |
|  5  |       fr_inst_1s4s4s      |   r  | 0x1 |  — |
| 12:6|       erase_reserved      |   r  | 0x0 |  — |
|  13 |       fr_inst_1s1d1d      |   r  | 0x0 |  — |
|  14 |       fr_inst_1s2d2d      |   r  | 0x0 |  — |
|  15 |       fr_inst_1s4d4d      |   r  | 0x0 |  — |
|19:16|      sector_reserved      |   r  | 0x0 |  — |
|  20 |       fr_inst_1s1s8s      |   r  | 0x0 |  — |
|  21 |       fr_inst_1s8s8s      |   r  | 0x0 |  — |
|  22 |       fr_inst_1s8d8d      |   r  | 0x0 |  — |
|  23 |page_program_support_1s1s8s|   r  | 0x0 |  — |
|  24 |page_program_support_1s8s8s|   r  | 0x0 |  — |

#### r_inst_1s1s1s field

<p>1s1s1s Read cmd inst 13h support(yes)</p>

#### fr_inst_1s1s1s field

<p>1s1s1s Fast Read cmd inst 0Ch support(yes)</p>

#### reserved_2s field

<p>2S not supported</p>

#### fr_inst_1s1s4s field

<p>1s1s4s fast Read cmd inst 34h support(yes)</p>

#### fr_inst_1s4s4s field

<p>1s4s4s fast Read cmd inst 3Eh support(yes)</p>

#### erase_reserved field

<p>Erase/Page cmds not supported</p>

#### fr_inst_1s1d1d field

<p>1s1d1d DTR Read cmd inst 0E support(no)</p>

#### fr_inst_1s2d2d field

<p>1s2d2d DTR Read cmd inst BEh support(no)</p>

#### fr_inst_1s4d4d field

<p>1s4d4d DTR Read cmd inst EEh support(no)</p>

#### sector_reserved field

<p>Sector cmds not supported</p>

#### fr_inst_1s1s8s field

<p>1s1s8s Fast Read cmd inst 7Ch support(no)</p>

#### fr_inst_1s8s8s field

<p>1s8s8s Fast Read cmd inst CCh support(no)</p>

#### fr_inst_1s8d8d field

<p>1s8d8d DTR Read cmd inst FDh support(no)</p>

#### page_program_support_1s1s8s field

<p>1s1s8s page program support (no)</p>

#### page_program_support_1s8s8s field

<p>1s8s8s page program support (no)</p>

### reg_6_7_4 register

- Absolute Address: 0x704
- Base Offset: 0x704
- Size: 0x4

|Bits|  Identifier  |Access|Reset|Name|
|----|--------------|------|-----|----|
|31:0|erase_reserved|   r  | 0x0 |  — |

#### erase_reserved field

<p>erase is not supported</p>

### reg_6_9_3 register

- Absolute Address: 0x900
- Base Offset: 0x900
- Size: 0x4

|Bits|      Identifier      |Access|Reset|Name|
|----|----------------------|------|-----|----|
| 4:0|       reserved       |   r  | 0x0 |  — |
|  5 |  enter_spi_supported |   r  | 0x1 |  — |
|14:6|     pgm_reserved     |   r  | 0x0 |  — |
| 15 |    deep_pd_support   |   r  | 0x1 |  — |
| 16 | cfg_reg_load_support |   r  | 0x1 |  — |
| 17 |  cfg_reg_read_suport |   r  | 0x1 |  — |
| 18 |  sts_reg_clr_support |   r  | 0x1 |  — |
| 19 | sts_reg_read_support |   r  | 0x1 |  — |
| 20 |     sren_support     |   r  | 0x0 |  — |
| 21 |     wren2_support    |   r  | 0x0 |  — |
| 22 |     wren1_support    |   r  | 0x0 |  — |
| 23 |   write_mem_linear   |   r  | 0x1 |  — |
| 24 |   write_mem_wrapped  |   r  | 0x0 |  — |
| 25 |   write_reg_linear   |   r  | 0x1 |  — |
| 26 |   write_reg_wrapped  |   r  | 0x0 |  — |
| 27 |    read_mem_linear   |   r  | 0x1 |  — |
| 28 |   read_mem_wrapped   |   r  | 0x0 |  — |
| 29 |    read_reg_linear   |   r  | 0x1 |  — |
| 30 |   read_reg_wrapped   |   r  | 0x0 |  — |
| 31 |xspi_profile_2_support|   r  | 0x1 |  — |

#### reserved field

<p>reserved</p>

#### enter_spi_supported field

<p>enter SPI supported</p>

#### pgm_reserved field

<p>program/erase not supported</p>

#### deep_pd_support field

<p>Deep Power down support(yes)</p>

#### cfg_reg_load_support field

<p>Cfg register load support(yes)</p>

#### cfg_reg_read_suport field

<p>Cfg register read support(yes)</p>

#### sts_reg_clr_support field

<p>Status register clear support(yes)</p>

#### sts_reg_read_support field

<p>Status register read support(yes)</p>

#### sren_support field

<p>SREN support(no)</p>

#### wren2_support field

<p>WREN2 support(no)</p>

#### wren1_support field

<p>WREN1 support(no)</p>

#### write_mem_linear field

<p>write memory linear support</p>

#### write_mem_wrapped field

<p>write memory wrapped support</p>

#### write_reg_linear field

<p>write register linear support</p>

#### write_reg_wrapped field

<p>write register wrapped support</p>

#### read_mem_linear field

<p>Read memory linear support</p>

#### read_mem_wrapped field

<p>Read memory wrapped support</p>

#### read_reg_linear field

<p>Read register linear support</p>

#### read_reg_wrapped field

<p>Read register wrapped support</p>

#### xspi_profile_2_support field

<p>xspi profile2 support</p>

### reg_6_9_4 register

- Absolute Address: 0x904
- Base Offset: 0x904
- Size: 0x4

|Bits|               Identifier              |Access|Reset|Name|
|----|---------------------------------------|------|-----|----|
| 6:2|cfg_bit_pattern_num_dymmy_cycl_required|   r  | 0x2 |  — |
|11:7|        num_dymmy_cycl_required        |   r  | 0x2 |  — |

#### cfg_bit_pattern_num_dymmy_cycl_required field

<p>200Mhz num cfg bit pattern to set num dummy cycl required TBD</p>

#### num_dymmy_cycl_required field

<p>200Mhz num dummy cycl required TBD</p>

### reg_6_9_5 register

- Absolute Address: 0x908
- Base Offset: 0x908
- Size: 0x4

| Bits|                 Identifier                |Access|Reset|Name|
|-----|-------------------------------------------|------|-----|----|
| 6:2 |cfg_bit_pattern_num_dymmy_cycl_required_100|   r  | 0x2 |  — |
| 11:7|        num_dymmy_cycl_required_100        |   r  | 0x2 |  — |
|16:12|cfg_bit_pattern_num_dymmy_cycl_required_133|   r  | 0x2 |  — |
|21:17|        num_dymmy_cycl_required_133        |   r  | 0x2 |  — |
|26:22|cfg_bit_pattern_num_dymmy_cycl_required_166|   r  | 0x2 |  — |
|31:27|        num_dymmy_cycl_required_166        |   r  | 0x2 |  — |

#### cfg_bit_pattern_num_dymmy_cycl_required_100 field

<p>100Mhz num cfg bit pattern to set num dummy cycl required TBD</p>

#### num_dymmy_cycl_required_100 field

<p>100Mhz num dummy cycl required TBD</p>

#### cfg_bit_pattern_num_dymmy_cycl_required_133 field

<p>133Mhz num cfg bit pattern to set num dummy cycl required TBD</p>

#### num_dymmy_cycl_required_133 field

<p>133Mhz num dummy cycl required TBD</p>

#### cfg_bit_pattern_num_dymmy_cycl_required_166 field

<p>166Mhz num cfg bit pattern to set num dummy cycl required TBD</p>

#### num_dymmy_cycl_required_166 field

<p>166Mhz num dummy cycl required TBD</p>

### reg_6_10_3 register

- Absolute Address: 0xA00
- Base Offset: 0xA00
- Size: 0x4

|Bits|   Identifier   |Access|Reset|Name|
|----|----------------|------|-----|----|
|31:0|volatile_address|   r  | 0x0 |  — |

#### volatile_address field

<p>Address offset for volatile registers TBD</p>

### reg_6_10_4 register

- Absolute Address: 0xA04
- Base Offset: 0xA04
- Size: 0x4

|Bits|     Identifier    |Access|Reset|Name|
|----|-------------------|------|-----|----|
|31:0|nonvolatile_address|   r  | 0x0 |  — |

#### nonvolatile_address field

<p>Address offset for non-volatile registers not supported</p>

### reg_6_10_5 register

- Absolute Address: 0xA08
- Base Offset: 0xA08
- Size: 0x4

| Bits|       Identifier      |Access|Reset|Name|
|-----|-----------------------|------|-----|----|
| 9:6 |num_dummy_cycles_8d8d8d|   r  | 0x0 |  — |
|13:10|num_dummy_cycles_8s8s8s|   r  | 0x0 |  — |
|17:14|num_dummy_cycles_4d4d4d|   r  | 0x0 |  — |
|21:18|num_dummy_cycles_4s4s4s|   r  | 0x0 |  — |
|25:22|num_dummy_cycles_2s2s2s|   r  | 0xF |  — |
|27:26|num_dummy_cycles_1s1s1s|   r  | 0x0 |  — |
|29:28|     num_addr_bytes    |   r  | 0x3 |  — |
|  30 |gen_reg_write_supported|   r  | 0x1 |  — |
|  31 | gen_reg_read_supported|   r  | 0x1 |  — |

#### num_dummy_cycles_8d8d8d field

<p>Number of dummy cycles for read in 8d-8d-8d mode</p>

#### num_dummy_cycles_8s8s8s field

<p>Number of dummy cycles for read in 8s-8s-8s mode</p>

#### num_dummy_cycles_4d4d4d field

<p>Number of dummy cycles for read in 4d-4d-4d mode</p>

#### num_dummy_cycles_4s4s4s field

<p>Number of dummy cycles for read in 4s-4s-4s mode</p>

#### num_dummy_cycles_2s2s2s field

<p>Number of dummy cycles for read in 2s-2s-2s mode</p>

#### num_dummy_cycles_1s1s1s field

<p>Number of dummy cycles for read in 1s-1s-1s mode</p>

#### num_addr_bytes field

<p>Number address bytes(32bit)</p>

#### gen_reg_write_supported field

<p>Generic Addressable Write Status/Control register command for volatile registers supported</p>

#### gen_reg_read_supported field

<p>Generic Addressable Read Status/Control register command for volatile registers supported</p>

### reg_6_10_6 register

- Absolute Address: 0xA0C
- Base Offset: 0xA0C
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0| reserved |   r  | 0x0 |  — |

#### reserved field

<p>No Non volatile registers</p>

### reg_6_10_7 register

- Absolute Address: 0xA10
- Base Offset: 0xA10
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0| reserved |   r  | 0x0 |  — |

#### reserved field

<p>No Write in progress bit TBD</p>

### reg_6_10_8 register

- Absolute Address: 0xA14
- Base Offset: 0xA14
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0| reserved |   r  | 0x0 |  — |

#### reserved field

<p>No Write enable bit TBD</p>

### reg_6_10_9 register

- Absolute Address: 0xA18
- Base Offset: 0xA18
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0| reserved |   r  | 0x0 |  — |

#### reserved field

<p>No program Error bit</p>

### reg_6_10_10 register

- Absolute Address: 0xA1C
- Base Offset: 0xA1C
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0| reserved |   r  | 0x0 |  — |

#### reserved field

<p>No Erase Error bit</p>

### reg_6_10_11 register

- Absolute Address: 0xA20
- Base Offset: 0xA20
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0| reserved |   r  | 0x0 |  — |

#### reserved field

<p>Variable dummy cycles not supported</p>

### reg_6_10_12 register

- Absolute Address: 0xA24
- Base Offset: 0xA24
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0| reserved |   r  | 0x0 |  — |

#### reserved field

<p>Variable dummy cycles (nvreg)not supported</p>

### reg_6_10_13 register

- Absolute Address: 0xA28
- Base Offset: 0xA28
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0| reserved |   r  | 0x0 |  — |

#### reserved field

<p>Variable dummy cycles not supported</p>

### reg_6_10_14 register

- Absolute Address: 0xA2C
- Base Offset: 0xA2C
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0| reserved |   r  | 0x0 |  — |

#### reserved field

<p>Variable dummy cycles not supported</p>

### reg_6_10_15 register

- Absolute Address: 0xA30
- Base Offset: 0xA30
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0| reserved |   r  | 0x0 |  — |

#### reserved field

<p>Variable dummy cycles not supported</p>

### reg_6_10_16 register

- Absolute Address: 0xA34
- Base Offset: 0xA34
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0| reserved |   r  | 0x0 |  — |

#### reserved field

<p>QPI mode not supported TBD</p>

### reg_6_10_17 register

- Absolute Address: 0xA38
- Base Offset: 0xA38
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0| reserved |   r  | 0x0 |  — |

#### reserved field

<p>QPI mode not supported TBD</p>

### reg_6_10_18 register

- Absolute Address: 0xA3C
- Base Offset: 0xA3C
- Size: 0x4

| Bits|       Identifier      |Access|Reset|Name|
|-----|-----------------------|------|-----|----|
|23:16|       reg_offset      |   r  | 0x0 |  — |
|26:24|        bit_loc        |   r  | 0x0 |  — |
|  27 |local_addr_in_last_byte|   r  | 0x0 |  — |
|  28 |      addressable      |   r  | 0x1 |  — |
|  30 |        polarity       |   r  | 0x0 |  — |
|  31 |   octal_mode_enable   |   r  | 0x1 |  — |

#### reg_offset field

<p>Reg Offset</p>

#### bit_loc field

<p>Bit location in reg (TBD)</p>

#### local_addr_in_last_byte field

<p>local address in last byte of address(yes)</p>

#### addressable field

<p>Bit is addressable</p>

#### polarity field

<p>Octal mode Enable polarity</p>

#### octal_mode_enable field

<p>STR/DDR Octal mode Enable Volatile</p>

### reg_6_10_19 register

- Absolute Address: 0xA40
- Base Offset: 0xA40
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0| reserved |   r  | 0x0 |  — |

#### reserved field

<p>Octal mode Enable non Volatile (not supported)</p>

### reg_6_10_20 register

- Absolute Address: 0xA44
- Base Offset: 0xA44
- Size: 0x4

| Bits|        Identifier       |Access|Reset|Name|
|-----|-------------------------|------|-----|----|
|23:16|        reg_offset       |   r  | 0x0 |  — |
|26:24|         bit_loc         |   r  | 0x0 |  — |
|  27 | local_addr_in_last_byte |   r  | 0x0 |  — |
|  28 |       addressable       |   r  | 0x1 |  — |
|  30 |         polarity        |   r  | 0x0 |  — |
|  31 |ddr_mode_select_available|   r  | 0x1 |  — |

#### reg_offset field

<p>Reg Offset</p>

#### bit_loc field

<p>Bit location in reg (TBD)</p>

#### local_addr_in_last_byte field

<p>local address in last byte of address(yes)</p>

#### addressable field

<p>Bit is addressable</p>

#### polarity field

<p>polarity</p>

#### ddr_mode_select_available field

<p>SDR/DDR mode select volatile (supported)</p>

### reg_6_10_21 register

- Absolute Address: 0xA48
- Base Offset: 0xA48
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0| reserved |   r  | 0x0 |  — |

#### reserved field

<p>SDR/DDR non Volatile (not supported)</p>

### reg_6_10_22 register

- Absolute Address: 0xA4C
- Base Offset: 0xA4C
- Size: 0x4

| Bits|       Identifier      |Access|Reset|Name|
|-----|-----------------------|------|-----|----|
|23:16|       reg_offset      |   r  | 0x0 |  — |
|26:24|        bit_loc        |   r  | 0x0 |  — |
|  27 |local_addr_in_last_byte|   r  | 0x0 |  — |
|  28 |      addressable      |   r  | 0x1 |  — |
|  30 |        polarity       |   r  | 0x0 |  — |
|  31 |   octal_mode_enable   |   r  | 0x1 |  — |

#### reg_offset field

<p>Reg Offset</p>

#### bit_loc field

<p>Bit location in reg (TBD)</p>

#### local_addr_in_last_byte field

<p>local address in last byte of address(yes)</p>

#### addressable field

<p>Bit is addressable</p>

#### polarity field

<p>Octal mode Enable polarity</p>

#### octal_mode_enable field

<p>STR Octal mode Enable Volatile Dup of 6_10_18? TBD</p>

### reg_6_10_23 register

- Absolute Address: 0xA50
- Base Offset: 0xA50
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0| reserved |   r  | 0x0 |  — |

#### reserved field

<p>SDR/DDR non Volatile (not supported)</p>

### reg_6_10_24 register

- Absolute Address: 0xA54
- Base Offset: 0xA54
- Size: 0x4

| Bits|       Identifier      |Access|Reset|Name|
|-----|-----------------------|------|-----|----|
|23:16|       reg_offset      |   r  | 0x0 |  — |
|26:24|        bit_loc        |   r  | 0x0 |  — |
|  27 |local_addr_in_last_byte|   r  | 0x0 |  — |
|  28 |      addressable      |   r  | 0x1 |  — |
|  30 |        polarity       |   r  | 0x0 |  — |
|  31 |   octal_mode_enable   |   r  | 0x1 |  — |

#### reg_offset field

<p>Reg Offset</p>

#### bit_loc field

<p>Bit location in reg (TBD)</p>

#### local_addr_in_last_byte field

<p>local address in last byte of address(yes)</p>

#### addressable field

<p>Bit is addressable</p>

#### polarity field

<p>Octal mode Enable polarity</p>

#### octal_mode_enable field

<p>DTR Octal mode Enable Volatile Dup of 6_10_18? TBD</p>

### reg_6_10_25 register

- Absolute Address: 0xA58
- Base Offset: 0xA58
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0| reserved |   r  | 0x0 |  — |

#### reserved field

<p>SDR/DDR non Volatile (not supported)</p>

### reg_6_10_26 register

- Absolute Address: 0xA5C
- Base Offset: 0xA5C
- Size: 0x4

| Bits|        Identifier       |Access|Reset|Name|
|-----|-------------------------|------|-----|----|
|23:16|        reg_offset       |   r  | 0x0 |  — |
|26:24|         bit_loc         |   r  | 0x0 |  — |
|  27 | local_addr_in_last_byte |   r  | 0x0 |  — |
|  28 |       addressable       |   r  | 0x1 |  — |
|  30 |         polarity        |   r  | 0x0 |  — |
|  31 |ddr_mode_select_available|   r  | 0x1 |  — |

#### reg_offset field

<p>Reg Offset</p>

#### bit_loc field

<p>Bit location in reg (TBD)</p>

#### local_addr_in_last_byte field

<p>local address in last byte of address(yes)</p>

#### addressable field

<p>Bit is addressable</p>

#### polarity field

<p>polarity</p>

#### ddr_mode_select_available field

<p>Deep power down select volatile (supported)</p>

### reg_6_10_27 register

- Absolute Address: 0xA60
- Base Offset: 0xA60
- Size: 0x4

| Bits|        Identifier       |Access|Reset|Name|
|-----|-------------------------|------|-----|----|
|23:16|        reg_offset       |   r  | 0x0 |  — |
|26:24|         bit_loc         |   r  | 0x0 |  — |
|  27 | local_addr_in_last_byte |   r  | 0x0 |  — |
|  28 |       addressable       |   r  | 0x1 |  — |
|  30 |         polarity        |   r  | 0x0 |  — |
|  31 |ddr_mode_select_available|   r  | 0x1 |  — |

#### reg_offset field

<p>Reg Offset</p>

#### bit_loc field

<p>Bit location in reg (TBD)</p>

#### local_addr_in_last_byte field

<p>local address in last byte of address(yes)</p>

#### addressable field

<p>Bit is addressable</p>

#### polarity field

<p>polarity</p>

#### ddr_mode_select_available field

<p>Ultra Deep power down select volatile (supported)</p>

### reg_6_10_28 register

- Absolute Address: 0xA64
- Base Offset: 0xA64
- Size: 0x4

| Bits|       Identifier      |Access|Reset|Name|
|-----|-----------------------|------|-----|----|
|23:16|       reg_offset      |   r  | 0x0 |  — |
|26:24|        bit_loc        |   r  | 0x0 |  — |
|  27 |local_addr_in_last_byte|   r  | 0x0 |  — |
|  28 |      addressable      |   r  | 0x1 |  — |
|31:30|        num_bits       |   r  | 0x3 |  — |

#### reg_offset field

<p>Reg Offset</p>

#### bit_loc field

<p>Bit location in reg (TBD)</p>

#### local_addr_in_last_byte field

<p>local address in last byte of address(yes)</p>

#### addressable field

<p>Bit is addressable</p>

#### num_bits field

<p>Output drive strength numbits(supported)</p>

### reg_6_10_29 register

- Absolute Address: 0xA68
- Base Offset: 0xA68
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0| reserved |   r  | 0x0 |  — |

#### reserved field

<p>non Volatile (not supported)</p>

### reg_6_11_3 register

- Absolute Address: 0xA6C
- Base Offset: 0xA6C
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0|  offset  |   r  | 0x0 |  — |

#### offset field

<p>Volatile reg offset TBD</p>

### reg_6_11_4 register

- Absolute Address: 0xA70
- Base Offset: 0xA70
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0|  offset  |   r  | 0x0 |  — |

#### offset field

<p>non Volatile reg offset TBD</p>

### reg_6_11_5 register

- Absolute Address: 0xB00
- Base Offset: 0xB00
- Size: 0x4

| Bits|        Identifier       |Access|Reset|Name|
|-----|-------------------------|------|-----|----|
| 2:0 |         reserved        |   r  | 0x0 |  — |
| 10:3|       wip_address       |   r  | 0x0 |  — |
|14:11|     wip_bit_location    |   r  | 0x0 |  — |
|  15 |wip_address_byte_location|   r  | 0x0 |  — |
|  16 |       wip_polarity      |   r  | 0x0 |  — |
|  17 |      wip_supported      |   r  | 0x0 |  — |
|22:18|dummy_cycles_non_volative|   r  | 0x0 |  — |
|27:23|  dummy_cycles_volative  |   r  | 0x0 |  — |
|29:28|      address_bytes      |   r  | 0x0 |  — |
|  30 |      write_ctrl_sts     |   r  | 0x1 |  — |
|  31 |      read_ctrl_sts      |   r  | 0x1 |  — |

#### reserved field

<p>Reserved</p>

#### wip_address field

<p>Address of WIP Bit(not supported)</p>

#### wip_bit_location field

<p>Bit location of WIP Bit(not supported)</p>

#### wip_address_byte_location field

<p>Local address of WIP Bit(not supported)</p>

#### wip_polarity field

<p>WIP Polarity(not supported)</p>

#### wip_supported field

<p>WIP (Device busy bit) (not supported)</p>

#### dummy_cycles_non_volative field

<p>Dummy cycles for non-volatile reg read TBD</p>

#### dummy_cycles_volative field

<p>Dummy cycles for volatile reg read TBD</p>

#### address_bytes field

<p>Address Bytes(6 bytes)</p>

#### write_ctrl_sts field

<p>Generic addressable write ctrl/sts registers(yes)</p>

#### read_ctrl_sts field

<p>Generic addressable read ctrl/sts registers(yes)</p>

### reg_6_11_6 register

- Absolute Address: 0xB04
- Base Offset: 0xB04
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0|  p_error |   r  | 0x0 |  — |

#### p_error field

<p>Program Error (Not Implemented)</p>

### reg_6_11_7 register

- Absolute Address: 0xB08
- Base Offset: 0xB08
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0|  e_error |   r  | 0x0 |  — |

#### e_error field

<p>Erase Error (Not Implemented)</p>

### reg_6_11_8 register

- Absolute Address: 0xB0C
- Base Offset: 0xB0C
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|30:0| reserved |   r  | 0x0 |  — |
| 31 | supported|   r  | 0x0 |  — |

#### reserved field

<p>Reserved</p>

#### supported field

<p>Variable number of dummy cycles volatile reg(Not Supported)</p>

### reg_6_11_9 register

- Absolute Address: 0xB10
- Base Offset: 0xB10
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|30:0| reserved |   r  | 0x0 |  — |
| 31 | supported|   r  | 0x0 |  — |

#### reserved field

<p>Reserved</p>

#### supported field

<p>Variable number of dummy cycles non-volatile reg(Not Supported)</p>

### reg_6_11_10 register

- Absolute Address: 0xB14
- Base Offset: 0xB14
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|30:0| reserved |   r  | 0x0 |  — |
| 31 | supported|   r  | 0x0 |  — |

#### reserved field

<p>Reserved</p>

#### supported field

<p>Variable number of dummy cycles Bit pattern(Not Supported)</p>

### reg_6_11_11 register

- Absolute Address: 0xB18
- Base Offset: 0xB18
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|30:0| reserved |   r  | 0x0 |  — |
| 31 | supported|   r  | 0x0 |  — |

#### reserved field

<p>Reserved</p>

#### supported field

<p>Variable number of dummy cycles Bit pattern(Not Supported)</p>

### reg_6_11_12 register

- Absolute Address: 0xB1C
- Base Offset: 0xB1C
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|30:0| reserved |   r  | 0x0 |  — |
| 31 | supported|   r  | 0x0 |  — |

#### reserved field

<p>Reserved</p>

#### supported field

<p>Variable number of dummy cycles Bit pattern(Not Supported)</p>

### reg_6_11_13 register

- Absolute Address: 0xB20
- Base Offset: 0xB20
- Size: 0x4

| Bits|       Identifier      |Access|Reset|Name|
|-----|-----------------------|------|-----|----|
|24:17|          addr         |   r  | 0x0 |  — |
|28:25|    msb_bit_location   |   r  | 0x0 |  — |
|  29 | addr_not_in_last_byte |   r  | 0x0 |  — |
|31:30|drive_strength_num_bits|   r  | 0x3 |  — |

#### addr field

<p>Address of register TBD (typo in spec?)</p>

#### msb_bit_location field

<p>Bit location of MSB Bit TBD</p>

#### addr_not_in_last_byte field

<p>addr in last_byte TBD</p>

#### drive_strength_num_bits field

<p>output drive strength num_bits (volatile)</p>

### reg_6_11_14 register

- Absolute Address: 0xB24
- Base Offset: 0xB24
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | reserved |   r  | 0x0 |  — |

#### reserved field

<p>output drive strength nv (not implemented)</p>

### reg_6_11_15 register

- Absolute Address: 0xB28
- Base Offset: 0xB28
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 |    tbd   |   r  | 0x0 |  — |

#### tbd field

<p>output drive strength bit pattern TBD</p>

### reg_6_17_3 register

- Absolute Address: 0xB2C
- Base Offset: 0xB2C
- Size: 0x4

| Bits|       Identifier      |Access|Reset|Name|
|-----|-----------------------|------|-----|----|
|  4  |        gram_spi       |   r  | 0x1 |  — |
|  5  |     address_shift     |   r  | 0x0 |  — |
| 11:8|   md_address_format   |   r  | 0x4 |  — |
|19:16|md_address_write_access|   r  | 0x0 |  — |
|23:20| md_address_read_access|   r  | 0x0 |  — |
|27:24|     md_active_die     |   r  | 0x0 |  — |
|31:28|   md_address_offset   |   r  | 0x0 |  — |

#### gram_spi field

<p>Gram SPI Mode TBD</p>

#### address_shift field

<p>Address Shift TBD</p>

#### md_address_format field

<p>Multi-Die Addressformat TBD</p>

#### md_address_write_access field

<p>Multi-Die Addressable reg read access TBD</p>

#### md_address_read_access field

<p>Multi-Die Addressable reg read access TBD</p>

#### md_active_die field

<p>Active-Die Selection for Multi Die Package TBD</p>

#### md_address_offset field

<p>Multi-Die Address offset for Addressable Register TBD</p>

### reg_6_17_4 register

- Absolute Address: 0xB30
- Base Offset: 0xB30
- Size: 0x4

| Bits|      Identifier     |Access|Reset|Name|
|-----|---------------------|------|-----|----|
| 7:0 |     write_opcode    |   r  | 0x71|  — |
| 15:8|     read_opcode     |   r  | 0x65|  — |
|20:16|     dummy_cycles    |   r  | 0x8 |  — |
|23:21|dummy_cycles_override|   r  | 0x0 |  — |
|27:24|     write_enable    |   r  | 0x0 |  — |
|31:28| volatile_addr_offset|   r  | 0x0 |  — |

#### write_opcode field

<p>Write Opcode</p>

#### read_opcode field

<p>Read Opcode</p>

#### dummy_cycles field

<p>Dummy cycles</p>

#### dummy_cycles_override field

<p>Dummy cycles override</p>

#### write_enable field

<p>Write enable</p>

#### volatile_addr_offset field

<p>Volatile address offset TBD</p>

### reg_6_17_5 register

- Absolute Address: 0xB34
- Base Offset: 0xB34
- Size: 0x4

| Bits|      Identifier     |Access|Reset|Name|
|-----|---------------------|------|-----|----|
| 7:0 |     write_opcode    |   r  | 0x71|  — |
| 15:8|     read_opcode     |   r  | 0x65|  — |
|20:16|     dummy_cycles    |   r  | 0x8 |  — |
|23:21|dummy_cycles_override|   r  | 0x0 |  — |
|27:24|     write_enable    |   r  | 0x0 |  — |
|31:28| volatile_addr_offset|   r  | 0x0 |  — |

#### write_opcode field

<p>Write Opcode</p>

#### read_opcode field

<p>Read Opcode</p>

#### dummy_cycles field

<p>Dummy cycles</p>

#### dummy_cycles_override field

<p>Dummy cycles override</p>

#### write_enable field

<p>Write enable</p>

#### volatile_addr_offset field

<p>Volatile address offset TBD</p>

### reg_6_17_6 register

- Absolute Address: 0xB38
- Base Offset: 0xB38
- Size: 0x4

| Bits|  Identifier  |Access|Reset|Name|
|-----|--------------|------|-----|----|
| 3:0 | statreg_bit0 |   r  | 0x1 |  — |
| 11:8|statreg_access|   r  | 0x1 |  — |
|14:12| dummy_cycles |   r  | 0x2 |  — |
|23:16|     aux1     |   r  | 0x0 |  — |
|31:24|     aux2     |   r  | 0x5 |  — |

#### statreg_bit0 field

<p>SR bit 0 is busy flag</p>

#### statreg_access field

<p>SR Access</p>

#### dummy_cycles field

<p>Dymmy Cycles</p>

#### aux1 field

<p>Aux 1 TBD SR address</p>

#### aux2 field

<p>Aux 2</p>
