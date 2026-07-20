# AXI4-Verification
A UVM-based verification environment for the AMBA AXI4 protocol, built to verify AXI4-compliant master/slave IPs against the ARM AMBA AXI4 protocol specification.
Overview

This project implements a constrained-random, coverage-driven verification (CRV) environment for AXI4 using SystemVerilog and UVM. It targets protocol compliance, functional correctness, and corner-case behavior of an AXI4 DUT (master and/or slave interface), with self-checking scoreboards and protocol assertions (SVA) to catch timing and handshake violations.
Features
UVM testbench (agents, sequencer, driver, monitor, scoreboard, environment)
Independent read and write channel handling (AW/W/B and AR/R channels)
Constrained-random sequence generation: bursts (FIXED / INCR / WRAP), variable burst lengths, narrow transfers, unaligned addresses, outstanding transactions
Protocol compliance checks via SystemVerilog Assertions (SVA) — handshake stability, valid/ready protocol, burst boundary rules
Functional coverage model (burst type, size, length, response type, outstanding depth)
Scoreboard with reference model for data/response checking
Regression-ready test list with reusable base test/sequence classes
