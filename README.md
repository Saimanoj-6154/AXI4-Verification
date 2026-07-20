# AXI4-Verification
A UVM-based verification environment for the AMBA AXI4 protocol, built to verify AXI4-compliant master/slave IPs against the ARM AMBA AXI4 protocol specification.
Overview

This project implements a constrained-random, coverage-driven verification (CRV) environment for AXI4 using SystemVerilog and UVM. It targets protocol compliance, functional correctness, and corner-case behavior of an AXI4 DUT (master and/or slave interface), with self-checking scoreboards and protocol assertions (SVA) to catch timing and handshake violations.


## Features

- UVM testbench (agents, sequencer, driver, monitor, scoreboard, environment)
- Independent read and write channel handling (AW/W/B and AR/R channels)
- Constrained-random sequence generation: bursts (FIXED / INCR / WRAP), variable burst lengths, narrow transfers, unaligned addresses, outstanding transactions
- Protocol compliance checks via SystemVerilog Assertions (SVA) — handshake stability, valid/ready protocol, burst boundary rules
- Functional coverage model (burst type, size, length, response type, outstanding depth)
- Scoreboard with reference model for data/response checking
- Regression-ready test list with reusable base test/sequence classes

---

## Repository Structure

```
axi4-verification/
├── rtl/                  # AXI4 DUT (master/slave) RTL sources
├── tb/
│   ├── agents/
│   │   ├── axi4_master_agent/
│   │   └── axi4_slave_agent/
│   ├── env/               # axi4_env, scoreboard, coverage collector
│   ├── sequences/         # base + directed + random sequence library
│   ├── tests/              # UVM test classes
│   └── top/                # tb_top, interface, clocking blocks
├── assertions/            # SVA protocol checkers (axi4_sva_pkg)
├── sim/                    # simulator scripts, filelists, waveform configs
├── docs/                   # verification plan, coverage plan
└── README.md
```

---

## Tools & Environment

| Category          | Tool(s)                          |
|--------------------|-----------------------------------|
| HDL / Verification | SystemVerilog, UVM 1.2, SVA       |
| Simulation          | QuestaSim / ModelSim               |
| Waveform             | GTKWave / QuestaSim WLF viewer     |
| Scripting             | Tcl, Makefile                      |
| Coverage               | Functional + code coverage (simulator native) |

---

### Prerequisites
- A SystemVerilog simulator with UVM 1.2 support (e.g., QuestaSim, VCS, Xcelium; Verilator with limited UVM support)
- `UVM_HOME` set to your UVM library installation

### Compile & Run
```bash
cd sim
make compile          # compiles RTL + TB sources
make run TEST=axi4_write_read_test   # runs a specific test
make regress           # runs full regression test list
```

### Waveforms
```bash
make waves TEST=axi4_write_read_test
```

### Coverage Report
```bash
make cov_report
```
## Verification Summary

| Feature                  | Status |
|----------------------------|--------|
| Single beat read/write      | ✅ |
| INCR burst (1–256 beats)     | ✅ |
| WRAP burst                    | ✅ |
| FIXED burst                    | ✅ |
| Narrow transfers                | ✅ |
| Unaligned start address          | ✅ |
| Outstanding/out-of-order transactions | ✅ |
| Error response (SLVERR/DECERR)         | ✅ |
| Protocol assertion checks               | ✅ |

## Results

- Functional coverage: `XX%`
- Code coverage: `XX%`
- Bugs found/fixed during verification: list key ones here
