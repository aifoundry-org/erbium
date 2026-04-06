# Minion
## ISA changes

Erbium presents a change in topology that affects some of the instructions that were available on ET-SoC1. All supported features are present with the following changes:

- ET Atomic extension instructions with global and local variants will affect the same level of memory hierarchy contrary to what happens in ET-SoC1.
- ET *TensorSend* and *TensorReceive* instructions will not be performed and set *tensor\_error\[9\]* when executed with *Receiver/Sender ET-Minion ID* outside the range of 0..7
- ET *TensorReduce* and *TensorBroadcast* instructions will not be performed and set *tensor\_error\[9\]* when executed with *Tree depth* outside the range of 0..2

The following instructions are not supported in Erbium and will raise an illegal exception

- TensorLoadL2Scp

ET-SoC1 had a set of deprecated features which suffered the following changes in Erbium:

- Messaging Extension has been removed
- M-mode Virtual Memory extension has been removed
- GFX extensions still present with the following changes
  - *frcp\_fix.rast,* *fcvt.ps.rast* and *fcvt.rast.ps* instructions have been removed and will raise an illegal instruction exception

## Errata fixes

Erbium fixes the following ET-SoC1 erratas. 

* RTLMIN-5374: Gather/Scatter instruction is missing some load/store operations since gscprogress register is not updated
* RTLMIN-6136: Tensor Conv clashes with a write to tensor\_mask
* RTLMIN-6221: Branch Taken events for performance counters are not correctly generated
* RTLMIN-6282: VPU not connected to Minion Shire warm reset
* RTLMIN-6488: Writes to PMU registers may happen twice
* RTLMIN-6520: Write to the Tensor mask does not wait for previous tensor\_conv\_size
* RTLMIN-6614: Intensive usage of UC operations in one Minion thread may produce starvation to the other thread
* RTLMIN-5985: HART ESR address is not correctly checked
* RTLMIN-6398: Part of a misaligned access may execute with the wrong privilege
* RTLMIN-6397: Exceptions on misaligned accesses may not release Minion resources
* RTLMIN-6455: Resume state machine only works for Minion 0
* RTLMIN-6452: Hart can execute unexpected instructions in debug mode
* RTLMIN-6496: Simultaneous reading from both Minion threads of the PMU registers may return incorrect data to the second thread doing the read
* RTLMIN-6509: Debug access to the L1 ICache tag memory incorrectly enables simultaneous access to the L0 microcache 0 memories

## CSR Changes

CSRs are the same as Minion ET-SoC1 with the following changes:

* *mtvec/stvec* CSRs *BASE* field requires
  * In Direct mode, *BASE* field contains bits XLEN-1 through 2 of a 4-byte aligned address
  * In Vector mode, *BASE* field contains bits XLEN-1 though 7 of a 128-byte aligned address. Bits 6 to 2 become WARL(0)
* Field *coopneighmask* in *tensor\_cooperation* becomes WARL(0..1)
* *matp* and *satp* are now WARL(0)
* *sum* field in *mstatus* is now RO(0)
* *marchid* CSR value changed to 0x4554000000000001
* *mimpid* CSR value changed to 0x10000
* The following CSRs were removed and will raise and illegal instruction exception
  * *portheadnb0*
  * *portheadnb1*
  * *portheadnb2*
  * *portheadnb3*
  * *porthead0*
  * *porthead1*
  * *porthead2*
  * *porthead3*
  * *portctl0*
  * *portctl1*
  * *portctl2*
  * *portctl3*
  * *tex\_send*
* The following new CSRs are implemented
  * *tdata3 \-* implemented as WARL(0)
