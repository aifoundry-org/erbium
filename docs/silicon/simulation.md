# Simulation Environment

* The Simulation environment is a mix of Cocotb + SystemVerilog.
* Existing unit level environments in SV/SV-UVM are retained as is.
* New environments are created using the cocotb framework.
* The simulation env for each module is in the testbench folder. This is a Makefile based cocotb environment.
* The Makefile is customized for VCS, for other simulators replace COMPILE_ARGS, PLUS_ARGS and SIM with the appropriate options.
* The code may contain language artifacts that cannot be processed by opensource simulators like Verilator/Icarus verilog.
* Python version equal to or higher than 3.10 is required to run the simulation.
* Use  test_digital.py as a template for new tests.
* Most of the SOC tests are in` erbium_digital/testbench` folder

## Steps for running verification

![Verification Environment](output/verification.png)

* git clone git@gitlab.veevx.net:erbium/hdl-et.git
* cd hdl-et/
* source .venv/bin/activate
* uv sync --upgrade
* make build 
* make <MODULE=testname>

To know more about cocotb ref

* [cocotb documentation](https://docs.cocotb.org),
* [cocotb tutorial](https://youtube.com/playlist?list=PL3Z0z1uoFF-CElbEpGoRa5ph-TJUzuKnm&si=4XN-64NIIUWVjFTf)
