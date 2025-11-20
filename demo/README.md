<p align="center">
  <strong>
    <a href="../README.md">🏠 Home</a> •
    <a href="../docs/">📘 Documentation</a> •
    <a href="../demo/">🎥 Demo Videos</a> •
    <a href="../data/">📊 Data Samples</a>
  </strong>
</p>

# 📁 Data Directory  

### *Synthetic CAN Bus & Telemetry Samples for Research and Visualization*

This directory contains **fully synthetic, non-proprietary CAN-style telemetry files** used throughout the CAN Bus Real-Time Vehicle Simulation research environment.  
The datasets here serve as safe, reproducible examples for:

- real-time visualization  
- machine learning prototyping  
- signal processing demonstrations  
- simulation playback  
- byte-level analysis  
- cognitive modeling experiments  

They mirror the *structure* of real automotive time-series data while masking all real-world identifiers or proprietary mappings.

---

# 📦 Included Datasets

## 1. `scion-frs-throttle_raw.csv`

A low-level synthetic throttle waveform dataset representing raw time-series telemetry.

### 📌 Useful For

- studying noisy throttle behavior  
- observing raw temporal structure  
- signal preprocessing and filtering  
- early-stage ML feature extraction  
- realistic noise model experimentation  

### 🚗 Contents

- timestamps  
- throttle percentage  
- RPM-adjacent synthetic behaviors  
- small random noise to emulate sensors  

This file approximates real CAN-adjacent throttle logs while remaining fully synthetic.

---

## 2. `scion-frs-throttle_logs.csv`

A cleaner, higher-level version of the raw throttle dataset.  
Ideal for pipelines that expect structured, ML-ready data.

### 📌 Useful For

- dashboard visualizations  
- calm, well-structured ML preprocessing  
- JSON conversion for WebSocket demos  
- time-aligned multi-signal research examples  

### 🚗 Contents

- processed throttle curve  
- simplified RPM dynamics  
- normalized timing  
- high-quality synthetic patterns  

This dataset demonstrates the difference between **raw** vs **processed** telemetry in research workflows.

---

# 🔍 Data Notes

These datasets capture:

- **realistic time-series structure**  
- **synthetic signal noise**  
- **deterministic playback behavior**  
- **patterns similar to vehicle subsystem dynamics**  

But they **do not** contain:

- real CAN IDs  
- manufacturer signal mappings  
- sensitive hardware information  
- identifiable driving behavior  

They are intentionally designed for **safe academic use**.

---

# 🔧 Recommended Research Uses

These synthetic time-series samples can be plugged directly into:

### 🧪 Machine Learning  

- LSTM/GRU sequence modeling  
- anomaly detection  
- forecasting  
- signal classification experiments  

### 📈 Signal Processing  

- smoothing and filtering  
- derivatives (acceleration/jerk)  
- low-pass vs high-pass filtering  
- resampling experiments  

### 🎮 Simulation  

- driving physics visualization  
- dashboard reconstruction  
- real-time playback via WebSockets  

### 👨‍🏫 Coursework  

Perfect for assignments in:

- cognitive science  
- machine learning  
- data visualization  
- real-time systems  

---

# 📁 Future Additions

Planned dataset expansions include:

- simulated multi-signal CAN frames  
- RPM-based telemetry  
- combined throttle–RPM–steering patterns  
- noise-injected variants for ML robustness testing  
- large-scale multi-session synthetic logs  

These will support growing research directions in **autonomy**, **embodied modeling**, and **predictive systems**.

---

# End of Document
