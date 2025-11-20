# 🛠️ CAN Bus Real-Time Vehicle Simulation System  

### *Research Case Study • Simulation Engineering • Cognitive Systems • Embedded Computing*

This repository documents the design, architecture, and frontend demonstration of a **real-time CAN bus visualization and vehicle simulation system** I developed during my research internship with the **Naval Information Warfare Center (NIWC)**.

The original codebase used during the internship is **not included** (restricted).  
This public repository contains:

- A full **system architecture case study**
- **Data pipeline documentation**
- A **frontend demo** using simulated CAN data
- **Physics engine design notes**
- Engineering diagrams and high-level design
- Research context and explanation

This repo highlights my experience in **simulation engineering**, **automotive telemetry**, **real-time systems**, **cognitive science**, and **machine learning-oriented environments**.

---

## 🚗 Project Overview

Modern vehicles generate hundreds of real-time CAN bus signals (speed, RPM, diagnostics, throttle, steering angle). Research teams need:

- A **safe, controlled simulation environment**
- Real-time **interactive visualization tools**
- A system capable of merging **physical simulation** with **streamed sensor data**
- A platform for **autonomy research**, **HMI**, and **cybersecurity testing**

### The original prototype had

- Static, non-interactive gauge images  
- No backend capable of streaming real data  
- No simulation engine  
- No extensible architecture  

### I rebuilt the system completely

✔ Real-time physics-based vehicle simulation  
✔ Raspberry Pi CAN interface integration  
✔ WebSockets for high-speed data streaming  
✔ Interactive visualization in 2D and 3D  
✔ Unified architecture for simulation + real signals  

This repository contains the **safe public version** of that work.

---

## 🎥 Demo

See the `demo/` folder for:

- `vehicle-sim.mp4` (driving demo recording)  
- `canbus-demo.mp4` (canbus session demo recording)  
- Showcases 2D speed, RPM, fuel & temp gauges
- 3D physics / vehicle suspension / recorded session playback
- Collisions (Not in demo, but fully integrated into the physics engine)  
- Screenshots

All data in the demo is **artificial**.

## 📊 Data Samples (Synthetic Telemetry)

 `/data` directory contains **synthetic CAN-style telemetry datasets** used to demonstrate the system’s playback, visualization, and preprocessing pipelines.  
These files simulate realistic throttle, RPM, and timing behavior while containing **no proprietary or hardware-derived CAN frames**.

---

## 📁 Included Files

Located in /data/

### 🔸 `scion-frs-throttle_raw.csv`

- Raw synthetic throttle waveform  
- High-frequency time-series data  
- Useful for testing parsers and preprocessing steps  

### 🔹 `scion-frs-throttle_logs.csv`

- Cleaned & structured throttle signals  
- Ideal for dashboards and ML examples  
- Demonstrates typical CAN-adjacent log formatting  

📌 For a full description of the datasets, visit:  
➡️ **[`/data/README.md`](data/README.md)**

---

## 🚀 Suggested Uses

- Driving frontend gauges and animations
- Training small time-series ML models
- Demonstrating CSV → JSON pipelines
- Teaching CAN-style preprocessing workflows
- Creating reproducible simulation playback demos

---

## 🧰 System Architecture

             [ CAN Hardware ]

                    ↓
      
      [ Raspberry Pi + CAN Interface ]

                    ↓
      
          [ Python CAN Listener ]

                    ↓
      
         [ WebSocket Data Server ]

                    ↓
      
    [ React / Three.js Visualization ]

### Architecture Layers

|           Layer         |                      Description                          |
|-------------------------|-----------------------------------------------------------|
|   **Hardware Layer**    | Raspberry Pi + CAN transceiver + OBD-II connection        |
|     **Data Layer**      | Python listener for CAN signals, message normalization    |
| **Communication Layer** | WebSocket server for broadcasting high-frequency frames   |
|  **Simulation Layer**   | Vehicle physics engine: forces, suspension, RPM, movement |
| **Visualization Layer** | Gauges, 3D scene, charts, real-time signal tracking       |

See `/docs/system-overview.md` for complete details.

---

## 🔍 Research Motivation

This project supports research in:

- Cognitive systems & computational modeling
- Embedded real-time systems  
- Vehicle cybersecurity  
- Human–machine interaction (HMI)  
- Machine learning using sensory/telemetry streams  
- Simulation environments for autonomous systems  

Vehicles are excellent cognitive systems:

- structured sensory input  
- predictable physical behavior  
- interpretable high-frequency data  
- clear cause–effect relationships  

This makes the domain ideal for ML, AI modeling, and signal decoding research.

---

## 🧪 Frontend Demo (Synthetic CAN Data)

The demo frontend includes:

<!-- - A simulated CAN feed (`fake-can-frames.json`)   -->
- 3D Simulation
- Live gauge updates  
- Line charts  
- Modular signal parser  

## 📚 Documentation

Located in /docs/

- system-overview.md – Full system explanation
- research-background.md – CAN bus architecture and motivation
- physics-engine-notes.md – Vehicle dynamics modeling

## 📊 Technologies

|      Category       |               Tools                |
|---------------------|------------------------------------|
|  **Embedded**       |  Raspberry Pi, CANable, socketcan  |
|  **Backend**        |  Python, python-can, asyncio       |
|  **Communication**  |  WebSockets, JSON                  |
|  **Simulation**     |  Cannon.js or custom JS physics    |
|  **Frontend**       |  React, Three.js                   |
|  **Documentation**  |  Markdown, Draw.io                 |

## ⚠️ Disclaimer

- This repo contains no proprietary or NIWC code.
- All CAN signals used in demos are fully synthetic.
- Architecture is generalized for portfolio and educational use.

## 🧑‍🔬 About Me

I am a Cognitive Science (Machine Learning) and Computer Science–focused research student interested in:

- embedded AI systems
- simulation engineering
- computational modeling
- robotics and autonomy
- automotive systems
- machine learning pipelines

This project represents the intersection of software engineering, cognitive science, and real-time embedded systems.

## ⭐ If you find this project valuable, please consider starring the repo

---

# End of Document
