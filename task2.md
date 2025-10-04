<div align="center">

# 🌈✨ Task 2 – Pre-Synthesis Simulation of VSDBabySoC

</div>
<p align="center"> 
  <img src="https://img.shields.io/badge/Language-Verilog-blue?style=for-the-badge&logo=verilog" /> 
  <img src="https://img.shields.io/badge/Simulator-Icarus%20Verilog-green?style=for-the-badge&logo=github" /> 
  <img src="https://img.shields.io/badge/Waveform-GTKWave-purple?style=for-the-badge&logo=gnuplot" /> 
  <img src="https://img.shields.io/badge/OS-Linux%20%7C%20macOS-orange?style=for-the-badge&logo=linux" /> 
  <img src="https://img.shields.io/badge/Project-VSDBabySoC-red?style=for-the-badge&logo=riscv" /> 
</p>

---

## 👋 Welcome to Task 2!

In this stage of our **SoC Design Journey 🚀**, we perform a **Pre-Synthesis Simulation** of the **VSDBabySoC** using **Icarus Verilog 🧠** and **GTKWave 📊**.

This task validates **functional behavior before synthesis 🧩**, ensuring our **RISC-V–based SoC** behaves exactly as intended.

---

## 🏗️ Step 1: Environment Setup

### 📂 Navigate to the Project Directory

<div style="background-color:#FFF0F5; border-radius:12px; padding:10px; margin:8px 0;">
<pre>cd ~/Desktop/VLSI/VSDBabySoC</pre>
</div>

### 🌐 Clone the Repository

<div style="background-color:#F0FFF0; border-radius:12px; padding:10px; margin:8px 0;">
<pre>git clone https://github.com/manili/VSDBabySoC.git</pre>
</div>

🔗 **Image Reference:** [Command 1 Screenshot](https://github.com/Gowtham007007/Week-2_RISC-V_Tapeout/blob/main/Images/command1.png)

---

## 🧩 Step 2: Python Virtual Environment Setup

### 🔧 Install Dependencies

<div style="background-color:#FFF8DC; border-radius:12px; padding:10px; margin:8px 0;">
<pre>sudo apt update
sudo apt install python3-venv python3-pip</pre>
</div>

### 🪄 Create & Activate Virtual Environment

<div style="background-color:#F0FFFF; border-radius:12px; padding:10px; margin:8px 0;">
<pre>cd ~/VLSI/VSDBabySoC/
python3 -m venv sp_env
source sp_env/bin/activate</pre>
</div>

### ⚡ Install SandPiper-SaaS

<div style="background-color:#FFE4E1; border-radius:12px; padding:10px; margin:8px 0;">
<pre>pip install pyyaml click sandpiper-saas</pre>
</div>

### 🧠 Convert TL-Verilog → Verilog

<div style="background-color:#F5F5DC; border-radius:12px; padding:10px; margin:8px 0;">
<pre>sandpiper-saas -i ./src/module/*.tlv -o rvmyth.v --bestsv --noline -p verilog --outdir ./src/module/</pre>
</div>

🔗 **Image Reference:** [Command 2 Screenshot](https://github.com/Gowtham007007/Week-2_RISC-V_Tapeout/blob/main/Images/command2.png)

💡 **Tip:** Make sure your virtual environment is **activated** before running SandPiper commands. ✅

---

## ⚙️ Step 3: Pre-Synthesis Simulation Process

### 🗂️ Go to Module Directory

<div style="background-color:#FFFACD; border-radius:12px; padding:10px; margin:8px 0;">
<pre>cd VLSI/VSDBabySoC/src/module</pre>
</div>

### 🏗️ Run Icarus Verilog Simulation

<div style="background-color:#E6E6FA; border-radius:12px; padding:10px; margin:8px 0;">
<pre>iverilog \
  -o /home/username/Desktop/VLSI/VSDBabySoC/output/pre_synth_sim/pre_synth_sim.out \
  -DPRE_SYNTH_SIM \
  -I /home/username/Desktop/VLSI/VSDBabySoC/src/include \
  -I /home/username/Desktop/VLSI/VSDBabySoC/src/module \
  /home/username/Desktop/VLSI/VSDBabySoC/src/module/testbench.v</pre>
</div>

### 📦 Create Output Directory

<div style="background-color:#FFF0F5; border-radius:12px; padding:10px; margin:8px 0;">
<pre>mkdir -p /home/username/Desktop/VLSI/VSDBabySoC/output/pre_synth_sim</pre>
</div>

### ✅ Verify Build Output

<div style="background-color:#F0FFF0; border-radius:12px; padding:10px; margin:8px 0;">
<pre>ls -l /home/username/Desktop/VLSI/VSDBabySoC/output/pre_synth_sim/pre_synth_sim.out</pre>
</div>

### ▶️ Execute Simulation

<div style="background-color:#FFF8DC; border-radius:12px; padding:10px; margin:8px 0;">
<pre>vvp /home/username/Desktop/VLSI/VSDBabySoC/output/pre_synth_sim/pre_synth_sim.out</pre>
</div>

### 🌈 View in GTKWave

<div style="background-color:#F0FFFF; border-radius:12px; padding:10px; margin:8px 0;">
<pre>gtkwave pre_synth_sim.vcd</pre>
</div>

🔗 **Image Reference:** [Waveform Screenshot](https://github.com/Gowtham007007/Week-2_RISC-V_Tapeout/blob/main/Images/vsdwave.png)

---

## 🌟 Waveform Analysis

| Signal | Status | Meaning |
| --- | --- | --- |
| 🕒 REF | Stable | Reference clock |
| ⚙️ OUT | Toggling | Shows system logic activity |
| 🔄 reset | Low | System active (not in reset) |
| 🚫 ENb_VCO | High | VCO block disabled |
| ❌ ENb_CP | Undefined | Charge pump inactive |
| ⚡ VREFH/VREFL | 3.3 V / 0 V | Reference levels OK |

---

## 🎛️ DAC Module Observation

✨ Inside `vsdbabysoc_tb` testbench:

- 🔢 `D[9:0]` and `Dext[10:0]` → Digital inputs changing actively
- 🟢 `EN = 1` → DAC enabled
- 🌊 `OUT` → Analog values (e.g., `0.396 → 0.343`)
- ⚡ `VREFH = 1`, `VREFL = 0` → Proper reference

✅ Confirms correct **digital-to-analog conversion**.

🔗 **Image Reference:** [DAC Waveform](https://github.com/Gowtham007007/Week-2_RISC-V_Tapeout/blob/main/Images/dac_gtkwave.png)

---

## 🧠 Analog Output Visualization in GTKWave

Right click → `Out (signal)`

Select → `Data Format → Analog → Step`

🔗 **Image Reference:** [Analog Waveform](https://github.com/Gowtham007007/Week-2_RISC-V_Tapeout/blob/main/Images/analogwave.png)

💖 DAC output appears as a **smooth real-valued waveform**, showing accurate D/A conversion 🌀

---

## 📈 Waveform Highlights

✨ Key Observations:

| Signal | Status | Meaning |
| --- | --- | --- |
| ENb_CP | Toggling | Active control logic |
| ENb_VCO | Toggling | VCO enable control |
| REF | Stable | Reference clock |
| OUT | Periodic | System output activity |
| reset | Low | Normal operation |
| VREFH/VREFL | 3.3 V / 0 V | Reference bias correct |

✅ Simulation ends cleanly with `$finish`. No errors!

---

## 🏁 🎯 Conclusion

The **Pre-Synthesis Simulation** of **VSDBabySoC 💡** was **completed successfully**.

- Control, clock, and DAC signals behaved correctly
- DAC produced valid analog outputs 🌊
- Design is **functional, stable, and ready for synthesis ✅**

💖 A perfect balance of **Digital & Analog harmony** — verified and ready for the next step! ✨

---

## 🧰 Tools Used

| Tool | Purpose |
| --- | --- |
| 🧠 Icarus Verilog | RTL Simulation |
| 📊 GTKWave | Waveform Viewer |
| ⚙️ SandPiper-SaaS | TL-Verilog Conversion |
| 🐍 Python 3 + venv | Environment Management |
| 💻 Ubuntu/Linux | Execution Platform |
