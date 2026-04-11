<!---
Markdown description for SystemRDL register map.

Don't override. Generated from: ErbiumxSPI_MemoryMap
  - top_xspi_mm.rdl
-->

# ErbiumxSPI_MemoryMap address map

- Absolute Address: 0x0
- Base Offset: 0x0
- Size: 0xFE016000

|  Offset  |   Identifier   |              Name             |
|----------|----------------|-------------------------------|
|0x00000000|      mram      |              MRAM             |
|0x40000000|system_registers|        System Registers       |
|0x40001000| mram_registers |AXI-to-MRAM Bridge Register Map|
|0x40002000|  i2c_registers |               —               |
|0x40003000| qspi_registers |         QSPI Registers        |
|0x40004000| uart_registers |         UART Registers        |
|0x40008000|     ROMRAM     |               —               |
|0x80000000|  cpu_registers |       ESR Map of Erbium       |
|0xA0000000|      plic      |               —               |
|0xFE000000|   nic_config   |               —               |

## mram memory

- Absolute Address: 0x0
- Base Offset: 0x0
- Size: 0x1000000

No supported members.


## system_registers address map

- Absolute Address: 0x40000000
- Base Offset: 0x40000000
- Size: 0xC4

<p>Register Controlling System Behavior</p>

|Offset|      Identifier     |           Name           |
|------|---------------------|--------------------------|
| 0x00 |       Version       |             —            |
| 0x08 |     SystemConfig    |             —            |
| 0x10 |    watchdog_count   |             —            |
| 0x18 |       Watchdog      |             —            |
| 0x20 |     SysInterrupt    |             —            |
| 0x28 |      SoftReset      |             —            |
| 0x30 |      ResetCause     |             —            |
| 0x38 |    PowerDomainReq   |             —            |
| 0x40 |    PowerDomainAck   |             —            |
| 0x48 |      PowerGood      |             —            |
| 0x50 |     PowerStatus     |             —            |
| 0x58 |       SpinLock      |             —            |
| 0x60 |       ChipMode      |             —            |
| 0x68 |       Mailbox0      |             —            |
| 0x70 |       Mailbox1      |             —            |
| 0x78 |       GPIO_OE       |             —            |
| 0x80 |        GPIO_I       |             —            |
| 0x88 |        GPIO_O       |             —            |
| 0x90 |GPIO_Interrupt_Enable|             —            |
| 0x98 |       ring_osc      |  Ring Oscillator Control |
| 0xA0 |     cpu_divider     |             —            |
| 0xA8 |    system_divider   |             —            |
| 0xB0 |    periph_divider   |             —            |
| 0xB8 |     tsense_ctrl     |Temperature Sensor Control|
| 0xC0 |    tsense_status    | Temperature Sensor Status|

### Version register

- Absolute Address: 0x40000000
- Base Offset: 0x0
- Size: 0x4

<p>Device identifier, used by software to identify the device family (chipid) variant, and bugfix version</p>

| Bits|Identifier|Access| Reset|Name|
|-----|----------|------|------|----|
| 7:0 |  respin  |   r  |  0x0 |  — |
| 15:8| variation|   r  |  0x0 |  — |
|31:16|  chipid  |   r  |0xEB68|  — |

### SystemConfig register

- Absolute Address: 0x40000008
- Base Offset: 0x8
- Size: 0x4

<p>System configuration fields. use to enable/disable various features</p>

|Bits|     Identifier     |Access|Reset|Name|
|----|--------------------|------|-----|----|
|  0 |sys_interrupt_enable|  rw  | 0x0 |  — |
|  1 | mram_startup_bypass|  rw  | 0x0 |  — |
|  2 |    wdog_disable    |  rw  | 0x1 |  — |
|  3 |     i2c_enable     |  rw  | 0x0 |  — |
|  4 |     spi_enable     |  rw  | 0x1 |  — |
|  5 |     qspi_enable    |  rw  | 0x0 |  — |
|  6 |     uart_enable    |  rw  | 0x0 |  — |
|  7 |   osc_out_enable   |  rw  | 0x0 |  — |

#### sys_interrupt_enable field

<p>reg interrupt:Writing to this bit generates an interrupt.</p>

#### mram_startup_bypass field

<p>connected to mram_startup_bypass of mram_wrapper</p>

#### wdog_disable field

<p>Watchdog Disable</p>

#### i2c_enable field

<p>I2C Enable</p>

#### spi_enable field

<p>SPI Enable</p>

#### qspi_enable field

<p>QSPI Enable</p>

#### uart_enable field

<p>UART Enable</p>

#### osc_out_enable field

<p>OSC_Out Enable</p>

### watchdog_count register

- Absolute Address: 0x40000010
- Base Offset: 0x10
- Size: 0x4

<p>The watchdog detects 'hang' conditions and resets the system. This feature is disabled by default. Clear <code>cpu_config.wdog_disable</code> to enable this. Once enabled, S/W should write to <code>Watchdog.kick</code> to reset the <code>WATCHDOG_COUNT.count</code> field. If the count reaches 0, it triggers a system reset.</p>

|Bits|  Identifier  |Access| Reset|Name|
|----|--------------|------|------|----|
|31:0|watchdog_count|  rw  |0xFFFF|  — |

#### watchdog_count field

<p>When the watchdog timer is enabled it counts down from this value</p>

### Watchdog register

- Absolute Address: 0x40000018
- Base Offset: 0x18
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  7 |   kick   |  rw  | 0x0 |  — |

#### kick field

<p>Resets the watchdog timer, cpu needs to regularly write to this bit to aviod a watchdog timeout based reset of the device</p>

### SysInterrupt register

- Absolute Address: 0x40000020
- Base Offset: 0x20
- Size: 0x4

|Bits|  Identifier  | Access |Reset|Name|
|----|--------------|--------|-----|----|
|  0 |   interrupt  |rw, rclr| 0x0 |  — |
|  1 |gpio_interrupt| r, rclr| 0x0 |  — |

#### interrupt field

<p>Write to this bit to generate an interrupt. Clear on read</p>

#### gpio_interrupt field

<p>GPIO In Interrupt. Clear on read</p>

### SoftReset register

- Absolute Address: 0x40000028
- Base Offset: 0x28
- Size: 0x4

|Bits|  Identifier  |Access|Reset|Name|
|----|--------------|------|-----|----|
|  0 |  soft_reset  |  rw  | 0x0 |  — |
|  1 |cpu_warm_reset|  rw  | 0x0 |  — |
|  2 |  mram_rst_b  |  rw  | 0x1 |  — |
|  3 |cpu_soft_reset|  rw  | 0x0 |  — |

#### soft_reset field

<p>System Soft Reset, Active High</p>

#### cpu_warm_reset field

<p>CPU Warm Reset, Active High</p>

#### mram_rst_b field

<p>MRAM Resetn, Active Low</p>

#### cpu_soft_reset field

<p>CPU cold Reset, Self clearing Active High</p>

### ResetCause register

- Absolute Address: 0x40000030
- Base Offset: 0x30
- Size: 0x4

<p>This register reports the cause of reset. There are multiple reset sources.
* Power on Reset,
* Brownout Reset, and
    * Various S/W reset requests. These clear on read bits capture the reset cause since the last read
    <strong>Note</strong> if the por bit is set ignore the other cause registers, they will have random values until the first read.</p>

|Bits|    Identifier   |Access|Reset|Name|
|----|-----------------|------|-----|----|
|  0 |       por       |   r  |  —  |  — |
|  1 |watchdog_timedout|   r  |  —  |  — |
|  2 |   sysreset_req  |   r  |  —  |  — |
|  3 |     brownout    |   r  |  —  |  — |
|  4 |    softreset    |   r  |  —  |  — |
|  5 |  cpu_warm_reset |   r  |  —  |  — |

#### por field

<p>System POR was toggled</p>

#### watchdog_timedout field

<p>Watchdog was enabled and CPU failed to clear the watchdog timer</p>

#### sysreset_req field

<p>NA. CPU detected an architecture level lockup and requested  a system reset</p>

#### brownout field

<p>The brownout detector triggered a reset</p>

#### softreset field

<p>The soft reset bit was written to</p>

#### cpu_warm_reset field

<p>NA. The cpu reset bit was written to</p>

### PowerDomainReq register

- Absolute Address: 0x40000038
- Base Offset: 0x38
- Size: 0x4

<p>Writing to PD fields initiates the shutdown of the corresponding power domain. A shutdown request is sent to the domain, This domain waits until all outstanding transactions are completed and then generates a corresponding ack signal. Once the ack signal is generated the power controller will turn off power to that domain.</p>

|Bits|    Identifier   |Access|Reset|Name|
|----|-----------------|------|-----|----|
|  0 |      cpu_pd     |  rw  | 0x0 |  — |
|  1 |cpu_rom_powerdown|  rw  | 0x0 |  — |
|  2 |cpu_ram_powerdown|  rw  | 0x0 |  — |
|  3 |    chiplet_pd   |  rw  | 0x0 |  — |
|  4 |     mram_pd     |  rw  | 0x0 |  — |
|  5 | system_poweroff |  rw  | 0x0 |  — |
|  6 |     xspi_pd     |  rw  | 0x0 |  — |
|15:8|    minion_pd    |  rw  | 0x0 |  — |
| 16 |  mram_dsleep_en |  rw  | 0x0 |  — |
| 17 |   cpu_sleep_en  |  rw  | 0x0 |  — |

#### cpu_pd field

<p>Poweroff the CPU Domain</p>

#### cpu_rom_powerdown field

<p>Powerdown the boot ROM</p>

#### cpu_ram_powerdown field

<p>Powerdown the CPU ram. this puts the ram in deepsleep mode</p>

#### chiplet_pd field

<p>Not used; chiplet power domain is controlled via the mode bits</p>

#### mram_pd field

<p>Power down for MRAM digital logic and MRAM domain. When set to 1, this powers off
the domain; setting to 0 powers it on.</p>

#### system_poweroff field

<p>Power off the chip. Only wakeup logic is powered on</p>

#### xspi_pd field

<p>Not used; hyperbus power domain is controlled via the mode bits.</p>

#### minion_pd field

<p>Minion PowerDown Req</p>

#### mram_dsleep_en field

<p>Connects directly to the MRAM's main power switch, bypassing the digital domain's
power switch. When set to 1, the MRAM is in deep sleep; setting to 0 powers the
MRAM on.</p>

#### cpu_sleep_en field

<p>currently not used. In future this will be used for CPU sleep management.</p>

### PowerDomainAck register

- Absolute Address: 0x40000040
- Base Offset: 0x40
- Size: 0x4

<p>This mirrors the Ack signal generated in response to power down request.</p>

|Bits|   Identifier  |Access|Reset|Name|
|----|---------------|------|-----|----|
|  0 |   cpu_pd_ack  |   r  | 0x0 |  — |
|  1 |  sram_pd_ack  |   r  | 0x0 |  — |
|  3 | chiplet_pd_ack|   r  | 0x0 |  — |
|  4 |  mram_pd_ack  |   r  | 0x0 |  — |
|  5 | system_pd_ack |   r  | 0x0 |  — |
|  6 |hyperbus_pd_ack|   r  | 0x0 |  — |
|15:8| minion_pd_ack |   r  | 0x0 |  — |

#### cpu_pd_ack field

<p>pd ack for cpu</p>

#### sram_pd_ack field

<p>Not used: pd ack for TCM</p>

#### chiplet_pd_ack field

<p>Not used: pd ack for chiplet</p>

#### mram_pd_ack field

<p>pd ack for mram</p>

#### system_pd_ack field

<p>pd ack for system</p>

#### hyperbus_pd_ack field

<p>Not used: pd ack for hy perbus</p>

#### minion_pd_ack field

<p>Minion PowerDown Req</p>

### PowerGood register

- Absolute Address: 0x40000048
- Base Offset: 0x48
- Size: 0x4

<p>When a power domain is switched on, it takes time for the voltage to stabalize, this time is process dependent. The default value is sufficiently large to account for all variations.</p>

|Bits|Identifier|Access| Reset |Name|
|----|----------|------|-------|----|
|20:0|  counter |  rw  |0xFFFFF|  — |

#### counter field

<p>Counter for powerGood</p>

### PowerStatus register

- Absolute Address: 0x40000050
- Base Offset: 0x50
- Size: 0x4

<p>Status</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 3:0| reserved |   r  | 0x0 |  — |

#### reserved field

<p>Asserted when MRAM is powered on/reset until internal setup is done.</p>

### SpinLock register

- Absolute Address: 0x40000058
- Base Offset: 0x58
- Size: 0x4

<p>initially locked=0, A read on this register will set the lock bit.
<strong>Usage:</strong>
1. Read this field. If you get a value of zero you got the lock. Else a different processing element acquired the lock. Poll at fixed intervals(dont spam) until you get the lock.
2. If you acquired the lock, Once you have finished interacting with the locked resource write 0 to this register to release the lock.</p>

|Bits|Identifier| Access |Reset|Name|
|----|----------|--------|-----|----|
|  0 |   lock   |rw, rset| 0x0 |  — |

### ChipMode register

- Absolute Address: 0x40000060
- Base Offset: 0x60
- Size: 0x4

|Bits|  Identifier |Access|Reset|Name|
|----|-------------|------|-----|----|
| 1:0|  chip_mode  |   r  |  —  |  — |
|  2 |  ifc_width  |   r  |  —  |  — |
| 4:3|   bootload  |  rw  | 0x0 |  — |
| 6:5|load_external|  rw  | 0x0 |  — |

#### chip_mode field

<p>The mode in which chip is working, hyperbus, axi,ahb,gci</p>

#### ifc_width field

<p>If chip is axi/ahb mode datawidth</p>

#### bootload field

<p>Jump to 00:no Jump, 01:TCM,10:MRAM</p>

#### load_external field

<p>Jump to 00:no load, 01:Load TCM via Chiplet,10:Load MRAM via Chiplet</p>

### Mailbox0 register

- Absolute Address: 0x40000068
- Base Offset: 0x68
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0|   mbox0  |  rw  | 0x0 |  — |

#### mbox0 field

<p>Mailbox0</p>

### Mailbox1 register

- Absolute Address: 0x40000070
- Base Offset: 0x70
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0|   mbox1  |  rw  | 0x0 |  — |

#### mbox1 field

<p>Mailbox1</p>

### GPIO_OE register

- Absolute Address: 0x40000078
- Base Offset: 0x78
- Size: 0x4

<p>Gpio Output enable.
Write 1 to this bit to set the GPIO register in output mode.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|10:0|  gpio_oe |  rw  | 0x0 |  — |

#### gpio_oe field

<p>Gpio output enable</p>

### GPIO_I register

- Absolute Address: 0x40000080
- Base Offset: 0x80
- Size: 0x4

<p>Gpio Input
For each bit in input mode this register captures the input value.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|10:0|  gpio_i  |   r  | 0x0 |  — |

#### gpio_i field

<p>Gpio input</p>

### GPIO_O register

- Absolute Address: 0x40000088
- Base Offset: 0x88
- Size: 0x4

<p>Gpio Output
For each bit in output mode the content of the corresponding bit in this register is reflected on the GPIO Pin</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|10:0|  gpio_o  |  rw  | 0x0 |  — |

#### gpio_o field

<p>Gpio input</p>

### GPIO_Interrupt_Enable register

- Absolute Address: 0x40000090
- Base Offset: 0x90
- Size: 0x4

<p>Gpio Interrupt Enable
For each bit in input mode if the input signal toggles and the content of the corresponding bit in this register is 1, then a GPIO interrupt is raised.</p>

|Bits|    Identifier   |Access|Reset|Name|
|----|-----------------|------|-----|----|
|10:0|gpio_interrupt_en|  rw  | 0x0 |  — |

#### gpio_interrupt_en field

<p>Gpio input</p>

### ring_osc register

- Absolute Address: 0x40000098
- Base Offset: 0x98
- Size: 0x4

<p>Controls the ring oscillator (ring_osc) input pins.
In normal mode (dbg_en=0), only en, divby2_sel, and trm are active.
In debug mode (dbg_en=1), the dbg_* fields independently gate the
analog bias block (anachip) and the oscillator core (rochip).</p>

|Bits|  Identifier  |Access|Reset|Name|
|----|--------------|------|-----|----|
|  0 |      en      |  rw  | 0x1 |  — |
|  1 |  divby2_sel  |  rw  | 0x1 |  — |
| 6:2|      trm     |  rw  | 0x1F|  — |
|  7 |    dbg_en    |  rw  | 0x0 |  — |
|  8 |dbg_anachip_en|  rw  | 0x0 |  — |
|  9 | dbg_rohcip_en|  rw  | 0x0 |  — |
| 10 | dbg_sah_en_b |  rw  | 0x0 |  — |

#### en field

<p>Master oscillator enable. Drive high to power up both the
analog bias block (anachip) and the ring oscillator core
(rochip). Has no effect when dbg_en is asserted.</p>

#### divby2_sel field

<p>Divide-by-2 frequency select.
0: Full-speed range (899 MHz to 1.608 GHz, set by trm).
1: Half-speed range (449 MHz to 794 MHz, set by trm).</p>

#### trm field

<p>Frequency trim code. Selects the oscillator output frequency
within the range determined by divby2_sel.
0x00 = fastest (1.608 GHz or 794 MHz).
0x1F = slowest (899 MHz or 449 MHz).
Frequency decreases linearly with increasing trim value.</p>

#### dbg_en field

<p>Debug override enable. When asserted, the en input is ignored
and dbg_anachip_en and dbg_rohcip_en independently control
the analog bias block and oscillator core respectively.
dbg_sah_en_b also becomes active.
0: Normal mode -- en controls both blocks.
1: Debug mode  -- dbg_* fields control each block separately.</p>

#### dbg_anachip_en field

<p>Debug enable for the analog bias block (anachip).
Only active when dbg_en=1.
When asserted with dbg_en=1, powers up the anachip and
drives h1_mnvdd09_g high, which is required for the
oscillator core to run.
When deasserted, h1_mnvdd09_g is held low and the
oscillator core cannot oscillate regardless of dbg_rohcip_en.</p>

#### dbg_rohcip_en field

<p>Debug enable for the ring oscillator core (rochip).
Only active when dbg_en=1.
When asserted with dbg_en=1 and dbg_anachip_en=1, the
oscillator core is enabled and clk will toggle.
When deasserted, the oscillator core is disabled and clk
is held low regardless of dbg_anachip_en.</p>

#### dbg_sah_en_b field

<p>Debug SAH enable (active low). Only active when dbg_en=1.
Selects the anachip operating mode:
0: Normal SAH operation  (anachip mode 3'b100, h1=1).
1: Test mode, high power (anachip mode 3'b101, h1=1).
In both cases h1_mnvdd09_g remains high when dbg_anachip_en=1;
this bit selects the internal anachip bias configuration only.</p>

### cpu_divider register

- Absolute Address: 0x400000A0
- Base Offset: 0xA0
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 3:0|   count  |  rw  | 0xF |  — |
|  4 |div_enable|  rw  | 0x1 |  — |

#### count field

<p>clock divider. output clk is 2 x count</p>

#### div_enable field

<p>Enable clk divider</p>

### system_divider register

- Absolute Address: 0x400000A8
- Base Offset: 0xA8
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 3:0|   count  |  rw  | 0xF |  — |
|  4 |div_enable|  rw  | 0x1 |  — |

#### count field

<p>clock divider. output clk is 2 x count</p>

#### div_enable field

<p>Enable clk divider</p>

### periph_divider register

- Absolute Address: 0x400000B0
- Base Offset: 0xB0
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 3:0|   count  |  rw  | 0xF |  — |
|  4 |div_enable|  rw  | 0x1 |  — |

#### count field

<p>clock divider. output clk is 2 x count</p>

#### div_enable field

<p>Enable clk divider</p>

### tsense_ctrl register

- Absolute Address: 0x400000B8
- Base Offset: 0xB8
- Size: 0x4

<p>Controls the temperature sensor and ADC conversion.
Write 1 to conv to trigger a single conversion. The bit
auto-clears after one cycle. Select which sensor to sample
with sen_sel, and set the ADC clock divider with clk_div.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 |   conv   |  rw  | 0x0 |  — |
|  1 |  sen_en  |  rw  | 0x0 |  — |
| 3:2|  sen_sel |  rw  | 0x0 |  — |
|11:4|  clk_div |  rw  | 0x1 |  — |

#### conv field

<p>Start conversion. Writing 1 triggers a single ADC sample.
Auto-clears to 0 after one cycle. Clears the valid bit
in tsense_status when written.</p>

#### sen_en field

<p>Sensor enable. When set, the sensor selected by sel is
powered on. When clear, all sensors are off.</p>

#### sen_sel field

<p>Sensor select. Selects which of the 4 temperature sensors
(0-3) is connected to the ADC.</p>

#### clk_div field

<p>ADC clock divider. The ADC clock frequency is
sys_clk / (2 * (clk_div + 1)).
0x00 = sys_clk/2 (fastest).
0xFF = sys_clk/512 (slowest).</p>

### tsense_status register

- Absolute Address: 0x400000C0
- Base Offset: 0xC0
- Size: 0x4

<p>Read-only status from the most recent ADC conversion.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 3:0|   data   |   r  | 0x0 |  — |
|  4 |   valid  |   r  | 0x0 |  — |
|  5 |  conv_b  |   r  | 0x1 |  — |

#### data field

<p>ADC output data from the last completed conversion.</p>

#### valid field

<p>Data valid. Set by hardware when a conversion completes.
Cleared when a new conversion is started (conv written).</p>

#### conv_b field

<p>ADC conversion status. Active-low while the ADC conversion is
in progress and high when idle / conversion complete.</p>

## mram_registers address map

- Absolute Address: 0x40001000
- Base Offset: 0x40001000
- Size: 0x4A0

<p>Unified register map for the AXI-to-MRAM bridge. Contains bridge
configuration registers and per-bank MRAM controller test registers.</p>

|Offset| Identifier|                      Name                     |
|------|-----------|-----------------------------------------------|
| 0x000|bridge_regs|AXI-to-MRAM Bridge Control and Status Registers|
| 0x100|bank0_tregs|     MRAM Control and Status Test Registers    |
| 0x200|bank1_tregs|     MRAM Control and Status Test Registers    |
| 0x300|bank2_tregs|     MRAM Control and Status Test Registers    |
| 0x400|bank3_tregs|     MRAM Control and Status Test Registers    |

## bridge_regs register file

- Absolute Address: 0x40001000
- Base Offset: 0x0
- Size: 0x38

<p>Register space for configuration and status of the AXI-to-MRAM bridge.</p>

|Offset|       Identifier       |          Name         |
|------|------------------------|-----------------------|
| 0x00 |    arbiter_mode_reg    |      Arbiter Mode     |
| 0x08 |    bridge_status_reg   |     Bridge Status     |
| 0x10 |    slverr_status_reg   | AXI Slave Error Status|
| 0x18 |       control_reg      |    AXI2MRAM Control   |
| 0x20 |ecc_1bit_error_count_reg|ECC 1-bit Error Counter|
| 0x28 |ecc_2bit_error_count_reg|ECC 2-bit Error Counter|
| 0x30 |ecc_3bit_error_count_reg|ECC 3-bit Error Counter|

### arbiter_mode_reg register

- Absolute Address: 0x40001000
- Base Offset: 0x0
- Size: 0x8

<p>Controls the read/write arbitration policy when both channels
have simultaneous pending requests.</p>

|Bits| Identifier |Access|Reset|    Name    |
|----|------------|------|-----|------------|
| 1:0|arbiter_mode|  rw  | 0x2 |arbiter_mode|

#### arbiter_mode field

<p>Arbitration mode selection.
0 = Write Priority  (writes always win)
1 = Read Priority   (reads always win)
2 = Round Robin     (alternate after each conflict)
3 = Oldest First    (whichever request arrived first wins)</p>

### bridge_status_reg register

- Absolute Address: 0x40001008
- Base Offset: 0x8
- Size: 0x8

<p>Read-only status indicators for the AXI-to-MRAM bridge.</p>

|Bits|   Identifier   |Access|Reset|      Name      |
|----|----------------|------|-----|----------------|
|  0 |    axi_busy    |   r  | 0x0 |    axi_busy    |
| 7:4|cmd_queue_active|   r  | 0x0 |cmd_queue_active|
|11:8|   mram_ready   |   r  | 0x0 |   mram_ready   |

#### axi_busy field

<p>High when the bridge has outstanding AXI transactions.</p>

#### cmd_queue_active field

<p>Per-bank command queue active flags. Bit N = bank N has
pending write/RMW commands.</p>

#### mram_ready field

<p>Per-bank ready signals for bringing MRAM out of deep
sleep. When the bit is 1, that bank is ready for
operations.</p>

### slverr_status_reg register

- Absolute Address: 0x40001010
- Base Offset: 0x10
- Size: 0x8

<p>Sticky status bits capturing the reason(s) why the bridge
returned SLVERR on the AXI bus. Bits are set by hardware and
cleared automatically when software reads this register
(clear-on-read). Multiple causes may be set simultaneously.</p>

|Bits|     Identifier    | Access|Reset|        Name       |
|----|-------------------|-------|-----|-------------------|
|  0 |      oor_read     |r, rclr| 0x0 |      oor_read     |
|  1 |     oor_write     |r, rclr| 0x0 |     oor_write     |
|  2 |   mram_not_ready  |r, rclr| 0x0 |   mram_not_ready  |
|  3 |   mram_unpowered  |r, rclr| 0x0 |   mram_unpowered  |
|  4 |    maintenance    |r, rclr| 0x0 |    maintenance    |
|  5 |unrecoverable_error|r, rclr| 0x0 |unrecoverable_error|

#### oor_read field

<p>Set when a read transaction was rejected with SLVERR
because ARADDR falls outside the valid MRAM window
(ARADDR[31:24] != 0, i.e. ARADDR &gt;= 0x100_0000).</p>

#### oor_write field

<p>Set when a write transaction was rejected with SLVERR
because AWADDR falls outside the valid MRAM window
(AWADDR[31:24] != 0, i.e. AWADDR &gt;= 0x100_0000).</p>

#### mram_not_ready field

<p>Set when a transaction was rejected with SLVERR because
the targeted MRAM bank reports not-ready.</p>

#### mram_unpowered field

<p>Set when a transaction was rejected with SLVERR because
the targeted MRAM bank reports power-not-ok.</p>

#### maintenance field

<p>Set when a transaction was rejected with SLVERR because
the targeted MRAM bank is in maintenance mode.</p>

#### unrecoverable_error field

<p>Set when read data was returned with an unrecoverable ECC
condition (triple-bit error) and the bridge responded with
SLVERR.</p>

### control_reg register

- Absolute Address: 0x40001018
- Base Offset: 0x18
- Size: 0x8

<p>Software control bits for the AXI-to-MRAM bridge.</p>

|Bits|    Identifier    |Access|Reset|       Name       |
|----|------------------|------|-----|------------------|
| 3:0|disable_clock_gate|  rw  | 0x0 |disable_clock_gate|
|  4 |ecc_1bit_intr_mask|  rw  | 0x1 |ecc_1bit_intr_mask|
|  5 |ecc_2bit_intr_mask|  rw  | 0x0 |ecc_2bit_intr_mask|
|  6 |ecc_3bit_intr_mask|  rw  | 0x0 |ecc_3bit_intr_mask|

#### disable_clock_gate field

<p>Per-bank clock-gate disable control. Bit N disables the
clock gating structure driving MRAM bank N so that a
continuous clock is driven into the bank interface.</p>

#### ecc_1bit_intr_mask field

<p>Masks CPU interrupt generation for 1-bit ECC events in
the ET interrupt logic. 1 = masked/suppressed, 0 =
unmasked/enabled. Reset default is 1 (masked).</p>

#### ecc_2bit_intr_mask field

<p>Masks CPU interrupt generation for 2-bit ECC events in
the ET interrupt logic. 1 = masked/suppressed, 0 =
unmasked/enabled. Reset default is 0 (enabled).</p>

#### ecc_3bit_intr_mask field

<p>Masks CPU interrupt generation for 3-bit ECC events in
the ET interrupt logic. 1 = masked/suppressed, 0 =
unmasked/enabled. Reset default is 0 (enabled).</p>

### ecc_1bit_error_count_reg register

- Absolute Address: 0x40001020
- Base Offset: 0x20
- Size: 0x8

<p>Counts observed 1-bit ECC events across all banks/lanes.
The counter increments by the number of asserted lane bits per
cycle (0..8).</p>

|Bits|Identifier|Access|Reset| Name|
|----|----------|------|-----|-----|
|31:0|   count  |   r  | 0x0 |count|

#### count field

<p>Accumulated 1-bit ECC event count.</p>

### ecc_2bit_error_count_reg register

- Absolute Address: 0x40001028
- Base Offset: 0x28
- Size: 0x8

<p>Counts observed 2-bit ECC events across all banks/lanes.
The counter increments by the number of asserted lane bits per
cycle (0..8).</p>

|Bits|Identifier|Access|Reset| Name|
|----|----------|------|-----|-----|
|31:0|   count  |   r  | 0x0 |count|

#### count field

<p>Accumulated 2-bit ECC event count.</p>

### ecc_3bit_error_count_reg register

- Absolute Address: 0x40001030
- Base Offset: 0x30
- Size: 0x8

<p>Counts observed 3-bit ECC events across all banks/lanes.
The counter increments by the number of asserted lane bits per
cycle (0..8).</p>

|Bits|Identifier|Access|Reset| Name|
|----|----------|------|-----|-----|
|31:0|   count  |   r  | 0x0 |count|

#### count field

<p>Accumulated 3-bit ECC event count.</p>

## bank0_tregs register file

- Absolute Address: 0x40001100
- Base Offset: 0x100
- Size: 0xA0

<p>Register space that contains the test registers for test functionality and debug of the MRAM.</p>

|Offset|     Identifier     |Name|
|------|--------------------|----|
| 0x00 |    mram_control    |  — |
| 0x20 | mram_control_pulse |  — |
| 0x28 |    gbl_cfg_ovr_0   |  — |
| 0x30 |      gbl_cfg_0     |  — |
| 0x38 |    man_control_0   |  — |
| 0x40 |    man_control_1   |  — |
| 0x48 |    mram_status_0   |  — |
| 0x50 |    mram_status_1   |  — |
| 0x58 |mram_dout_even_lower|  — |
| 0x60 | mram_dout_odd_lower|  — |
| 0x68 |  mram_dout_uppers  |  — |
| 0x70 |    bist_status_0   |  — |
| 0x78 |    bist_control    |  — |
| 0x88 |   ecc_correction   |  — |
| 0x98 |    bist_status_1   |  — |

### mram_control register

- Absolute Address: 0x40001100
- Base Offset: 0x0
- Size: 0x20

|  Bits |       Identifier      |Access|Reset|          Name         |
|-------|-----------------------|------|-----|-----------------------|
|  16:0 |        addr_in        |  rw  | 0x0 |        addr_in        |
| 24:17 |           ce          |  rw  | 0x0 |           ce          |
|   25  |           we          |  rw  | 0x0 |           we          |
|   26  |    rd_pulse_meas_en   |  rw  | 0x0 |    rd_pulse_meas_en   |
| 33:27 |        rca_ovr        |  rw  | 0x0 |        rca_ovr        |
|   34  |       rca_ovr_en      |  rw  | 0x0 |       rca_ovr_en      |
|   35  |     gbl_cfg_ovr_en    |  rw  | 0x0 |     gbl_cfg_ovr_en    |
|   36  |       rd_en_ovr       |  rw  | 0x0 |       rd_en_ovr       |
|   37  |       ref_prg_en      |  rw  | 0x0 |       ref_prg_en      |
|   38  |     dsleep_mram_en    |  rw  | 0x0 |     dsleep_mram_en    |
|   39  |reg_logic_sup_sleep_ovr|  rw  | 0x1 |reg_logic_sup_sleep_ovr|
|   40  |      prg_rd1_byp      |  rw  | 0x0 |      prg_rd1_byp      |
|   41  |       wr_en_ovr       |  rw  | 0x0 |       wr_en_ovr       |
|   42  |         dma_en        |  rw  | 0x0 |         dma_en        |
|   43  |  vblslx_gain_mode_ovr |  rw  | 0x0 |  vblslx_gain_mode_ovr |
| 47:44 | powerup_trim_load_ovr |  rw  | 0x0 | powerup_trim_load_ovr |
|   52  |      test_cal_en      |  rw  | 0x0 |      test_cal_en      |
| 55:53 |      anatest0_sel     |  rw  | 0x0 |      anatest0_sel     |
| 58:56 |      anatest1_sel     |  rw  | 0x0 |      anatest1_sel     |
|   59  |   eccrom_deep_sleep   |  rw  | 0x1 |   eccrom_deep_sleep   |
|   60  |      ref_ecc_sel      |  rw  | 0x0 |      ref_ecc_sel      |
|   61  |    disable_cpu_intr   |  rw  | 0x0 |    disable_cpu_intr   |
|   62  |      disable_ted      |  rw  | 0x0 |      disable_ted      |
|   63  |     ecc_bypass_en     |  rw  | 0x0 |     ecc_bypass_en     |
| 142:64|          bwe          |  rw  | 0x0 |          bwe          |
|  143  |      mram_clk_en      |  rw  | 0x1 |      mram_clk_en      |
|222:144|          din          |  rw  | 0x0 |          din          |
|  223  |    test_reg_ovr_en    |  rw  | 0x0 |    test_reg_ovr_en    |
|  224  |       otp_wr_en       |  rw  | 0x0 |       otp_wr_en       |
|  225  |      rst_cpu_intr     |  rw  | 0x0 |      rst_cpu_intr     |
|233:226|        dout_en        |  rw  | 0x0 |        dout_en        |
|236:234|         ecc_en        |  rw  | 0x0 |         ecc_en        |
|240:237|  even_man_stripe_sel  |  rw  | 0x0 |  even_man_stripe_sel  |
|  241  |     even_man_wr_0     |  rw  | 0x0 |     even_man_wr<0>    |
|  242  |     even_man_wr_1     |  rw  | 0x0 |     even_man_wr<1>    |
|  243  |     even_man_wr_2     |  rw  | 0x0 |     even_man_wr<2>    |
|  244  |     even_man_wr_3     |  rw  | 0x0 |     even_man_wr<3>    |
|248:245|   odd_man_stripe_sel  |  rw  | 0x0 |   odd_man_stripe_sel  |
|  249  |      odd_man_wr_0     |  rw  | 0x0 |     odd_man_wr<0>     |
|  250  |      odd_man_wr_1     |  rw  | 0x0 |     odd_man_wr<1>     |
|  251  |      odd_man_wr_2     |  rw  | 0x0 |     odd_man_wr<2>     |
|  252  |      odd_man_wr_3     |  rw  | 0x0 |     odd_man_wr<3>     |
|  253  |         sah_en        |  rw  | 0x1 |         sah_en        |
|  254  |       scc_otp_en      |  rw  | 0x0 |       scc_otp_en      |
|  255  |    maintenance_mode   |  rw  | 0x0 |    maintenance_mode   |

### mram_control_pulse register

- Absolute Address: 0x40001120
- Base Offset: 0x20
- Size: 0x8

|Bits|             Identifier             |Access|Reset|                 Name                |
|----|------------------------------------|------|-----|-------------------------------------|
|  0 |powerup_trim_load_ovr_single_pulse_0|  rw  | 0x0 |powerup_trim_load_ovr_single_pulse<0>|
|  1 |powerup_trim_load_ovr_single_pulse_1|  rw  | 0x0 |powerup_trim_load_ovr_single_pulse<1>|
|  2 |powerup_trim_load_ovr_single_pulse_2|  rw  | 0x0 |powerup_trim_load_ovr_single_pulse<2>|
|  3 |powerup_trim_load_ovr_single_pulse_3|  rw  | 0x0 |powerup_trim_load_ovr_single_pulse<3>|
|  4 |        mram_clk_single_pulse       |  rw  | 0x0 |        mram_clk_single_pulse        |

### gbl_cfg_ovr_0 register

- Absolute Address: 0x40001128
- Base Offset: 0x28
- Size: 0x8

| Bits|    Identifier   |Access|Reset|         Name         |
|-----|-----------------|------|-----|----------------------|
| 1:0 |  sa_equal_trim  |  rw  | 0x1 |  sa_equal_trim<1:0>  |
| 4:2 |vblslx_boost_trim|  rw  | 0x4 |vblslx_boost_trim<2:0>|
| 8:5 |  wr_en_msb_trim |  rw  | 0x9 |  wr_en_msb_trim<3:0> |
| 11:9|  wr_en_lsb_trim |  rw  | 0x6 |  wr_en_lsb_trim<2:0> |
|  12 | vblslx_gain_mode|  rw  | 0x0 |   vblslx_gain_mode   |
|16:13|   repulse_trim  |  rw  | 0x6 |   repulse_trim<3:0>  |
|  17 |    repulse_en   |  rw  | 0x1 |      repulse_en      |
|20:18|    rd_en_trim   |  rw  | 0x5 |    rd_en_trim<2:0>   |
|25:22| osc_wr_div_trim |  rw  | 0x3 | osc_wr_div_trim<3:0> |
|29:26|    vblsl_trim   |  rw  | 0x4 |    vblsl_trim<3:0>   |
|33:30|    tcsel_trim   |  rw  | 0x3 |    tcsel_trim<3:0>   |
|37:34|    vwlwr_trim   |  rw  | 0x7 |    vwlwr_trim<3:0>   |
|41:38|  vcr_gate_trim  |  rw  | 0xE |  vcr_gate_trim<3:0>  |

### gbl_cfg_0 register

- Absolute Address: 0x40001130
- Base Offset: 0x30
- Size: 0x8

| Bits|    Identifier   |Access|Reset|         Name         |
|-----|-----------------|------|-----|----------------------|
| 1:0 |  sa_equal_trim  |   r  |  —  |  sa_equal_trim<1:0>  |
| 4:2 |vblslx_boost_trim|   r  |  —  |vblslx_boost_trim<2:0>|
| 8:5 |  wr_en_msb_trim |   r  |  —  |  wr_en_msb_trim<3:0> |
| 11:9|  wr_en_lsb_trim |   r  |  —  |  wr_en_lsb_trim<2:0> |
|  12 | vblslx_gain_mode|   r  |  —  |   vblslx_gain_mode   |
|16:13|   repulse_trim  |   r  |  —  |   repulse_trim<3:0>  |
|  17 |    repulse_en   |   r  |  —  |      repulse_en      |
|20:18|    rd_en_trim   |   r  |  —  |    rd_en_trim<2:0>   |
|25:22| osc_wr_div_trim |   r  |  —  | osc_wr_div_trim<3:0> |
|29:26|    vblsl_trim   |   r  |  —  |    vblsl_trim<3:0>   |
|33:30|    tcsel_trim   |   r  |  —  |    tcsel_trim<3:0>   |
|37:34|    vwlwr_trim   |   r  |  —  |    vwlwr_trim<3:0>   |
|41:38|  vcr_gate_trim  |   r  |  —  |  vcr_gate_trim<3:0>  |

### man_control_0 register

- Absolute Address: 0x40001138
- Base Offset: 0x38
- Size: 0x8

| Bits|  Identifier |Access|Reset|       Name       |
|-----|-------------|------|-----|------------------|
| 3:0 |blk0_man_ccnt|   r  |  —  |blk0_man_ccnt<3:0>|
| 7:4 |blk0_man_cnfg|  rw  | 0x0 |blk0_man_cnfg<3:0>|
| 9:8 |blk0_man_fcnt|   r  |  —  |blk0_man_fcnt<1:0>|
|19:16|blk1_man_ccnt|   r  |  —  |blk1_man_ccnt<3:0>|
|23:20|blk1_man_cnfg|  rw  | 0x0 |blk1_man_cnfg<3:0>|
|25:24|blk1_man_fcnt|   r  |  —  |blk1_man_fcnt<1:0>|
|35:32|blk2_man_ccnt|   r  |  —  |blk2_man_ccnt<3:0>|
|39:36|blk2_man_cnfg|  rw  | 0x0 |blk2_man_cnfg<3:0>|
|41:40|blk2_man_fcnt|   r  |  —  |blk2_man_fcnt<1:0>|
|51:48|blk3_man_ccnt|   r  |  —  |blk3_man_ccnt<3:0>|
|55:52|blk3_man_cnfg|  rw  | 0x0 |blk3_man_cnfg<3:0>|
|57:56|blk3_man_fcnt|   r  |  —  |blk3_man_fcnt<1:0>|

### man_control_1 register

- Absolute Address: 0x40001140
- Base Offset: 0x40
- Size: 0x8

| Bits|  Identifier |Access|Reset|       Name       |
|-----|-------------|------|-----|------------------|
| 3:0 |blk4_man_ccnt|   r  |  —  |blk4_man_ccnt<3:0>|
| 7:4 |blk4_man_cnfg|  rw  | 0x0 |blk4_man_cnfg<3:0>|
| 9:8 |blk4_man_fcnt|   r  |  —  |blk4_man_fcnt<1:0>|
|19:16|blk5_man_ccnt|   r  |  —  |blk5_man_ccnt<3:0>|
|23:20|blk5_man_cnfg|  rw  | 0x0 |blk5_man_cnfg<3:0>|
|25:24|blk5_man_fcnt|   r  |  —  |blk5_man_fcnt<1:0>|
|35:32|blk6_man_ccnt|   r  |  —  |blk6_man_ccnt<3:0>|
|39:36|blk6_man_cnfg|  rw  | 0x0 |blk6_man_cnfg<3:0>|
|41:40|blk6_man_fcnt|   r  |  —  |blk6_man_fcnt<1:0>|
|51:48|blk7_man_ccnt|   r  |  —  |blk7_man_ccnt<3:0>|
|55:52|blk7_man_cnfg|  rw  | 0x0 |blk7_man_cnfg<3:0>|
|57:56|blk7_man_fcnt|   r  |  —  |blk7_man_fcnt<1:0>|

### mram_status_0 register

- Absolute Address: 0x40001148
- Base Offset: 0x48
- Size: 0x8

| Bits|   Identifier   |Access|Reset|         Name         |
|-----|----------------|------|-----|----------------------|
| 15:0| bist_error_loop|   r  |  —  | bist_error_loop<15:0>|
|33:17|bist_error_count|   r  |  —  |bist_error_count<16:0>|
|40:34|    bist_rh0    |   r  |  —  |     bist_rh0<6:0>    |
|47:41|    bist_rh1    |   r  |  —  |     bist_rh1<6:0>    |
|54:48|    bist_rh2    |   r  |  —  |     bist_rh2<6:0>    |
|56:55|  cpu_intr_flag |   r  |  —  |     cpu_intr_flag    |
|58:57|  ecc_1bit_flag |   r  |  —  |  ecc_1bit_flag<1:0>  |
|60:59|  ecc_2bit_flag |   r  |  —  |  ecc_2bit_flag<1:0>  |
|62:61|  ecc_3bit_flag |   r  |  —  |  ecc_3bit_flag<1:0>  |

### mram_status_1 register

- Absolute Address: 0x40001150
- Base Offset: 0x50
- Size: 0x8

| Bits|      Identifier     |Access|Reset|            Name           |
|-----|---------------------|------|-----|---------------------------|
| 1:0 |         temp        |   r  |  —  |         temp<1:0>         |
| 4:3 |       ecc_1bit      |   r  |  —  |       ecc_1bit<1:0>       |
| 6:5 |       ecc_2bit      |   r  |  —  |       ecc_2bit<1:0>       |
| 8:7 |       ecc_3bit      |   r  |  —  |       ecc_3bit<1:0>       |
|  9  |        pwr_ok       |   r  |  —  |           pwr_ok          |
|  10 |    eccrom_pwr_ok    |   r  |  —  |       eccrom_pwr_ok       |
|29:11|intr_error_lane0_addr|   r  |  —  |intr_error_lane0_addr<18:0>|
|48:30|intr_error_lane1_addr|   r  |  —  |intr_error_lane1_addr<18:0>|
|57:50|         busy        |   r  |  —  |         busy<7:0>         |

### mram_dout_even_lower register

- Absolute Address: 0x40001158
- Base Offset: 0x58
- Size: 0x8

|Bits|Identifier|Access|Reset|   Name   |
|----|----------|------|-----|----------|
|63:0|   dout   |   r  |  —  |dout<63:0>|

### mram_dout_odd_lower register

- Absolute Address: 0x40001160
- Base Offset: 0x60
- Size: 0x8

|Bits|Identifier|Access|Reset|    Name    |
|----|----------|------|-----|------------|
|63:0|   dout   |   r  |  —  |dout<142:79>|

### mram_dout_uppers register

- Absolute Address: 0x40001168
- Base Offset: 0x68
- Size: 0x8

| Bits|  Identifier |Access|Reset|     Name    |
|-----|-------------|------|-----|-------------|
| 14:0|dout_even_msb|   r  |  —  | dout<78:64> |
|46:32| dout_odd_msb|   r  |  —  |dout<157:143>|

### bist_status_0 register

- Absolute Address: 0x40001170
- Base Offset: 0x70
- Size: 0x8

|Bits|   Identifier   |Access|Reset|         Name         |
|----|----------------|------|-----|----------------------|
|63:0|bist_error_value|   r  |  —  |bist_error_value<63:0>|

### bist_control register

- Absolute Address: 0x40001178
- Base Offset: 0x78
- Size: 0x10

| Bits|     Identifier     |Access|Reset|          Name         |
|-----|--------------------|------|-----|-----------------------|
|  0  |     bist_rte_en    |  rw  | 0x0 |      bist_rte_en      |
|  1  |    bist_data_inv   |  rw  | 0x0 |     bist_data_inv     |
| 4:2 |    bist_add_inc    |  rw  | 0x0 |   bist_add_inc<2:0>   |
|  5  | bist_stop_on_error |  rw  | 0x0 |   bist_stop_on_error  |
| 25:6|   bist_start_add   |  rw  | 0x0 |  bist_start_add<19:0> |
|45:26|    bist_stop_add   |  rw  | 0x0 |  bist_stop_add<19:0>  |
|50:46|      RH4margin     |  rw  | 0xA |     RH4margin<4:0>    |
|55:51|     rh2_offset     |  rw  | 0x0 |    rh2_offset<4:0>    |
|78:64|  bist_error_value  |   r  |  —  |bist_error_value<78:64>|
|94:79|   bist_loop_count  |  rw  | 0x0 | bist_loop_count<15:0> |
|  95 |     bist_start     |  rw  | 0x0 |       bist_start      |
|  96 |   bist_trim_mode   |  rw  | 0x0 |     bist_trim_mode    |
|  97 |bist_stop_on_repl_of|  rw  | 0x0 |  bist_stop_on_repl_of |
|  98 |     bist_rst_b     |  rw  | 0x1 |       bist_rst_b      |
|  99 |     bist_reset     |  rw  | 0x0 |       bist_reset      |
| 100 |     bist_rd_en     |  rw  | 0x0 |       bist_rd_en      |
| 101 |     bist_wr_en     |  rw  | 0x0 |       bist_wr_en      |

### ecc_correction register

- Absolute Address: 0x40001188
- Base Offset: 0x88
- Size: 0x10

| Bits|Identifier|Access|Reset|    Name   |
|-----|----------|------|-----|-----------|
|127:0|   dout   |   r  |  —  |dout<127:0>|

### bist_status_1 register

- Absolute Address: 0x40001198
- Base Offset: 0x98
- Size: 0x8

|Bits| Identifier |Access|Reset|       Name       |
|----|------------|------|-----|------------------|
|19:0|bist_err_add|   r  |  —  |bist_err_add<19:0>|
| 20 | bist_error |   r  |  —  |    bist_error    |
| 21 |  bist_busy |   r  |  —  |     bist_busy    |

## bank1_tregs register file

- Absolute Address: 0x40001200
- Base Offset: 0x200
- Size: 0xA0

<p>Register space that contains the test registers for test functionality and debug of the MRAM.</p>

|Offset|     Identifier     |Name|
|------|--------------------|----|
| 0x00 |    mram_control    |  — |
| 0x20 | mram_control_pulse |  — |
| 0x28 |    gbl_cfg_ovr_0   |  — |
| 0x30 |      gbl_cfg_0     |  — |
| 0x38 |    man_control_0   |  — |
| 0x40 |    man_control_1   |  — |
| 0x48 |    mram_status_0   |  — |
| 0x50 |    mram_status_1   |  — |
| 0x58 |mram_dout_even_lower|  — |
| 0x60 | mram_dout_odd_lower|  — |
| 0x68 |  mram_dout_uppers  |  — |
| 0x70 |    bist_status_0   |  — |
| 0x78 |    bist_control    |  — |
| 0x88 |   ecc_correction   |  — |
| 0x98 |    bist_status_1   |  — |

### mram_control register

- Absolute Address: 0x40001200
- Base Offset: 0x0
- Size: 0x20

|  Bits |       Identifier      |Access|Reset|          Name         |
|-------|-----------------------|------|-----|-----------------------|
|  16:0 |        addr_in        |  rw  | 0x0 |        addr_in        |
| 24:17 |           ce          |  rw  | 0x0 |           ce          |
|   25  |           we          |  rw  | 0x0 |           we          |
|   26  |    rd_pulse_meas_en   |  rw  | 0x0 |    rd_pulse_meas_en   |
| 33:27 |        rca_ovr        |  rw  | 0x0 |        rca_ovr        |
|   34  |       rca_ovr_en      |  rw  | 0x0 |       rca_ovr_en      |
|   35  |     gbl_cfg_ovr_en    |  rw  | 0x0 |     gbl_cfg_ovr_en    |
|   36  |       rd_en_ovr       |  rw  | 0x0 |       rd_en_ovr       |
|   37  |       ref_prg_en      |  rw  | 0x0 |       ref_prg_en      |
|   38  |     dsleep_mram_en    |  rw  | 0x0 |     dsleep_mram_en    |
|   39  |reg_logic_sup_sleep_ovr|  rw  | 0x1 |reg_logic_sup_sleep_ovr|
|   40  |      prg_rd1_byp      |  rw  | 0x0 |      prg_rd1_byp      |
|   41  |       wr_en_ovr       |  rw  | 0x0 |       wr_en_ovr       |
|   42  |         dma_en        |  rw  | 0x0 |         dma_en        |
|   43  |  vblslx_gain_mode_ovr |  rw  | 0x0 |  vblslx_gain_mode_ovr |
| 47:44 | powerup_trim_load_ovr |  rw  | 0x0 | powerup_trim_load_ovr |
|   52  |      test_cal_en      |  rw  | 0x0 |      test_cal_en      |
| 55:53 |      anatest0_sel     |  rw  | 0x0 |      anatest0_sel     |
| 58:56 |      anatest1_sel     |  rw  | 0x0 |      anatest1_sel     |
|   59  |   eccrom_deep_sleep   |  rw  | 0x1 |   eccrom_deep_sleep   |
|   60  |      ref_ecc_sel      |  rw  | 0x0 |      ref_ecc_sel      |
|   61  |    disable_cpu_intr   |  rw  | 0x0 |    disable_cpu_intr   |
|   62  |      disable_ted      |  rw  | 0x0 |      disable_ted      |
|   63  |     ecc_bypass_en     |  rw  | 0x0 |     ecc_bypass_en     |
| 142:64|          bwe          |  rw  | 0x0 |          bwe          |
|  143  |      mram_clk_en      |  rw  | 0x1 |      mram_clk_en      |
|222:144|          din          |  rw  | 0x0 |          din          |
|  223  |    test_reg_ovr_en    |  rw  | 0x0 |    test_reg_ovr_en    |
|  224  |       otp_wr_en       |  rw  | 0x0 |       otp_wr_en       |
|  225  |      rst_cpu_intr     |  rw  | 0x0 |      rst_cpu_intr     |
|233:226|        dout_en        |  rw  | 0x0 |        dout_en        |
|236:234|         ecc_en        |  rw  | 0x0 |         ecc_en        |
|240:237|  even_man_stripe_sel  |  rw  | 0x0 |  even_man_stripe_sel  |
|  241  |     even_man_wr_0     |  rw  | 0x0 |     even_man_wr<0>    |
|  242  |     even_man_wr_1     |  rw  | 0x0 |     even_man_wr<1>    |
|  243  |     even_man_wr_2     |  rw  | 0x0 |     even_man_wr<2>    |
|  244  |     even_man_wr_3     |  rw  | 0x0 |     even_man_wr<3>    |
|248:245|   odd_man_stripe_sel  |  rw  | 0x0 |   odd_man_stripe_sel  |
|  249  |      odd_man_wr_0     |  rw  | 0x0 |     odd_man_wr<0>     |
|  250  |      odd_man_wr_1     |  rw  | 0x0 |     odd_man_wr<1>     |
|  251  |      odd_man_wr_2     |  rw  | 0x0 |     odd_man_wr<2>     |
|  252  |      odd_man_wr_3     |  rw  | 0x0 |     odd_man_wr<3>     |
|  253  |         sah_en        |  rw  | 0x1 |         sah_en        |
|  254  |       scc_otp_en      |  rw  | 0x0 |       scc_otp_en      |
|  255  |    maintenance_mode   |  rw  | 0x0 |    maintenance_mode   |

### mram_control_pulse register

- Absolute Address: 0x40001220
- Base Offset: 0x20
- Size: 0x8

|Bits|             Identifier             |Access|Reset|                 Name                |
|----|------------------------------------|------|-----|-------------------------------------|
|  0 |powerup_trim_load_ovr_single_pulse_0|  rw  | 0x0 |powerup_trim_load_ovr_single_pulse<0>|
|  1 |powerup_trim_load_ovr_single_pulse_1|  rw  | 0x0 |powerup_trim_load_ovr_single_pulse<1>|
|  2 |powerup_trim_load_ovr_single_pulse_2|  rw  | 0x0 |powerup_trim_load_ovr_single_pulse<2>|
|  3 |powerup_trim_load_ovr_single_pulse_3|  rw  | 0x0 |powerup_trim_load_ovr_single_pulse<3>|
|  4 |        mram_clk_single_pulse       |  rw  | 0x0 |        mram_clk_single_pulse        |

### gbl_cfg_ovr_0 register

- Absolute Address: 0x40001228
- Base Offset: 0x28
- Size: 0x8

| Bits|    Identifier   |Access|Reset|         Name         |
|-----|-----------------|------|-----|----------------------|
| 1:0 |  sa_equal_trim  |  rw  | 0x1 |  sa_equal_trim<1:0>  |
| 4:2 |vblslx_boost_trim|  rw  | 0x4 |vblslx_boost_trim<2:0>|
| 8:5 |  wr_en_msb_trim |  rw  | 0x9 |  wr_en_msb_trim<3:0> |
| 11:9|  wr_en_lsb_trim |  rw  | 0x6 |  wr_en_lsb_trim<2:0> |
|  12 | vblslx_gain_mode|  rw  | 0x0 |   vblslx_gain_mode   |
|16:13|   repulse_trim  |  rw  | 0x6 |   repulse_trim<3:0>  |
|  17 |    repulse_en   |  rw  | 0x1 |      repulse_en      |
|20:18|    rd_en_trim   |  rw  | 0x5 |    rd_en_trim<2:0>   |
|25:22| osc_wr_div_trim |  rw  | 0x3 | osc_wr_div_trim<3:0> |
|29:26|    vblsl_trim   |  rw  | 0x4 |    vblsl_trim<3:0>   |
|33:30|    tcsel_trim   |  rw  | 0x3 |    tcsel_trim<3:0>   |
|37:34|    vwlwr_trim   |  rw  | 0x7 |    vwlwr_trim<3:0>   |
|41:38|  vcr_gate_trim  |  rw  | 0xE |  vcr_gate_trim<3:0>  |

### gbl_cfg_0 register

- Absolute Address: 0x40001230
- Base Offset: 0x30
- Size: 0x8

| Bits|    Identifier   |Access|Reset|         Name         |
|-----|-----------------|------|-----|----------------------|
| 1:0 |  sa_equal_trim  |   r  |  —  |  sa_equal_trim<1:0>  |
| 4:2 |vblslx_boost_trim|   r  |  —  |vblslx_boost_trim<2:0>|
| 8:5 |  wr_en_msb_trim |   r  |  —  |  wr_en_msb_trim<3:0> |
| 11:9|  wr_en_lsb_trim |   r  |  —  |  wr_en_lsb_trim<2:0> |
|  12 | vblslx_gain_mode|   r  |  —  |   vblslx_gain_mode   |
|16:13|   repulse_trim  |   r  |  —  |   repulse_trim<3:0>  |
|  17 |    repulse_en   |   r  |  —  |      repulse_en      |
|20:18|    rd_en_trim   |   r  |  —  |    rd_en_trim<2:0>   |
|25:22| osc_wr_div_trim |   r  |  —  | osc_wr_div_trim<3:0> |
|29:26|    vblsl_trim   |   r  |  —  |    vblsl_trim<3:0>   |
|33:30|    tcsel_trim   |   r  |  —  |    tcsel_trim<3:0>   |
|37:34|    vwlwr_trim   |   r  |  —  |    vwlwr_trim<3:0>   |
|41:38|  vcr_gate_trim  |   r  |  —  |  vcr_gate_trim<3:0>  |

### man_control_0 register

- Absolute Address: 0x40001238
- Base Offset: 0x38
- Size: 0x8

| Bits|  Identifier |Access|Reset|       Name       |
|-----|-------------|------|-----|------------------|
| 3:0 |blk0_man_ccnt|   r  |  —  |blk0_man_ccnt<3:0>|
| 7:4 |blk0_man_cnfg|  rw  | 0x0 |blk0_man_cnfg<3:0>|
| 9:8 |blk0_man_fcnt|   r  |  —  |blk0_man_fcnt<1:0>|
|19:16|blk1_man_ccnt|   r  |  —  |blk1_man_ccnt<3:0>|
|23:20|blk1_man_cnfg|  rw  | 0x0 |blk1_man_cnfg<3:0>|
|25:24|blk1_man_fcnt|   r  |  —  |blk1_man_fcnt<1:0>|
|35:32|blk2_man_ccnt|   r  |  —  |blk2_man_ccnt<3:0>|
|39:36|blk2_man_cnfg|  rw  | 0x0 |blk2_man_cnfg<3:0>|
|41:40|blk2_man_fcnt|   r  |  —  |blk2_man_fcnt<1:0>|
|51:48|blk3_man_ccnt|   r  |  —  |blk3_man_ccnt<3:0>|
|55:52|blk3_man_cnfg|  rw  | 0x0 |blk3_man_cnfg<3:0>|
|57:56|blk3_man_fcnt|   r  |  —  |blk3_man_fcnt<1:0>|

### man_control_1 register

- Absolute Address: 0x40001240
- Base Offset: 0x40
- Size: 0x8

| Bits|  Identifier |Access|Reset|       Name       |
|-----|-------------|------|-----|------------------|
| 3:0 |blk4_man_ccnt|   r  |  —  |blk4_man_ccnt<3:0>|
| 7:4 |blk4_man_cnfg|  rw  | 0x0 |blk4_man_cnfg<3:0>|
| 9:8 |blk4_man_fcnt|   r  |  —  |blk4_man_fcnt<1:0>|
|19:16|blk5_man_ccnt|   r  |  —  |blk5_man_ccnt<3:0>|
|23:20|blk5_man_cnfg|  rw  | 0x0 |blk5_man_cnfg<3:0>|
|25:24|blk5_man_fcnt|   r  |  —  |blk5_man_fcnt<1:0>|
|35:32|blk6_man_ccnt|   r  |  —  |blk6_man_ccnt<3:0>|
|39:36|blk6_man_cnfg|  rw  | 0x0 |blk6_man_cnfg<3:0>|
|41:40|blk6_man_fcnt|   r  |  —  |blk6_man_fcnt<1:0>|
|51:48|blk7_man_ccnt|   r  |  —  |blk7_man_ccnt<3:0>|
|55:52|blk7_man_cnfg|  rw  | 0x0 |blk7_man_cnfg<3:0>|
|57:56|blk7_man_fcnt|   r  |  —  |blk7_man_fcnt<1:0>|

### mram_status_0 register

- Absolute Address: 0x40001248
- Base Offset: 0x48
- Size: 0x8

| Bits|   Identifier   |Access|Reset|         Name         |
|-----|----------------|------|-----|----------------------|
| 15:0| bist_error_loop|   r  |  —  | bist_error_loop<15:0>|
|33:17|bist_error_count|   r  |  —  |bist_error_count<16:0>|
|40:34|    bist_rh0    |   r  |  —  |     bist_rh0<6:0>    |
|47:41|    bist_rh1    |   r  |  —  |     bist_rh1<6:0>    |
|54:48|    bist_rh2    |   r  |  —  |     bist_rh2<6:0>    |
|56:55|  cpu_intr_flag |   r  |  —  |     cpu_intr_flag    |
|58:57|  ecc_1bit_flag |   r  |  —  |  ecc_1bit_flag<1:0>  |
|60:59|  ecc_2bit_flag |   r  |  —  |  ecc_2bit_flag<1:0>  |
|62:61|  ecc_3bit_flag |   r  |  —  |  ecc_3bit_flag<1:0>  |

### mram_status_1 register

- Absolute Address: 0x40001250
- Base Offset: 0x50
- Size: 0x8

| Bits|      Identifier     |Access|Reset|            Name           |
|-----|---------------------|------|-----|---------------------------|
| 1:0 |         temp        |   r  |  —  |         temp<1:0>         |
| 4:3 |       ecc_1bit      |   r  |  —  |       ecc_1bit<1:0>       |
| 6:5 |       ecc_2bit      |   r  |  —  |       ecc_2bit<1:0>       |
| 8:7 |       ecc_3bit      |   r  |  —  |       ecc_3bit<1:0>       |
|  9  |        pwr_ok       |   r  |  —  |           pwr_ok          |
|  10 |    eccrom_pwr_ok    |   r  |  —  |       eccrom_pwr_ok       |
|29:11|intr_error_lane0_addr|   r  |  —  |intr_error_lane0_addr<18:0>|
|48:30|intr_error_lane1_addr|   r  |  —  |intr_error_lane1_addr<18:0>|
|57:50|         busy        |   r  |  —  |         busy<7:0>         |

### mram_dout_even_lower register

- Absolute Address: 0x40001258
- Base Offset: 0x58
- Size: 0x8

|Bits|Identifier|Access|Reset|   Name   |
|----|----------|------|-----|----------|
|63:0|   dout   |   r  |  —  |dout<63:0>|

### mram_dout_odd_lower register

- Absolute Address: 0x40001260
- Base Offset: 0x60
- Size: 0x8

|Bits|Identifier|Access|Reset|    Name    |
|----|----------|------|-----|------------|
|63:0|   dout   |   r  |  —  |dout<142:79>|

### mram_dout_uppers register

- Absolute Address: 0x40001268
- Base Offset: 0x68
- Size: 0x8

| Bits|  Identifier |Access|Reset|     Name    |
|-----|-------------|------|-----|-------------|
| 14:0|dout_even_msb|   r  |  —  | dout<78:64> |
|46:32| dout_odd_msb|   r  |  —  |dout<157:143>|

### bist_status_0 register

- Absolute Address: 0x40001270
- Base Offset: 0x70
- Size: 0x8

|Bits|   Identifier   |Access|Reset|         Name         |
|----|----------------|------|-----|----------------------|
|63:0|bist_error_value|   r  |  —  |bist_error_value<63:0>|

### bist_control register

- Absolute Address: 0x40001278
- Base Offset: 0x78
- Size: 0x10

| Bits|     Identifier     |Access|Reset|          Name         |
|-----|--------------------|------|-----|-----------------------|
|  0  |     bist_rte_en    |  rw  | 0x0 |      bist_rte_en      |
|  1  |    bist_data_inv   |  rw  | 0x0 |     bist_data_inv     |
| 4:2 |    bist_add_inc    |  rw  | 0x0 |   bist_add_inc<2:0>   |
|  5  | bist_stop_on_error |  rw  | 0x0 |   bist_stop_on_error  |
| 25:6|   bist_start_add   |  rw  | 0x0 |  bist_start_add<19:0> |
|45:26|    bist_stop_add   |  rw  | 0x0 |  bist_stop_add<19:0>  |
|50:46|      RH4margin     |  rw  | 0xA |     RH4margin<4:0>    |
|55:51|     rh2_offset     |  rw  | 0x0 |    rh2_offset<4:0>    |
|78:64|  bist_error_value  |   r  |  —  |bist_error_value<78:64>|
|94:79|   bist_loop_count  |  rw  | 0x0 | bist_loop_count<15:0> |
|  95 |     bist_start     |  rw  | 0x0 |       bist_start      |
|  96 |   bist_trim_mode   |  rw  | 0x0 |     bist_trim_mode    |
|  97 |bist_stop_on_repl_of|  rw  | 0x0 |  bist_stop_on_repl_of |
|  98 |     bist_rst_b     |  rw  | 0x1 |       bist_rst_b      |
|  99 |     bist_reset     |  rw  | 0x0 |       bist_reset      |
| 100 |     bist_rd_en     |  rw  | 0x0 |       bist_rd_en      |
| 101 |     bist_wr_en     |  rw  | 0x0 |       bist_wr_en      |

### ecc_correction register

- Absolute Address: 0x40001288
- Base Offset: 0x88
- Size: 0x10

| Bits|Identifier|Access|Reset|    Name   |
|-----|----------|------|-----|-----------|
|127:0|   dout   |   r  |  —  |dout<127:0>|

### bist_status_1 register

- Absolute Address: 0x40001298
- Base Offset: 0x98
- Size: 0x8

|Bits| Identifier |Access|Reset|       Name       |
|----|------------|------|-----|------------------|
|19:0|bist_err_add|   r  |  —  |bist_err_add<19:0>|
| 20 | bist_error |   r  |  —  |    bist_error    |
| 21 |  bist_busy |   r  |  —  |     bist_busy    |

## bank2_tregs register file

- Absolute Address: 0x40001300
- Base Offset: 0x300
- Size: 0xA0

<p>Register space that contains the test registers for test functionality and debug of the MRAM.</p>

|Offset|     Identifier     |Name|
|------|--------------------|----|
| 0x00 |    mram_control    |  — |
| 0x20 | mram_control_pulse |  — |
| 0x28 |    gbl_cfg_ovr_0   |  — |
| 0x30 |      gbl_cfg_0     |  — |
| 0x38 |    man_control_0   |  — |
| 0x40 |    man_control_1   |  — |
| 0x48 |    mram_status_0   |  — |
| 0x50 |    mram_status_1   |  — |
| 0x58 |mram_dout_even_lower|  — |
| 0x60 | mram_dout_odd_lower|  — |
| 0x68 |  mram_dout_uppers  |  — |
| 0x70 |    bist_status_0   |  — |
| 0x78 |    bist_control    |  — |
| 0x88 |   ecc_correction   |  — |
| 0x98 |    bist_status_1   |  — |

### mram_control register

- Absolute Address: 0x40001300
- Base Offset: 0x0
- Size: 0x20

|  Bits |       Identifier      |Access|Reset|          Name         |
|-------|-----------------------|------|-----|-----------------------|
|  16:0 |        addr_in        |  rw  | 0x0 |        addr_in        |
| 24:17 |           ce          |  rw  | 0x0 |           ce          |
|   25  |           we          |  rw  | 0x0 |           we          |
|   26  |    rd_pulse_meas_en   |  rw  | 0x0 |    rd_pulse_meas_en   |
| 33:27 |        rca_ovr        |  rw  | 0x0 |        rca_ovr        |
|   34  |       rca_ovr_en      |  rw  | 0x0 |       rca_ovr_en      |
|   35  |     gbl_cfg_ovr_en    |  rw  | 0x0 |     gbl_cfg_ovr_en    |
|   36  |       rd_en_ovr       |  rw  | 0x0 |       rd_en_ovr       |
|   37  |       ref_prg_en      |  rw  | 0x0 |       ref_prg_en      |
|   38  |     dsleep_mram_en    |  rw  | 0x0 |     dsleep_mram_en    |
|   39  |reg_logic_sup_sleep_ovr|  rw  | 0x1 |reg_logic_sup_sleep_ovr|
|   40  |      prg_rd1_byp      |  rw  | 0x0 |      prg_rd1_byp      |
|   41  |       wr_en_ovr       |  rw  | 0x0 |       wr_en_ovr       |
|   42  |         dma_en        |  rw  | 0x0 |         dma_en        |
|   43  |  vblslx_gain_mode_ovr |  rw  | 0x0 |  vblslx_gain_mode_ovr |
| 47:44 | powerup_trim_load_ovr |  rw  | 0x0 | powerup_trim_load_ovr |
|   52  |      test_cal_en      |  rw  | 0x0 |      test_cal_en      |
| 55:53 |      anatest0_sel     |  rw  | 0x0 |      anatest0_sel     |
| 58:56 |      anatest1_sel     |  rw  | 0x0 |      anatest1_sel     |
|   59  |   eccrom_deep_sleep   |  rw  | 0x1 |   eccrom_deep_sleep   |
|   60  |      ref_ecc_sel      |  rw  | 0x0 |      ref_ecc_sel      |
|   61  |    disable_cpu_intr   |  rw  | 0x0 |    disable_cpu_intr   |
|   62  |      disable_ted      |  rw  | 0x0 |      disable_ted      |
|   63  |     ecc_bypass_en     |  rw  | 0x0 |     ecc_bypass_en     |
| 142:64|          bwe          |  rw  | 0x0 |          bwe          |
|  143  |      mram_clk_en      |  rw  | 0x1 |      mram_clk_en      |
|222:144|          din          |  rw  | 0x0 |          din          |
|  223  |    test_reg_ovr_en    |  rw  | 0x0 |    test_reg_ovr_en    |
|  224  |       otp_wr_en       |  rw  | 0x0 |       otp_wr_en       |
|  225  |      rst_cpu_intr     |  rw  | 0x0 |      rst_cpu_intr     |
|233:226|        dout_en        |  rw  | 0x0 |        dout_en        |
|236:234|         ecc_en        |  rw  | 0x0 |         ecc_en        |
|240:237|  even_man_stripe_sel  |  rw  | 0x0 |  even_man_stripe_sel  |
|  241  |     even_man_wr_0     |  rw  | 0x0 |     even_man_wr<0>    |
|  242  |     even_man_wr_1     |  rw  | 0x0 |     even_man_wr<1>    |
|  243  |     even_man_wr_2     |  rw  | 0x0 |     even_man_wr<2>    |
|  244  |     even_man_wr_3     |  rw  | 0x0 |     even_man_wr<3>    |
|248:245|   odd_man_stripe_sel  |  rw  | 0x0 |   odd_man_stripe_sel  |
|  249  |      odd_man_wr_0     |  rw  | 0x0 |     odd_man_wr<0>     |
|  250  |      odd_man_wr_1     |  rw  | 0x0 |     odd_man_wr<1>     |
|  251  |      odd_man_wr_2     |  rw  | 0x0 |     odd_man_wr<2>     |
|  252  |      odd_man_wr_3     |  rw  | 0x0 |     odd_man_wr<3>     |
|  253  |         sah_en        |  rw  | 0x1 |         sah_en        |
|  254  |       scc_otp_en      |  rw  | 0x0 |       scc_otp_en      |
|  255  |    maintenance_mode   |  rw  | 0x0 |    maintenance_mode   |

### mram_control_pulse register

- Absolute Address: 0x40001320
- Base Offset: 0x20
- Size: 0x8

|Bits|             Identifier             |Access|Reset|                 Name                |
|----|------------------------------------|------|-----|-------------------------------------|
|  0 |powerup_trim_load_ovr_single_pulse_0|  rw  | 0x0 |powerup_trim_load_ovr_single_pulse<0>|
|  1 |powerup_trim_load_ovr_single_pulse_1|  rw  | 0x0 |powerup_trim_load_ovr_single_pulse<1>|
|  2 |powerup_trim_load_ovr_single_pulse_2|  rw  | 0x0 |powerup_trim_load_ovr_single_pulse<2>|
|  3 |powerup_trim_load_ovr_single_pulse_3|  rw  | 0x0 |powerup_trim_load_ovr_single_pulse<3>|
|  4 |        mram_clk_single_pulse       |  rw  | 0x0 |        mram_clk_single_pulse        |

### gbl_cfg_ovr_0 register

- Absolute Address: 0x40001328
- Base Offset: 0x28
- Size: 0x8

| Bits|    Identifier   |Access|Reset|         Name         |
|-----|-----------------|------|-----|----------------------|
| 1:0 |  sa_equal_trim  |  rw  | 0x1 |  sa_equal_trim<1:0>  |
| 4:2 |vblslx_boost_trim|  rw  | 0x4 |vblslx_boost_trim<2:0>|
| 8:5 |  wr_en_msb_trim |  rw  | 0x9 |  wr_en_msb_trim<3:0> |
| 11:9|  wr_en_lsb_trim |  rw  | 0x6 |  wr_en_lsb_trim<2:0> |
|  12 | vblslx_gain_mode|  rw  | 0x0 |   vblslx_gain_mode   |
|16:13|   repulse_trim  |  rw  | 0x6 |   repulse_trim<3:0>  |
|  17 |    repulse_en   |  rw  | 0x1 |      repulse_en      |
|20:18|    rd_en_trim   |  rw  | 0x5 |    rd_en_trim<2:0>   |
|25:22| osc_wr_div_trim |  rw  | 0x3 | osc_wr_div_trim<3:0> |
|29:26|    vblsl_trim   |  rw  | 0x4 |    vblsl_trim<3:0>   |
|33:30|    tcsel_trim   |  rw  | 0x3 |    tcsel_trim<3:0>   |
|37:34|    vwlwr_trim   |  rw  | 0x7 |    vwlwr_trim<3:0>   |
|41:38|  vcr_gate_trim  |  rw  | 0xE |  vcr_gate_trim<3:0>  |

### gbl_cfg_0 register

- Absolute Address: 0x40001330
- Base Offset: 0x30
- Size: 0x8

| Bits|    Identifier   |Access|Reset|         Name         |
|-----|-----------------|------|-----|----------------------|
| 1:0 |  sa_equal_trim  |   r  |  —  |  sa_equal_trim<1:0>  |
| 4:2 |vblslx_boost_trim|   r  |  —  |vblslx_boost_trim<2:0>|
| 8:5 |  wr_en_msb_trim |   r  |  —  |  wr_en_msb_trim<3:0> |
| 11:9|  wr_en_lsb_trim |   r  |  —  |  wr_en_lsb_trim<2:0> |
|  12 | vblslx_gain_mode|   r  |  —  |   vblslx_gain_mode   |
|16:13|   repulse_trim  |   r  |  —  |   repulse_trim<3:0>  |
|  17 |    repulse_en   |   r  |  —  |      repulse_en      |
|20:18|    rd_en_trim   |   r  |  —  |    rd_en_trim<2:0>   |
|25:22| osc_wr_div_trim |   r  |  —  | osc_wr_div_trim<3:0> |
|29:26|    vblsl_trim   |   r  |  —  |    vblsl_trim<3:0>   |
|33:30|    tcsel_trim   |   r  |  —  |    tcsel_trim<3:0>   |
|37:34|    vwlwr_trim   |   r  |  —  |    vwlwr_trim<3:0>   |
|41:38|  vcr_gate_trim  |   r  |  —  |  vcr_gate_trim<3:0>  |

### man_control_0 register

- Absolute Address: 0x40001338
- Base Offset: 0x38
- Size: 0x8

| Bits|  Identifier |Access|Reset|       Name       |
|-----|-------------|------|-----|------------------|
| 3:0 |blk0_man_ccnt|   r  |  —  |blk0_man_ccnt<3:0>|
| 7:4 |blk0_man_cnfg|  rw  | 0x0 |blk0_man_cnfg<3:0>|
| 9:8 |blk0_man_fcnt|   r  |  —  |blk0_man_fcnt<1:0>|
|19:16|blk1_man_ccnt|   r  |  —  |blk1_man_ccnt<3:0>|
|23:20|blk1_man_cnfg|  rw  | 0x0 |blk1_man_cnfg<3:0>|
|25:24|blk1_man_fcnt|   r  |  —  |blk1_man_fcnt<1:0>|
|35:32|blk2_man_ccnt|   r  |  —  |blk2_man_ccnt<3:0>|
|39:36|blk2_man_cnfg|  rw  | 0x0 |blk2_man_cnfg<3:0>|
|41:40|blk2_man_fcnt|   r  |  —  |blk2_man_fcnt<1:0>|
|51:48|blk3_man_ccnt|   r  |  —  |blk3_man_ccnt<3:0>|
|55:52|blk3_man_cnfg|  rw  | 0x0 |blk3_man_cnfg<3:0>|
|57:56|blk3_man_fcnt|   r  |  —  |blk3_man_fcnt<1:0>|

### man_control_1 register

- Absolute Address: 0x40001340
- Base Offset: 0x40
- Size: 0x8

| Bits|  Identifier |Access|Reset|       Name       |
|-----|-------------|------|-----|------------------|
| 3:0 |blk4_man_ccnt|   r  |  —  |blk4_man_ccnt<3:0>|
| 7:4 |blk4_man_cnfg|  rw  | 0x0 |blk4_man_cnfg<3:0>|
| 9:8 |blk4_man_fcnt|   r  |  —  |blk4_man_fcnt<1:0>|
|19:16|blk5_man_ccnt|   r  |  —  |blk5_man_ccnt<3:0>|
|23:20|blk5_man_cnfg|  rw  | 0x0 |blk5_man_cnfg<3:0>|
|25:24|blk5_man_fcnt|   r  |  —  |blk5_man_fcnt<1:0>|
|35:32|blk6_man_ccnt|   r  |  —  |blk6_man_ccnt<3:0>|
|39:36|blk6_man_cnfg|  rw  | 0x0 |blk6_man_cnfg<3:0>|
|41:40|blk6_man_fcnt|   r  |  —  |blk6_man_fcnt<1:0>|
|51:48|blk7_man_ccnt|   r  |  —  |blk7_man_ccnt<3:0>|
|55:52|blk7_man_cnfg|  rw  | 0x0 |blk7_man_cnfg<3:0>|
|57:56|blk7_man_fcnt|   r  |  —  |blk7_man_fcnt<1:0>|

### mram_status_0 register

- Absolute Address: 0x40001348
- Base Offset: 0x48
- Size: 0x8

| Bits|   Identifier   |Access|Reset|         Name         |
|-----|----------------|------|-----|----------------------|
| 15:0| bist_error_loop|   r  |  —  | bist_error_loop<15:0>|
|33:17|bist_error_count|   r  |  —  |bist_error_count<16:0>|
|40:34|    bist_rh0    |   r  |  —  |     bist_rh0<6:0>    |
|47:41|    bist_rh1    |   r  |  —  |     bist_rh1<6:0>    |
|54:48|    bist_rh2    |   r  |  —  |     bist_rh2<6:0>    |
|56:55|  cpu_intr_flag |   r  |  —  |     cpu_intr_flag    |
|58:57|  ecc_1bit_flag |   r  |  —  |  ecc_1bit_flag<1:0>  |
|60:59|  ecc_2bit_flag |   r  |  —  |  ecc_2bit_flag<1:0>  |
|62:61|  ecc_3bit_flag |   r  |  —  |  ecc_3bit_flag<1:0>  |

### mram_status_1 register

- Absolute Address: 0x40001350
- Base Offset: 0x50
- Size: 0x8

| Bits|      Identifier     |Access|Reset|            Name           |
|-----|---------------------|------|-----|---------------------------|
| 1:0 |         temp        |   r  |  —  |         temp<1:0>         |
| 4:3 |       ecc_1bit      |   r  |  —  |       ecc_1bit<1:0>       |
| 6:5 |       ecc_2bit      |   r  |  —  |       ecc_2bit<1:0>       |
| 8:7 |       ecc_3bit      |   r  |  —  |       ecc_3bit<1:0>       |
|  9  |        pwr_ok       |   r  |  —  |           pwr_ok          |
|  10 |    eccrom_pwr_ok    |   r  |  —  |       eccrom_pwr_ok       |
|29:11|intr_error_lane0_addr|   r  |  —  |intr_error_lane0_addr<18:0>|
|48:30|intr_error_lane1_addr|   r  |  —  |intr_error_lane1_addr<18:0>|
|57:50|         busy        |   r  |  —  |         busy<7:0>         |

### mram_dout_even_lower register

- Absolute Address: 0x40001358
- Base Offset: 0x58
- Size: 0x8

|Bits|Identifier|Access|Reset|   Name   |
|----|----------|------|-----|----------|
|63:0|   dout   |   r  |  —  |dout<63:0>|

### mram_dout_odd_lower register

- Absolute Address: 0x40001360
- Base Offset: 0x60
- Size: 0x8

|Bits|Identifier|Access|Reset|    Name    |
|----|----------|------|-----|------------|
|63:0|   dout   |   r  |  —  |dout<142:79>|

### mram_dout_uppers register

- Absolute Address: 0x40001368
- Base Offset: 0x68
- Size: 0x8

| Bits|  Identifier |Access|Reset|     Name    |
|-----|-------------|------|-----|-------------|
| 14:0|dout_even_msb|   r  |  —  | dout<78:64> |
|46:32| dout_odd_msb|   r  |  —  |dout<157:143>|

### bist_status_0 register

- Absolute Address: 0x40001370
- Base Offset: 0x70
- Size: 0x8

|Bits|   Identifier   |Access|Reset|         Name         |
|----|----------------|------|-----|----------------------|
|63:0|bist_error_value|   r  |  —  |bist_error_value<63:0>|

### bist_control register

- Absolute Address: 0x40001378
- Base Offset: 0x78
- Size: 0x10

| Bits|     Identifier     |Access|Reset|          Name         |
|-----|--------------------|------|-----|-----------------------|
|  0  |     bist_rte_en    |  rw  | 0x0 |      bist_rte_en      |
|  1  |    bist_data_inv   |  rw  | 0x0 |     bist_data_inv     |
| 4:2 |    bist_add_inc    |  rw  | 0x0 |   bist_add_inc<2:0>   |
|  5  | bist_stop_on_error |  rw  | 0x0 |   bist_stop_on_error  |
| 25:6|   bist_start_add   |  rw  | 0x0 |  bist_start_add<19:0> |
|45:26|    bist_stop_add   |  rw  | 0x0 |  bist_stop_add<19:0>  |
|50:46|      RH4margin     |  rw  | 0xA |     RH4margin<4:0>    |
|55:51|     rh2_offset     |  rw  | 0x0 |    rh2_offset<4:0>    |
|78:64|  bist_error_value  |   r  |  —  |bist_error_value<78:64>|
|94:79|   bist_loop_count  |  rw  | 0x0 | bist_loop_count<15:0> |
|  95 |     bist_start     |  rw  | 0x0 |       bist_start      |
|  96 |   bist_trim_mode   |  rw  | 0x0 |     bist_trim_mode    |
|  97 |bist_stop_on_repl_of|  rw  | 0x0 |  bist_stop_on_repl_of |
|  98 |     bist_rst_b     |  rw  | 0x1 |       bist_rst_b      |
|  99 |     bist_reset     |  rw  | 0x0 |       bist_reset      |
| 100 |     bist_rd_en     |  rw  | 0x0 |       bist_rd_en      |
| 101 |     bist_wr_en     |  rw  | 0x0 |       bist_wr_en      |

### ecc_correction register

- Absolute Address: 0x40001388
- Base Offset: 0x88
- Size: 0x10

| Bits|Identifier|Access|Reset|    Name   |
|-----|----------|------|-----|-----------|
|127:0|   dout   |   r  |  —  |dout<127:0>|

### bist_status_1 register

- Absolute Address: 0x40001398
- Base Offset: 0x98
- Size: 0x8

|Bits| Identifier |Access|Reset|       Name       |
|----|------------|------|-----|------------------|
|19:0|bist_err_add|   r  |  —  |bist_err_add<19:0>|
| 20 | bist_error |   r  |  —  |    bist_error    |
| 21 |  bist_busy |   r  |  —  |     bist_busy    |

## bank3_tregs register file

- Absolute Address: 0x40001400
- Base Offset: 0x400
- Size: 0xA0

<p>Register space that contains the test registers for test functionality and debug of the MRAM.</p>

|Offset|     Identifier     |Name|
|------|--------------------|----|
| 0x00 |    mram_control    |  — |
| 0x20 | mram_control_pulse |  — |
| 0x28 |    gbl_cfg_ovr_0   |  — |
| 0x30 |      gbl_cfg_0     |  — |
| 0x38 |    man_control_0   |  — |
| 0x40 |    man_control_1   |  — |
| 0x48 |    mram_status_0   |  — |
| 0x50 |    mram_status_1   |  — |
| 0x58 |mram_dout_even_lower|  — |
| 0x60 | mram_dout_odd_lower|  — |
| 0x68 |  mram_dout_uppers  |  — |
| 0x70 |    bist_status_0   |  — |
| 0x78 |    bist_control    |  — |
| 0x88 |   ecc_correction   |  — |
| 0x98 |    bist_status_1   |  — |

### mram_control register

- Absolute Address: 0x40001400
- Base Offset: 0x0
- Size: 0x20

|  Bits |       Identifier      |Access|Reset|          Name         |
|-------|-----------------------|------|-----|-----------------------|
|  16:0 |        addr_in        |  rw  | 0x0 |        addr_in        |
| 24:17 |           ce          |  rw  | 0x0 |           ce          |
|   25  |           we          |  rw  | 0x0 |           we          |
|   26  |    rd_pulse_meas_en   |  rw  | 0x0 |    rd_pulse_meas_en   |
| 33:27 |        rca_ovr        |  rw  | 0x0 |        rca_ovr        |
|   34  |       rca_ovr_en      |  rw  | 0x0 |       rca_ovr_en      |
|   35  |     gbl_cfg_ovr_en    |  rw  | 0x0 |     gbl_cfg_ovr_en    |
|   36  |       rd_en_ovr       |  rw  | 0x0 |       rd_en_ovr       |
|   37  |       ref_prg_en      |  rw  | 0x0 |       ref_prg_en      |
|   38  |     dsleep_mram_en    |  rw  | 0x0 |     dsleep_mram_en    |
|   39  |reg_logic_sup_sleep_ovr|  rw  | 0x1 |reg_logic_sup_sleep_ovr|
|   40  |      prg_rd1_byp      |  rw  | 0x0 |      prg_rd1_byp      |
|   41  |       wr_en_ovr       |  rw  | 0x0 |       wr_en_ovr       |
|   42  |         dma_en        |  rw  | 0x0 |         dma_en        |
|   43  |  vblslx_gain_mode_ovr |  rw  | 0x0 |  vblslx_gain_mode_ovr |
| 47:44 | powerup_trim_load_ovr |  rw  | 0x0 | powerup_trim_load_ovr |
|   52  |      test_cal_en      |  rw  | 0x0 |      test_cal_en      |
| 55:53 |      anatest0_sel     |  rw  | 0x0 |      anatest0_sel     |
| 58:56 |      anatest1_sel     |  rw  | 0x0 |      anatest1_sel     |
|   59  |   eccrom_deep_sleep   |  rw  | 0x1 |   eccrom_deep_sleep   |
|   60  |      ref_ecc_sel      |  rw  | 0x0 |      ref_ecc_sel      |
|   61  |    disable_cpu_intr   |  rw  | 0x0 |    disable_cpu_intr   |
|   62  |      disable_ted      |  rw  | 0x0 |      disable_ted      |
|   63  |     ecc_bypass_en     |  rw  | 0x0 |     ecc_bypass_en     |
| 142:64|          bwe          |  rw  | 0x0 |          bwe          |
|  143  |      mram_clk_en      |  rw  | 0x1 |      mram_clk_en      |
|222:144|          din          |  rw  | 0x0 |          din          |
|  223  |    test_reg_ovr_en    |  rw  | 0x0 |    test_reg_ovr_en    |
|  224  |       otp_wr_en       |  rw  | 0x0 |       otp_wr_en       |
|  225  |      rst_cpu_intr     |  rw  | 0x0 |      rst_cpu_intr     |
|233:226|        dout_en        |  rw  | 0x0 |        dout_en        |
|236:234|         ecc_en        |  rw  | 0x0 |         ecc_en        |
|240:237|  even_man_stripe_sel  |  rw  | 0x0 |  even_man_stripe_sel  |
|  241  |     even_man_wr_0     |  rw  | 0x0 |     even_man_wr<0>    |
|  242  |     even_man_wr_1     |  rw  | 0x0 |     even_man_wr<1>    |
|  243  |     even_man_wr_2     |  rw  | 0x0 |     even_man_wr<2>    |
|  244  |     even_man_wr_3     |  rw  | 0x0 |     even_man_wr<3>    |
|248:245|   odd_man_stripe_sel  |  rw  | 0x0 |   odd_man_stripe_sel  |
|  249  |      odd_man_wr_0     |  rw  | 0x0 |     odd_man_wr<0>     |
|  250  |      odd_man_wr_1     |  rw  | 0x0 |     odd_man_wr<1>     |
|  251  |      odd_man_wr_2     |  rw  | 0x0 |     odd_man_wr<2>     |
|  252  |      odd_man_wr_3     |  rw  | 0x0 |     odd_man_wr<3>     |
|  253  |         sah_en        |  rw  | 0x1 |         sah_en        |
|  254  |       scc_otp_en      |  rw  | 0x0 |       scc_otp_en      |
|  255  |    maintenance_mode   |  rw  | 0x0 |    maintenance_mode   |

### mram_control_pulse register

- Absolute Address: 0x40001420
- Base Offset: 0x20
- Size: 0x8

|Bits|             Identifier             |Access|Reset|                 Name                |
|----|------------------------------------|------|-----|-------------------------------------|
|  0 |powerup_trim_load_ovr_single_pulse_0|  rw  | 0x0 |powerup_trim_load_ovr_single_pulse<0>|
|  1 |powerup_trim_load_ovr_single_pulse_1|  rw  | 0x0 |powerup_trim_load_ovr_single_pulse<1>|
|  2 |powerup_trim_load_ovr_single_pulse_2|  rw  | 0x0 |powerup_trim_load_ovr_single_pulse<2>|
|  3 |powerup_trim_load_ovr_single_pulse_3|  rw  | 0x0 |powerup_trim_load_ovr_single_pulse<3>|
|  4 |        mram_clk_single_pulse       |  rw  | 0x0 |        mram_clk_single_pulse        |

### gbl_cfg_ovr_0 register

- Absolute Address: 0x40001428
- Base Offset: 0x28
- Size: 0x8

| Bits|    Identifier   |Access|Reset|         Name         |
|-----|-----------------|------|-----|----------------------|
| 1:0 |  sa_equal_trim  |  rw  | 0x1 |  sa_equal_trim<1:0>  |
| 4:2 |vblslx_boost_trim|  rw  | 0x4 |vblslx_boost_trim<2:0>|
| 8:5 |  wr_en_msb_trim |  rw  | 0x9 |  wr_en_msb_trim<3:0> |
| 11:9|  wr_en_lsb_trim |  rw  | 0x6 |  wr_en_lsb_trim<2:0> |
|  12 | vblslx_gain_mode|  rw  | 0x0 |   vblslx_gain_mode   |
|16:13|   repulse_trim  |  rw  | 0x6 |   repulse_trim<3:0>  |
|  17 |    repulse_en   |  rw  | 0x1 |      repulse_en      |
|20:18|    rd_en_trim   |  rw  | 0x5 |    rd_en_trim<2:0>   |
|25:22| osc_wr_div_trim |  rw  | 0x3 | osc_wr_div_trim<3:0> |
|29:26|    vblsl_trim   |  rw  | 0x4 |    vblsl_trim<3:0>   |
|33:30|    tcsel_trim   |  rw  | 0x3 |    tcsel_trim<3:0>   |
|37:34|    vwlwr_trim   |  rw  | 0x7 |    vwlwr_trim<3:0>   |
|41:38|  vcr_gate_trim  |  rw  | 0xE |  vcr_gate_trim<3:0>  |

### gbl_cfg_0 register

- Absolute Address: 0x40001430
- Base Offset: 0x30
- Size: 0x8

| Bits|    Identifier   |Access|Reset|         Name         |
|-----|-----------------|------|-----|----------------------|
| 1:0 |  sa_equal_trim  |   r  |  —  |  sa_equal_trim<1:0>  |
| 4:2 |vblslx_boost_trim|   r  |  —  |vblslx_boost_trim<2:0>|
| 8:5 |  wr_en_msb_trim |   r  |  —  |  wr_en_msb_trim<3:0> |
| 11:9|  wr_en_lsb_trim |   r  |  —  |  wr_en_lsb_trim<2:0> |
|  12 | vblslx_gain_mode|   r  |  —  |   vblslx_gain_mode   |
|16:13|   repulse_trim  |   r  |  —  |   repulse_trim<3:0>  |
|  17 |    repulse_en   |   r  |  —  |      repulse_en      |
|20:18|    rd_en_trim   |   r  |  —  |    rd_en_trim<2:0>   |
|25:22| osc_wr_div_trim |   r  |  —  | osc_wr_div_trim<3:0> |
|29:26|    vblsl_trim   |   r  |  —  |    vblsl_trim<3:0>   |
|33:30|    tcsel_trim   |   r  |  —  |    tcsel_trim<3:0>   |
|37:34|    vwlwr_trim   |   r  |  —  |    vwlwr_trim<3:0>   |
|41:38|  vcr_gate_trim  |   r  |  —  |  vcr_gate_trim<3:0>  |

### man_control_0 register

- Absolute Address: 0x40001438
- Base Offset: 0x38
- Size: 0x8

| Bits|  Identifier |Access|Reset|       Name       |
|-----|-------------|------|-----|------------------|
| 3:0 |blk0_man_ccnt|   r  |  —  |blk0_man_ccnt<3:0>|
| 7:4 |blk0_man_cnfg|  rw  | 0x0 |blk0_man_cnfg<3:0>|
| 9:8 |blk0_man_fcnt|   r  |  —  |blk0_man_fcnt<1:0>|
|19:16|blk1_man_ccnt|   r  |  —  |blk1_man_ccnt<3:0>|
|23:20|blk1_man_cnfg|  rw  | 0x0 |blk1_man_cnfg<3:0>|
|25:24|blk1_man_fcnt|   r  |  —  |blk1_man_fcnt<1:0>|
|35:32|blk2_man_ccnt|   r  |  —  |blk2_man_ccnt<3:0>|
|39:36|blk2_man_cnfg|  rw  | 0x0 |blk2_man_cnfg<3:0>|
|41:40|blk2_man_fcnt|   r  |  —  |blk2_man_fcnt<1:0>|
|51:48|blk3_man_ccnt|   r  |  —  |blk3_man_ccnt<3:0>|
|55:52|blk3_man_cnfg|  rw  | 0x0 |blk3_man_cnfg<3:0>|
|57:56|blk3_man_fcnt|   r  |  —  |blk3_man_fcnt<1:0>|

### man_control_1 register

- Absolute Address: 0x40001440
- Base Offset: 0x40
- Size: 0x8

| Bits|  Identifier |Access|Reset|       Name       |
|-----|-------------|------|-----|------------------|
| 3:0 |blk4_man_ccnt|   r  |  —  |blk4_man_ccnt<3:0>|
| 7:4 |blk4_man_cnfg|  rw  | 0x0 |blk4_man_cnfg<3:0>|
| 9:8 |blk4_man_fcnt|   r  |  —  |blk4_man_fcnt<1:0>|
|19:16|blk5_man_ccnt|   r  |  —  |blk5_man_ccnt<3:0>|
|23:20|blk5_man_cnfg|  rw  | 0x0 |blk5_man_cnfg<3:0>|
|25:24|blk5_man_fcnt|   r  |  —  |blk5_man_fcnt<1:0>|
|35:32|blk6_man_ccnt|   r  |  —  |blk6_man_ccnt<3:0>|
|39:36|blk6_man_cnfg|  rw  | 0x0 |blk6_man_cnfg<3:0>|
|41:40|blk6_man_fcnt|   r  |  —  |blk6_man_fcnt<1:0>|
|51:48|blk7_man_ccnt|   r  |  —  |blk7_man_ccnt<3:0>|
|55:52|blk7_man_cnfg|  rw  | 0x0 |blk7_man_cnfg<3:0>|
|57:56|blk7_man_fcnt|   r  |  —  |blk7_man_fcnt<1:0>|

### mram_status_0 register

- Absolute Address: 0x40001448
- Base Offset: 0x48
- Size: 0x8

| Bits|   Identifier   |Access|Reset|         Name         |
|-----|----------------|------|-----|----------------------|
| 15:0| bist_error_loop|   r  |  —  | bist_error_loop<15:0>|
|33:17|bist_error_count|   r  |  —  |bist_error_count<16:0>|
|40:34|    bist_rh0    |   r  |  —  |     bist_rh0<6:0>    |
|47:41|    bist_rh1    |   r  |  —  |     bist_rh1<6:0>    |
|54:48|    bist_rh2    |   r  |  —  |     bist_rh2<6:0>    |
|56:55|  cpu_intr_flag |   r  |  —  |     cpu_intr_flag    |
|58:57|  ecc_1bit_flag |   r  |  —  |  ecc_1bit_flag<1:0>  |
|60:59|  ecc_2bit_flag |   r  |  —  |  ecc_2bit_flag<1:0>  |
|62:61|  ecc_3bit_flag |   r  |  —  |  ecc_3bit_flag<1:0>  |

### mram_status_1 register

- Absolute Address: 0x40001450
- Base Offset: 0x50
- Size: 0x8

| Bits|      Identifier     |Access|Reset|            Name           |
|-----|---------------------|------|-----|---------------------------|
| 1:0 |         temp        |   r  |  —  |         temp<1:0>         |
| 4:3 |       ecc_1bit      |   r  |  —  |       ecc_1bit<1:0>       |
| 6:5 |       ecc_2bit      |   r  |  —  |       ecc_2bit<1:0>       |
| 8:7 |       ecc_3bit      |   r  |  —  |       ecc_3bit<1:0>       |
|  9  |        pwr_ok       |   r  |  —  |           pwr_ok          |
|  10 |    eccrom_pwr_ok    |   r  |  —  |       eccrom_pwr_ok       |
|29:11|intr_error_lane0_addr|   r  |  —  |intr_error_lane0_addr<18:0>|
|48:30|intr_error_lane1_addr|   r  |  —  |intr_error_lane1_addr<18:0>|
|57:50|         busy        |   r  |  —  |         busy<7:0>         |

### mram_dout_even_lower register

- Absolute Address: 0x40001458
- Base Offset: 0x58
- Size: 0x8

|Bits|Identifier|Access|Reset|   Name   |
|----|----------|------|-----|----------|
|63:0|   dout   |   r  |  —  |dout<63:0>|

### mram_dout_odd_lower register

- Absolute Address: 0x40001460
- Base Offset: 0x60
- Size: 0x8

|Bits|Identifier|Access|Reset|    Name    |
|----|----------|------|-----|------------|
|63:0|   dout   |   r  |  —  |dout<142:79>|

### mram_dout_uppers register

- Absolute Address: 0x40001468
- Base Offset: 0x68
- Size: 0x8

| Bits|  Identifier |Access|Reset|     Name    |
|-----|-------------|------|-----|-------------|
| 14:0|dout_even_msb|   r  |  —  | dout<78:64> |
|46:32| dout_odd_msb|   r  |  —  |dout<157:143>|

### bist_status_0 register

- Absolute Address: 0x40001470
- Base Offset: 0x70
- Size: 0x8

|Bits|   Identifier   |Access|Reset|         Name         |
|----|----------------|------|-----|----------------------|
|63:0|bist_error_value|   r  |  —  |bist_error_value<63:0>|

### bist_control register

- Absolute Address: 0x40001478
- Base Offset: 0x78
- Size: 0x10

| Bits|     Identifier     |Access|Reset|          Name         |
|-----|--------------------|------|-----|-----------------------|
|  0  |     bist_rte_en    |  rw  | 0x0 |      bist_rte_en      |
|  1  |    bist_data_inv   |  rw  | 0x0 |     bist_data_inv     |
| 4:2 |    bist_add_inc    |  rw  | 0x0 |   bist_add_inc<2:0>   |
|  5  | bist_stop_on_error |  rw  | 0x0 |   bist_stop_on_error  |
| 25:6|   bist_start_add   |  rw  | 0x0 |  bist_start_add<19:0> |
|45:26|    bist_stop_add   |  rw  | 0x0 |  bist_stop_add<19:0>  |
|50:46|      RH4margin     |  rw  | 0xA |     RH4margin<4:0>    |
|55:51|     rh2_offset     |  rw  | 0x0 |    rh2_offset<4:0>    |
|78:64|  bist_error_value  |   r  |  —  |bist_error_value<78:64>|
|94:79|   bist_loop_count  |  rw  | 0x0 | bist_loop_count<15:0> |
|  95 |     bist_start     |  rw  | 0x0 |       bist_start      |
|  96 |   bist_trim_mode   |  rw  | 0x0 |     bist_trim_mode    |
|  97 |bist_stop_on_repl_of|  rw  | 0x0 |  bist_stop_on_repl_of |
|  98 |     bist_rst_b     |  rw  | 0x1 |       bist_rst_b      |
|  99 |     bist_reset     |  rw  | 0x0 |       bist_reset      |
| 100 |     bist_rd_en     |  rw  | 0x0 |       bist_rd_en      |
| 101 |     bist_wr_en     |  rw  | 0x0 |       bist_wr_en      |

### ecc_correction register

- Absolute Address: 0x40001488
- Base Offset: 0x88
- Size: 0x10

| Bits|Identifier|Access|Reset|    Name   |
|-----|----------|------|-----|-----------|
|127:0|   dout   |   r  |  —  |dout<127:0>|

### bist_status_1 register

- Absolute Address: 0x40001498
- Base Offset: 0x98
- Size: 0x8

|Bits| Identifier |Access|Reset|       Name       |
|----|------------|------|-----|------------------|
|19:0|bist_err_add|   r  |  —  |bist_err_add<19:0>|
| 20 | bist_error |   r  |  —  |    bist_error    |
| 21 |  bist_busy |   r  |  —  |     bist_busy    |

## i2c_registers address map

- Absolute Address: 0x40002000
- Base Offset: 0x40002000
- Size: 0x24

|Offset|Identifier|       Name      |
|------|----------|-----------------|
| 0x00 | Commands |Command Registers|
| 0x08 |  Status  |        —        |
| 0x10 |    Cfg   |        —        |
| 0x18 |   Wdata  |        —        |
| 0x20 |   Rdata  |        —        |

### Commands register

- Absolute Address: 0x40002000
- Base Offset: 0x0
- Size: 0x4

<p>I2C Command Registers</p>

|Bits|  Identifier  |Access|Reset|Name|
|----|--------------|------|-----|----|
|  0 |     start    |  rw  | 0x0 |  — |
|  1 |     read     |  rw  | 0x0 |  — |
|  2 |     write    |  rw  | 0x0 |  — |
|  3 |write_multiple|  rw  | 0x0 |  — |
|  4 |     stop     |  rw  | 0x0 |  — |
|  5 |      enq     |  rw  | 0x0 |  — |
|14:8|    address   |  rw  | 0x0 |  — |

#### start field

<p>Start</p>

#### read field

<p>TODO</p>

#### write field

<p>TODO</p>

#### write_multiple field

<p>TODO</p>

#### stop field

<p>TODO</p>

#### enq field

<p>TODO</p>

#### address field

<p>Address</p>

### Status register

- Absolute Address: 0x40002008
- Base Offset: 0x8
- Size: 0x4

|Bits|  Identifier | Access|Reset|Name|
|----|-------------|-------|-----|----|
|  0 |     busy    |   r   | 0x0 |  — |
|  1 | bus_control |   r   | 0x0 |  — |
|  2 |  bus_active |   r   | 0x0 |  — |
|  3 |  missed_ack |r, rclr| 0x0 |  — |
|  4 |cmd_ff_n_full|   r   |  —  |  — |
|  5 | tx_ff_n_full|   r   |  —  |  — |
|  6 | rx_ff_n_full|   r   |  —  |  — |
|  7 | rx_overflow |   r   |  —  |  — |

#### busy field

<p>Transaction ongoing</p>

#### bus_control field

<p>Transaction ongoing</p>

#### bus_active field

<p>Transaction ongoing</p>

#### missed_ack field

<p>Transaction ongoing</p>

#### cmd_ff_n_full field

<p>cmd_ff not Full</p>

#### tx_ff_n_full field

<p>tx_ff not Full</p>

#### rx_ff_n_full field

<p>rx_ff not Full</p>

#### rx_overflow field

<p>rx overflow</p>

### Cfg register

- Absolute Address: 0x40002010
- Base Offset: 0x10
- Size: 0x4

|Bits| Identifier |Access|Reset|Name|
|----|------------|------|-----|----|
|15:0|  prescale  |  rw  | 0x0 |  — |
| 16 |stop_on_idle|  rw  | 0x0 |  — |

#### prescale field

<p>Prescale</p>

#### stop_on_idle field

<p>Stop on Idle</p>

### Wdata register

- Absolute Address: 0x40002018
- Base Offset: 0x18
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 7:0|   wdata  |   w  | 0x0 |  — |
|  8 |   wlast  |   w  | 0x0 |  — |

#### wdata field

<p>TxData</p>

#### wlast field

<p>Write Last</p>

### Rdata register

- Absolute Address: 0x40002020
- Base Offset: 0x20
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 7:0|   rdata  |   r  | 0x0 |  — |
|  8 |   rlast  |   r  | 0x0 |  — |

#### rdata field

<p>RxData</p>

#### rlast field

<p>Read Last</p>

## qspi_registers address map

- Absolute Address: 0x40003000
- Base Offset: 0x40003000
- Size: 0x64

<p>Shakti QSPI Registers</p>

|Offset|Identifier|Name|
|------|----------|----|
| 0x00 |    CR    |  — |
| 0x08 |    DCR   |  — |
| 0x10 |    SR    |  — |
| 0x18 |    FCR   |  — |
| 0x20 |    DLR   |  — |
| 0x28 |    CCR   |  — |
| 0x30 |    AR    |  — |
| 0x38 |    ABR   |  — |
| 0x40 |    DR    |  — |
| 0x48 |   PSMKR  |  — |
| 0x50 |   PSMAR  |  — |
| 0x58 |    PIR   |  — |
| 0x60 |   LPTR   |  — |

### CR register

- Absolute Address: 0x40003000
- Base Offset: 0x0
- Size: 0x4

| Bits| Identifier|Access|Reset|Name|
|-----|-----------|------|-----|----|
|  0  |qspi_enable|  rw  | 0x0 |  — |
|  1  |   abort   |  rw  | 0x0 |  — |
|  2  |   dmaen   |  rw  | 0x0 |  — |
|  3  |    tcen   |  rw  | 0x0 |  — |
|  4  |   sshift  |  rw  | 0x0 |  — |
|  6  |    dfm    |  rw  | 0x0 |  — |
|  7  |    fsel   |  rw  | 0x0 |  — |
| 12:8|   fthres  |  rw  | 0x0 |  — |
|  16 |    teie   |  rw  | 0x0 |  — |
|  17 |    tcie   |  rw  | 0x0 |  — |
|  18 |    ftie   |  rw  | 0x0 |  — |
|  19 |    smie   |  rw  | 0x0 |  — |
|  20 |    toie   |  rw  | 0x0 |  — |
|  22 |    apms   |  rw  | 0x0 |  — |
|  23 |    pmm    |  rw  | 0x0 |  — |
|31:24| prescaler |  rw  | 0x0 |  — |

#### qspi_enable field

<p>QSPI enable</p>

#### abort field

<p>Abort request</p>

#### dmaen field

<p>DMA enable</p>

#### tcen field

<p>Timeout counter enable</p>

#### sshift field

<p>Sample shift</p>

#### dfm field

<p>Dual flash mode enable</p>

#### fsel field

<p>Flash select</p>

#### fthres field

<p>FIFO threshold level</p>

#### teie field

<p>Transfer error interrupt enable</p>

#### tcie field

<p>Transfer complete interrupt enable</p>

#### ftie field

<p>FIFO threshold interrupt enable</p>

#### smie field

<p>Status match interrupt enable</p>

#### toie field

<p>Timeout interrupt enable</p>

#### apms field

<p>Automatic polling mode stop</p>

#### pmm field

<p>Polling match mode (0=AND,1=OR)</p>

#### prescaler field

<p>Clock prescaler (PRESCALER[7:0])</p>

### DCR register

- Absolute Address: 0x40003008
- Base Offset: 0x8
- Size: 0x4

| Bits|Identifier|Access|Reset|Name|
|-----|----------|------|-----|----|
|  0  |  ckmode  |  rw  | 0x0 |  — |
| 10:8|   csht   |  rw  | 0x0 |  — |
|20:16|   fsize  |  rw  | 0x0 |  — |

#### ckmode field

<p>Clock mode (0=Mode0,1=Mode3)</p>

#### csht field

<p>Chip select high time</p>

#### fsize field

<p>Flash memory size</p>

### SR register

- Absolute Address: 0x40003010
- Base Offset: 0x10
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 |    tef   |   r  |  —  |  — |
|  1 |    tcf   |   r  |  —  |  — |
|  2 |    ftf   |   r  |  —  |  — |
|  3 |    smf   |   r  |  —  |  — |
|  4 |    tof   |   r  |  —  |  — |
|  5 |   busy   |   r  |  —  |  — |
|13:8|  flevel  |   r  |  —  |  — |

#### tef field

<p>Transfer error flag</p>

#### tcf field

<p>Transfer complete flag</p>

#### ftf field

<p>FIFO threshold flag</p>

#### smf field

<p>Status match flag</p>

#### tof field

<p>Timeout flag</p>

#### busy field

<p>Busy flag</p>

#### flevel field

<p>FIFO level</p>

### FCR register

- Absolute Address: 0x40003018
- Base Offset: 0x18
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 |   ctef   |  rw  | 0x0 |  — |
|  1 |   ctcf   |  rw  | 0x0 |  — |
|  3 |   csmf   |  rw  | 0x0 |  — |
|  4 |   ctof   |  rw  | 0x0 |  — |

#### ctef field

<p>Clear transfer error flag</p>

#### ctcf field

<p>Clear transfer complete flag</p>

#### csmf field

<p>Clear status match flag</p>

#### ctof field

<p>Clear timeout flag</p>

### DLR register

- Absolute Address: 0x40003020
- Base Offset: 0x20
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0|    dl    |  rw  | 0x0 |  — |

#### dl field

<p>Number of bytes to transfer (value+1)</p>

### CCR register

- Absolute Address: 0x40003028
- Base Offset: 0x28
- Size: 0x4

| Bits|Identifier|Access|Reset|Name|
|-----|----------|------|-----|----|
| 7:0 |   instr  |  rw  | 0x0 |  — |
| 9:8 |   imode  |  rw  | 0x0 |  — |
|11:10|  admode  |  rw  | 0x0 |  — |
|13:12|  adsize  |  rw  | 0x0 |  — |
|15:14|  abmode  |  rw  | 0x0 |  — |
|17:16|  absize  |  rw  | 0x0 |  — |
|22:18|   dcyc   |  rw  | 0x0 |  — |
|  23 |  d_conf  |  rw  | 0x0 |  — |
|25:24|   dmode  |  rw  | 0x0 |  — |
|27:26|   fmode  |  rw  | 0x0 |  — |
|  28 |   sioo   |  rw  | 0x0 |  — |
|  30 |   dhhc   |  rw  | 0x0 |  — |
|  31 |   ddrm   |  rw  | 0x0 |  — |

#### instr field

<p>Instruction opcode</p>

#### imode field

<p>Instruction mode</p>

#### admode field

<p>Address mode</p>

#### adsize field

<p>Address size</p>

#### abmode field

<p>Alternate byte mode</p>

#### absize field

<p>Alternate byte size</p>

#### dcyc field

<p>Dummy cycles</p>

#### d_conf field

<p>Dummy confirmation</p>

#### dmode field

<p>Data mode</p>

#### fmode field

<p>Functional mode</p>

#### sioo field

<p>Send instruction only once</p>

#### dhhc field

<p>DDR hold quarter cycle</p>

#### ddrm field

<p>DDR mode enable</p>

### AR register

- Absolute Address: 0x40003030
- Base Offset: 0x30
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0|  address |  rw  | 0x0 |  — |

#### address field

<p>Flash address</p>

### ABR register

- Absolute Address: 0x40003038
- Base Offset: 0x38
- Size: 0x4

|Bits|   Identifier  |Access|Reset|Name|
|----|---------------|------|-----|----|
|31:0|alternate_bytes|  rw  | 0x0 |  — |

#### alternate_bytes field

<p>Alternate bytes</p>

### DR register

- Absolute Address: 0x40003040
- Base Offset: 0x40
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0|   data   |  rw  | 0x0 |  — |

#### data field

<p>Data register (FIFO access)</p>

### PSMKR register

- Absolute Address: 0x40003048
- Base Offset: 0x48
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0|   mask   |  rw  | 0x0 |  — |

#### mask field

<p>Polling status mask</p>

### PSMAR register

- Absolute Address: 0x40003050
- Base Offset: 0x50
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0|   match  |  rw  | 0x0 |  — |

#### match field

<p>Polling status match value</p>

### PIR register

- Absolute Address: 0x40003058
- Base Offset: 0x58
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0| interval |  rw  | 0x0 |  — |

#### interval field

<p>Polling interval in clock cycles</p>

### LPTR register

- Absolute Address: 0x40003060
- Base Offset: 0x60
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0|  timeout |  rw  | 0x0 |  — |

#### timeout field

<p>Low power timeout value</p>

## uart_registers address map

- Absolute Address: 0x40004000
- Base Offset: 0x40004000
- Size: 0x44

<p>UART Registers Refer shakti GC doc for details</p>

|Offset| Identifier |Name|
|------|------------|----|
| 0x00 |   BaudReg  |  — |
| 0x08 |    TxReg   |  — |
| 0x10 |    RxReg   |  — |
| 0x18 |  StatusReg |  — |
| 0x20 |  DelayReg  |  — |
| 0x28 | ControlReg |  — |
| 0x30 | InterruptEn|  — |
| 0x38 |     IQC    |  — |
| 0x40 |Rx_Threshold|  — |

### BaudReg register

- Absolute Address: 0x40004000
- Base Offset: 0x0
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|15:0|baud_value|  rw  | 0x5 |  — |

#### baud_value field

<p>Baud = Clk_Freq/(16* baud_value)</p>

### TxReg register

- Absolute Address: 0x40004008
- Base Offset: 0x8
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0|   data   |   w  | 0x0 |  — |

#### data field



### RxReg register

- Absolute Address: 0x40004010
- Base Offset: 0x10
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0|   data   |   r  | 0x0 |  — |

#### data field



### StatusReg register

- Absolute Address: 0x40004018
- Base Offset: 0x18
- Size: 0x4

|Bits|    Identifier   |Access|Reset|Name|
|----|-----------------|------|-----|----|
|  0 |     tx_empty    |   r  | 0x0 |  — |
|  1 |     tx_full     |   r  | 0x0 |  — |
|  2 |   rx_notEmpty   |   r  | 0x0 |  — |
|  3 |     rx_full     |   r  | 0x0 |  — |
|  4 |   parity_error  |   r  | 0x0 |  — |
|  5 |  overrun_error  |   r  | 0x0 |  — |
|  6 |   frame_error   |   r  | 0x0 |  — |
|  7 |   break_error   |   r  | 0x0 |  — |
|  8 |rx_fifo_threshold|   r  | 0x0 |  — |

#### tx_empty field

<p>Tx FIFO is Empty</p>

#### tx_full field

<p>Tx FIFO is Full</p>

#### rx_notEmpty field

<p>Rx FIFO is Not Empty</p>

#### rx_full field

<p>Rx FIFO is Full</p>

#### parity_error field

<p>Rx Parity error</p>

#### overrun_error field

<p>Rx FIFO overflow</p>

#### frame_error field

<p>Rx stop bit is zero</p>

#### break_error field

<p>Rx Data and stop bits are zero</p>

#### rx_fifo_threshold field

<p>Threshold level crossed on Rx.</p>

### DelayReg register

- Absolute Address: 0x40004020
- Base Offset: 0x20
- Size: 0x4

|Bits|  Identifier |Access|Reset|Name|
|----|-------------|------|-----|----|
|15:0|delay_control|  rw  | 0x0 |  — |

#### delay_control field

<p>Transmit delay count</p>

### ControlReg register

- Absolute Address: 0x40004028
- Base Offset: 0x28
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 2:1| stopbits |  rw  | 0x0 |  — |
| 4:3|  parity  |  rw  | 0x0 |  — |
|10:5| charsize |  rw  | 0x8 |  — |

#### stopbits field

<p>00 -&gt; 1 stop bit; 01 -&gt; 1.5 stop bits ; 10 -&gt; 2 stop bits</p>

#### parity field

<p>0-&gt; no parity, 1 -&gt; odd parity; 2 -&gt; even parity</p>

#### charsize field

<p>char size of data (max 32b)</p>

### InterruptEn register

- Absolute Address: 0x40004030
- Base Offset: 0x30
- Size: 0x4

|Bits|     Identifier     |Access|Reset|Name|
|----|--------------------|------|-----|----|
|  0 |     tx_done_en     |  rw  | 0x0 |  — |
|  1 |   tx_not_full_en   |  rw  | 0x0 |  — |
|  2 |   rx_not_full_en   |  rw  | 0x0 |  — |
|  3 |   rx_not_empty_en  |  rw  | 0x0 |  — |
|  4 |   parity_error_en  |  rw  | 0x0 |  — |
|  5 |  overrun_error_en  |  rw  | 0x0 |  — |
|  6 |   frame_error_en   |  rw  | 0x0 |  — |
|  7 |   break_error_en   |  rw  | 0x0 |  — |
|  8 |rx_fifo_threshold_en|  rw  | 0x0 |  — |

#### tx_done_en field

<p>Transmission Done Interrupt Enable</p>

#### tx_not_full_en field

<p>Transmitter Not Full Interrupt Enable</p>

#### rx_not_full_en field

<p>Receiver Not Full Interrupt Enable</p>

#### rx_not_empty_en field

<p>Receiver Not Empty Interrupt Enable</p>

#### parity_error_en field

<p>Parity Error Interrupt Enable</p>

#### overrun_error_en field

<p>Overrun Interrupt Enable</p>

#### frame_error_en field

<p>Frame Error Interrupt Enable</p>

#### break_error_en field

<p>Break Error Interrupt Enable</p>

#### rx_fifo_threshold_en field

<p>RX FIFO ~80% Full Interrupt Enable</p>

### IQC register

- Absolute Address: 0x40004038
- Base Offset: 0x38
- Size: 0x4

|Bits| Identifier|Access|Reset|Name|
|----|-----------|------|-----|----|
| 7:0|qual_cycles|  rw  | 0x0 |  — |

#### qual_cycles field



### Rx_Threshold register

- Absolute Address: 0x40004040
- Base Offset: 0x40
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 7:0| rx_level |  rw  | 0x5 |  — |

#### rx_level field



## ROMRAM address map

- Absolute Address: 0x40008000
- Base Offset: 0x40008000
- Size: 0x5000

|Offset|Identifier|  Name |
|------|----------|-------|
|0x0000|    ROM   |BootROM|
|0x4000|   SRAM   |  SRAM |

## ROM memory

- Absolute Address: 0x40008000
- Base Offset: 0x0
- Size: 0x2000

No supported members.


## SRAM memory

- Absolute Address: 0x4000C000
- Base Offset: 0x4000
- Size: 0x1000

No supported members.


## cpu_registers address map

- Absolute Address: 0x80000000
- Base Offset: 0x80000000
- Size: 0xF40318

| Offset |  Identifier  |   Name   |
|--------|--------------|----------|
|0x100000|  User_neigh  |  U_neigh |
|0x340000|   User_cpu   |   U_cpu  |
|0x740000|Supervisor_cpu|   S_cpu  |
|0x800000|  D_hart_esr  |D_hart_esr|
|0x900000|    D_neigh   |  D_neigh |
|0xB5F000|     D_cpu    |   D_cpu  |
|0xD00000| Machine_neigh|  M_neigh |
|0xF40000|  Machine_cpu |   M_cpu  |

## User_neigh address map

- Absolute Address: 0x80100000
- Base Offset: 0x100000
- Size: 0x48

|Offset|   Identifier  |      Name     |
|------|---------------|---------------|
| 0x40 |ipi_redirect_pc|ipi_redirect_pc|

### ipi_redirect_pc register

- Absolute Address: 0x80100040
- Base Offset: 0x40
- Size: 0x8

|Bits|   Identifier  |Access|Reset|Name|
|----|---------------|------|-----|----|
|47:0|ipi_redirect_pc|  rw  | 0x0 |  — |

#### ipi_redirect_pc field

<p>In bits 47:0 of this register, user-level software writes the 48 least significant bits of a target virtual PC of a redirect IPI for all the 
harts in a given neighborhood.Also, bit 0 of the PC is always 0</p>

## User_cpu address map

- Absolute Address: 0x80340000
- Base Offset: 0x340000
- Size: 0x300

|Offset|     Identifier     |        Name        |
|------|--------------------|--------------------|
| 0x080|ipi_redirect_trigger|ipi_redirect_trigger|
| 0x0C0|      CREDINC0      |      CREDINC0      |
| 0x0C8|      CREDINC1      |      CREDINC1      |
| 0x0D0|      CREDINC2      |      CREDINC2      |
| 0x0D8|      CREDINC3      |      CREDINC3      |
| 0x100| fast_local_barrier0| fast_local_barrier0|
| 0x108| fast_local_barrier1| fast_local_barrier1|
| 0x110| fast_local_barrier2| fast_local_barrier2|
| 0x118| fast_local_barrier3| fast_local_barrier3|
| 0x120| fast_local_barrier4| fast_local_barrier4|
| 0x128| fast_local_barrier5| fast_local_barrier5|
| 0x130| fast_local_barrier6| fast_local_barrier6|
| 0x138| fast_local_barrier7| fast_local_barrier7|
| 0x140| fast_local_barrier8| fast_local_barrier8|
| 0x148| fast_local_barrier9| fast_local_barrier9|
| 0x150|fast_local_barrier10|fast_local_barrier10|
| 0x158|fast_local_barrier11|fast_local_barrier11|
| 0x160|fast_local_barrier12|fast_local_barrier12|
| 0x168|fast_local_barrier13|fast_local_barrier13|
| 0x170|fast_local_barrier14|fast_local_barrier14|
| 0x178|fast_local_barrier15|fast_local_barrier15|
| 0x180|fast_local_barrier16|fast_local_barrier16|
| 0x188|fast_local_barrier17|fast_local_barrier17|
| 0x190|fast_local_barrier18|fast_local_barrier18|
| 0x198|fast_local_barrier19|fast_local_barrier19|
| 0x1A0|fast_local_barrier20|fast_local_barrier20|
| 0x1A8|fast_local_barrier21|fast_local_barrier21|
| 0x1B0|fast_local_barrier22|fast_local_barrier22|
| 0x1B8|fast_local_barrier23|fast_local_barrier23|
| 0x1C0|fast_local_barrier24|fast_local_barrier24|
| 0x1C8|fast_local_barrier25|fast_local_barrier25|
| 0x1D0|fast_local_barrier26|fast_local_barrier26|
| 0x1D8|fast_local_barrier27|fast_local_barrier27|
| 0x1E0|fast_local_barrier28|fast_local_barrier28|
| 0x1E8|fast_local_barrier29|fast_local_barrier29|
| 0x1F0|fast_local_barrier30|fast_local_barrier30|
| 0x1F8|fast_local_barrier31|fast_local_barrier31|
| 0x2F8|  icache_uprefetch  |  icache_uprefetch  |

### ipi_redirect_trigger register

- Absolute Address: 0x80340080
- Base Offset: 0x80
- Size: 0x8

|Bits|     Identifier     |Access|Reset|Name|
|----|--------------------|------|-----|----|
|15:0|ipi_redirect_trigger|  rw  |  —  |  — |

#### ipi_redirect_trigger field

<p>User-level software writes a bitmask to this register to request an IPI redirect to all harts indicated by the mask. Before delivery, the bitmask is unconditionally ANDed with the value in IPI_REDIRECT_FILTER. The register is encoded as follows:
Bit 0: Minion 0, hart 0
Bit 1: Minion 0, hart 1
Bit 2: Minion 1, hart 0
Bit 3: Minion 1, hart 1
…
Bit 12: Minion 6, hart 0
Bit 13: Minion 6, hart 1
Bit 14: Minion 7, hart 0
Bit 15: Minion 7, hart 1
When a redirect IPI is delivered to a hart, that hart must satisfy two conditions, It must be executing in user mode. It must be capable of blocking on a stall CSR read instruction.If either condition is violated, 
the hart must take a trap into M-mode with, mcause set to Bad IPI redirect interrupt (5'h10), mtval set to the redirection PC.
Reading this register returns a 0x0 value</p>

### CREDINC0 register

- Absolute Address: 0x803400C0
- Base Offset: 0xC0
- Size: 0x8

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 7:0|   mask0  |   r  |  —  |  — |

#### mask0 field

<p>Writing this register increments the COUNTER0 credit counter for the first hart of all the cores selected in MASK0. Reading this register returns a value of 0.</p>

### CREDINC1 register

- Absolute Address: 0x803400C8
- Base Offset: 0xC8
- Size: 0x8

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 7:0|   mask1  |   r  |  —  |  — |

#### mask1 field

<p>Writing this register increments the COUNTER1 credit counter for the first hart of all the cores selected in MASK1.</p>

### CREDINC2 register

- Absolute Address: 0x803400D0
- Base Offset: 0xD0
- Size: 0x8

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 7:0|   mask2  |   r  |  —  |  — |

#### mask2 field

<p>Writing this register increments the COUNTER2 credit counter for the first hart of all the cores selected in MASK2. Reading this register returns a value of 0.</p>

### CREDINC3 register

- Absolute Address: 0x803400D8
- Base Offset: 0xD8
- Size: 0x8

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 7:0|   mask3  |   r  |  —  |  — |

#### mask3 field

<p>Writing this register increments the COUNTER3 credit counter for the first hart of all the cores selected in MASK3. Reading this register returns a value of 0.</p>

### fast_local_barrier0 register

- Absolute Address: 0x80340100
- Base Offset: 0x100
- Size: 0x8

|Bits|     Identifier    |Access|Reset|Name|
|----|-------------------|------|-----|----|
| 7:0|fast_local_barrier0|  rw  | 0x0 |  — |

#### fast_local_barrier0 field

<p>The Esperanto Fast Local Barrier (FLB) extension registers provide fast barrier capabilities across the Minions within a Shire. Multiple barrier counters allow a subset of threads in a Shire to atomically modify a barrier counter and determine whether all participating threads have reached the barrier.<br />
The FLB extension provides 32 barrier counters, each 8 bits wide, supporting an all-thread (64 threads) barrier in the Shire. Barrier counter i should be initialized by software before starting the barrier operation using a regular RISC-V store instruction to address (address + i * 8). Software typically initializes barrier counters to zero, 
but any value from 0 to 255 is legal.  For maximum performance, FLB counters are directly accessible by threads in the Shire using CSRRW instructions. Threads participating in a barrier use CSRRW to atomically increment the barrier counter. If a thread is the last to join the barrier,
the CSRRW returns 0x1; otherwise, it returns 0x0.</p>

### fast_local_barrier1 register

- Absolute Address: 0x80340108
- Base Offset: 0x108
- Size: 0x8

|Bits|     Identifier    |Access|Reset|Name|
|----|-------------------|------|-----|----|
| 7:0|fast_local_barrier1|  rw  | 0x0 |  — |

#### fast_local_barrier1 field

<p>see description for fast_local_barrier_0</p>

### fast_local_barrier2 register

- Absolute Address: 0x80340110
- Base Offset: 0x110
- Size: 0x8

|Bits|     Identifier    |Access|Reset|Name|
|----|-------------------|------|-----|----|
| 7:0|fast_local_barrier2|  rw  | 0x0 |  — |

#### fast_local_barrier2 field

<p>see description for fast_local_barrier_0</p>

### fast_local_barrier3 register

- Absolute Address: 0x80340118
- Base Offset: 0x118
- Size: 0x8

|Bits|     Identifier    |Access|Reset|Name|
|----|-------------------|------|-----|----|
| 7:0|fast_local_barrier3|  rw  | 0x0 |  — |

#### fast_local_barrier3 field

<p>see description for fast_local_barrier_0</p>

### fast_local_barrier4 register

- Absolute Address: 0x80340120
- Base Offset: 0x120
- Size: 0x8

|Bits|     Identifier    |Access|Reset|Name|
|----|-------------------|------|-----|----|
| 7:0|fast_local_barrier4|  rw  | 0x0 |  — |

#### fast_local_barrier4 field

<p>see description for fast_local_barrier_0</p>

### fast_local_barrier5 register

- Absolute Address: 0x80340128
- Base Offset: 0x128
- Size: 0x8

|Bits|     Identifier    |Access|Reset|Name|
|----|-------------------|------|-----|----|
| 7:0|fast_local_barrier5|  rw  | 0x0 |  — |

#### fast_local_barrier5 field

<p>see description for fast_local_barrier_0</p>

### fast_local_barrier6 register

- Absolute Address: 0x80340130
- Base Offset: 0x130
- Size: 0x8

|Bits|     Identifier    |Access|Reset|Name|
|----|-------------------|------|-----|----|
| 7:0|fast_local_barrier6|  rw  | 0x0 |  — |

#### fast_local_barrier6 field

<p>see description for fast_local_barrier_0</p>

### fast_local_barrier7 register

- Absolute Address: 0x80340138
- Base Offset: 0x138
- Size: 0x8

|Bits|     Identifier    |Access|Reset|Name|
|----|-------------------|------|-----|----|
| 7:0|fast_local_barrier7|  rw  | 0x0 |  — |

#### fast_local_barrier7 field

<p>see description for fast_local_barrier_0</p>

### fast_local_barrier8 register

- Absolute Address: 0x80340140
- Base Offset: 0x140
- Size: 0x8

|Bits|     Identifier    |Access|Reset|Name|
|----|-------------------|------|-----|----|
| 7:0|fast_local_barrier8|  rw  | 0x0 |  — |

#### fast_local_barrier8 field

<p>see description for fast_local_barrier_0</p>

### fast_local_barrier9 register

- Absolute Address: 0x80340148
- Base Offset: 0x148
- Size: 0x8

|Bits|     Identifier    |Access|Reset|Name|
|----|-------------------|------|-----|----|
| 7:0|fast_local_barrier9|  rw  | 0x0 |  — |

#### fast_local_barrier9 field

<p>see description for fast_local_barrier_0</p>

### fast_local_barrier10 register

- Absolute Address: 0x80340150
- Base Offset: 0x150
- Size: 0x8

|Bits|     Identifier     |Access|Reset|Name|
|----|--------------------|------|-----|----|
| 7:0|fast_local_barrier10|  rw  | 0x0 |  — |

#### fast_local_barrier10 field

<p>see description for fast_local_barrier_0</p>

### fast_local_barrier11 register

- Absolute Address: 0x80340158
- Base Offset: 0x158
- Size: 0x8

|Bits|     Identifier     |Access|Reset|Name|
|----|--------------------|------|-----|----|
| 7:0|fast_local_barrier11|  rw  | 0x0 |  — |

#### fast_local_barrier11 field

<p>see description for fast_local_barrier_0</p>

### fast_local_barrier12 register

- Absolute Address: 0x80340160
- Base Offset: 0x160
- Size: 0x8

|Bits|     Identifier     |Access|Reset|Name|
|----|--------------------|------|-----|----|
| 7:0|fast_local_barrier12|  rw  | 0x0 |  — |

#### fast_local_barrier12 field

<p>see description for fast_local_barrier_0</p>

### fast_local_barrier13 register

- Absolute Address: 0x80340168
- Base Offset: 0x168
- Size: 0x8

|Bits|     Identifier     |Access|Reset|Name|
|----|--------------------|------|-----|----|
| 7:0|fast_local_barrier13|  rw  | 0x0 |  — |

#### fast_local_barrier13 field

<p>see description for fast_local_barrier_0</p>

### fast_local_barrier14 register

- Absolute Address: 0x80340170
- Base Offset: 0x170
- Size: 0x8

|Bits|     Identifier     |Access|Reset|Name|
|----|--------------------|------|-----|----|
| 7:0|fast_local_barrier14|  rw  | 0x0 |  — |

#### fast_local_barrier14 field

<p>see description for fast_local_barrier_0</p>

### fast_local_barrier15 register

- Absolute Address: 0x80340178
- Base Offset: 0x178
- Size: 0x8

|Bits|     Identifier     |Access|Reset|Name|
|----|--------------------|------|-----|----|
| 7:0|fast_local_barrier15|  rw  | 0x0 |  — |

#### fast_local_barrier15 field

<p>see description for fast_local_barrier_0</p>

### fast_local_barrier16 register

- Absolute Address: 0x80340180
- Base Offset: 0x180
- Size: 0x8

|Bits|     Identifier     |Access|Reset|Name|
|----|--------------------|------|-----|----|
| 7:0|fast_local_barrier16|  rw  | 0x0 |  — |

#### fast_local_barrier16 field

<p>see description for fast_local_barrier_0</p>

### fast_local_barrier17 register

- Absolute Address: 0x80340188
- Base Offset: 0x188
- Size: 0x8

|Bits|     Identifier     |Access|Reset|Name|
|----|--------------------|------|-----|----|
| 7:0|fast_local_barrier17|  rw  | 0x0 |  — |

#### fast_local_barrier17 field

<p>see description for fast_local_barrier_0</p>

### fast_local_barrier18 register

- Absolute Address: 0x80340190
- Base Offset: 0x190
- Size: 0x8

|Bits|     Identifier     |Access|Reset|Name|
|----|--------------------|------|-----|----|
| 7:0|fast_local_barrier18|  rw  | 0x0 |  — |

#### fast_local_barrier18 field

<p>see description for fast_local_barrier_0</p>

### fast_local_barrier19 register

- Absolute Address: 0x80340198
- Base Offset: 0x198
- Size: 0x8

|Bits|     Identifier     |Access|Reset|Name|
|----|--------------------|------|-----|----|
| 7:0|fast_local_barrier19|  rw  | 0x0 |  — |

#### fast_local_barrier19 field

<p>see description for fast_local_barrier_0</p>

### fast_local_barrier20 register

- Absolute Address: 0x803401A0
- Base Offset: 0x1A0
- Size: 0x8

|Bits|     Identifier     |Access|Reset|Name|
|----|--------------------|------|-----|----|
| 7:0|fast_local_barrier20|  rw  | 0x0 |  — |

#### fast_local_barrier20 field

<p>see description for fast_local_barrier_0</p>

### fast_local_barrier21 register

- Absolute Address: 0x803401A8
- Base Offset: 0x1A8
- Size: 0x8

|Bits|     Identifier     |Access|Reset|Name|
|----|--------------------|------|-----|----|
| 7:0|fast_local_barrier21|  rw  | 0x0 |  — |

#### fast_local_barrier21 field

<p>see description for fast_local_barrier_0</p>

### fast_local_barrier22 register

- Absolute Address: 0x803401B0
- Base Offset: 0x1B0
- Size: 0x8

|Bits|     Identifier     |Access|Reset|Name|
|----|--------------------|------|-----|----|
| 7:0|fast_local_barrier22|  rw  | 0x0 |  — |

#### fast_local_barrier22 field

<p>see description for fast_local_barrier_0</p>

### fast_local_barrier23 register

- Absolute Address: 0x803401B8
- Base Offset: 0x1B8
- Size: 0x8

|Bits|     Identifier     |Access|Reset|Name|
|----|--------------------|------|-----|----|
| 7:0|fast_local_barrier23|  rw  | 0x0 |  — |

#### fast_local_barrier23 field

<p>see description for fast_local_barrier_0</p>

### fast_local_barrier24 register

- Absolute Address: 0x803401C0
- Base Offset: 0x1C0
- Size: 0x8

|Bits|     Identifier     |Access|Reset|Name|
|----|--------------------|------|-----|----|
| 7:0|fast_local_barrier24|  rw  | 0x0 |  — |

#### fast_local_barrier24 field

<p>see description for fast_local_barrier_0</p>

### fast_local_barrier25 register

- Absolute Address: 0x803401C8
- Base Offset: 0x1C8
- Size: 0x8

|Bits|     Identifier     |Access|Reset|Name|
|----|--------------------|------|-----|----|
| 7:0|fast_local_barrier25|  rw  | 0x0 |  — |

#### fast_local_barrier25 field

<p>see description for fast_local_barrier_0</p>

### fast_local_barrier26 register

- Absolute Address: 0x803401D0
- Base Offset: 0x1D0
- Size: 0x8

|Bits|     Identifier     |Access|Reset|Name|
|----|--------------------|------|-----|----|
| 7:0|fast_local_barrier26|  rw  | 0x0 |  — |

#### fast_local_barrier26 field

<p>see description for fast_local_barrier_0</p>

### fast_local_barrier27 register

- Absolute Address: 0x803401D8
- Base Offset: 0x1D8
- Size: 0x8

|Bits|     Identifier     |Access|Reset|Name|
|----|--------------------|------|-----|----|
| 7:0|fast_local_barrier27|  rw  | 0x0 |  — |

#### fast_local_barrier27 field

<p>see description for fast_local_barrier_0</p>

### fast_local_barrier28 register

- Absolute Address: 0x803401E0
- Base Offset: 0x1E0
- Size: 0x8

|Bits|     Identifier     |Access|Reset|Name|
|----|--------------------|------|-----|----|
| 7:0|fast_local_barrier28|  rw  | 0x0 |  — |

#### fast_local_barrier28 field

<p>see description for fast_local_barrier_0</p>

### fast_local_barrier29 register

- Absolute Address: 0x803401E8
- Base Offset: 0x1E8
- Size: 0x8

|Bits|     Identifier     |Access|Reset|Name|
|----|--------------------|------|-----|----|
| 7:0|fast_local_barrier29|  rw  | 0x0 |  — |

#### fast_local_barrier29 field

<p>see description for fast_local_barrier_0</p>

### fast_local_barrier30 register

- Absolute Address: 0x803401F0
- Base Offset: 0x1F0
- Size: 0x8

|Bits|     Identifier     |Access|Reset|Name|
|----|--------------------|------|-----|----|
| 7:0|fast_local_barrier30|  rw  | 0x0 |  — |

#### fast_local_barrier30 field

<p>see description for fast_local_barrier_0</p>

### fast_local_barrier31 register

- Absolute Address: 0x803401F8
- Base Offset: 0x1F8
- Size: 0x8

|Bits|     Identifier     |Access|Reset|Name|
|----|--------------------|------|-----|----|
| 7:0|fast_local_barrier31|  rw  | 0x0 |  — |

#### fast_local_barrier31 field

<p>see description for fast_local_barrier_0</p>

### icache_uprefetch register

- Absolute Address: 0x803402F8
- Base Offset: 0x2F8
- Size: 0x8

<p>If no prefetch with a higher privilege mode associated with it is in progress, a write in this ESR prefetches Count+1 consecutive lines starting at address Address to the instruction cache.
                The privilege mode associated with this operation is User-mode, and all memory accesses are performed with User-mode privileges.
                If any of the memory requests generated by the prefetch engine generates an exception, the line is not prefetched and the operation continues with the next line.
                Reading this register returns the idle status of the prefetch engine.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 5:0|   count  |  rw  | 0x0 |  — |
|47:6|  address |  rw  |  —  |  — |

#### count field

<p>Number of lines to be prefetched (minus 1) starting at the given Address.</p>

#### address field

<p>Bits [47:6] of the address where prefetching should start from (aligned to a cacheline).</p>

## Supervisor_cpu address map

- Absolute Address: 0x80740000
- Base Offset: 0x740000
- Size: 0x308

|Offset|   Identifier   |      Name      |
|------|----------------|----------------|
| 0x290| shire_coop_mode| shire_coop_mode|
| 0x300|icache_sprefetch|icache_sprefetch|

### shire_coop_mode register

- Absolute Address: 0x80740290
- Base Offset: 0x290
- Size: 0x8

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | coop_mode|  rw  | 0x0 |  — |

#### coop_mode field

<p>Software can set this bit to enable cooperative prefetches, loads, and stores.</p>

### icache_sprefetch register

- Absolute Address: 0x80740300
- Base Offset: 0x300
- Size: 0x8

<p>If no prefetch with a higher privilege mode associated with it is in progress, a write in this ESR prefetches Count+1 consecutive lines starting at address Address to the instruction caches.
                The privilege mode associated with this operation is Supervisor-mode, and all memory accesses are performed with Supervisor-mode privileges.
                If any of the memory requests generated by the prefetch engine generates an exception, the line is not prefetched and the operation continues with the next line.
                Reading this register returns the idle status of the prefetch engine.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 5:0|   count  |  rw  | 0x0 |  — |
|47:6|  address |  rw  |  —  |  — |

#### count field

<p>Number of lines to be prefetched (minus 1) starting at the given Address.</p>

#### address field

<p>Bits [47:6] of the address where prefetching should start from (aligned to a cacheline).</p>

## D_hart_esr address map

- Absolute Address: 0x80800000
- Base Offset: 0x800000
- Size: 0xF7C8

<p>These registers are per hart.([15:12] bits) in the address indicates hart_id. bits[15:13] minion id and bit [12] is thread id.In table below all these bits are indicated as 1</p>

|Offset| Identifier|    Name   |
|------|-----------|-----------|
|0xF780|  NXDATA0  |  NXDATA0  |
|0xF788|  NXDATA1  |  NXDATA1  |
|0xF790|  AXDATA0  |  AXDATA0  |
|0xF798|  AXDATA1  |  AXDATA1  |
|0xF7A0|AXPROGBUFF0|AXPROGBUFF0|
|0xF7A8|AXPROGBUFF1|AXPROGBUFF1|
|0xF7B0|NXPROGBUFF0|NXPROGBUFF0|
|0xF7B8|NXPROGBUFF1|NXPROGBUFF1|
|0xF7C0|   ABSCMD  |   ABSCMD  |

### NXDATA0 register

- Absolute Address: 0x8080F780
- Base Offset: 0xF780
- Size: 0x8

| Bits|Identifier|Access|Reset|Name|
|-----|----------|------|-----|----|
| 31:0|NXDATA0_f0|  rw  |  —  |  — |
|63:32|NXDATA0_f1|  rw  |  —  |  — |

#### NXDATA0_f0 field

<p>The low (nxdata0)  of ddata0</p>

#### NXDATA0_f1 field

<p>WIRI</p>

### NXDATA1 register

- Absolute Address: 0x8080F788
- Base Offset: 0xF788
- Size: 0x8

| Bits|Identifier|Access|Reset|Name|
|-----|----------|------|-----|----|
| 31:0|NXDATA1_f0|  rw  |  —  |  — |
|63:32|NXDATA1_f1|  rw  |  —  |  — |

#### NXDATA1_f0 field

<p>The high (nxdata0)  of ddata0</p>

#### NXDATA1_f1 field

<p>WIRI</p>

### AXDATA0 register

- Absolute Address: 0x8080F790
- Base Offset: 0xF790
- Size: 0x8

| Bits|Identifier|Access|Reset|Name|
|-----|----------|------|-----|----|
| 31:0|AXDATA0_f0|  rw  |  —  |  — |
|63:32|AXDATA0_f1|  rw  |  —  |  — |

#### AXDATA0_f0 field

<p>This register is shadow, and have the same layout as the nxdata0 register. A write to this register "wakes up" a halted hart, after ddata0 is written, and starts execution from the beginning of the instruction buffer</p>

### AXDATA1 register

- Absolute Address: 0x8080F798
- Base Offset: 0xF798
- Size: 0x8

| Bits|Identifier|Access|Reset|Name|
|-----|----------|------|-----|----|
| 31:0|AXDATA1_f0|  rw  |  —  |  — |
|63:32|AXDATA1_f1|  rw  |  —  |  — |

#### AXDATA1_f0 field

<p>This register is shadow, and have the same layout as the nxdata1 register. A write to this register "wakes up" a halted hart, after ddata0 is written, and starts execution from the beginning of the instruction buffer.</p>

### AXPROGBUFF0 register

- Absolute Address: 0x8080F7A0
- Base Offset: 0xF7A0
- Size: 0x8

|Bits| Identifier|Access|Reset|Name|
|----|-----------|------|-----|----|
|31:0|AXPROGBUFF0|  rw  |  —  |  — |

#### AXPROGBUFF0 field

<p>This register shadows the nxprogbuf0 register. A write to this register wakes up a halted hart, after the instruction buffer is written, and starts execution from the beginning of the instruction buffer, until either an ebreak instruction is executed or the end of the instruction buffer is reached, at which point the hart goes back to being halted.</p>

### AXPROGBUFF1 register

- Absolute Address: 0x8080F7A8
- Base Offset: 0xF7A8
- Size: 0x8

|Bits| Identifier|Access|Reset|Name|
|----|-----------|------|-----|----|
|31:0|AXPROGBUFF1|  rw  |  —  |  — |

#### AXPROGBUFF1 field

<p>This register shadows the nxprogbuf1 register. A write to this register wakes up a halted hart, after the instruction buffer is written, and starts execution from the beginning of the instruction buffer, until either an ebreak instruction is executed or the end of the instruction buffer is reached, at which point the hart goes back to being halted.</p>

### NXPROGBUFF0 register

- Absolute Address: 0x8080F7B0
- Base Offset: 0xF7B0
- Size: 0x8

|Bits| Identifier|Access|Reset|Name|
|----|-----------|------|-----|----|
|31:0|NXPROGBUFF0|  rw  |  —  |  — |

#### NXPROGBUFF0 field

<p>This register holds bits 64-95 of the instruction buffer from where instructions can be executed when the hart is halted (see also abscmd), encoded in the lower half of the register.</p>

### NXPROGBUFF1 register

- Absolute Address: 0x8080F7B8
- Base Offset: 0xF7B8
- Size: 0x8

|Bits| Identifier|Access|Reset|Name|
|----|-----------|------|-----|----|
|31:0|NXPROGBUFF1|  rw  |  —  |  — |

#### NXPROGBUFF1 field

<p>This register holds bits 96-127 of the instruction buffer from where instructions can be executed when the hart is halted (see also abscmd), encoded in the lower half of the register.</p>

### ABSCMD register

- Absolute Address: 0x8080F7C0
- Base Offset: 0xF7C0
- Size: 0x8

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|63:0|  ABSCMD  |  rw  |  —  |  — |

#### ABSCMD field

<p>This register holds bits 0-63 of the instruction buffer from where instructions can be executed when the hart is halted. The first instruction in the buffer is in the lower order 16 or 32 bits of the ABSCMD register. Writing to this register wakes up a halted hart, after the instruction buffer is written, and starts execution from the beginning of the instruction buffer, until either an ebreak instruction is executed or the end of the instruction buffer is reached, at which point the hart goes back to being halted.</p>

## D_neigh address map

- Absolute Address: 0x80900000
- Base Offset: 0x900000
- Size: 0xFFA0

|Offset|  Identifier  |     Name     |
|------|--------------|--------------|
|0xFF80|    hactrl    |    hactrl    |
|0xFF88|   hastatus0  |   hastatus0  |
|0xFF90|   hastatus1  |   hastatus1  |
|0xFF98|and_or_tree_IO|and_or_tree_IO|

### hactrl register

- Absolute Address: 0x8090FF80
- Base Offset: 0xFF80
- Size: 0x8

| Bits|Identifier|Access|Reset|Name|
|-----|----------|------|-----|----|
| 15:0| hawindow |  rw  | 0x0 |  — |
|31:16| hart_mask|  rw  | 0x0 |  — |
|47:32| resethalt|   r  | 0x0 |  — |

#### hawindow field

<p>The n-th bit selects the n-th hart in the neighborhood, if hasel is 1. Non-selected harts ignore the reset (except ndmreset), halt and resume requests from the DM.</p>

#### hart_mask field

<p>The n-th bit selects the n-th hart in the neighborhood (independent of the value of hasel). Non-selected harts ignore the reset (except ndmreset), halt and resume requests from the DM.</p>

#### resethalt field

<p>Each bit in this field corresponds to one hart in the neighborhood. While a given resethalt bit is asserted, the corresponding hart will halt upon the next deassertion of its reset. These bits are set for all selected harts when the setresethaltreq bit in the RISC-V Debug Module Control register (DMCTRL) is written. 
This field is cleared for all selected harts when the clrresethaltreq bit in the DMCTRL register is written.</p>

### hastatus0 register

- Absolute Address: 0x8090FF88
- Base Offset: 0xFF88
- Size: 0x8

| Bits|Identifier|Access|Reset|Name|
|-----|----------|------|-----|----|
| 15:0|  halted  |   r  | 0x0 |  — |
|31:16|  running |   r  | 0x0 |  — |
|47:32| resumeack|   r  | 0x0 |  — |
|63:48| havereset|   r  | 0x0 |  — |

#### halted field

<p>Each bit in this field corresponds to one of the 16 harts in the neighborhood. The sticky halted bit for a hart is asserted when the hart is in Debug Mode, and hardware clears this bit when the hart receives a reset or resume request.</p>

#### running field

<p>Each bit in this field corresponds to one of the 16 harts in the neighborhood. The sticky running bit for each hart is asserted when a hart finishes resuming execution, and hardware clears this bit when a hart receives a reset or halt request.</p>

#### resumeack field

<p>Each bit in this field corresponds to one of the 16 harts in the neighborhood. The sticky resumeack bit for a hart is asserted when a hart finishes resuming execution, and hardware clears this bit whenever the resumereq bit in the RISC-V Debug Module Control register (DMCTRL) is deasserted.</p>

#### havereset field

<p>Each bit in this field corresponds to one of the 16 harts in the neighborhood. The sticky havereset bit for a hart is asserted when a hart exits reset, and hardware clears this bit whenever the ackhavereset bit in the RISC-V Debug Module Control register (DMCTRL) is written.
Each ET-Minion core contains two harts; however, it is not possible to reset an individual hart within an ET-Minion core. Therefore, the havereset field can be implemented as eight physical bits, with bits 2m and 2m+1 corresponding to the m-th Minion hardwired to the same value.
For example, bits 0 and 1 correspond to the two harts in Minion core 0, but only one of these bits is required to reset both threads. Similarly, bits 2 and 3 correspond to ET-Minion core 1, and so on</p>

### hastatus1 register

- Absolute Address: 0x8090FF90
- Base Offset: 0xFF90
- Size: 0x8

| Bits|Identifier|Access|Reset|Name|
|-----|----------|------|-----|----|
| 15:0|   busy   |   r  | 0x0 |  — |
|31:16| exception|  rw  | 0x0 |  — |
|47:32|   error  |  rw  | 0x0 |  — |

#### busy field

<p>Each bit in this field corresponds to one of the 16 harts in the neighborhood, and a bit is set to 1 while the corresponding hart executes an Abstract Command or a Program Buffer program.</p>

#### exception field

<p>Each bit in this field corresponds to one of the 16 harts in the neighborhood. A bit is set to 1 if the execution of an Abstract Command or a Program Buffer program by the corresponding hart generates an exception. These bits are sticky and must be cleared using an explicit write to the register.</p>

#### error field

<p>Each bit in this field corresponds to one of the 16 harts in the neighborhood. A bit is set to 1 if the execution of an Abstract Command or a Program Buffer program by the corresponding hart cannot complete, but no exception is generated. 
Examples of this include writes to ET-Minion core registers such as abscmd, axprogbuf0, axprogbuf1, nxprogbuf0, nxprogbuf1, and so on. These bits are sticky and must be cleared using an explicit write to the register.</p>

### and_or_tree_IO register

- Absolute Address: 0x8090FF98
- Base Offset: 0xFF98
- Size: 0x8

|Bits|  Identifier  |Access|Reset|Name|
|----|--------------|------|-----|----|
|  0 |   anyhalted  |   r  |  —  |  — |
|  1 |   allhalted  |   r  |  —  |  — |
|  2 |  anyrunning  |   r  |  —  |  — |
|  3 |  allrunning  |   r  |  —  |  — |
|  4 | anyresumeack |   r  |  —  |  — |
|  5 | allresumeack |   r  |  —  |  — |
|  6 | anyhavereset |   r  |  —  |  — |
|  7 | allhavereset |   r  |  —  |  — |
|  8 |anyunavailable|   r  |  —  |  — |
|  9 |  anyselected |   r  |  —  |  — |

#### anyhalted field

<p>Hardware sets this bit whenever any of the 16 bits of the halted field in the Esperanto Neighborhood Hart Status 0 register for the selected harts is set, and the hasel bit in the RISC-V Debug Module Control register (DMCTRL) is 1.</p>

#### allhalted field

<p>Hardware sets this bit when all 16 bits of the halted field in the Esperanto Neighborhood Hart Status 0 register for the selected harts are set, and the hasel bit in the RISC-V Debug Module Control register (DMCTRL) is 1.</p>

#### anyrunning field

<p>Hardware sets this bit whenever any of the 16 bits of the running field in the Esperanto Neighborhood Hart Status 0 register for the selected harts is set, and the hasel bit in the RISC-V Debug Module Control register (DMCTRL) is 1.</p>

#### allrunning field

<p>Hardware sets this bit whenever all 16 bits of the running field in the Esperanto Neighborhood Hart Status 0 register for the selected harts are set, and the hasel bit in the RISC-V Debug Module Control register (DMCTRL) is 1.</p>

#### anyresumeack field

<p>Hardware sets this bit whenever any of the 16 bits of the resumeack field in the Esperanto Neighborhood Hart Status 0 register for the selected harts is set, and the hasel bit in the RISC-V Debug Module Control register (DMCTRL) is 1.</p>

#### allresumeack field

<p>Hardware sets this bit whenever any of the 16 bits of the resumeack field in the Esperanto Neighborhood Hart Status 0 register for the selected harts is set, and the hasel bit in the RISC-V Debug Module Control register (DMCTRL) is 1.</p>

#### anyhavereset field

<p>Hardware sets this bit whenever any 16 bits of the havereset field in the Esperanto Neighborhood Hart Status 0 register for the selected harts are set, and the hasel bit in the RISC-V Debug Module Control register (DMCTRL) is 1.</p>

#### allhavereset field

<p>Hardware sets this bit whenever all of the 16 bits of the havereset field in the Esperanto Neighborhood Hart Status 0 register for the selected harts is set, and the hasel bit in the RISC-V Debug Module Control register (DMCTRL) is 1.</p>

#### anyunavailable field

<p>Hardware sets this bit when any of the selected harts in the neighborhood are unavailable, and the hasel bit in the RISC-V Debug Module Control register (DMCTRL) is 1. A selected hart is considered unavailable if both HASTATUS0.halted[n] and HASTATUS0.running[n] are 0.</p>

#### anyselected field

<p>Hardware sets this bit when any of the harts in the neighborhood are selected, and the hasel bit in the RISC-V Debug Module Control register (DMCTRL) is 1.</p>

## D_cpu address map

- Absolute Address: 0x80B5F000
- Base Offset: 0xB5F000
- Size: 0xFD8

|Offset|Identifier|   Name   |
|------|----------|----------|
| 0xF88|  dmctrl  |  dmctrl  |
| 0xF90| sm_config| sm_config|
| 0xF98|sm_trigger|sm_trigger|
| 0xFA8| sm_match | sm_match |
| 0xFB0|sm_filter0|sm_filter0|
| 0xFB8|sm_filter1|sm_filter1|
| 0xFC0|sm_filter2|sm_filter2|
| 0xFC8| sm_data0 | sm_data0 |
| 0xFD0| sm_data1 | sm_data1 |

### dmctrl register

- Absolute Address: 0x80B5FF88
- Base Offset: 0xF88
- Size: 0x8

|Bits|   Identifier  |Access|Reset|Name|
|----|---------------|------|-----|----|
|  0 |    dmactive   |  rw  | 0x0 |  — |
|  1 |    ndmreset   |  rw  |  —  |  — |
|  2 |clrresethaltreq|  rw  |  —  |  — |
|  3 |setresethaltreq|  rw  |  —  |  — |
|25:4|  reserved25_4 |   r  |  —  |  — |
| 26 |     hasel     |  rw  |  —  |  — |
| 27 |   reserved27  |   r  |  —  |  — |
| 28 |  ackhavereset |  rw  |  —  |  — |
| 29 |   hartreset   |  rw  |  —  |  — |
| 30 |   resumereq   |  rw  |  —  |  — |
| 31 |    haltreq    |  rw  |  —  |  — |

#### dmactive field

<p>This bit controls the dmactive signal from the DM; it is broadcast to all Minion shires. When the signal is low it should hold at reset the debug logic of the receiving harts, and of the DM. After writing 1, the debugger should poll DMCTRL until dmactive is high. Hardware may take an arbitrarily long time to initialize and will indicate completion by setting dmactive to 1</p>

#### ndmreset field

<p>This bit controls the ndmreset signal from the DM; it is broadcast to all Minion shires. The signal should reset every part of the receiving shire, except for any logic required for debug.</p>

#### clrresethaltreq field

<p>This bit controls the clrresethaltreq signal from the DM; it is broadcast to all Minion shires. Writing 1 to this bit clears the HACTRL.resethalt bits of all currently selected harts. This bit always reads as 0.</p>

#### setresethaltreq field

<p>This bit controls the setresethaltreq signal from the DM; it is broadcast to all Minion shires. Writing 1 to this bit sets the HACTRL.resethalt bits of all currently selected harts, unless clrresethaltreq is simultaneously set to 1. This bit always reads as 0.</p>

#### reserved25_4 field

<p>WARL(0)</p>

#### hasel field

<p>This bit controls the hasel signal from the DM; it is broadcast to all Minion shires. If set to 0, then DM requests, such as halt and resume apply only to the harts that are selected by HACTRL.hartmask. If set to 1, then DM requests apply to all harts selected by the union of HACTRL.hartmask and HACTRL.hawindow.</p>

#### reserved27 field

<p>WARL(0)</p>

#### ackhavereset field

<p>This bit controls the ackhavereset signal from the DM; it is broadcast to all Minion shires. Writing 1 to this bit clears HASTATUS0.havereset for all currently selected harts. This bit always reads as 0.</p>

#### hartreset field

<p>This bit controls the hartreset signal from the DM; it is broadcast to all Minion shires.</p>

#### resumereq field

<p>This bit controls the resumereq signal from the DM; it is broadcast to all Minion shires. Writing 1 to this bit causes the currently selected harts to resume and clears the HASTATUS0.resumeack bit for those harts. This bit always reads as 0.</p>

#### haltreq field

<p>Bits [31:31]: This bit controls the haltreq signal from the DM; it is broadcast to all Minion shires. Writing 1 to this bit sets the halt request bit for all currently selected harts. Writing 0 to this bit clears the halt request bit for all currently selected harts. This may cancel outstanding halt requests for those harts. This bit always reads as 0.</p>

### sm_config register

- Absolute Address: 0x80B5FF90
- Base Offset: 0xF90
- Size: 0x8

|Bits|  Identifier |Access|Reset|Name|
|----|-------------|------|-----|----|
| 6:0| sm_data_sel |  rw  | 0x0 |  — |
|10:7|sm_target_sel|  rw  |  —  |  — |
| 11 |  sm_enable  |  rw  |  —  |  — |

#### sm_data_sel field

<p>Data selector within each target</p>

#### sm_target_sel field

<p>Target selector:</p>

#### sm_enable field

<p>Status Monitor logic enable.</p>

### sm_trigger register

- Absolute Address: 0x80B5FF98
- Base Offset: 0xF98
- Size: 0x8

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 |sm_trigger|   r  |  —  |  — |

#### sm_trigger field

<p>Writing this bit triggers a simultaneous snapshot captured in all the SM ESRs</p>

### sm_match register

- Absolute Address: 0x80B5FFA8
- Base Offset: 0xFA8
- Size: 0x8

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|63:0| sm_match |   r  |  —  |  — |

#### sm_match field

<p>Match bus</p>

### sm_filter0 register

- Absolute Address: 0x80B5FFB0
- Base Offset: 0xFB0
- Size: 0x8

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|63:0|sm_filter0|   r  |  —  |  — |

#### sm_filter0 field

<p>Filter bus [63:0]</p>

### sm_filter1 register

- Absolute Address: 0x80B5FFB8
- Base Offset: 0xFB8
- Size: 0x8

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|63:0|sm_filter1|   r  |  —  |  — |

#### sm_filter1 field

<p>Filter bus [127:64]</p>

### sm_filter2 register

- Absolute Address: 0x80B5FFC0
- Base Offset: 0xFC0
- Size: 0x8

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|63:0|sm_filter2|   r  |  —  |  — |

#### sm_filter2 field

<p>Filter bus [191:128]</p>

### sm_data0 register

- Absolute Address: 0x80B5FFC8
- Base Offset: 0xFC8
- Size: 0x8

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|63:0| sm_data0 |   r  |  —  |  — |

#### sm_data0 field

<p>Data bus [63:0]</p>

### sm_data1 register

- Absolute Address: 0x80B5FFD0
- Base Offset: 0xFD0
- Size: 0x8

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|63:0| sm_data1 |   r  |  —  |  — |

#### sm_data1 field

<p>Data bus [127:64]</p>

## Machine_neigh address map

- Absolute Address: 0x80D00000
- Base Offset: 0xD00000
- Size: 0x98

|Offset|      Identifier      |         Name         |
|------|----------------------|----------------------|
| 0x18 |      minion_boot     |      minion_boot     |
| 0x38 |         mprot        |         mprot        |
| 0x68 |       pmu_ctrl       |       pmu_ctrl       |
| 0x70 |     neigh_chicken    |     neigh_chicken    |
| 0x78 |  icache_err_log_ctl  |  icache_err_log_ctl  |
| 0x80 |  icache_err_log_info |  icache_err_log_info |
| 0x88 |icache_err_log_address|icache_err_log_address|
| 0x90 | icache_sbe_dbe_counts| icache_sbe_dbe_counts|

### minion_boot register

- Absolute Address: 0x80D00018
- Base Offset: 0x18
- Size: 0x8

|Bits| Identifier|Access|  Reset  |Name|
|----|-----------|------|---------|----|
|47:0|minion_boot|  rw  |0x2008000|  — |

#### minion_boot field

<p>Each neighborhood contains a MINION_BOOT ESR that determines the initial PC of the Minions in the neighborhood after reset. This register holds the 48 least significant bits of the reset PC, bits 63:48 of the PC are ignored on writes. Software must make sure that fetching from the PC value written in this register will not generate any faults.</p>

### mprot register

- Absolute Address: 0x80D00038
- Base Offset: 0x38
- Size: 0x8

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 3:0|smode_size|  rw  | 0x0 |  — |
| 7:4|mmode_size|  rw  | 0x0 |  — |
|  8 | mprot_en |  rw  | 0x0 |  — |

#### smode_size field

<p>Size of the MRAM region which can be only accessed by Smode. The size is 4KB<em>(2^SMODE_SIZE) - 4KB</em>(2^MMODE_SIZE) starting at offset 4KB*(2^MMODE_SIZE) in the MRAM.</p>

#### mmode_size field

<p>Size of the MRAM region which can be only accessed by Mmode. The size is 4KB*(2^MMODE_SIZE) starting at offset 0 in the MRAM.</p>

#### mprot_en field

<p>Enable privilege based memory protection.</p>

### pmu_ctrl register

- Absolute Address: 0x80D00068
- Base Offset: 0x68
- Size: 0x8

|Bits|  Identifier |Access|Reset|Name|
|----|-------------|------|-----|----|
|  0 |disable_clock|  rw  | 0x0 |  — |

#### disable_clock field

<p>Set this bit to disable the clock</p>

### neigh_chicken register

- Absolute Address: 0x80D00070
- Base Offset: 0x70
- Size: 0x8

|Bits|   Identifier   |Access|Reset|Name|
|----|----------------|------|-----|----|
|  0 |  bypass_icache |  rw  | 0x0 |  — |
|  1 |  bypass_dcache |  rw  | 0x0 |  — |
|  2 | force_dest_fifo|  rw  | 0x0 |  — |
| 4:3|    dest_fifo   |  rw  | 0x0 |  — |
|  5 |force_all_agents|  rw  | 0x0 |  — |
|  6 |  agent_forced  |  rw  | 0x0 |  — |

#### bypass_icache field

<p>Setting this bit bypasses the instruction cache.</p>

#### bypass_dcache field

<p>Setting this bit bypasses the data cache.</p>

#### force_dest_fifo field

<p>If enabled, all traffic from agents specified by the force_all_agents and agent_forced fields in the neighborhood will be routed to the destination specified in the dest_fifo field.</p>

#### dest_fifo field

<p>Destination to which requests are routed when the force_dest_fifo bit of this register is set:</p>

#### force_all_agents field

<p>When the force_dest_fifo bit and this bit are set, requests from all agents in the neighborhood go to the FIFO selected by the dest_fifo field.</p>

#### agent_forced field

<p>When the force_dest_fifo bit is set and the force_all_agents bit is clear, this field selects agents from which requests will be forced to go to the FIFO selected by the dest_fifo field. 0: Requests are routed to the corresponding bank FIFO, according to the destination address.
1: Requests are routed to the UC FIFO. 2-3: Reserved</p>

### icache_err_log_ctl register

- Absolute Address: 0x80D00078
- Base Offset: 0x78
- Size: 0x8

|Bits|     Identifier     |Access|Reset|Name|
|----|--------------------|------|-----|----|
| 2:0|err_interrupt_enable|  rw  | 0x6 |  — |

#### err_interrupt_enable field

<p>This 3-bit field is used to enable or prevent certain categories of logged errors from generating interrupts or sending error responses. In general, single-bit ECC errors should not generate an interrupt. Software may choose whether the ECC error counter saturation should generate an interrupt. Each bit has a specific meaning: Bit 0 enables single-bit ECC errors, Bit 1 enables double-bit ECC errors, and Bit 2 enables ECC counter saturation. Error codes that are not enabled are still logged but have lower priority than errors that generate interrupts. Masked interrupts do not prevent subsequent unmasked errors from being recorded. When an enabled interrupt error overwrites a masked error, the multiple error bit is not set, and multiple masked errors also do not cause the multiple error bit to be set. The multiple error bit is intended to indicate that a fatal error was missed.</p>

### icache_err_log_info register

- Absolute Address: 0x80D00080
- Base Offset: 0x80
- Size: 0x8

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 |   valid  |  rw  | 0x0 |  — |
|  1 |   multi  |  rw  | 0x0 |  — |
|  2 |  enabled |  rw  | 0x0 |  — |
|  3 | reserved |   r  |  —  |  — |
| 7:4| err_code |  rw  | 0x0 |  — |
|63:8|   info   |  rw  |  —  |  — |

#### valid field

<p>When set, this bit indicates an error has occurred and that the register contents are valid. This can be cleared by writing a 1 to this field and writing the matching code to err_code.</p>

#### multi field

<p>When set, this bit indicates that multiple errors have occurred. When an error is detected, the esr_icache_err_log_info register records the details of the first error encountered. Any subsequent errors set this bit to indicate that another fatal error occurred, but their details are not recorded.</p>

#### enabled field

<p>The error detected was enabled by esr_icache_err_log_ctl.err_interrupt_enable. Error codes that are not enabled are still logged, but they have lower priority than errors that generate interrupts.</p>

#### err_code field

<p>This 4-bit field indicates the type of error. This field is used to determine how to decode the info bits in positions 63:8.
              0: ECC single-bit error
              1: ECC double-bit error
              2: ECC error counter saturation</p>

#### info field

<p>Additional information about the error. The format of this field is dependent upon the type of error.
SBE_DBE format:
    - Bits 14:8: set. This field indicates the way that contained the error
    - Bits 16:15: way. This field indicates the way that contained the error
    - Bits 47:40: error_bits.  Indicates which doubleword contained the error. The error_bits field is multi-hot.
ECC_Saturation format:
    - Bit 52: double. This bit indicates the type of error counter that saturated and is encoded as follows:
        0: The single-bit error counter saturated.
        1: The double-bit error counter saturated.</p>

### icache_err_log_address register

- Absolute Address: 0x80D00088
- Base Offset: 0x88
- Size: 0x8

|Bits|        Identifier       |Access|Reset|Name|
|----|-------------------------|------|-----|----|
|33:0|icache_err_log_address_f0|   r  | 0x0 |  — |

#### icache_err_log_address_f0 field

<p>This register contains the physical address (PA) associated with the error if it is available.</p>

### icache_sbe_dbe_counts register

- Absolute Address: 0x80D00090
- Base Offset: 0x90
- Size: 0x8

<p>Single-bit errors (SBEs) are corrected so normal processing can continue, and no error response is sent to the requesting core because the request was processed correctly. SBEs should be logged locally, and no action should be taken.
Double-bit errors (DBEs) cannot be corrected and are considered fatal, requiring immediate reporting. SBE and DBE responses occur once per ECC protection, meaning one error bit per dword in the cache line (8 bits). 
The SBE counter is 8 bits and saturates at 255, while the DBE counter is 3 bits and saturates at 7. All fields of this register are read-only. Writing all ones to a field clears its respective counter. 
If a counter saturates, it can be error-logged as described in the icache_err_log_info register.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 7:0|sbe_counts|  rw  | 0x0 |  — |
|10:8|dbe_counts|  rw  |  —  |  — |

#### sbe_counts field

<p>This field stores the data RAM single-bit error count.</p>

#### dbe_counts field

<p>This field stores the data RAM double-bit error count.</p>

## Machine_cpu address map

- Absolute Address: 0x80F40000
- Base Offset: 0xF40000
- Size: 0x318

|Offset|     Identifier    |        Name       |
|------|-------------------|-------------------|
| 0x000|   minion_feature  |   minion_feature  |
| 0x010|  thread1_disable  |  thread1_disable  |
| 0x088|ipi_redirect_filter|ipi_redirect_filter|
| 0x090|    ipi_trigger    |    ipi_trigger    |
| 0x098| ipi_trigger_clear | ipi_trigger_clear |
| 0x200|       mtime       |       mtime       |
| 0x208|     mtime_cmp     |     mtime_cmp     |
| 0x210|    time_config    |    time_config    |
| 0x218| mtime_local_target| mtime_local_target|
| 0x240|  thread0_disable  |  thread0_disable  |
| 0x308|  icache_mprefetch |  icache_mprefetch |
| 0x310|   clk_gate_ctrl   |   clk_gate_ctrl   |

### minion_feature register

- Absolute Address: 0x80F40000
- Base Offset: 0x0
- Size: 0x8

|Bits|      Identifier      |Access|Reset|Name|
|----|----------------------|------|-----|----|
|  0 |      trap_on_gfx     |  rw  | 0x1 |  — |
|  1 |      trap_on_ml      |  rw  | 0x0 |  — |
|  2 |  trap_on_u_cacheops  |  rw  | 0x0 |  — |
|  3 |     trap_on_u_scp    |  rw  | 0x0 |  — |
|  4 |disable_multithreading|  rw  | 0x0 |  — |
|  5 |  disable_lock_unlock |  rw  | 0x0 |  — |

#### trap_on_gfx field

<p>Set this bit to trap on GFX. When this bit is enabled, GFX instructions generate an illegal instruction exception.</p>

#### trap_on_ml field

<p>Set this bit to trap on ML. When this bit is set, tensor pseudo-instructions generate an illegal instruction exception.</p>

#### trap_on_u_cacheops field

<p>Setting this bit disables user cacheops. If set, user mode will not have access to the cache op pseudo-instructions.</p>

#### trap_on_u_scp field

<p>Setting this bit disables the user scratchpad. When set, user mode cannot enable or disable the scratchpad.</p>

#### disable_multithreading field

<p>Set this bit to disable multithreading, making only thread 0 available. The hart IDs for all thread 0s in a Shire must be contiguous.</p>

#### disable_lock_unlock field

<p>Set this bit to disable lock/unlock. When set, user mode cannot use the LockVA and UnlockVA operations.</p>

### thread1_disable register

- Absolute Address: 0x80F40010
- Base Offset: 0x10
- Size: 0x8

|Bits|    Identifier    |Access|Reset|Name|
|----|------------------|------|-----|----|
| 7:0|thread1_disable_f0|  rw  | 0xFF|  — |

#### thread1_disable_f0 field

<p>Each bit of this register corresponds to thread 1 of each Minion core in the Neighborhood. When a bit is set, thread 1 of the corresponding Minion is disabled. The field is encoded as follows:
            Bit 0: Minion 0, thread 1
            Bit 1: Minion 1, thread 1
            Bit 2: Minion 2, thread 1
            …
            Bit 7: Minion 7, thread 1</p>

### ipi_redirect_filter register

- Absolute Address: 0x80F40088
- Base Offset: 0x88
- Size: 0x8

|Bits|     Identifier    |Access| Reset|Name|
|----|-------------------|------|------|----|
|15:0|ipi_redirect_filter|  rw  |0xFFFF|  — |

#### ipi_redirect_filter field

<p>ipi_redirect_filter Writing a 16-bit value to this register sets the hart ID filter mask for subsequent writes to the IPI_REDIRECT_TRIGGER register. This register is used by privileged software (M-Mode) to prevent accidental user-level redirections. Its value is ANDed with the IPI_REDIRECT_TRIGGER ESR before sending any user-level redirections; setting this register to 0x0 disables all user-level redirections. The encoding of this register is as follows: 
            Bit 0: Minion 0, hart 0
            Bit 1: Minion 0, hart 1
            Bit 2: Minion 1, hart 0
            Bit 3: Minion 1, hart 1
            …
            Bit 12: Minion 6, hart 0
            Bit 13: Minion 6, hart 1
            Bit 14: Minion 7, hart 0
            Bit 15: Minion 7, hart 1</p>

### ipi_trigger register

- Absolute Address: 0x80F40090
- Base Offset: 0x90
- Size: 0x8

|Bits| Identifier|Access|Reset|Name|
|----|-----------|------|-----|----|
|15:0|ipi_trigger|  rw  | 0x0 |  — |

#### ipi_trigger field

<p>Machine-level software writes a a bit-mask into this register to set the MSIP bit of one or more harts in the Neighborhood. The encoding of this register is as follows:
Bit 0: Minion 0, hart 0
Bit 1: Minion 0, hart 1
Bit 2: Minion 1, hart 0
Bit 3: Minion 1, hart 1
…
Bit 12: Minion 6, hart 0
Bit 13: Minion 6, hart 1
Bit 14: Minion 7, hart 0
Bit 15: Minion 7, hart 1
Reading this register reads the value of the MSIP bits of the harts in the Neighborhood. Writing a value with the i-th bit set to 0,
will have no effect on the value of the MSIP bit of the corresponding hart.</p>

### ipi_trigger_clear register

- Absolute Address: 0x80F40098
- Base Offset: 0x98
- Size: 0x8

|Bits|    Identifier   |Access|Reset|Name|
|----|-----------------|------|-----|----|
|15:0|ipi_trigger_clear|   r  | 0x0 |  — |

#### ipi_trigger_clear field

<p>Machine-level software writes a bit-mask into this register to clear the MSIP bit of one or more harts in the Neighborhood. The encoding of this register is as follows:
            Bit 0: Minion 0, hart 0
            Bit 1: Minion 0, hart 1
            Bit 2: Minion 1, hart 0
            Bit 3: Minion 1, hart 1
            …
            Bit 12: Minion 6, hart 0
            Bit 13: Minion 6, hart 1
            Bit 14: Minion 7, hart 0
            Bit 15: Minion 7, hart 1
            Reading this register returns a 0x0 value.</p>

### mtime register

- Absolute Address: 0x80F40200
- Base Offset: 0x200
- Size: 0x8

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|63:0|   mtime  |  rw  | 0x0 |  — |

#### mtime field

<p>This register matches the definition on the RISCV Privilege v1.1 specification. 64-bit timer counter. This timer increments in 100ns intervals. The mtimecmp register is compared to the value in this register. When the two are equal, a timer interrupt is generated.</p>

### mtime_cmp register

- Absolute Address: 0x80F40208
- Base Offset: 0x208
- Size: 0x8

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|63:0| mtime_cmp|  rw  | 0x0 |  — |

#### mtime_cmp field

<p>This register matches the definition on the RISCV Privilege v1.1 specification. 64-bit timer counter compare. Software sets the desired timer interval using this register. The value is then compared to the value in the mtime register. When the two are equal, an timer interrupt is generated.</p>

### time_config register

- Absolute Address: 0x80F40210
- Base Offset: 0x210
- Size: 0x8

|Bits|     Identifier    |Access|Reset|Name|
|----|-------------------|------|-----|----|
| 0:6|prescalar_threshold|  rw  | 0x28|  — |
|  7 |   ref_clock_mux   |  rw  | 0x0 |  — |

#### prescalar_threshold field

<p>The value in this field will be used as the timer prescalar threshold.</p>

#### ref_clock_mux field

<p>When this field holds 0 the timer is driven by the external reference clock. When this field holds 1 the timer is driven by the same clock that drives the cpu subsystem (external clock or ring oscillator)</p>

### mtime_local_target register

- Absolute Address: 0x80F40218
- Base Offset: 0x218
- Size: 0x8

|Bits|    Identifier    |Access| Reset|Name|
|----|------------------|------|------|----|
|15:0|mtime_local_target|  rw  |0xFFFF|  — |

#### mtime_local_target field

<p>This register controls which harts receive a timer interrupt. If bit N in mtime_local_target register is 1, hart N would be able to observe a timer interrupt in mip CSR if the mtimecmp is greater than mtime. If bit N is 0, the interrupt will be masked and not observable on hart N mip CSR.</p>

### thread0_disable register

- Absolute Address: 0x80F40240
- Base Offset: 0x240
- Size: 0x8

|Bits|   Identifier  |Access|Reset|Name|
|----|---------------|------|-----|----|
| 7:0|thread0_disable|  rw  | 0xFE|  — |

#### thread0_disable field

<p>Each bit of this register corresponds to thread 0 of each Minion core in the Neighborhood. When a bit is set, thread 0 of the corresponding Minion is disabled. The field is encoded as follows:  Bit 0: Minion 0, thread 0 Bit 1: Minion 1, thread 0 Bit 2: Minion 2, thread 0 Bit 7: Minion 7, thread 0</p>

### icache_mprefetch register

- Absolute Address: 0x80F40308
- Base Offset: 0x308
- Size: 0x8

<p>A write in this ESR prefetches Count+1 consecutive lines starting at address Address to the instruction cache.
               The privilege mode associated with this operation is Machine-mode, and all memory accesses are performed with Machine-mode privileges.
               If any of the memory requests generated by the prefetch engine generates an exception, the line is not prefetched and the operation continues with the next line.
               Reading this register returns the idle status of the prefetch engine.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 5:0|   count  |  rw  | 0x0 |  — |
|47:6|  address |  rw  | 0x0 |  — |

#### count field

<p>Number of lines to be prefetched (minus 1) starting at the given Address.</p>

#### address field

<p>Bits [47:6] of the address where prefetching should start from (aligned to a cacheline).</p>

### clk_gate_ctrl register

- Absolute Address: 0x80F40310
- Base Offset: 0x310
- Size: 0x8

|Bits|           Identifier          |Access|Reset|Name|
|----|-------------------------------|------|-----|----|
|  0 | min_intpipe_clock_gate_disable|  rw  | 0x0 |  — |
|  1 | min_vpulane_clock_gate_disable|  rw  | 0x0 |  — |
|  2 | min_vputima_clock_gate_disable|  rw  | 0x0 |  — |
|  3 |min_vputrans_clock_gate_disable|  rw  | 0x0 |  — |
|  4 | min_dcache_clock_gate_disable |  rw  |  —  |  — |
|  5 |           reserved0           |   r  |  —  |  — |
|  6 |min_frontend_clock_gate_disable|  rw  | 0x0 |  — |
|10:7|           reserved1           |   r  |  —  |  — |

#### min_intpipe_clock_gate_disable field

<p>.Setting this bit disables integer pipeline clock gating</p>

#### min_vpulane_clock_gate_disable field

<p>Setting this bit disables VPU lane clock gating.</p>

#### min_vputima_clock_gate_disable field

<p>Setting this bit disables VPUtima clock gating</p>

#### min_vputrans_clock_gate_disable field

<p>Setting this bit disables VPUtrans clock gating</p>

#### min_dcache_clock_gate_disable field

<p>Setting this bit disables data cache clock gating</p>

#### reserved0 field

<p>Write as zero. Returns 0 on read.</p>

#### min_frontend_clock_gate_disable field

<p>Setting this bit disables front end clock gating.</p>

#### reserved1 field

<p>Write as zero. Returns 0 on read.</p>

## plic address map

- Absolute Address: 0xA0000000
- Base Offset: 0xA0000000
- Size: 0x21F008

<p>RISC-V Platform-Level Interrupt Controller register map.</p>

| Offset |     Identifier     |                Name                |
|--------|--------------------|------------------------------------|
|0x000004|   priority_src01   |                  —                 |
|0x000008|   priority_src02   |                  —                 |
|0x00000C|   priority_src03   |                  —                 |
|0x000010|   priority_src04   |                  —                 |
|0x000014|   priority_src05   |                  —                 |
|0x000018|   priority_src06   |                  —                 |
|0x001000|       pending      |                  —                 |
|0x002000|    enable_ctx00    |  Interrupt Enable – Hart 0, M-mode |
|0x002080|    enable_ctx01    |  Interrupt Enable – Hart 0, S-mode |
|0x002100|    enable_ctx02    |  Interrupt Enable – Hart 1, M-mode |
|0x002180|    enable_ctx03    |  Interrupt Enable – Hart 1, S-mode |
|0x002200|    enable_ctx04    |  Interrupt Enable – Hart 2, M-mode |
|0x002280|    enable_ctx05    |  Interrupt Enable – Hart 2, S-mode |
|0x002300|    enable_ctx06    |  Interrupt Enable – Hart 3, M-mode |
|0x002380|    enable_ctx07    |  Interrupt Enable – Hart 3, S-mode |
|0x002400|    enable_ctx08    |  Interrupt Enable – Hart 4, M-mode |
|0x002480|    enable_ctx09    |  Interrupt Enable – Hart 4, S-mode |
|0x002500|    enable_ctx10    |  Interrupt Enable – Hart 5, M-mode |
|0x002580|    enable_ctx11    |  Interrupt Enable – Hart 5, S-mode |
|0x002600|    enable_ctx12    |  Interrupt Enable – Hart 6, M-mode |
|0x002680|    enable_ctx13    |  Interrupt Enable – Hart 6, S-mode |
|0x002700|    enable_ctx14    |  Interrupt Enable – Hart 7, M-mode |
|0x002780|    enable_ctx15    |  Interrupt Enable – Hart 7, S-mode |
|0x002800|    enable_ctx16    |  Interrupt Enable – Hart 8, M-mode |
|0x002880|    enable_ctx17    |  Interrupt Enable – Hart 8, S-mode |
|0x002900|    enable_ctx18    |  Interrupt Enable – Hart 9, M-mode |
|0x002980|    enable_ctx19    |  Interrupt Enable – Hart 9, S-mode |
|0x002A00|    enable_ctx20    | Interrupt Enable – Hart 10, M-mode |
|0x002A80|    enable_ctx21    | Interrupt Enable – Hart 10, S-mode |
|0x002B00|    enable_ctx22    | Interrupt Enable – Hart 11, M-mode |
|0x002B80|    enable_ctx23    | Interrupt Enable – Hart 11, S-mode |
|0x002C00|    enable_ctx24    | Interrupt Enable – Hart 12, M-mode |
|0x002C80|    enable_ctx25    | Interrupt Enable – Hart 12, S-mode |
|0x002D00|    enable_ctx26    | Interrupt Enable – Hart 13, M-mode |
|0x002D80|    enable_ctx27    | Interrupt Enable – Hart 13, S-mode |
|0x002E00|    enable_ctx28    | Interrupt Enable – Hart 14, M-mode |
|0x002E80|    enable_ctx29    | Interrupt Enable – Hart 14, S-mode |
|0x002F00|    enable_ctx30    | Interrupt Enable – Hart 15, M-mode |
|0x002F80|    enable_ctx31    | Interrupt Enable – Hart 15, S-mode |
|0x200000|   threshold_ctx00  | Priority Threshold – Hart 0, M-mode|
|0x200004|claim_complete_ctx00|   Claim/Complete – Hart 0, M-mode  |
|0x201000|   threshold_ctx01  | Priority Threshold – Hart 0, S-mode|
|0x201004|claim_complete_ctx01|   Claim/Complete – Hart 0, S-mode  |
|0x202000|   threshold_ctx02  | Priority Threshold – Hart 1, M-mode|
|0x202004|claim_complete_ctx02|   Claim/Complete – Hart 1, M-mode  |
|0x203000|   threshold_ctx03  | Priority Threshold – Hart 1, S-mode|
|0x203004|claim_complete_ctx03|   Claim/Complete – Hart 1, S-mode  |
|0x204000|   threshold_ctx04  | Priority Threshold – Hart 2, M-mode|
|0x204004|claim_complete_ctx04|   Claim/Complete – Hart 2, M-mode  |
|0x205000|   threshold_ctx05  | Priority Threshold – Hart 2, S-mode|
|0x205004|claim_complete_ctx05|   Claim/Complete – Hart 2, S-mode  |
|0x206000|   threshold_ctx06  | Priority Threshold – Hart 3, M-mode|
|0x206004|claim_complete_ctx06|   Claim/Complete – Hart 3, M-mode  |
|0x207000|   threshold_ctx07  | Priority Threshold – Hart 3, S-mode|
|0x207004|claim_complete_ctx07|   Claim/Complete – Hart 3, S-mode  |
|0x208000|   threshold_ctx08  | Priority Threshold – Hart 4, M-mode|
|0x208004|claim_complete_ctx08|   Claim/Complete – Hart 4, M-mode  |
|0x209000|   threshold_ctx09  | Priority Threshold – Hart 4, S-mode|
|0x209004|claim_complete_ctx09|   Claim/Complete – Hart 4, S-mode  |
|0x20A000|   threshold_ctx10  | Priority Threshold – Hart 5, M-mode|
|0x20A004|claim_complete_ctx10|   Claim/Complete – Hart 5, M-mode  |
|0x20B000|   threshold_ctx11  | Priority Threshold – Hart 5, S-mode|
|0x20B004|claim_complete_ctx11|   Claim/Complete – Hart 5, S-mode  |
|0x20C000|   threshold_ctx12  | Priority Threshold – Hart 6, M-mode|
|0x20C004|claim_complete_ctx12|   Claim/Complete – Hart 6, M-mode  |
|0x20D000|   threshold_ctx13  | Priority Threshold – Hart 6, S-mode|
|0x20D004|claim_complete_ctx13|   Claim/Complete – Hart 6, S-mode  |
|0x20E000|   threshold_ctx14  | Priority Threshold – Hart 7, M-mode|
|0x20E004|claim_complete_ctx14|   Claim/Complete – Hart 7, M-mode  |
|0x20F000|   threshold_ctx15  | Priority Threshold – Hart 7, S-mode|
|0x20F004|claim_complete_ctx15|   Claim/Complete – Hart 7, S-mode  |
|0x210000|   threshold_ctx16  | Priority Threshold – Hart 8, M-mode|
|0x210004|claim_complete_ctx16|   Claim/Complete – Hart 8, M-mode  |
|0x211000|   threshold_ctx17  | Priority Threshold – Hart 8, S-mode|
|0x211004|claim_complete_ctx17|   Claim/Complete – Hart 8, S-mode  |
|0x212000|   threshold_ctx18  | Priority Threshold – Hart 9, M-mode|
|0x212004|claim_complete_ctx18|   Claim/Complete – Hart 9, M-mode  |
|0x213000|   threshold_ctx19  | Priority Threshold – Hart 9, S-mode|
|0x213004|claim_complete_ctx19|   Claim/Complete – Hart 9, S-mode  |
|0x214000|   threshold_ctx20  |Priority Threshold – Hart 10, M-mode|
|0x214004|claim_complete_ctx20|  Claim/Complete – Hart 10, M-mode  |
|0x215000|   threshold_ctx21  |Priority Threshold – Hart 10, S-mode|
|0x215004|claim_complete_ctx21|  Claim/Complete – Hart 10, S-mode  |
|0x216000|   threshold_ctx22  |Priority Threshold – Hart 11, M-mode|
|0x216004|claim_complete_ctx22|  Claim/Complete – Hart 11, M-mode  |
|0x217000|   threshold_ctx23  |Priority Threshold – Hart 11, S-mode|
|0x217004|claim_complete_ctx23|  Claim/Complete – Hart 11, S-mode  |
|0x218000|   threshold_ctx24  |Priority Threshold – Hart 12, M-mode|
|0x218004|claim_complete_ctx24|  Claim/Complete – Hart 12, M-mode  |
|0x219000|   threshold_ctx25  |Priority Threshold – Hart 12, S-mode|
|0x219004|claim_complete_ctx25|  Claim/Complete – Hart 12, S-mode  |
|0x21A000|   threshold_ctx26  |Priority Threshold – Hart 13, M-mode|
|0x21A004|claim_complete_ctx26|  Claim/Complete – Hart 13, M-mode  |
|0x21B000|   threshold_ctx27  |Priority Threshold – Hart 13, S-mode|
|0x21B004|claim_complete_ctx27|  Claim/Complete – Hart 13, S-mode  |
|0x21C000|   threshold_ctx28  |Priority Threshold – Hart 14, M-mode|
|0x21C004|claim_complete_ctx28|  Claim/Complete – Hart 14, M-mode  |
|0x21D000|   threshold_ctx29  |Priority Threshold – Hart 14, S-mode|
|0x21D004|claim_complete_ctx29|  Claim/Complete – Hart 14, S-mode  |
|0x21E000|   threshold_ctx30  |Priority Threshold – Hart 15, M-mode|
|0x21E004|claim_complete_ctx30|  Claim/Complete – Hart 15, M-mode  |
|0x21F000|   threshold_ctx31  |Priority Threshold – Hart 15, S-mode|
|0x21F004|claim_complete_ctx31|  Claim/Complete – Hart 15, S-mode  |

### priority_src01 register

- Absolute Address: 0xA0000004
- Base Offset: 0x4
- Size: 0x4

<p>Interrupt source priority. Hardwired to 1 — no priority levels are implemented.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | PRIORITY |   r  | 0x1 |  — |

#### PRIORITY field

<p>Priority level (always 1)</p>

### priority_src02 register

- Absolute Address: 0xA0000008
- Base Offset: 0x8
- Size: 0x4

<p>Interrupt source priority. Hardwired to 1 — no priority levels are implemented.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | PRIORITY |   r  | 0x1 |  — |

#### PRIORITY field

<p>Priority level (always 1)</p>

### priority_src03 register

- Absolute Address: 0xA000000C
- Base Offset: 0xC
- Size: 0x4

<p>Interrupt source priority. Hardwired to 1 — no priority levels are implemented.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | PRIORITY |   r  | 0x1 |  — |

#### PRIORITY field

<p>Priority level (always 1)</p>

### priority_src04 register

- Absolute Address: 0xA0000010
- Base Offset: 0x10
- Size: 0x4

<p>Interrupt source priority. Hardwired to 1 — no priority levels are implemented.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | PRIORITY |   r  | 0x1 |  — |

#### PRIORITY field

<p>Priority level (always 1)</p>

### priority_src05 register

- Absolute Address: 0xA0000014
- Base Offset: 0x14
- Size: 0x4

<p>Interrupt source priority. Hardwired to 1 — no priority levels are implemented.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | PRIORITY |   r  | 0x1 |  — |

#### PRIORITY field

<p>Priority level (always 1)</p>

### priority_src06 register

- Absolute Address: 0xA0000018
- Base Offset: 0x18
- Size: 0x4

<p>Interrupt source priority. Hardwired to 1 — no priority levels are implemented.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | PRIORITY |   r  | 0x1 |  — |

#### PRIORITY field

<p>Priority level (always 1)</p>

### pending register

- Absolute Address: 0xA0001000
- Base Offset: 0x1000
- Size: 0x4

<p>Interrupt pending bits. Hardware-managed; read-only for software.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | RESERVED |   r  | 0x0 |  — |
| 6:1|  PENDING |   r  | 0x0 |  — |

#### RESERVED field

<p>Reserved — source 0 does not exist</p>

#### PENDING field

<p>Pending flags for interrupt sources 1..6</p>

### enable_ctx00 register

- Absolute Address: 0xA0002000
- Base Offset: 0x2000
- Size: 0x4

<p>Interrupt enable bits for context 0 (hart 0, Machine mode). Bit N enables source N for this context.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | RESERVED |   r  | 0x0 |  — |
| 6:1|  ENABLE  |  rw  | 0x0 |  — |

#### RESERVED field

<p>Reserved — source 0 does not exist</p>

#### ENABLE field

<p>Enable bits for interrupt sources 1..6</p>

### enable_ctx01 register

- Absolute Address: 0xA0002080
- Base Offset: 0x2080
- Size: 0x4

<p>Interrupt enable bits for context 1 (hart 0, Supervisor mode). Bit N enables source N for this context.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | RESERVED |   r  | 0x0 |  — |
| 6:1|  ENABLE  |  rw  | 0x0 |  — |

#### RESERVED field

<p>Reserved — source 0 does not exist</p>

#### ENABLE field

<p>Enable bits for interrupt sources 1..6</p>

### enable_ctx02 register

- Absolute Address: 0xA0002100
- Base Offset: 0x2100
- Size: 0x4

<p>Interrupt enable bits for context 2 (hart 1, Machine mode). Bit N enables source N for this context.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | RESERVED |   r  | 0x0 |  — |
| 6:1|  ENABLE  |  rw  | 0x0 |  — |

#### RESERVED field

<p>Reserved — source 0 does not exist</p>

#### ENABLE field

<p>Enable bits for interrupt sources 1..6</p>

### enable_ctx03 register

- Absolute Address: 0xA0002180
- Base Offset: 0x2180
- Size: 0x4

<p>Interrupt enable bits for context 3 (hart 1, Supervisor mode). Bit N enables source N for this context.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | RESERVED |   r  | 0x0 |  — |
| 6:1|  ENABLE  |  rw  | 0x0 |  — |

#### RESERVED field

<p>Reserved — source 0 does not exist</p>

#### ENABLE field

<p>Enable bits for interrupt sources 1..6</p>

### enable_ctx04 register

- Absolute Address: 0xA0002200
- Base Offset: 0x2200
- Size: 0x4

<p>Interrupt enable bits for context 4 (hart 2, Machine mode). Bit N enables source N for this context.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | RESERVED |   r  | 0x0 |  — |
| 6:1|  ENABLE  |  rw  | 0x0 |  — |

#### RESERVED field

<p>Reserved — source 0 does not exist</p>

#### ENABLE field

<p>Enable bits for interrupt sources 1..6</p>

### enable_ctx05 register

- Absolute Address: 0xA0002280
- Base Offset: 0x2280
- Size: 0x4

<p>Interrupt enable bits for context 5 (hart 2, Supervisor mode). Bit N enables source N for this context.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | RESERVED |   r  | 0x0 |  — |
| 6:1|  ENABLE  |  rw  | 0x0 |  — |

#### RESERVED field

<p>Reserved — source 0 does not exist</p>

#### ENABLE field

<p>Enable bits for interrupt sources 1..6</p>

### enable_ctx06 register

- Absolute Address: 0xA0002300
- Base Offset: 0x2300
- Size: 0x4

<p>Interrupt enable bits for context 6 (hart 3, Machine mode). Bit N enables source N for this context.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | RESERVED |   r  | 0x0 |  — |
| 6:1|  ENABLE  |  rw  | 0x0 |  — |

#### RESERVED field

<p>Reserved — source 0 does not exist</p>

#### ENABLE field

<p>Enable bits for interrupt sources 1..6</p>

### enable_ctx07 register

- Absolute Address: 0xA0002380
- Base Offset: 0x2380
- Size: 0x4

<p>Interrupt enable bits for context 7 (hart 3, Supervisor mode). Bit N enables source N for this context.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | RESERVED |   r  | 0x0 |  — |
| 6:1|  ENABLE  |  rw  | 0x0 |  — |

#### RESERVED field

<p>Reserved — source 0 does not exist</p>

#### ENABLE field

<p>Enable bits for interrupt sources 1..6</p>

### enable_ctx08 register

- Absolute Address: 0xA0002400
- Base Offset: 0x2400
- Size: 0x4

<p>Interrupt enable bits for context 8 (hart 4, Machine mode). Bit N enables source N for this context.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | RESERVED |   r  | 0x0 |  — |
| 6:1|  ENABLE  |  rw  | 0x0 |  — |

#### RESERVED field

<p>Reserved — source 0 does not exist</p>

#### ENABLE field

<p>Enable bits for interrupt sources 1..6</p>

### enable_ctx09 register

- Absolute Address: 0xA0002480
- Base Offset: 0x2480
- Size: 0x4

<p>Interrupt enable bits for context 9 (hart 4, Supervisor mode). Bit N enables source N for this context.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | RESERVED |   r  | 0x0 |  — |
| 6:1|  ENABLE  |  rw  | 0x0 |  — |

#### RESERVED field

<p>Reserved — source 0 does not exist</p>

#### ENABLE field

<p>Enable bits for interrupt sources 1..6</p>

### enable_ctx10 register

- Absolute Address: 0xA0002500
- Base Offset: 0x2500
- Size: 0x4

<p>Interrupt enable bits for context 10 (hart 5, Machine mode). Bit N enables source N for this context.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | RESERVED |   r  | 0x0 |  — |
| 6:1|  ENABLE  |  rw  | 0x0 |  — |

#### RESERVED field

<p>Reserved — source 0 does not exist</p>

#### ENABLE field

<p>Enable bits for interrupt sources 1..6</p>

### enable_ctx11 register

- Absolute Address: 0xA0002580
- Base Offset: 0x2580
- Size: 0x4

<p>Interrupt enable bits for context 11 (hart 5, Supervisor mode). Bit N enables source N for this context.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | RESERVED |   r  | 0x0 |  — |
| 6:1|  ENABLE  |  rw  | 0x0 |  — |

#### RESERVED field

<p>Reserved — source 0 does not exist</p>

#### ENABLE field

<p>Enable bits for interrupt sources 1..6</p>

### enable_ctx12 register

- Absolute Address: 0xA0002600
- Base Offset: 0x2600
- Size: 0x4

<p>Interrupt enable bits for context 12 (hart 6, Machine mode). Bit N enables source N for this context.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | RESERVED |   r  | 0x0 |  — |
| 6:1|  ENABLE  |  rw  | 0x0 |  — |

#### RESERVED field

<p>Reserved — source 0 does not exist</p>

#### ENABLE field

<p>Enable bits for interrupt sources 1..6</p>

### enable_ctx13 register

- Absolute Address: 0xA0002680
- Base Offset: 0x2680
- Size: 0x4

<p>Interrupt enable bits for context 13 (hart 6, Supervisor mode). Bit N enables source N for this context.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | RESERVED |   r  | 0x0 |  — |
| 6:1|  ENABLE  |  rw  | 0x0 |  — |

#### RESERVED field

<p>Reserved — source 0 does not exist</p>

#### ENABLE field

<p>Enable bits for interrupt sources 1..6</p>

### enable_ctx14 register

- Absolute Address: 0xA0002700
- Base Offset: 0x2700
- Size: 0x4

<p>Interrupt enable bits for context 14 (hart 7, Machine mode). Bit N enables source N for this context.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | RESERVED |   r  | 0x0 |  — |
| 6:1|  ENABLE  |  rw  | 0x0 |  — |

#### RESERVED field

<p>Reserved — source 0 does not exist</p>

#### ENABLE field

<p>Enable bits for interrupt sources 1..6</p>

### enable_ctx15 register

- Absolute Address: 0xA0002780
- Base Offset: 0x2780
- Size: 0x4

<p>Interrupt enable bits for context 15 (hart 7, Supervisor mode). Bit N enables source N for this context.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | RESERVED |   r  | 0x0 |  — |
| 6:1|  ENABLE  |  rw  | 0x0 |  — |

#### RESERVED field

<p>Reserved — source 0 does not exist</p>

#### ENABLE field

<p>Enable bits for interrupt sources 1..6</p>

### enable_ctx16 register

- Absolute Address: 0xA0002800
- Base Offset: 0x2800
- Size: 0x4

<p>Interrupt enable bits for context 16 (hart 8, Machine mode). Bit N enables source N for this context.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | RESERVED |   r  | 0x0 |  — |
| 6:1|  ENABLE  |  rw  | 0x0 |  — |

#### RESERVED field

<p>Reserved — source 0 does not exist</p>

#### ENABLE field

<p>Enable bits for interrupt sources 1..6</p>

### enable_ctx17 register

- Absolute Address: 0xA0002880
- Base Offset: 0x2880
- Size: 0x4

<p>Interrupt enable bits for context 17 (hart 8, Supervisor mode). Bit N enables source N for this context.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | RESERVED |   r  | 0x0 |  — |
| 6:1|  ENABLE  |  rw  | 0x0 |  — |

#### RESERVED field

<p>Reserved — source 0 does not exist</p>

#### ENABLE field

<p>Enable bits for interrupt sources 1..6</p>

### enable_ctx18 register

- Absolute Address: 0xA0002900
- Base Offset: 0x2900
- Size: 0x4

<p>Interrupt enable bits for context 18 (hart 9, Machine mode). Bit N enables source N for this context.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | RESERVED |   r  | 0x0 |  — |
| 6:1|  ENABLE  |  rw  | 0x0 |  — |

#### RESERVED field

<p>Reserved — source 0 does not exist</p>

#### ENABLE field

<p>Enable bits for interrupt sources 1..6</p>

### enable_ctx19 register

- Absolute Address: 0xA0002980
- Base Offset: 0x2980
- Size: 0x4

<p>Interrupt enable bits for context 19 (hart 9, Supervisor mode). Bit N enables source N for this context.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | RESERVED |   r  | 0x0 |  — |
| 6:1|  ENABLE  |  rw  | 0x0 |  — |

#### RESERVED field

<p>Reserved — source 0 does not exist</p>

#### ENABLE field

<p>Enable bits for interrupt sources 1..6</p>

### enable_ctx20 register

- Absolute Address: 0xA0002A00
- Base Offset: 0x2A00
- Size: 0x4

<p>Interrupt enable bits for context 20 (hart 10, Machine mode). Bit N enables source N for this context.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | RESERVED |   r  | 0x0 |  — |
| 6:1|  ENABLE  |  rw  | 0x0 |  — |

#### RESERVED field

<p>Reserved — source 0 does not exist</p>

#### ENABLE field

<p>Enable bits for interrupt sources 1..6</p>

### enable_ctx21 register

- Absolute Address: 0xA0002A80
- Base Offset: 0x2A80
- Size: 0x4

<p>Interrupt enable bits for context 21 (hart 10, Supervisor mode). Bit N enables source N for this context.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | RESERVED |   r  | 0x0 |  — |
| 6:1|  ENABLE  |  rw  | 0x0 |  — |

#### RESERVED field

<p>Reserved — source 0 does not exist</p>

#### ENABLE field

<p>Enable bits for interrupt sources 1..6</p>

### enable_ctx22 register

- Absolute Address: 0xA0002B00
- Base Offset: 0x2B00
- Size: 0x4

<p>Interrupt enable bits for context 22 (hart 11, Machine mode). Bit N enables source N for this context.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | RESERVED |   r  | 0x0 |  — |
| 6:1|  ENABLE  |  rw  | 0x0 |  — |

#### RESERVED field

<p>Reserved — source 0 does not exist</p>

#### ENABLE field

<p>Enable bits for interrupt sources 1..6</p>

### enable_ctx23 register

- Absolute Address: 0xA0002B80
- Base Offset: 0x2B80
- Size: 0x4

<p>Interrupt enable bits for context 23 (hart 11, Supervisor mode). Bit N enables source N for this context.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | RESERVED |   r  | 0x0 |  — |
| 6:1|  ENABLE  |  rw  | 0x0 |  — |

#### RESERVED field

<p>Reserved — source 0 does not exist</p>

#### ENABLE field

<p>Enable bits for interrupt sources 1..6</p>

### enable_ctx24 register

- Absolute Address: 0xA0002C00
- Base Offset: 0x2C00
- Size: 0x4

<p>Interrupt enable bits for context 24 (hart 12, Machine mode). Bit N enables source N for this context.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | RESERVED |   r  | 0x0 |  — |
| 6:1|  ENABLE  |  rw  | 0x0 |  — |

#### RESERVED field

<p>Reserved — source 0 does not exist</p>

#### ENABLE field

<p>Enable bits for interrupt sources 1..6</p>

### enable_ctx25 register

- Absolute Address: 0xA0002C80
- Base Offset: 0x2C80
- Size: 0x4

<p>Interrupt enable bits for context 25 (hart 12, Supervisor mode). Bit N enables source N for this context.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | RESERVED |   r  | 0x0 |  — |
| 6:1|  ENABLE  |  rw  | 0x0 |  — |

#### RESERVED field

<p>Reserved — source 0 does not exist</p>

#### ENABLE field

<p>Enable bits for interrupt sources 1..6</p>

### enable_ctx26 register

- Absolute Address: 0xA0002D00
- Base Offset: 0x2D00
- Size: 0x4

<p>Interrupt enable bits for context 26 (hart 13, Machine mode). Bit N enables source N for this context.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | RESERVED |   r  | 0x0 |  — |
| 6:1|  ENABLE  |  rw  | 0x0 |  — |

#### RESERVED field

<p>Reserved — source 0 does not exist</p>

#### ENABLE field

<p>Enable bits for interrupt sources 1..6</p>

### enable_ctx27 register

- Absolute Address: 0xA0002D80
- Base Offset: 0x2D80
- Size: 0x4

<p>Interrupt enable bits for context 27 (hart 13, Supervisor mode). Bit N enables source N for this context.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | RESERVED |   r  | 0x0 |  — |
| 6:1|  ENABLE  |  rw  | 0x0 |  — |

#### RESERVED field

<p>Reserved — source 0 does not exist</p>

#### ENABLE field

<p>Enable bits for interrupt sources 1..6</p>

### enable_ctx28 register

- Absolute Address: 0xA0002E00
- Base Offset: 0x2E00
- Size: 0x4

<p>Interrupt enable bits for context 28 (hart 14, Machine mode). Bit N enables source N for this context.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | RESERVED |   r  | 0x0 |  — |
| 6:1|  ENABLE  |  rw  | 0x0 |  — |

#### RESERVED field

<p>Reserved — source 0 does not exist</p>

#### ENABLE field

<p>Enable bits for interrupt sources 1..6</p>

### enable_ctx29 register

- Absolute Address: 0xA0002E80
- Base Offset: 0x2E80
- Size: 0x4

<p>Interrupt enable bits for context 29 (hart 14, Supervisor mode). Bit N enables source N for this context.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | RESERVED |   r  | 0x0 |  — |
| 6:1|  ENABLE  |  rw  | 0x0 |  — |

#### RESERVED field

<p>Reserved — source 0 does not exist</p>

#### ENABLE field

<p>Enable bits for interrupt sources 1..6</p>

### enable_ctx30 register

- Absolute Address: 0xA0002F00
- Base Offset: 0x2F00
- Size: 0x4

<p>Interrupt enable bits for context 30 (hart 15, Machine mode). Bit N enables source N for this context.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | RESERVED |   r  | 0x0 |  — |
| 6:1|  ENABLE  |  rw  | 0x0 |  — |

#### RESERVED field

<p>Reserved — source 0 does not exist</p>

#### ENABLE field

<p>Enable bits for interrupt sources 1..6</p>

### enable_ctx31 register

- Absolute Address: 0xA0002F80
- Base Offset: 0x2F80
- Size: 0x4

<p>Interrupt enable bits for context 31 (hart 15, Supervisor mode). Bit N enables source N for this context.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | RESERVED |   r  | 0x0 |  — |
| 6:1|  ENABLE  |  rw  | 0x0 |  — |

#### RESERVED field

<p>Reserved — source 0 does not exist</p>

#### ENABLE field

<p>Enable bits for interrupt sources 1..6</p>

### threshold_ctx00 register

- Absolute Address: 0xA0200000
- Base Offset: 0x200000
- Size: 0x4

<p>Priority threshold for context 0 (hart 0, Machine mode). Hardwired to 0 — all enabled pending interrupts are forwarded to this hart.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | THRESHOLD|   r  | 0x0 |  — |

#### THRESHOLD field

<p>Threshold (always 0)</p>

### claim_complete_ctx00 register

- Absolute Address: 0xA0200004
- Base Offset: 0x200004
- Size: 0x4

<p>Claim/Complete for context 0 (hart 0, Machine mode). Read to claim the highest-priority pending interrupt (returns 0 if none); write the claimed ID to signal completion.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 2:0|    ID    |  rw  | 0x0 |  — |

#### ID field

<p>Interrupt ID: 0 = no interrupt pending, 1..6 = valid interrupt source</p>

### threshold_ctx01 register

- Absolute Address: 0xA0201000
- Base Offset: 0x201000
- Size: 0x4

<p>Priority threshold for context 1 (hart 0, Supervisor mode). Hardwired to 0 — all enabled pending interrupts are forwarded to this hart.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | THRESHOLD|   r  | 0x0 |  — |

#### THRESHOLD field

<p>Threshold (always 0)</p>

### claim_complete_ctx01 register

- Absolute Address: 0xA0201004
- Base Offset: 0x201004
- Size: 0x4

<p>Claim/Complete for context 1 (hart 0, Supervisor mode). Read to claim the highest-priority pending interrupt (returns 0 if none); write the claimed ID to signal completion.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 2:0|    ID    |  rw  | 0x0 |  — |

#### ID field

<p>Interrupt ID: 0 = no interrupt pending, 1..6 = valid interrupt source</p>

### threshold_ctx02 register

- Absolute Address: 0xA0202000
- Base Offset: 0x202000
- Size: 0x4

<p>Priority threshold for context 2 (hart 1, Machine mode). Hardwired to 0 — all enabled pending interrupts are forwarded to this hart.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | THRESHOLD|   r  | 0x0 |  — |

#### THRESHOLD field

<p>Threshold (always 0)</p>

### claim_complete_ctx02 register

- Absolute Address: 0xA0202004
- Base Offset: 0x202004
- Size: 0x4

<p>Claim/Complete for context 2 (hart 1, Machine mode). Read to claim the highest-priority pending interrupt (returns 0 if none); write the claimed ID to signal completion.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 2:0|    ID    |  rw  | 0x0 |  — |

#### ID field

<p>Interrupt ID: 0 = no interrupt pending, 1..6 = valid interrupt source</p>

### threshold_ctx03 register

- Absolute Address: 0xA0203000
- Base Offset: 0x203000
- Size: 0x4

<p>Priority threshold for context 3 (hart 1, Supervisor mode). Hardwired to 0 — all enabled pending interrupts are forwarded to this hart.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | THRESHOLD|   r  | 0x0 |  — |

#### THRESHOLD field

<p>Threshold (always 0)</p>

### claim_complete_ctx03 register

- Absolute Address: 0xA0203004
- Base Offset: 0x203004
- Size: 0x4

<p>Claim/Complete for context 3 (hart 1, Supervisor mode). Read to claim the highest-priority pending interrupt (returns 0 if none); write the claimed ID to signal completion.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 2:0|    ID    |  rw  | 0x0 |  — |

#### ID field

<p>Interrupt ID: 0 = no interrupt pending, 1..6 = valid interrupt source</p>

### threshold_ctx04 register

- Absolute Address: 0xA0204000
- Base Offset: 0x204000
- Size: 0x4

<p>Priority threshold for context 4 (hart 2, Machine mode). Hardwired to 0 — all enabled pending interrupts are forwarded to this hart.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | THRESHOLD|   r  | 0x0 |  — |

#### THRESHOLD field

<p>Threshold (always 0)</p>

### claim_complete_ctx04 register

- Absolute Address: 0xA0204004
- Base Offset: 0x204004
- Size: 0x4

<p>Claim/Complete for context 4 (hart 2, Machine mode). Read to claim the highest-priority pending interrupt (returns 0 if none); write the claimed ID to signal completion.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 2:0|    ID    |  rw  | 0x0 |  — |

#### ID field

<p>Interrupt ID: 0 = no interrupt pending, 1..6 = valid interrupt source</p>

### threshold_ctx05 register

- Absolute Address: 0xA0205000
- Base Offset: 0x205000
- Size: 0x4

<p>Priority threshold for context 5 (hart 2, Supervisor mode). Hardwired to 0 — all enabled pending interrupts are forwarded to this hart.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | THRESHOLD|   r  | 0x0 |  — |

#### THRESHOLD field

<p>Threshold (always 0)</p>

### claim_complete_ctx05 register

- Absolute Address: 0xA0205004
- Base Offset: 0x205004
- Size: 0x4

<p>Claim/Complete for context 5 (hart 2, Supervisor mode). Read to claim the highest-priority pending interrupt (returns 0 if none); write the claimed ID to signal completion.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 2:0|    ID    |  rw  | 0x0 |  — |

#### ID field

<p>Interrupt ID: 0 = no interrupt pending, 1..6 = valid interrupt source</p>

### threshold_ctx06 register

- Absolute Address: 0xA0206000
- Base Offset: 0x206000
- Size: 0x4

<p>Priority threshold for context 6 (hart 3, Machine mode). Hardwired to 0 — all enabled pending interrupts are forwarded to this hart.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | THRESHOLD|   r  | 0x0 |  — |

#### THRESHOLD field

<p>Threshold (always 0)</p>

### claim_complete_ctx06 register

- Absolute Address: 0xA0206004
- Base Offset: 0x206004
- Size: 0x4

<p>Claim/Complete for context 6 (hart 3, Machine mode). Read to claim the highest-priority pending interrupt (returns 0 if none); write the claimed ID to signal completion.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 2:0|    ID    |  rw  | 0x0 |  — |

#### ID field

<p>Interrupt ID: 0 = no interrupt pending, 1..6 = valid interrupt source</p>

### threshold_ctx07 register

- Absolute Address: 0xA0207000
- Base Offset: 0x207000
- Size: 0x4

<p>Priority threshold for context 7 (hart 3, Supervisor mode). Hardwired to 0 — all enabled pending interrupts are forwarded to this hart.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | THRESHOLD|   r  | 0x0 |  — |

#### THRESHOLD field

<p>Threshold (always 0)</p>

### claim_complete_ctx07 register

- Absolute Address: 0xA0207004
- Base Offset: 0x207004
- Size: 0x4

<p>Claim/Complete for context 7 (hart 3, Supervisor mode). Read to claim the highest-priority pending interrupt (returns 0 if none); write the claimed ID to signal completion.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 2:0|    ID    |  rw  | 0x0 |  — |

#### ID field

<p>Interrupt ID: 0 = no interrupt pending, 1..6 = valid interrupt source</p>

### threshold_ctx08 register

- Absolute Address: 0xA0208000
- Base Offset: 0x208000
- Size: 0x4

<p>Priority threshold for context 8 (hart 4, Machine mode). Hardwired to 0 — all enabled pending interrupts are forwarded to this hart.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | THRESHOLD|   r  | 0x0 |  — |

#### THRESHOLD field

<p>Threshold (always 0)</p>

### claim_complete_ctx08 register

- Absolute Address: 0xA0208004
- Base Offset: 0x208004
- Size: 0x4

<p>Claim/Complete for context 8 (hart 4, Machine mode). Read to claim the highest-priority pending interrupt (returns 0 if none); write the claimed ID to signal completion.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 2:0|    ID    |  rw  | 0x0 |  — |

#### ID field

<p>Interrupt ID: 0 = no interrupt pending, 1..6 = valid interrupt source</p>

### threshold_ctx09 register

- Absolute Address: 0xA0209000
- Base Offset: 0x209000
- Size: 0x4

<p>Priority threshold for context 9 (hart 4, Supervisor mode). Hardwired to 0 — all enabled pending interrupts are forwarded to this hart.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | THRESHOLD|   r  | 0x0 |  — |

#### THRESHOLD field

<p>Threshold (always 0)</p>

### claim_complete_ctx09 register

- Absolute Address: 0xA0209004
- Base Offset: 0x209004
- Size: 0x4

<p>Claim/Complete for context 9 (hart 4, Supervisor mode). Read to claim the highest-priority pending interrupt (returns 0 if none); write the claimed ID to signal completion.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 2:0|    ID    |  rw  | 0x0 |  — |

#### ID field

<p>Interrupt ID: 0 = no interrupt pending, 1..6 = valid interrupt source</p>

### threshold_ctx10 register

- Absolute Address: 0xA020A000
- Base Offset: 0x20A000
- Size: 0x4

<p>Priority threshold for context 10 (hart 5, Machine mode). Hardwired to 0 — all enabled pending interrupts are forwarded to this hart.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | THRESHOLD|   r  | 0x0 |  — |

#### THRESHOLD field

<p>Threshold (always 0)</p>

### claim_complete_ctx10 register

- Absolute Address: 0xA020A004
- Base Offset: 0x20A004
- Size: 0x4

<p>Claim/Complete for context 10 (hart 5, Machine mode). Read to claim the highest-priority pending interrupt (returns 0 if none); write the claimed ID to signal completion.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 2:0|    ID    |  rw  | 0x0 |  — |

#### ID field

<p>Interrupt ID: 0 = no interrupt pending, 1..6 = valid interrupt source</p>

### threshold_ctx11 register

- Absolute Address: 0xA020B000
- Base Offset: 0x20B000
- Size: 0x4

<p>Priority threshold for context 11 (hart 5, Supervisor mode). Hardwired to 0 — all enabled pending interrupts are forwarded to this hart.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | THRESHOLD|   r  | 0x0 |  — |

#### THRESHOLD field

<p>Threshold (always 0)</p>

### claim_complete_ctx11 register

- Absolute Address: 0xA020B004
- Base Offset: 0x20B004
- Size: 0x4

<p>Claim/Complete for context 11 (hart 5, Supervisor mode). Read to claim the highest-priority pending interrupt (returns 0 if none); write the claimed ID to signal completion.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 2:0|    ID    |  rw  | 0x0 |  — |

#### ID field

<p>Interrupt ID: 0 = no interrupt pending, 1..6 = valid interrupt source</p>

### threshold_ctx12 register

- Absolute Address: 0xA020C000
- Base Offset: 0x20C000
- Size: 0x4

<p>Priority threshold for context 12 (hart 6, Machine mode). Hardwired to 0 — all enabled pending interrupts are forwarded to this hart.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | THRESHOLD|   r  | 0x0 |  — |

#### THRESHOLD field

<p>Threshold (always 0)</p>

### claim_complete_ctx12 register

- Absolute Address: 0xA020C004
- Base Offset: 0x20C004
- Size: 0x4

<p>Claim/Complete for context 12 (hart 6, Machine mode). Read to claim the highest-priority pending interrupt (returns 0 if none); write the claimed ID to signal completion.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 2:0|    ID    |  rw  | 0x0 |  — |

#### ID field

<p>Interrupt ID: 0 = no interrupt pending, 1..6 = valid interrupt source</p>

### threshold_ctx13 register

- Absolute Address: 0xA020D000
- Base Offset: 0x20D000
- Size: 0x4

<p>Priority threshold for context 13 (hart 6, Supervisor mode). Hardwired to 0 — all enabled pending interrupts are forwarded to this hart.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | THRESHOLD|   r  | 0x0 |  — |

#### THRESHOLD field

<p>Threshold (always 0)</p>

### claim_complete_ctx13 register

- Absolute Address: 0xA020D004
- Base Offset: 0x20D004
- Size: 0x4

<p>Claim/Complete for context 13 (hart 6, Supervisor mode). Read to claim the highest-priority pending interrupt (returns 0 if none); write the claimed ID to signal completion.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 2:0|    ID    |  rw  | 0x0 |  — |

#### ID field

<p>Interrupt ID: 0 = no interrupt pending, 1..6 = valid interrupt source</p>

### threshold_ctx14 register

- Absolute Address: 0xA020E000
- Base Offset: 0x20E000
- Size: 0x4

<p>Priority threshold for context 14 (hart 7, Machine mode). Hardwired to 0 — all enabled pending interrupts are forwarded to this hart.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | THRESHOLD|   r  | 0x0 |  — |

#### THRESHOLD field

<p>Threshold (always 0)</p>

### claim_complete_ctx14 register

- Absolute Address: 0xA020E004
- Base Offset: 0x20E004
- Size: 0x4

<p>Claim/Complete for context 14 (hart 7, Machine mode). Read to claim the highest-priority pending interrupt (returns 0 if none); write the claimed ID to signal completion.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 2:0|    ID    |  rw  | 0x0 |  — |

#### ID field

<p>Interrupt ID: 0 = no interrupt pending, 1..6 = valid interrupt source</p>

### threshold_ctx15 register

- Absolute Address: 0xA020F000
- Base Offset: 0x20F000
- Size: 0x4

<p>Priority threshold for context 15 (hart 7, Supervisor mode). Hardwired to 0 — all enabled pending interrupts are forwarded to this hart.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | THRESHOLD|   r  | 0x0 |  — |

#### THRESHOLD field

<p>Threshold (always 0)</p>

### claim_complete_ctx15 register

- Absolute Address: 0xA020F004
- Base Offset: 0x20F004
- Size: 0x4

<p>Claim/Complete for context 15 (hart 7, Supervisor mode). Read to claim the highest-priority pending interrupt (returns 0 if none); write the claimed ID to signal completion.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 2:0|    ID    |  rw  | 0x0 |  — |

#### ID field

<p>Interrupt ID: 0 = no interrupt pending, 1..6 = valid interrupt source</p>

### threshold_ctx16 register

- Absolute Address: 0xA0210000
- Base Offset: 0x210000
- Size: 0x4

<p>Priority threshold for context 16 (hart 8, Machine mode). Hardwired to 0 — all enabled pending interrupts are forwarded to this hart.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | THRESHOLD|   r  | 0x0 |  — |

#### THRESHOLD field

<p>Threshold (always 0)</p>

### claim_complete_ctx16 register

- Absolute Address: 0xA0210004
- Base Offset: 0x210004
- Size: 0x4

<p>Claim/Complete for context 16 (hart 8, Machine mode). Read to claim the highest-priority pending interrupt (returns 0 if none); write the claimed ID to signal completion.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 2:0|    ID    |  rw  | 0x0 |  — |

#### ID field

<p>Interrupt ID: 0 = no interrupt pending, 1..6 = valid interrupt source</p>

### threshold_ctx17 register

- Absolute Address: 0xA0211000
- Base Offset: 0x211000
- Size: 0x4

<p>Priority threshold for context 17 (hart 8, Supervisor mode). Hardwired to 0 — all enabled pending interrupts are forwarded to this hart.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | THRESHOLD|   r  | 0x0 |  — |

#### THRESHOLD field

<p>Threshold (always 0)</p>

### claim_complete_ctx17 register

- Absolute Address: 0xA0211004
- Base Offset: 0x211004
- Size: 0x4

<p>Claim/Complete for context 17 (hart 8, Supervisor mode). Read to claim the highest-priority pending interrupt (returns 0 if none); write the claimed ID to signal completion.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 2:0|    ID    |  rw  | 0x0 |  — |

#### ID field

<p>Interrupt ID: 0 = no interrupt pending, 1..6 = valid interrupt source</p>

### threshold_ctx18 register

- Absolute Address: 0xA0212000
- Base Offset: 0x212000
- Size: 0x4

<p>Priority threshold for context 18 (hart 9, Machine mode). Hardwired to 0 — all enabled pending interrupts are forwarded to this hart.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | THRESHOLD|   r  | 0x0 |  — |

#### THRESHOLD field

<p>Threshold (always 0)</p>

### claim_complete_ctx18 register

- Absolute Address: 0xA0212004
- Base Offset: 0x212004
- Size: 0x4

<p>Claim/Complete for context 18 (hart 9, Machine mode). Read to claim the highest-priority pending interrupt (returns 0 if none); write the claimed ID to signal completion.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 2:0|    ID    |  rw  | 0x0 |  — |

#### ID field

<p>Interrupt ID: 0 = no interrupt pending, 1..6 = valid interrupt source</p>

### threshold_ctx19 register

- Absolute Address: 0xA0213000
- Base Offset: 0x213000
- Size: 0x4

<p>Priority threshold for context 19 (hart 9, Supervisor mode). Hardwired to 0 — all enabled pending interrupts are forwarded to this hart.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | THRESHOLD|   r  | 0x0 |  — |

#### THRESHOLD field

<p>Threshold (always 0)</p>

### claim_complete_ctx19 register

- Absolute Address: 0xA0213004
- Base Offset: 0x213004
- Size: 0x4

<p>Claim/Complete for context 19 (hart 9, Supervisor mode). Read to claim the highest-priority pending interrupt (returns 0 if none); write the claimed ID to signal completion.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 2:0|    ID    |  rw  | 0x0 |  — |

#### ID field

<p>Interrupt ID: 0 = no interrupt pending, 1..6 = valid interrupt source</p>

### threshold_ctx20 register

- Absolute Address: 0xA0214000
- Base Offset: 0x214000
- Size: 0x4

<p>Priority threshold for context 20 (hart 10, Machine mode). Hardwired to 0 — all enabled pending interrupts are forwarded to this hart.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | THRESHOLD|   r  | 0x0 |  — |

#### THRESHOLD field

<p>Threshold (always 0)</p>

### claim_complete_ctx20 register

- Absolute Address: 0xA0214004
- Base Offset: 0x214004
- Size: 0x4

<p>Claim/Complete for context 20 (hart 10, Machine mode). Read to claim the highest-priority pending interrupt (returns 0 if none); write the claimed ID to signal completion.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 2:0|    ID    |  rw  | 0x0 |  — |

#### ID field

<p>Interrupt ID: 0 = no interrupt pending, 1..6 = valid interrupt source</p>

### threshold_ctx21 register

- Absolute Address: 0xA0215000
- Base Offset: 0x215000
- Size: 0x4

<p>Priority threshold for context 21 (hart 10, Supervisor mode). Hardwired to 0 — all enabled pending interrupts are forwarded to this hart.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | THRESHOLD|   r  | 0x0 |  — |

#### THRESHOLD field

<p>Threshold (always 0)</p>

### claim_complete_ctx21 register

- Absolute Address: 0xA0215004
- Base Offset: 0x215004
- Size: 0x4

<p>Claim/Complete for context 21 (hart 10, Supervisor mode). Read to claim the highest-priority pending interrupt (returns 0 if none); write the claimed ID to signal completion.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 2:0|    ID    |  rw  | 0x0 |  — |

#### ID field

<p>Interrupt ID: 0 = no interrupt pending, 1..6 = valid interrupt source</p>

### threshold_ctx22 register

- Absolute Address: 0xA0216000
- Base Offset: 0x216000
- Size: 0x4

<p>Priority threshold for context 22 (hart 11, Machine mode). Hardwired to 0 — all enabled pending interrupts are forwarded to this hart.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | THRESHOLD|   r  | 0x0 |  — |

#### THRESHOLD field

<p>Threshold (always 0)</p>

### claim_complete_ctx22 register

- Absolute Address: 0xA0216004
- Base Offset: 0x216004
- Size: 0x4

<p>Claim/Complete for context 22 (hart 11, Machine mode). Read to claim the highest-priority pending interrupt (returns 0 if none); write the claimed ID to signal completion.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 2:0|    ID    |  rw  | 0x0 |  — |

#### ID field

<p>Interrupt ID: 0 = no interrupt pending, 1..6 = valid interrupt source</p>

### threshold_ctx23 register

- Absolute Address: 0xA0217000
- Base Offset: 0x217000
- Size: 0x4

<p>Priority threshold for context 23 (hart 11, Supervisor mode). Hardwired to 0 — all enabled pending interrupts are forwarded to this hart.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | THRESHOLD|   r  | 0x0 |  — |

#### THRESHOLD field

<p>Threshold (always 0)</p>

### claim_complete_ctx23 register

- Absolute Address: 0xA0217004
- Base Offset: 0x217004
- Size: 0x4

<p>Claim/Complete for context 23 (hart 11, Supervisor mode). Read to claim the highest-priority pending interrupt (returns 0 if none); write the claimed ID to signal completion.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 2:0|    ID    |  rw  | 0x0 |  — |

#### ID field

<p>Interrupt ID: 0 = no interrupt pending, 1..6 = valid interrupt source</p>

### threshold_ctx24 register

- Absolute Address: 0xA0218000
- Base Offset: 0x218000
- Size: 0x4

<p>Priority threshold for context 24 (hart 12, Machine mode). Hardwired to 0 — all enabled pending interrupts are forwarded to this hart.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | THRESHOLD|   r  | 0x0 |  — |

#### THRESHOLD field

<p>Threshold (always 0)</p>

### claim_complete_ctx24 register

- Absolute Address: 0xA0218004
- Base Offset: 0x218004
- Size: 0x4

<p>Claim/Complete for context 24 (hart 12, Machine mode). Read to claim the highest-priority pending interrupt (returns 0 if none); write the claimed ID to signal completion.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 2:0|    ID    |  rw  | 0x0 |  — |

#### ID field

<p>Interrupt ID: 0 = no interrupt pending, 1..6 = valid interrupt source</p>

### threshold_ctx25 register

- Absolute Address: 0xA0219000
- Base Offset: 0x219000
- Size: 0x4

<p>Priority threshold for context 25 (hart 12, Supervisor mode). Hardwired to 0 — all enabled pending interrupts are forwarded to this hart.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | THRESHOLD|   r  | 0x0 |  — |

#### THRESHOLD field

<p>Threshold (always 0)</p>

### claim_complete_ctx25 register

- Absolute Address: 0xA0219004
- Base Offset: 0x219004
- Size: 0x4

<p>Claim/Complete for context 25 (hart 12, Supervisor mode). Read to claim the highest-priority pending interrupt (returns 0 if none); write the claimed ID to signal completion.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 2:0|    ID    |  rw  | 0x0 |  — |

#### ID field

<p>Interrupt ID: 0 = no interrupt pending, 1..6 = valid interrupt source</p>

### threshold_ctx26 register

- Absolute Address: 0xA021A000
- Base Offset: 0x21A000
- Size: 0x4

<p>Priority threshold for context 26 (hart 13, Machine mode). Hardwired to 0 — all enabled pending interrupts are forwarded to this hart.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | THRESHOLD|   r  | 0x0 |  — |

#### THRESHOLD field

<p>Threshold (always 0)</p>

### claim_complete_ctx26 register

- Absolute Address: 0xA021A004
- Base Offset: 0x21A004
- Size: 0x4

<p>Claim/Complete for context 26 (hart 13, Machine mode). Read to claim the highest-priority pending interrupt (returns 0 if none); write the claimed ID to signal completion.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 2:0|    ID    |  rw  | 0x0 |  — |

#### ID field

<p>Interrupt ID: 0 = no interrupt pending, 1..6 = valid interrupt source</p>

### threshold_ctx27 register

- Absolute Address: 0xA021B000
- Base Offset: 0x21B000
- Size: 0x4

<p>Priority threshold for context 27 (hart 13, Supervisor mode). Hardwired to 0 — all enabled pending interrupts are forwarded to this hart.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | THRESHOLD|   r  | 0x0 |  — |

#### THRESHOLD field

<p>Threshold (always 0)</p>

### claim_complete_ctx27 register

- Absolute Address: 0xA021B004
- Base Offset: 0x21B004
- Size: 0x4

<p>Claim/Complete for context 27 (hart 13, Supervisor mode). Read to claim the highest-priority pending interrupt (returns 0 if none); write the claimed ID to signal completion.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 2:0|    ID    |  rw  | 0x0 |  — |

#### ID field

<p>Interrupt ID: 0 = no interrupt pending, 1..6 = valid interrupt source</p>

### threshold_ctx28 register

- Absolute Address: 0xA021C000
- Base Offset: 0x21C000
- Size: 0x4

<p>Priority threshold for context 28 (hart 14, Machine mode). Hardwired to 0 — all enabled pending interrupts are forwarded to this hart.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | THRESHOLD|   r  | 0x0 |  — |

#### THRESHOLD field

<p>Threshold (always 0)</p>

### claim_complete_ctx28 register

- Absolute Address: 0xA021C004
- Base Offset: 0x21C004
- Size: 0x4

<p>Claim/Complete for context 28 (hart 14, Machine mode). Read to claim the highest-priority pending interrupt (returns 0 if none); write the claimed ID to signal completion.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 2:0|    ID    |  rw  | 0x0 |  — |

#### ID field

<p>Interrupt ID: 0 = no interrupt pending, 1..6 = valid interrupt source</p>

### threshold_ctx29 register

- Absolute Address: 0xA021D000
- Base Offset: 0x21D000
- Size: 0x4

<p>Priority threshold for context 29 (hart 14, Supervisor mode). Hardwired to 0 — all enabled pending interrupts are forwarded to this hart.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | THRESHOLD|   r  | 0x0 |  — |

#### THRESHOLD field

<p>Threshold (always 0)</p>

### claim_complete_ctx29 register

- Absolute Address: 0xA021D004
- Base Offset: 0x21D004
- Size: 0x4

<p>Claim/Complete for context 29 (hart 14, Supervisor mode). Read to claim the highest-priority pending interrupt (returns 0 if none); write the claimed ID to signal completion.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 2:0|    ID    |  rw  | 0x0 |  — |

#### ID field

<p>Interrupt ID: 0 = no interrupt pending, 1..6 = valid interrupt source</p>

### threshold_ctx30 register

- Absolute Address: 0xA021E000
- Base Offset: 0x21E000
- Size: 0x4

<p>Priority threshold for context 30 (hart 15, Machine mode). Hardwired to 0 — all enabled pending interrupts are forwarded to this hart.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | THRESHOLD|   r  | 0x0 |  — |

#### THRESHOLD field

<p>Threshold (always 0)</p>

### claim_complete_ctx30 register

- Absolute Address: 0xA021E004
- Base Offset: 0x21E004
- Size: 0x4

<p>Claim/Complete for context 30 (hart 15, Machine mode). Read to claim the highest-priority pending interrupt (returns 0 if none); write the claimed ID to signal completion.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 2:0|    ID    |  rw  | 0x0 |  — |

#### ID field

<p>Interrupt ID: 0 = no interrupt pending, 1..6 = valid interrupt source</p>

### threshold_ctx31 register

- Absolute Address: 0xA021F000
- Base Offset: 0x21F000
- Size: 0x4

<p>Priority threshold for context 31 (hart 15, Supervisor mode). Hardwired to 0 — all enabled pending interrupts are forwarded to this hart.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | THRESHOLD|   r  | 0x0 |  — |

#### THRESHOLD field

<p>Threshold (always 0)</p>

### claim_complete_ctx31 register

- Absolute Address: 0xA021F004
- Base Offset: 0x21F004
- Size: 0x4

<p>Claim/Complete for context 31 (hart 15, Supervisor mode). Read to claim the highest-priority pending interrupt (returns 0 if none); write the claimed ID to signal completion.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
| 2:0|    ID    |  rw  | 0x0 |  — |

#### ID field

<p>Interrupt ID: 0 = no interrupt pending, 1..6 = valid interrupt source</p>

## nic_config address map

- Absolute Address: 0xFE000000
- Base Offset: 0xFE000000
- Size: 0x16000

|Offset|   Identifier  |Name|
|------|---------------|----|
|  0x0 |ni700_registers|  — |

## ni700_registers memory

- Absolute Address: 0xFE000000
- Base Offset: 0x0
- Size: 0x16000

<p>Refer to arm_corelink_ni_700_network_on_chip_trm_101566_0201_09_en-3.pdf for details</p>

No supported members.

