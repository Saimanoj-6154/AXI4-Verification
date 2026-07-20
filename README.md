# AXI4-Verification
A UVM-based verification environment for the AMBA AXI4 protocol, built to verify AXI4-compliant master/slave IPs against the ARM AMBA AXI4 protocol specification.
Overview

This project implements a constrained-random, coverage-driven verification (CRV) environment for AXI4 using SystemVerilog and UVM. It targets protocol compliance, functional correctness, and corner-case behavior of an AXI4 DUT (master and/or slave interface), with self-checking scoreboards and protocol assertions (SVA) to catch timing and handshake violations.
