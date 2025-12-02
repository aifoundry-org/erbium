<!---
Markdown description for SystemRDL register map.

Don't override. Generated from: System_Reg
  - ../regblocks/systemrdl/system.rdl
-->

# System_Reg address map

- Absolute Address: 0x0
- Base Offset: 0x0
- Size: 0x8C

<p>Register Controlling System Behavior</p>

|Offset|      Identifier     |Name|
|------|---------------------|----|
| 0x00 |       Version       |  — |
| 0x08 |     SystemConfig    |  — |
| 0x10 |    WATCHDOG_COUNT   |  — |
| 0x18 |       Watchdog      |  — |
| 0x20 |     SysInterrupt    |  — |
| 0x28 |      SoftReset      |  — |
| 0x30 |      ResetCause     |  — |
| 0x38 |    PowerDomainReq   |  — |
| 0x40 |    PowerDomainAck   |  — |
| 0x48 |      PowerGood      |  — |
| 0x50 |       SpinLock      |  — |
| 0x58 |       ChipMode      |  — |
| 0x60 |       Mailbox0      |  — |
| 0x68 |       Mailbox1      |  — |
| 0x70 |       GPIO_OE       |  — |
| 0x78 |        GPIO_I       |  — |
| 0x80 |        GPIO_O       |  — |
| 0x88 |GPIO_Interrupt_Enable|  — |

### Version register

- Absolute Address: 0x0
- Base Offset: 0x0
- Size: 0x4

<p>Device identifier, used by software to identify the device family (chipid) variant, and bugfix version</p>

| Bits|Identifier|Access| Reset|Name|
|-----|----------|------|------|----|
| 7:0 |  respin  |   r  |  0x0 |  — |
| 15:8| variation|   r  |  0x0 |  — |
|31:16|  chipid  |   r  |0xEB68|  — |

### SystemConfig register

- Absolute Address: 0x8
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

### WATCHDOG_COUNT register

- Absolute Address: 0x10
- Base Offset: 0x10
- Size: 0x4

<p>The watchdog detects 'hang' conditions and resets the system. This feature is disabled by default. Clear <code>cpu_config.wdog_disable</code> to enable this. Once enabled, S/W should write to <code>Watchdog.kick</code> to reset the <code>WATCHDOG_COUNT.count</code> field. If the count reaches 0, it triggers a system reset.</p>

|Bits|  Identifier  |Access| Reset|Name|
|----|--------------|------|------|----|
|31:0|watchdog_count|  rw  |0xFFFF|  — |

#### watchdog_count field

<p>When the watchdog timer is enabled it counts down from this value</p>

### Watchdog register

- Absolute Address: 0x18
- Base Offset: 0x18
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  7 |   kick   |  rw  | 0x0 |  — |

#### kick field

<p>Resets the watchdog timer, cpu needs to regularly write to this bit to aviod a watchdog timeout based reset of the device</p>

### SysInterrupt register

- Absolute Address: 0x20
- Base Offset: 0x20
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|  0 | interrupt|  rw  | 0x0 |  — |

#### interrupt field

<p>Write to this bit to generate an interrupt</p>

### SoftReset register

- Absolute Address: 0x28
- Base Offset: 0x28
- Size: 0x4

|Bits|  Identifier  |Access|Reset|Name|
|----|--------------|------|-----|----|
|  0 |  soft_reset  |  rw  | 0x0 |  — |
|  1 |cpu_warm_reset|  rw  | 0x0 |  — |
|  2 |  mram_rst_b  |  rw  | 0x1 |  — |

#### soft_reset field

<p>System Soft Reset, Active High</p>

#### cpu_warm_reset field

<p>CPU Warm Reset, Active High</p>

#### mram_rst_b field

<p>MRAM Resetn, Active Low</p>

### ResetCause register

- Absolute Address: 0x30
- Base Offset: 0x30
- Size: 0x4

<p>This register reports the cause of reset. There are multiple reset sources.
            * Power on Reset,
            * Brownout Reset, and
                * Various S/W reset requests. These clear on read bits capture the reset cause since the last read
<strong>Note</strong> if the por bit is set ignore the other cause registers, they will have random values until the first read.</p>

|Bits|    Identifier   | Access|Reset|Name|
|----|-----------------|-------|-----|----|
|  0 |       por       |r, rclr| 0x1 |  — |
|  1 |watchdog_timedout|r, rclr|  —  |  — |
|  2 |   sysreset_req  |r, rclr|  —  |  — |
|  3 |     brownout    |r, rclr|  —  |  — |
|  4 |    softreset    |r, rclr|  —  |  — |
|  5 |     hresetn     |r, rclr|  —  |  — |

#### por field

<p>System POR was toggled</p>

#### watchdog_timedout field

<p>Watchdog was enabled and CPU failed to clear the watchdog timer</p>

#### sysreset_req field

<p>CPU detected an architecture level lockup and requested  a system reset</p>

#### brownout field

<p>The brownout detector triggered a reset</p>

#### softreset field

<p>The soft reset bit was written to</p>

#### hresetn field

<p>The cpu reset bit was written to</p>

### PowerDomainReq register

- Absolute Address: 0x38
- Base Offset: 0x38
- Size: 0x4

<p>Writing to PD fields initiates the shutdown of the corresponding power domain. A shutdown request is sent to the domain, This domain waits until all outstanding transactions are completed and then generates a corresponding ack signal. Once the ack signal is generated the power controller will turn off power to that domain.</p>

|Bits|    Identifier   |Access|Reset|Name|
|----|-----------------|------|-----|----|
|  0 |      cpu_pd     |  rw  | 0x0 |  — |
|  1 |     sram_pd     |   r  | 0x0 |  — |
|  2 |cpu_ram_powerdown|  rw  | 0x0 |  — |
|  3 |    chiplet_pd   |   r  | 0x0 |  — |
|  4 |     mram_pd     |  rw  | 0x0 |  — |
|  5 | system_poweroff |   w  | 0x0 |  — |
|  6 |     hyperbus    |   r  | 0x0 |  — |
|15:8|    minion_pd    |  rw  | 0x0 |  — |
| 16 |  mram_dsleep_en |  rw  | 0x1 |  — |
| 17 |   cpu_sleep_en  |  rw  | 0x0 |  — |

#### cpu_pd field

<p>Poweroff the ARM Domain</p>

#### sram_pd field

<p>Not used, in future connected to TCM poweroff bit</p>

#### cpu_ram_powerdown field

<p>Powerdown the CPU ram. this puts the ram in deepsleep mode</p>

#### chiplet_pd field

<p>Not used; chiplet power domain is controlled via the mode bits</p>

#### mram_pd field

<p>Power down for MRAM digital logic</p>

#### system_poweroff field

<p>Power of the chip.only wakeup logic is powered on</p>

#### hyperbus field

<p>Not used; hyperbus power domain is controlled via the mode bits.</p>

#### minion_pd field

<p>Minion PowerDown Req</p>

#### mram_dsleep_en field

<p>connected to dsleep pin on mram_wrapper</p>

#### cpu_sleep_en field

<p>currently not used. In future this will be used for CPU sleep management.</p>

### PowerDomainAck register

- Absolute Address: 0x40
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
|15:8| minion_pd_ack |  rw  | 0x0 |  — |

#### cpu_pd_ack field

<p>pd ack for cpu</p>

#### sram_pd_ack field

<p>Not used;pd ack for TCM</p>

#### chiplet_pd_ack field

<p>Not used;pd ack for chiplet</p>

#### mram_pd_ack field

<p>pd ack for mram</p>

#### system_pd_ack field

<p>pd ack for system</p>

#### hyperbus_pd_ack field

<p>Not used;pd ack for hyperbus</p>

#### minion_pd_ack field

<p>Minion PowerDown Req</p>

### PowerGood register

- Absolute Address: 0x48
- Base Offset: 0x48
- Size: 0x4

<p>When a power domain is switched on, it takes time for the voltage to stabalize, this time is process dependent. The default value is sufficiently large to account for all variations.</p>

|Bits|Identifier|Access| Reset |Name|
|----|----------|------|-------|----|
|20:0|  counter |  rw  |0xFFFFF|  — |

#### counter field

<p>Counter for powerGood</p>

### SpinLock register

- Absolute Address: 0x50
- Base Offset: 0x50
- Size: 0x4

<p>initially locked=0, A read on this register will set the lock bit.
<strong>Usage:</strong> 
1. Read this field. If you get a value of zero you got the lock. Else a different processing element acquired the lock. Poll at fixed intervals(dont spam) until you get the lock.
2. If you acquired the lock, Once you have finished interacting with the locked resource write 0 to this register to release the lock.</p>

|Bits|Identifier| Access |Reset|Name|
|----|----------|--------|-----|----|
|  0 |   lock   |rw, rset| 0x0 |  — |

### ChipMode register

- Absolute Address: 0x58
- Base Offset: 0x58
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

- Absolute Address: 0x60
- Base Offset: 0x60
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0|   mbox0  |  rw  | 0x0 |  — |

#### mbox0 field

<p>Mailbox0</p>

### Mailbox1 register

- Absolute Address: 0x68
- Base Offset: 0x68
- Size: 0x4

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|31:0|   mbox1  |  rw  | 0x0 |  — |

#### mbox1 field

<p>Mailbox1</p>

### GPIO_OE register

- Absolute Address: 0x70
- Base Offset: 0x70
- Size: 0x4

<p>Gpio Output enable.
Write 1 to this bit to set the GPIO register in output mode.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|10:0|  gpio_oe |  rw  | 0x0 |  — |

#### gpio_oe field

<p>Gpio output enable</p>

### GPIO_I register

- Absolute Address: 0x78
- Base Offset: 0x78
- Size: 0x4

<p>Gpio Input
For each bit in input mode this register captures the input value.</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|10:0|  gpio_i  |   r  | 0x0 |  — |

#### gpio_i field

<p>Gpio input</p>

### GPIO_O register

- Absolute Address: 0x80
- Base Offset: 0x80
- Size: 0x4

<p>Gpio Output
For each bit in output mode the content of the corresponding bit in this register is reflected on the GPIO Pin</p>

|Bits|Identifier|Access|Reset|Name|
|----|----------|------|-----|----|
|10:0|  gpio_o  |   r  | 0x0 |  — |

#### gpio_o field

<p>Gpio input</p>

### GPIO_Interrupt_Enable register

- Absolute Address: 0x88
- Base Offset: 0x88
- Size: 0x4

<p>Gpio Interrupt Enable
For each bit in input mode if the input signal toggles and the content of the corresponding bit in this register is 1, then a GPIO interrupt is raised.</p>

|Bits|    Identifier   |Access|Reset|Name|
|----|-----------------|------|-----|----|
|10:0|gpio_interrupt_en|   r  | 0x0 |  — |

#### gpio_interrupt_en field

<p>Gpio input</p>
