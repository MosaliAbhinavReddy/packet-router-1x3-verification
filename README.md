# Packet Router 1x3 Design and Verification

This project implements a synthesizable RTL model and a UVM-based verification environment for a 1x3 packet router using SystemVerilog. The router receives packets via a single input port and routes them to one of three output ports based on a 2-bit destination address in the packet header.

---

## 📁 Project Structure

Router1x3-Design-Verification-master/
│
├── rtl/              # RTL design files (router, FSM, register, FIFO, synchronizer)
├── tb/               # UVM testbench environment (env, sequencer, scoreboard, top)
├── wr_agt_top/       # Write agent components (driver, monitor, sequences)
├── rd_agt_top/       # Read agent components (driver, monitor, sequences)
├── test/             # Test classes and configuration
├── doc/              # Reports (router_report.pdf, router_report.docx)
└── README.md         # Project description and instructions

---

##  Features

- **Packet Format**: Header (DA + Length), Payload (1–63 bytes), Parity (8-bit)
- **Routing Logic**: Routes based on 2-bit destination address (0–2), address 3 is invalid
- **FIFO Buffers**: Three 16x9 FIFOs (one per output port)
- **Error Handling**: Parity checking, FIFO timeout detection, high-impedance data output on error
- **UVM Testbench**: Modular verification with sequencers, monitors, scoreboard, and coverage model

---

##  Test Scenarios

- Valid packets (1–63 bytes payload)
- Corrupt packets (bad parity)
- FIFO timeout / unread packets
- Simultaneous read/write handling
- FIFO full behavior with busy signal

---

##  How to Run Simulation

> Replace `<simulator>` with `vcs`, `modelsim`, etc., as per your setup

1. Open terminal in project root
2. Run your simulation script or use:

```sh
cd code/tb/
<simulator> top.sv ../rtl/*.v ../wr_agt_top/*.sv ../rd_agt_top/*.sv ../tb/*.sv ../test/*.sv

 Documentation
	•	router_report.pdf: Detailed architecture, protocol, FSM, and simulation results
	•	Includes design decisions, error handling, and coverage of critical corner cases



Abhinav Reddy Mosali
