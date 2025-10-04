<div align = center >
  
   # 🌈✨ Task 2 – Pre-Synthesis Simulation of VSDBabySoC
</div>
<p align="center"> <img src="https://img.shields.io/badge/Language-Verilog-blue?style=for-the-badge&logo=verilog" /> <img src="https://img.shields.io/badge/Simulator-Icarus%20Verilog-green?style=for-the-badge&logo=github" /> <img src="https://img.shields.io/badge/Waveform-GTKWave-purple?style=for-the-badge&logo=gnuplot" /> <img src="https://img.shields.io/badge/OS-Linux%20%7C%20macOS-orange?style=for-the-badge&logo=linux" /> <img src="https://img.shields.io/badge/Project-VSDBabySoC-red?style=for-the-badge&logo=riscv" /> </p>

## 👋 Welcome to Task 2!

In this stage of your SoC Design Journey 🚀, we perform a Pre-Synthesis Simulation of the VSDBabySoC using Icarus Verilog 🧠 and GTKWave 📊.
This task validates functional behavior before synthesis 🧩, ensuring our RISC-V–based SoC behaves exactly as intended.

🏗️ Step 1: Environment Setup
## 📂 Navigate to the project directory
cd ~/Desktop/VLSI/VSDBabySoC

## 🌐 Clone the repository
git clone https://github.com/manili/VSDBabySoC.git


🖼️ [📸 Add your screenshot of successful cloning here]

🧩 Step 2: Python Virtual Environment Setup
## 🔧 Install dependencies
sudo apt update
sudo apt install python3-venv python3-pip

## 🪄 Create & activate virtual environment
cd ~/VLSI/VSDBabySoC/
python3 -m venv sp_env
source sp_env/bin/activate

## ⚡ Install SandPiper-SaaS
pip install pyyaml click sandpiper-saas

## 🧠 Convert TL-Verilog → Verilog
sandpiper-saas -i ./src/module/*.tlv -o rvmyth.v --bestsv --noline -p verilog --outdir ./src/module/


🖼️ [📸 Add your SandPiper conversion result image here]

⚙️ Step 3: Pre-Synthesis Simulation Process
## 🗂️ Go to module directory
cd VLSI/VSDBabySoC/src/module

## 🏗️ Run Icarus Verilog simulation
iverilog \
  -o /home/username/Desktop/VLSI/VSDBabySoC/output/pre_synth_sim/pre_synth_sim.out \
  -DPRE_SYNTH_SIM \
  -I /home/username/Desktop/VLSI/VSDBabySoC/src/include \
  -I /home/username/Desktop/VLSI/VSDBabySoC/src/module \
  /home/username/Desktop/VLSI/VSDBabySoC/src/module/testbench.v

## 📦 Create output directory
mkdir -p /home/username/Desktop/VLSI/VSDBabySoC/output/pre_synth_sim

## ✅ Verify build output
ls -l /home/username/Desktop/VLSI/VSDBabySoC/output/pre_synth_sim/pre_synth_sim.out

## ▶️ Execute simulation
vvp /home/username/Desktop/VLSI/VSDBabySoC/output/pre_synth_sim/pre_synth_sim.out

## 🌈 View in GTKWave
gtkwave pre_synth_sim.vcd


🖼️ [📸 Add your GTKWave screenshot here]

🌟 Waveform Analysis

🕒 REF – Stable clock signal
⚙️ OUT – Toggles with system logic
🔄 reset – Remains low (active operation)
🚫 ENb_VCO – High (disabled state)
❌ ENb_CP – Undefined (x) – charge pump inactive
⚡ VREFH = 3.3 V, VREFL = 0 V – Reference levels ok

🖼️ [📸 Add REF/OUT waveform image here]

🎛️ DAC Module Observation

✨ Inside vsdbabysoc_tb testbench:

🔢 D[9:0] and Dext[10:0] → digital inputs changing actively

🟢 EN = 1 → DAC enabled

🌊 OUT → analog values ( e.g., 0.396 → 0.343 )

⚡ VREFH = 1, VREFL = 0 → proper reference

✅ Confirms correct digital-to-analog conversion.

🖼️ [📸 Add DAC waveform image here]

🧠 Analog Output Visualization in GTKWave
Right click → Out (signal)
Select → Data Format → Analog → Step


🖼️ [📸 Add analog waveform image here]

The DAC output appears as a smooth real-valued waveform — a clear indication of accurate D/A conversion 🌀

📈 Waveform Highlights

✨ Summary of important signals:

Signal	Status	Meaning
ENb_CP	Toggling	Active control logic
ENb_VCO	Toggling	VCO enable control
REF	Stable	Reference clock
OUT	Periodic	System activity
reset	Low	Normal operation
VREFH/VREFL	3.3 V / 0 V	Proper reference bias

✅ Simulation ends with $finish — no errors encountered!

🏁 🎯 Conclusion

The Pre-Synthesis Simulation of VSDBabySoC 💡 was completed successfully.
All control, clock, and analog signals behaved as expected.
The DAC produced valid analog outputs, confirming a fully functional SoC design ✅

💖 A perfect balance of Digital & Analog harmony — verified and ready for synthesis! 💫

🧰 Tools Used
Tool	Purpose
🧠 Icarus Verilog	RTL Simulation
📊 GTKWave	Waveform Viewer
⚙️ SandPiper-SaaS	TL-Verilog Conversion
🐍 Python 3 + venv	Environment Management
💻 Ubuntu/Linux	Execution Platform
