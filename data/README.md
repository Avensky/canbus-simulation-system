# 📁 Data Directory  

### Synthetic CAN Bus & Vehicle Telemetry Samples

This directory contains **synthetic CAN bus–style telemetry files** used for demonstration, visualization, and reproducibility in the *CAN Bus Real-Time Vehicle Simulation System*. These files are **entirely simulated** and do **not** contain proprietary or hardware-derived CAN data.

They allow the public version of the project to:

- replay realistic throttle and RPM patterns  
- visualize time-series behavior  
- drive the demo dashboard  
- support example machine learning workflows  
- document the data-processing pipeline  

---

# 📦 Included Files

## 1. `scion-frs-throttle_raw.csv`

A synthetic dataset representing low-level throttle-related signals.  
Useful for examining:

- raw timing behavior  
- throttle waveform patterns  
- preprocessing steps  
- noise simulation  

This dataset imitates the structure of raw CAN-adjacent telemetry with:

- timestamps  
- throttle percentages  
- engine behavior signals  
- simulated noise  

---

## 2. `scion-frs-throttle_logs.csv`

A higher-level processed version of the throttle dataset.  
Contains cleaner, more structured signals suitable for:

- dashboard visualization  
- ML preprocessing examples  
- demonstration of pipeline steps  
- conversion to JSON for web demos  

---

# 🔍 Data Notes

These datasets represent:

- realistic **time-series samples**  
- **non-proprietary**, simulated telemetry  
- **deterministic** patterns useful for playback  
- a safe demonstration of the data pipeline described in `system-overview.md`

They can be used to:

- prototype signal parsers  
- animate 3D vehicle components  
- simulate CAN dashboards  
- benchmark ML experiments  
- demonstrate CSV → JSON → WebSocket workflows  

---

# 🚫 Important Notice

These files:

- **are not recorded from a real vehicle**  
- do not contain authentic CAN IDs  
- are safe for public release and research use  
- follow structural characteristics similar to automotive time-series data  

Their purpose is educational and illustrative.

---

# 🔧 Suggested Uses in Repos & Coursework

You can plug these CSVs into:

- a React/Three.js frontend visualization  
- Python notebooks for signal analysis  
- ML pipelines  
- simulation playback scripts  
- documentation examples  

They help demonstrate how a real CAN system *would* behave, without exposing restricted content.

---

# 📁 Future Additions

Planned data expansions include:

- simulated RPM-based datasets  
- multi-signal synthetic CAN frames
- noise-injected variants for ML testing  
- simulation log archives  

---

# ✔ End of Document
