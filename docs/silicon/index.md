# Overview


![Erbuim RISCV Isotope](output/dut.png)


## Features
* External Interfaces
	* JTAG
	* UART
	* xSPI Target,
	* I2C Controller
	* (Q)SPI Controller
	* 11 GPIO
	* Chiplet Interfaces
		* AHB
		* AXI
* CPU:
	* 8C,16T RISCV64(IMDFC +Tensor, +Vector) 

### xSPI Interface

* JESD251C and JESD216H compliant
* Supports
	* 1S-1S-1S
	* 4S-4D-4D
	* 4D-4D-4D
	* 8S-8S-8S
	* 8D-8D-8D (Octal)
	* 8D-8D-8D (Hyperbus)
* Operating frequency 200 Mhz
* 64 bit register and memory access 
* Linear Burst capable.

### Chiplet Interface

* 2 Interfaces AXI, AHB
* AXI and AHB in 32bit and 64 bit variants.
* Chiplet interface is not available in testchip tapeouts.

**Note:** While the chiplet interface is a part of the design it is not available(optimised away during PD) in testchips. i.e. erbium will not have the chiplet interface.
	
