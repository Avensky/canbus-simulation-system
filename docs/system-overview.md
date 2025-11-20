<p align="center">
  <strong>
    <a href="../README.md">🏠 Home</a> •
    <a href="../docs/">📘 Documentation</a> •
    <a href="../demo/">🎥 Demo Videos</a> •
    <a href="../data/">📊 Data Samples</a>
  </strong>
</p>

# 📘 System Overview  

### *CAN Bus Real-Time Vehicle Simulation System*

This document provides an academic, research-focused overview of the **CAN Bus Real-Time Vehicle Simulation System**—an environment designed for studying **embodied cognition**, **real-time data pipelines**, **vehicle physics**, and **machine learning** using synthetic CAN-style telemetry.  

All content here is **safe**, **synthetic**, and represents the public version of work developed during my NIWC research internship.

---

# 🧩 1. System Goals

The system is engineered to serve as a **research testbed** where interactive simulation, signal processing, and ML workflows coexist.  
Its goals are to provide:

1. **A realistic, physics-based vehicle simulation environment**  
2. **Interactive visualization** of high-frequency CAN-like signals  
3. **Reliable real-time communication** between backend and frontend  
4. **A modular architecture suitable for scientific experimentation**  
5. **Compatibility with embedded CAN hardware or synthetic data**  
6. **A flexible platform** for studying cognitive systems, autonomy, and robotics

The architecture emphasizes **interpretability**, **reproducibility**, and **modularity**, enabling research across cognitive science, machine learning, and embedded systems.

---

# 🛠️ 2. High-Level Architecture

```
[ CAN Hardware or Synthetic Playback ]
                  ↓
        [ Python Normalization Layer ]
                  ↓
          [ WebSocket Data Server ]
                  ↓
        [ Real-Time Visualization ]
                  ↓
       [ 3D Physics-Based Simulation ]
```

### Components

| Component | Purpose |
|----------|---------|
| **CAN Hardware / Synthetic Data** | Provides high-frequency signals representing throttle, RPM, steering, etc. |
| **Raspberry Pi or Host Machine** | Interfaces with CAN or supplies synthetic data |
| **Python Listener** | Normalizes raw frames into structured messages |
| **WebSocket Server** | Broadcasts signals at 30–120 Hz |
| **3D Visualization Client** | Interactive visualization via React + Three.js |
| **Physics Engine** | Models vehicle dynamics and motion |

This layered design supports both **research reproducibility** and **interactive exploration**.

---

# 📡 3. Data Pipeline

### **Step 1 — Data Acquisition**

CAN frames or synthetic playback are received at **10–100+ Hz**.  
Example source technologies:

- `socketcan`  
- `python-can`  
- synthetic CSV-based telemetry  

### **Step 2 — Normalization**

Frames are converted into structured packets:

```json
{
  "speed_kph": 36,
  "rpm": 2120,
  "steering_angle": 1.2,
  "timestamp": 3.883
}
```

### **Step 3 — Streaming**

A lightweight WebSocket server broadcasts data to the frontend with minimal latency.

### **Step 4 — Visualization**

The frontend renders:

- dashboard gauges  
- time-series plots  
- byte-level frame heatmaps  
- 3D vehicle state updates  

This architecture supports **real-time cognitive system modeling**, where perception, state estimation, and action are all visible.

---

# 🔧 4. Simulation Engine Overview

The simulation engine models realistic vehicle physics to enable:

- embodied agent behavior  
- sensor-stream consistency  
- real-time feedback  
- smooth visualization  

### Key Physical Subsystems

#### **Suspension**

A spring-damper system provides vertical motion and stability.

#### **Wheel Forces**

Includes:

- longitudinal traction  
- lateral slip  
- realistic grip curves  

#### **Engine Model**

Torque → RPM → wheel speed computations based on:

- gear ratios  
- throttle input  
- simulated driveline behavior  

#### **Vehicle Body**

Mass, inertia, drag, and lift determine overall motion.  
Orientation is handled using **quaternions**, avoiding gimbal lock.

This physics layer allows the system to eventually support **drones**, **UGVs**, **tracked vehicles**, and more.

---

# 🎮 5. Real-Time Visualization

The visualization frontend is built on:

- **React**  
- **Three.js / React Three Fiber**  
- **WebSockets**  
- optional **Recharts / D3**  

### Visual elements include

- Speed & RPM gauges  
- Steering angle visualization  
- Time-series graphs  
- Live hex heatmaps for bytes  
- 3D vehicle simulation  
- Smooth 3rd-person ↔ 1st-person camera transitions  

This design intentionally blends **research tooling** with the **expressiveness of games**, creating a powerful medium for understanding dynamic systems.

---

# 🧪 6. Synthetic Demo Mode

To keep the public version safe and open:

- All CAN signals are **synthetic**
- Ranges and timing mimic real CAN behavior
- No proprietary IDs or mappings are used  
- Noise models simulate realistic imperfections  

This enables:

- reproducible demos  
- ML experiments  
- safe open-source release  

---

# 🧠 7. Cognitive Science & ML Applications

This system supports research in:

### **Embodied Cognition**

Vehicles function as interpretable, physical agents:

- sensors → state → action → feedback

### **Time-Series Machine Learning**

Frames can train models for:

- anomaly detection  
- predictive modeling  
- sequence modeling  
- sensor fusion  

### **Autonomy & Robotics**

The simulation environment can support:

- imitation learning  
- reinforcement learning  
- behavioral cloning  
- autonomous drone and UGV extensions  

### **HMI Research**

3D visualization aids human-machine interaction studies.

---

# 📄 8. Public Version Limitations

This repository does **not** include:

- restricted NIWC code  
- real CAN bus captures  
- proprietary decoding logic  
- sensitive system mappings  

All materials here are educational and research-oriented.

---

# 📌 9. Future Work

Upcoming directions include:

- improved vehicle physics fidelity  
- synthetic multi-vehicle environments  
- anomaly-injection datasets  
- drone & autonomous robot simulation  
- ML-ready dataset generators  
- advanced byte-level analytics tools  

---

# End of Document
