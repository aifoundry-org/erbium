<!---
Markdown description for SystemRDL register map.

Don't override. Generated from: SCCR_Reg
  - ../../ip/xspi/systemrdl/sccr.rdl
-->

## SCCR_Reg address map

- Absolute Address: 0x0
- Base Offset: 0x0
- Size: 0x38

<p>Status and control Registers</p>

|Offset|   Identifier   |Name|
|------|----------------|----|
| 0x00 |       ID0      | id0|
| 0x08 |       ID1      | ID1|
| 0x10 |       CFG      |  — |
| 0x18 |   xspi_status  |  — |
| 0x20 |  xspi_control  |  — |
| 0x28 |   xspi_rates   |  — |
| 0x30 |interrupt_status|  — |

### ID0 register

- Absolute Address: 0x0
- Base Offset: 0x0
- Size: 0x8

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 3:0|  mgf_id  |  rw  | 0x2 |  — |
|15:4|  devid0  |  rw  | 0x0 |  — |

#### mgf_id field

<p>Manufacturer: TODO check how to obtain this number</p>

#### devid0 field

<p>DEVID0 TODO Use as suitable</p>

### ID1 register

- Absolute Address: 0x8
- Base Offset: 0x8
- Size: 0x8

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 3:0| dev_type |  rw  | 0x0 |  — |
|15:4|  devid1  |  rw  | 0x0 |  — |

#### dev_type field

<p>Device Type set to hyperram</p>

#### devid1 field

<p>TODO Use as appropriate</p>

### CFG register

- Absolute Address: 0x10
- Base Offset: 0x10
- Size: 0x8

| Bits|    Identifier    |Access|Reset|Name|
|-----|------------------|------|-----|----|
| 1:0 |    BurstLength   |  rw  | 0x2 |  — |
|  2  | HybridBurstEnable|   r  | 0x0 |  — |
|  3  |   FixedLatency   |   r  | 0x1 |  — |
| 7:4 |  InitialLatency  |  rw  | 0x8 |  — |
| 11:8|     Reserved     |   r  | 0x1 |  — |
|14:12|   DriveStrength  |   r  | 0x3 |  — |
|  15 |   DeepPowerDown  |  rw  | 0x0 |  — |
|  16 |    BurstEnable   |  rw  | 0x0 |  — |
|  17 |UltraDeepPowerDown|  rw  | 0x0 |  — |

#### BurstLength field

<p>Burst Length</p>

#### HybridBurstEnable field

<p>Burst Enable</p>

#### FixedLatency field

<p>Fixed Latency</p>

#### InitialLatency field

<p>Initial Latency.</p>

#### DriveStrength field

<p>Drive Strength.</p>

#### DeepPowerDown field

<p>Deep Power down, Not too deep, not too shallow</p>

#### BurstEnable field

<p>Enable bust access. Applicable only to memory access. Register access are one at a time</p>

#### UltraDeepPowerDown field

<p>Ultra Deep Power down.</p>

### xspi_status register

- Absolute Address: 0x18
- Base Offset: 0x18
- Size: 0x8

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 |    wip   |   r  | 0x0 |  — |

#### wip field

<p>write in progress; Valid only after a write mem transaction</p>

### xspi_control register

- Absolute Address: 0x20
- Base Offset: 0x20
- Size: 0x8

|Bits|   Identifier   |Access|Reset|Name|
|----|----------------|------|-----|----|
|  0 |  use_xspi_clk  |  rw  | 0x0 |  — |
|  1 |interrupt_enable|  rw  | 0x0 |  — |

#### use_xspi_clk field

<p>Use xspi clock as system clock</p>

#### interrupt_enable field

<p>Use xspi clock as system clock</p>

### xspi_rates register

- Absolute Address: 0x28
- Base Offset: 0x28
- Size: 0x8

| Bits|Identifier|Access|Reset|Name|
|-----|----------|------|-----|----|
| 7:0 | cmd_rate |  rw  | 0x0 |  — |
| 15:8| addr_rate|  rw  | 0x0 |  — |
|23:16| data_rate|  rw  | 0x0 |  — |

#### cmd_rate field

<p>CMD Rate</p>

#### addr_rate field

<p>CMD Rate</p>

#### data_rate field

<p>CMD Rate</p>

### interrupt_status register

- Absolute Address: 0x30
- Base Offset: 0x30
- Size: 0x8

|Bits|  Identifier  | Access|Reset|Name|
|----|--------------|-------|-----|----|
| 1:0|   axi_resp   |r, rclr| 0x0 |  — |
|  2 |read_underflow|r, rclr| 0x0 |  — |
|  3 |write_overflow|r, rclr| 0x0 |  — |

#### axi_resp field

<p>AXI Resp Error</p>

#### read_underflow field

<p>Read FIFO Underflow Error</p>

#### write_overflow field

<p>Write FIFO Overflow Error</p>
