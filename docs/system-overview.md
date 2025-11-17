# 📘 System Overview  
### CAN Bus Real-Time Vehicle Simulation System

This document provides a full technical and conceptual overview of the simulation + visualization system developed during my research internship at the Naval Information Warfare Center (NIWC).  
The system merges:

- real-time CAN bus telemetry  
- embedded hardware (Raspberry Pi)  
- a physics-based vehicle simulation engine  
- real-time WebSocket streaming  
- a 3D visualization client  

All content here is safe and generalized.

# 🧩 1. System Goals

The system was designed to provide:

1. **A realistic vehicle simulation environment**  
2. **Interactive visualization of CAN signals**  
3. **Reliable real-time communication across devices**  
4. **A modular architecture suitable for research**  
5. **Compatibility with embedded CAN hardware**  
6. **A flexible platform for ML and cognitive science experiments**

This enabled researchers to:

- test signal decoding logic  
- visualize vehicle dynamics  
- simulate failure events  
- support prototyping in autonomy/cybersecurity  

---

# 🛠️ 2. High-Level Architecture
[ CAN Hardware ] → [ Raspberry Pi ] → [ Python Listener ] 
→ [ WebSocket Server ] → [ Visualization Client ]


### Components

|        Component        |                               Purpose                                   |
|-------------------------|-------------------------------------------------------------------------|
|    **CAN Hardware**     | Collects real vehicle data through OBD-II or direct CAN tapping         |
|    **Raspberry Pi**     | Converts CAN frames to socketcan interface & streams to Python listener |
|   **Python Listener**   | Reads frames, decodes them, normalizes signal values                    |
|   **WebSocket Server**  | Broadcasts high-frequency frames to frontend clients                    |
|    **Visualization**    | Interactive gauges, charts, and optional 3D dynamics                    |

---

# 📡 3. Data Pipeline

### Step 1 — CAN Acquisition  
The Raspberry Pi listens on a CAN network using tools like:

- `socketcan`
- `python-can`

Frames are captured at **10–100 Hz**, depending on bus load.

### Step 2 — Normalization  
Each frame is parsed:

- ID  
- timestamp  
- data bytes  
- interpreted values (speed, rpm, throttle, etc.)

### Step 3 — Broadcasting  
Frames are sent over WebSockets using JSON packets:

```json
{
  "speed_kph": 32,
  "rpm": 2050,
  "steering_angle": -1.0,
  "timestamp": 1.024
}
```

### Step 4 — Visualization
The frontend updates:
- speed gauge
- rpm gauge
- time-series graphs
- 3D model animations
- All updates are real-time.

# 🔧 4. Simulation Engine Overview
The physics system uses concepts from raycast vehicle dynamics:

## ✔ Suspension simulation
Spring–damper model:
- stiffness
- damping
- rest length

## ✔ Wheel forces
- longitudinal friction
- lateral slip
- traction curve

## ✔ Engine model
- RPM → torque curve
- gear ratios
- clutch slip
- rev limiter

## ✔ Vehicle body
- inertia tensor
- mass
- center of mass
- drag and lift

## ✔ Orientation handling
Quaternion math for smooth rotation without gimbal lock.

# 🎮 5. Frontend Visualization
The frontend is built with:
- React → UI, components
- Three.js → 3D vehicle representation
- D3.js / Recharts → signal graphs
- WebSocket client → real-time updates
- Visualization elements:
- Speed & RPM gauges
- Line graphs for signals
- 3D wheel or chassis animation
- CAN frame inspector panel

# 🧪 6. Synthetic Demo Mode
The public demo uses:
fake CAN frames
smoothed speed + rpm curves
randomized sensor noise
This allows safe display without using restricted or proprietary data.

# 🧠 7. Cognitive Science & ML Applications
This system supports research in:
- Cognitive Systems
- Vehicles act as observable cognitive agents with:
- sensory input
- internal state
- feedback loops
- action outputs
- Machine Learning

Real-time frames can train:
- state estimation models
- anomaly detection
- behavior prediction systems
- signal classification algorithms
- Human–Machine Interaction
- 3D visuals support usability research.

# 📄 8. Limitations (Public Version)
This repo excludes:
- original NIWC code
- real CAN data
- security-sensitive details
- proprietary tooling

The simulation and diagrams are conceptual and educational.

# 📌 9. Future Work
- Expand 3D simulation accuracy
- Add traffic + environment simulation
- Create ML-ready datasets
- Build CAN anomaly detection models
- Add dashboard customization

---

# End of Document
