# 🌟 Week 2: System on Chip (SoC) Design – Theory & Practical Exploration

🎉 **Welcome to Week 2 of the SoC Design Journey!**

This week, we embark on an exciting deep dive into the **world of System on Chip (SoC) architecture** — where multiple components such as CPUs, memory, and peripherals are integrated into a single silicon chip 🧠⚙️

Through this week, we’ll combine **conceptual understanding** and **hands-on experimentation** using the open-source **VSDBabySoC** — a compact and educational **RISC-V based SoC** that demonstrates the true essence of modern chip design. 💻✨

---

## 📚 Task 1: SoC Design Fundamentals & Introduction to VSDBabySoC

🔍 **Objective:**

Gain a solid foundation in SoC architecture and learn how different hardware modules work together to form a complete chip.

### 🧠 **What You’ll Learn**

- 🧩 **System on Chip (SoC) Overview:**
    
    Understand how a SoC integrates processor cores, memory blocks, analog/digital peripherals, and communication interfaces on a single die.
    
- ⚙️ **RISC-V Architecture Basics:**
    
    Learn about the open-source RISC-V ISA and how it powers the CPU core in VSDBabySoC.
    
- 🕒 **PLL (Phase-Locked Loop):**
    
    Explore how PLL circuits stabilize and control clock signals to synchronize operations within the chip.
    
- 🎛️ **DAC (Digital-to-Analog Converter):**
    
    See how the DAC converts digital signals into analog outputs, enabling the SoC to interact with real-world systems.
    
- 🔄 **Interconnections & Hierarchical Design:**
    
    Understand how buses and interconnects link modules like CPU, memory, and peripherals.
    

📘 In short, this task builds your conceptual backbone for SoC design — how each block fits together like puzzle pieces to form a functional chip!

👉 [**🧾 Read Task 1 Summary & Explanation**](https://github.com/harishj123/RISC-V_Soc_Tape_out_week_2/blob/main/Week_2/task_1.md)

---

## ⚙️ Task 2: Practical Simulation of VSDBabySoC SoC Design

🧪 **Objective:**

Put your theoretical understanding into practice by simulating and visualizing the VSDBabySoC design!

### 🧰 **Hands-On Activities**

- 🏗️ **Project Structure Breakdown:**
    
    Explore the organization of Verilog files and understand how modules like the RVMYTH CPU, PLL, and DAC connect together.
    
- 💡 **Simulation Workflow:**
    
    Learn how to compile and simulate your SoC using **Icarus Verilog**, and analyze the design behavior in **GTKWave**.
    
- 🧮 **Pre-Synthesis vs Post-Synthesis:**
    
    Observe the differences between functional and gate-level simulations — understanding how synthesis affects timing and performance.
    
- 📈 **Waveform Analysis:**
    
    View and interpret output signals using GTKWave to confirm proper data flow and module functionality.
    

### 🧱 **Expected Outcomes**

By completing this task, you’ll:

✅ Understand the functional operation of the VSDBabySoC

✅ Perform RTL simulation and waveform verification

✅ Strengthen your Verilog debugging and visualization skills

👉 [**🔬 Explore Task 2 Simulation & Verification Guide**](https://github.com/harishj123/RISC-V_Soc_Tape_out_week_2/blob/main/Week_2/task_2.md)

---

## 🧰 Tools & Requirements

| 🛠️ Tool | 💡 Purpose |
| --- | --- |
| 🧩 **Icarus Verilog** | Compile & simulate Verilog design files |
| 📊 **GTKWave** | Visualize simulation waveforms (`.vcd` files) |
| 💻 **Recommended OS** | macOS 🍎 / Linux 🐧 (for Unix-like environment and tool compatibility) |

🪄 **Pro Tip:**

Make sure `iverilog` and `gtkwave` are properly installed and accessible from your terminal. You can verify using:

```bash
iverilog -v
gtkwave -v

```

---

## 🧠 Learning Outcomes

By the end of **Week 2**, you’ll be able to:

- 🌐 Understand **how an SoC integrates multiple components** into a single chip.
- 🧩 Recognize the **role of key modules** like CPU, PLL, and DAC in a complete system.
- 🛠️ Perform **Verilog-based simulation and waveform verification** using open-source EDA tools.
- 🧠 Gain **practical experience** in SoC-level design and testing workflows.

---

## 🎓 Why This Matters

System on Chip design represents the **heart of modern electronic innovation** — from smartphones 📱 to IoT devices 🌍 and autonomous systems 🚗💡.

Learning to design, simulate, and verify these systems helps you bridge the gap between **theory and real-world chip implementation**.

This week’s content gives you **hands-on exposure** to the **complete design cycle**, preparing you for advanced SoC development, VLSI projects, and future research. 🧬

---

## 🙌 Thank You!

✨ Keep exploring, keep building, and never stop learning!

Your journey toward mastering **VLSI and SoC design** has just begun.

Let’s continue creating the future of silicon — one design at a time. ⚡💻💫
