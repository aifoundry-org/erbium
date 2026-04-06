# DV Master Plan
(for ET Erbium)

## Architecture Freeze - DV Plan

## Mission

Verify functional correctness\, robustness\, and compliance before tape\-out

## Verification Strategy



* Methodology:
  * Directed testing
  * Constrained randoms to uncover corner cases\, unexpected interactions and boost confidence in the design
* Testbench Architecture:
  * Re\-use and improve
    * Erbium and ET\-SoC\-1 testbenches
    * Copper SOC testbench
    * MRAM testbench
  * Develop
    * ET\-Link to AXI4 bridge testbench
    * Periph testbench \( QSPI\, xSPI\, I2C\, UART\)
* Regression and automation:
  * B4C \(Github CI\) to validate new changes \(subset of tests\)
  * Weekly regression to measure overall progress and readiness \(full test suite\)


## DV Testbenches



* Esperanto Verification Library \(EVL\):
  * Based on SystemVerilog and Universal Verification Methodology \(UVM\)
  * Covers only Neigh and Minion verification
  * Source code:  _[nekkoai/et\-soc](https://github.com/nekkoai/et-soc/tree/erbium/dev)_
* ET\-Link to AXI4 \(ETL2AXI\):
  * Based on PyUVM\, written in Python
  * Covers only the ET\-Link to AXI4 Bridge
  * Source code:  _[nekkoai/etl2axi\-tb](https://github.com/nekkoai/etl2axi-tb/tree/main)_
* CocoTB:
  * Based on Python
  * Covers Full Chip verification
  * Source code:  _[Erbium/HDL](http://gitlab.veevx.net/erbium/hdl/-/tree/dev/erbium_digital/testbench?ref_type=heads)_
* MRAM:
  * Based on SystemVerilog and Universal Verification Methodology \(UVM\)
  * Covers AXI Bridge\, BIST\, and target MRAM functionality\.
  * Source code:  _[Erbium/Netlist Testbenches](http://gitlab.veevx.net/erbium/netlist-testbenches)_


## DV Testbenches - EVL



* EVL includes many checking mechanisms:
  * L1 Data Cache scoreboard
  * Neighborhood scoreboard
  * Bus \(ET\-Link\) verification components
  * SystemVerilog Assertions
* Co\-simulation:
  * Covers the gap that EVL checkers leave \(e\.g\. memory consistency checking\, ISA checking\)
* Stimulus:
  * Current number of C and Asm tests: 1529
  * Will require porting shire build tests to the neigh build
  * Re\-use ET\-SoC\-1 coverage to measure how thoroughly the design has been tested against its specifications\.


## DV Testbenches - ETL2AXI



* Why a new testbench?
  * __New development:__  Bridge will be implemented largely from scratch → initial verification confidence is low
  * __Critical component:__   <span style="color:#26221f">Any malfunction could stall cores\, block transactions\, corrupt data\, and isolate the Minions from the outside the Neigh world</span>
  * __Verification approach:__  Build a lightweight yet comprehensive testbench to ensure robustness and reliability while enabling faster turnaround
* Checking mechanisms:
  * Bus protocol \(ET\-Link and AXI4\) scoreboards
  * ET\-Link to AXI4 translation scoreboards
  * Assertion based protocol checks
* Stimulus:
  * Random bus requests injected directly into the RTL bridge bus interface
  * Error injection and back pressure knobs


## DV Testbenches - CocoTB



* Full Chip verification scope:
  * Verify data flow and connectivity between Minions\, MRAM\, interconnects and peripherals
  * Verify system\-level interactions like interrupts and IO devices
  * Test the real bootrom in the RTL
  * Verify top level pad connections
* Co\-simulation:
  * Integrate sysemu co\-simulation in CocoTB \(very nice to have\)
* Stimulus:
  * <span style="color:#ff0000">TODO \- Tests? </span>  _[Verification\_Plan\_Veevx\.xlsx](https://veevx.sharepoint.com/:x:/s/contractors/IQANelpaDbq3Rq0ptIR6YDb_ATRs7LV7596cWXatl8Te9-c?e=062u6I)_
  * <span style="color:#ff0000">TODO \- Coverage?</span>


## DV Testbenches - MRAM



* Focused Functional Verification:
  * __Multi\-level testbench: __ Reduces test time by running different hierarchies of the MRAM with directed testing of different features
  * __AXI protocol checking:__  checks the AXI2MRAM bridge for adherence to the underlying protocol\.
  * __Debug interface checking:__  ensures that all test registers are accessible and have their desired functionality
* Checking Mechanism:
  * ???
* Stimulus:
  * Directed Testing
  * Directed Random


## DV Testbenches - xSPI



* Requirements
  * Synopsys VIP: For functional verification using UVM\.
  * Synaptics\-Lab Controller: For verification on FPGA\.
  * Various Opensource SPI/QSPI/xSPI\(?\) Controllers: For compatibility testing
  * cocotbext\-spi: For SPI Mode verification
  * cocotbext\-xspi: Inhouse developed for all mode verification\.
* Environments
  * Multiple Testbenches:
  * Cocotb xspi Env: Developed inhouse\. for testing all features\.
  * UVM Env with Synopsys VIP: For mitigating the risks of same person developing RTL and cocotb VIP\.
  * Env with QSPI RTL: For testing compatibility with available controller\.
  * FPGA with QSPI controller\, for testing compatibility\.
* Checking Mechanism:
  * Assertion/Scoreboard\.
  * Waveform Analysis \(WAL?\)
* Stimulus:
  * Directed Testing\(TOML file Based\)
  * Directed Random\(Cross of Rates\, Bursts\,Transaction types\,XIP\,Error cases\)
* Coverage:
  * 100% line\, close to 100% for branch\,toggle\, fsm\.
  * 100% Functional with waivers


## DV Testbenches - I2C, QSPI, UART



* Opensource IP’s either FPGA or Silicon Proven\. with their own testbenches\.
* Tasks:
  * Check testbenches for completeness\, code \+functional coverages\.
  * Assume testbench suffers from “same developer error” Reimplement in cocotb and reverify\.
* Environments
  * Unit level testbenches for each IP:
  * Cocotb xspi Env: Developed inhouse\. for testing all features\.
  * UVM Env with Synopsys VIP: For mitigating the risks of same person developing RTL and cocotb VIP\.
  * cocotbext\-spi\,cocotbext\-i2c\,cocotbext\-uart based unit testing\.
* Checking Mechanism:
  * Assertion/Scoreboard\.
* Stimulus:
  * Directed Testing\(TOML file Based\)
  * Directed Random\(Cross of Rates\, Bursts\,Transaction types\,XIP\,Error cases\)
* Coverage:
  * 100% line\, close to 100% for branch\,toggle\, fsm\.
  * 100% Functional with waivers


## DV Testbenches - SOC



* Plan
  * Existing Cocotb based TB with mix of SV/UVM code\.
  * Add new tests for QSPI\, UART\, I2C
    * Use cocotbext\-\[SPI\,UART\,I2C\] VIP’s
    * Test QSPI using Synopsys xSPI VIP in SPI and QSPI Mode\.
  * Modify C code from ARM to RISC\-V
  * Add New tests for Changes in Registers\.
  * Add CPU\-Subsystem integration tests\.
* Goal:
  * Assume all features are unit tested\. Focus on integration and functionality tests\.
  * Check every unit is able to communicate with every other unit in every mode of operation\.
  * Verify Memory Map\.
  * Check robustness of communication with outside world\.
  * Run at least one realworld usecase and measure performance\.
* Coverage methodology\.
  * Coverage will not be considered for IP’s which are unit tested\.
    * Pin toggle covered will be considered for integration verification completeness
  * RAL Tests will not contribute to coverage for any environment \(unit\, system\,soc\)


## DV Testbenches - Validation

Validation on Alveo U250

## DV Co-Simulation



* Use  _sysemu_  to handle the co\-simulation in RTL
  * Source code:  _[aifoundry\-org/et\-platform](https://github.com/aifoundry-org/et-platform)_
* How co\-simulation works?
  * Every time a Minion commits an instruction\, its architectural state is captured
  * During test execution\, the captured architectural state is continuously compared against the golden model \(sysemu\)
* Example of co\-simulation checks :
  * Ensure that RTL does not violate software program order
  * Check memory consistency order
  * Verify memory data correctness


## Constrained Randoms



* Corner\-case bugs are often difficult to anticipate and even more challenging to reproduce reliably\.
* Some ET\-SoC\-1 show\-stopper bugs that would have been missed by directed tests:
  * _[RTLMIN\-5813](https://esperantotech.atlassian.net/browse/RTLMIN-5813)_ : Thread 1 starves Thread 0 to complete a Tensor Store
  * _[RTLMIN\-5929](https://esperantotech.atlassian.net/browse/RTLMIN-5929)_ : DCACHE replay\_queue and buffer\_array entry counters may not discount allocated entries \(credit/counter leaking\) when gsc and regular operations overlap
  * _[RTLMIN\-6181](https://esperantotech.atlassian.net/browse/RTLMIN-6181)_ : TensorReduce stalls both threads 0 and 1 from executing VPU instructions ends up in deadlock
* For ET\-SoC\-1 we used STING \(commercial\, Synopsys\)\, but for post\-silicon we developed an in\-house random test generator named MTG\.
* __Proposal:__  revive MTG to fill the gap and boost confidence in the design
* MTG is written in Python\, does not require a license and is highly configurable
* Source code:  _[nekkoai/dv](https://github.com/nekkoai/dv/tree/main/mtg)_


## Verification Flows

__RTL Simulation: __ Validates functionality at a high level with zero\-delay models\.

__Gate\-Level Simulation:__  Runs on the synthesized netlist\, supporting either zero\-delay \(for faster simulation\) or real timing delays \(closer to silicon behavior\)

__X\-Propagation:__  Model unknown values \(X\) realistically\, ensuring simulation reflects real silicon behavior

__Power\-Aware verification \(UPF\):__  validates power intent across domains

__Emulation \(FPGA\):__  Run the design on hardware to accelerate verification and enable early software testing

## DV tools



* __Primary toolset:__  Synopsys tools \(commercial\)
  * Verilator is currently not supported but it is something we should explore in the future
* Key functions:
  * Simulation \(VCS\) for block\-level and full\-chip tests
  * Coverage analysis and closure tracking
  * Debug environment for waveform and log analysis
* Licenses requirement:
  * For CI \(B4C\):  <span style="color:#ff0000">TBD</span>
    * \# of ET Tests: 134
    * Total time assuming one license
  * For Regressions:  <span style="color:#ff0000">TBD</span>
    * \# of Erbium tests:  <span style="color:#ff0000">\(?\)</span>
    * \# of ET tests: 1529
    * Total time assuming one license


## Verification Goals

Achieve 100% of planned functional coverage

Reach >=95% code coverage on reachable logic

All directed test passing in regression

All random tests passing and stable in regression

Enable co\-simulation with sysemu

Run successfully the bootrom in simulation

Run MRAM wellness algorithm in simulation

…

## DV Master Plan
(for ET Erbium)

## Architecture Freeze - DV Plan

