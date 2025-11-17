🛠️ CAN Bus Real-Time Vehicle Simulation System
Research Case Study • Simulation Engineering • Cognitive Systems • Embedded Computing

This repository documents the design, architecture, and frontend demonstration of a real-time CAN bus visualization and vehicle simulation system I developed during my research internship with the Naval Information Warfare Center (NIWC).

The original codebase used during research is not included (restricted), but this public case study captures:

the system architecture

data pipeline design

research approach

a frontend demo using synthetic CAN data

the physics simulation concepts I implemented

diagrams, documentation, and engineering notes

This repo represents my work in automotive telemetry, simulation engineering, cognitive systems, and embedded computing.

🚗 Project Overview

Modern vehicles generate hundreds of real-time CAN bus signals—from speed and RPM to steering angle and diagnostics. Research teams often need:

A safe simulation environment

Real-time visualization tools

The ability to merge sensor data with virtual physics

A platform for algorithm prototyping, machine learning, and cybersecurity

The original system I inherited could only display static gauge images, with no real-time updates or interactivity.

I rebuilt the entire system from the ground up.

✔ Built a real-time 3D simulation using an open-source physics engine
✔ Integrated a Raspberry Pi + CAN interface for hardware-level signal acquisition
✔ Designed a socket-based pipeline for streaming vehicular data
✔ Created an interactive 3D visualization environment
✔ Enabled live CAN signal decoding, plotting, and display

This repository shares the public-safe version of that work.

🎥 Demo

The demo/ folder contains:

Synthetic CAN frame playback

Gauge visualization

Optional 3D component (vehicle speed → wheel rotation)

Demo video (video-demo.mp4)

Screenshots & UI captures

This reflects the frontend functionality of the real system, using artificial data.

🧰 System Architecture

Below is the architecture used in the real system, reproduced through diagrams inside /docs:

[ CAN Hardware ] 
      ↓
[ Raspberry Pi + CAN Interface ] 
      ↓
[ Python CAN Listener ] 
      ↓
[ WebSocket Data Server ] 
      ↓
[ Client Visualization ]
    (React / Three.js)

Core components
Layer	Description
Hardware Layer	Raspberry Pi, CAN transceiver, OBD-II connection
Data Layer	Python-based CAN bus decoding, data normalization
Communication Layer	WebSocket server streaming real-time frames
Simulation Layer	Physics engine computing vehicle movement
Visualization Layer	3D scene + dynamic gauges + signal graphs

See /docs/system-overview.md for full details.

🔍 Motivation & Research Alignment

This project supports research in:

Cognitive systems

Machine learning for vehicle behavior prediction

Human–machine interaction

Automotive cybersecurity

Real-time embedded systems

Simulation-based testing

Vehicle telemetry systems serve as rich cognitive environments with:

structured signals

interpretable low-level sensory data

high-frequency state changes

predictable physics

This makes them ideal for ML, signal processing, and cognitive modeling applications.

🧪 Frontend Demo (Synthetic CAN Data)

The demo/can-simulator-frontend/ folder includes:

Fake CAN frames

A JavaScript client that parses and displays them

Example gauges (speed, rpm, throttle)

A small interactive 3D object responding to CAN values

Example synthetic frame:

{
  "id": "0x100",
  "timestamp": 0.421,
  "speed_kph": 32,
  "rpm": 2040
}


All data is fabricated for demonstration.

📚 Documentation

Inside the /docs folder:

🔹 system-overview.md

High-level architecture, motivation, diagrams, and design goals.

🔹 research-background.md

CAN bus architecture, automotive networks, and simulation rationale.

🔹 physics-engine-notes.md

Details on vehicle dynamics modeling, including:

raycast suspension

longitudinal and lateral friction

steering model

clutch/engine force

chassis inertia

quaternion orientation

🔹 fake-can-frames.json

Dataset used by the demo.

📊 Technologies Used
Category	Tools
Embedded Systems	Raspberry Pi, CANable interfaces, socketcan
Backend	Python, asyncio, Python-CAN
Communication	WebSockets, JSON
Simulation	Cannon.js or custom physics engine
Frontend	React, Three.js, d3.js
Documentation	Markdown, Draw.io
⚠️ Disclaimer

This repository contains no proprietary, sensitive, or NIWC-specific code.
All CAN data shown is artificially generated for public demonstration.
Architectural descriptions are generalized for educational and portfolio use.

🧑‍🔬 About Me

I am a Cognitive Science (Machine Learning) and Computer Science–focused student with research experience in:

autonomous systems

vehicle telematics

real-time simulation

computational modeling

embedded AI

I built this system to support research in automotive cognition, cybersecurity, and real-time system design.

📌 Status

This repository is an ongoing documentation project.
I am currently expanding:

interactive demo features

physics accuracy

signal decoding examples

cognitive modeling notes

⭐ If you find this project useful, please consider starring the repo.
🌐 Contact

GitHub: Avensky
Email: urielzacarias@gmail.com
Portfolio: urielzacarias.com
