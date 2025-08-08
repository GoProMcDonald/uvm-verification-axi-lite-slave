# AXI-Lite UVM Verification Environment

## Overview
This project implements a **SystemVerilog UVM verification environment** for an AXI4-Lite slave register module.  
It demonstrates the **full UVM testbench structure** including sequence, driver, monitor, scoreboard, and environment,  
and verifies basic read/write transactions against a DUT (Design Under Test) that implements a simple register file.

This project is suitable for:
- Learning UVM fundamentals with a practical AXI-Lite example
- Serving as a base for industrial AXI-Lite verification
- Demonstrating verification skills in job applications

---
---

## Run Simulation (EDA Playground)

This project can be run directly on **EDA Playground** with the following settings:

**Languages & Libraries**
- **Testbench + Design:** `SystemVerilog/Verilog`
- **UVM / OVM:** `UVM 1.2`
- **Other Libraries:** `None`
- **Enable TL-Verilog:** unchecked
- **Enable Easier UVM:** unchecked
- **Enable VUnit:** unchecked

**Tools & Simulators**
- **Simulator:** `Synopsys VCS 2023.03`

**Compile Options**

## Features
- **AXI4-Lite protocol** for read/write transactions
- **UVM-based layered architecture**:  
  - Transaction (`axi_seq_item`)  
  - Sequence (`axi_smoke_seq`)  
  - Driver (`axi_driver`)  
  - Monitor (`axi_monitor`)  
  - Scoreboard (`axi_scoreboard`)  
  - Agent & Environment (`axi_agent`, `axi_env`)
- **Configurable virtual interface** injection via `uvm_config_db`
- **Self-checking** via scoreboard with shadow memory model
- Simulation waveform dump for EPWave or GTKWave

---

.
├── design.sv # AXI-Lite slave register DUT
├── axi_if.sv # AXI-Lite interface
├── my_uvm_pkg.svh # All UVM components (sequence, driver, monitor, etc.)
├── tb_top.sv # Testbench top module
└── README.md # Project documentation
## File Structure


---

## How It Works
1. **Sequence** generates read/write transactions to specific addresses.
2. **Driver** converts transactions into AXI-Lite valid/ready handshake signals.
3. **Monitor** captures bus activity and sends it to the scoreboard.
4. **Scoreboard** compares DUT output with expected shadow memory values.
5. **Simulation waveform** is dumped for debugging.

---

## Example Waveform
Below is a sample read/write sequence showing address/data handshakes:

![AXI-Lite Waveform Example](waveform.png)

---

## Run Simulation
This project was tested with **EDA Playground** and **Verilator**.

**EDA Playground:**
1. Copy files into EDA Playground (SystemVerilog + UVM 1.2)
2. Select `Run` and open EPWave for waveform view

**Verilator (local run):**
```bash
verilator --cc --exe --sv --trace tb_top.sv design.sv
make -C obj_dir -f Vtb_top.mk
./obj_dir/Vtb_top


<img width="1826" height="687" alt="image" src="https://github.com/user-attachments/assets/4705d5bd-21cd-4a57-ad40-d38eecba2ce0" />
