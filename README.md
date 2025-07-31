# 🔍 UVM-Based Verification of UART Transmitter and Receiver


---

This project demonstrates the **UVM-based verification** of a **UART (Universal Asynchronous Receiver Transmitter)** module using **SystemVerilog** and **QuestaSim**. It includes a full-featured UVM testbench that validates UART transmitter and receiver logic by simulating UART frames, verifying protocol compliance, and tracking data correctness.

---

## 🎯 Objectives

- Verify UART TX and RX behavior for correctness and completeness.
- Develop reusable UVM components following modular design.
- Achieve protocol-level checks: start bit, data bits, stop bit, and parity (if any).
- Use **scoreboarding** and **functional simulation** to ensure data integrity.

---

## 🧱 Project Structure

```
UVM_Based_UART_Protocol_Verification/
│
├── rtl/                  # UART RTL Design
│   ├── uart_top.v
│   ├── uart_receiver.v
│   ├── uart_transmitter.v
│   ├── uart_tfifo.v
│   ├── uart_rfifo.v
│   ├── uart_regs.v
│   ├── uart_sync_flops.v
│   └── uart_defines.v
│
├── agent/                # UVM Agent Components
│   ├── driver.sv
│   ├── monitor.sv
│   ├── sequencer.sv
│   ├── sequence.sv
│   ├── xtn.sv
│   ├── agent.sv
│   └── agent_config.sv
│
├── env/                  # UVM Environment & Scoreboard
│   ├── env.sv
│   ├── scoreboard.sv
│   ├── env_config.sv
│   ├── virtual_sequence.sv
│   └── virtual_sequencer.sv
│
├── test/                 # UVM Test Layer
│   └── test.sv
│
├── sim/                  # Simulation Files
│   ├── Makefile
│   └── sim.py            # Optional simulation automation
│
├── top/                  # Docs & Metadata
│   ├── UART_16550.pdf
│   ├── arch.png
│   ├── LICENSE
│   └── README.md
```

---

## 🔧 Tools & Technologies

| Tool             | Purpose                            |
|------------------|-------------------------------------|
| **SystemVerilog** | Testbench & RTL design              |
| **UVM**           | Universal Verification Methodology |
| **QuestaSim**     | Simulation & waveform debugging     |
| **Makefile**      | Build & compile automation         |

---

## 🚦 UVM Components Implemented

- ✅ **Transaction (`xtn.sv`)** – UART stimulus object  
- ✅ **Sequence** – Drives randomized or directed UART operations  
- ✅ **Sequencer** – Manages item flow to the driver  
- ✅ **Driver** – Applies data to UART TX interface  
- ✅ **Monitor** – Samples and forwards RX data  
- ✅ **Scoreboard** – Checks received vs expected data  
- ✅ **Agent** – Wraps driver, monitor, sequencer  
- ✅ **Environment** – Integrates agent and scoreboard  
- ✅ **Test** – Runs sequences and applies configs  

---

## ▶️ How to Run the Simulation (QuestaSim)

> **Step 1: Setup Project in QuestaSim**
```sh
vlib work
vlog +acc rtl/*.v agent/*.sv env/*.sv test/*.sv
vsim -c top_tb -do "run -all; quit"
```

> **Step 2 (Optional): Use Makefile**
```sh
cd sim/
make
```

> **Step 3: View Waveform**
- Open `dump.vcd` in **QuestaSim GUI** or **GTKWave**

---

## 📚 References

- [UART 16550 Specification (PDF)](top/UART_16550.pdf)
- UVM User Guide – [Accellera UVM 1.2](https://accellera.org/downloads/standards/uvm)

---

## 📜 License

This project is licensed under the **MIT License** – see [LICENSE](./LICENSE) for details.

---

## 👤 Author

**Rahul R**  
[GitHub: @RahulkannaR](https://github.com/RahulkannaR)

> Feel free to fork, use, and extend this project for your learning or professional work!
