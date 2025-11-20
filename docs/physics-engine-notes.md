<p align="center">
  <strong>
    <a href="../README.md">🏠 Home</a> •
    <a href="../docs/">📘 Documentation</a> •
    <a href="../demo/">🎥 Demo Videos</a> •
    <a href="../data/">📊 Data Samples</a>
  </strong>
</p>

# 🧮 Physics Engine Notes  

### *Vehicle Dynamics Model for Real-Time CAN Bus & Embodied Simulation Research*

This document provides a structured overview of the physics engine powering the real-time simulation environment.  
Its purpose is **research clarity**, **reproducibility**, and **future extensibility** as the project grows to support other autonomous systems (UGVs, tracked vehicles, drones).

The engine is designed to produce **physically plausible behavior** with **low computational cost**, enabling real-time performance for visualization, CAN signal synthesis, and interactive control.

---

# 1. Conceptual Overview

The simulation engine models the dynamics of an **embodied agent**—a vehicle with:

- forces  
- mass  
- wheels  
- friction  
- suspension  
- orientation  

This enables researchers to explore:

- signal behavior under physical constraints  
- sensorimotor loops (input → state → action → feedback)  
- machine-learning on consistent time-series data  
- simulation-to-real transfer experiments  

The engine is built on a simplified but robust model inspired by real automotive dynamics and game-engine physics.

---

# 2. Coordinate System

A **right-handed** coordinate system is used:

- **X-axis** → right  
- **Y-axis** → up  
- **Z-axis** → forward  

Vehicle motion occurs primarily in the **XZ plane**, with Y reserved for suspension and body pitch/roll.

---

# 3. Core Mathematical Tools

### **3.1 Vectors**

Used for position, velocity, force, wheel direction, and linear acceleration.

### **3.2 Quaternions**

Used for orientation to avoid gimbal lock and maintain smooth rotation across 3D axes.

### **3.3 Numerical Integration**

The engine uses a **semi-implicit Euler integrator**:

```
v = v + a * dt
x = x + v * dt
```

This method is stable, inexpensive, and well-suited for real-time applications.

---

# 4. Vehicle Body Parameters

Representative parameters (adjustable per vehicle):

```
mass = 1500 kg
wheelRadius = 0.34 m
wheelBase = 2.8 m
trackWidth = 1.6 m
inertiaTensor = { x: 400, y: 1200, z: 1300 }
dragCoefficient = 0.32
rollingResistance = 12.5
```

These values determine:

- responsiveness  
- stability  
- traction  
- orientation dynamics  

The architecture supports **future expansion** to drones and tracked/holonomic platforms.

---

# 5. Suspension Model (Raycast Vehicle)

Each wheel uses a **spring-damper** suspension system:

```
F_spring = k * (restLength - currentLength)
F_damper = c * compressionSpeed
```

Where:

- **k** = spring stiffness  
- **c** = damping coefficient  

Suspension stabilizes the vehicle, preserves wheel-ground contact, and affects ride dynamics.

---

# 6. Wheel Physics

Wheels are the primary interface between the simulated agent and the ground.

### **6.1 Longitudinal Slip (Acceleration & Braking)**

Slip ratio:

```
slip = (wheelAngularVelocity * wheelRadius - vehicleForwardSpeed) 
        / max(vehicleForwardSpeed, smallValue)
```

### **6.2 Traction Curve**

A simplified traction curve approximates the **Pacejka Magic Formula**:

```
F_longitudinal = tractionCurve(slip) * normalForce
```

This governs:

- grip  
- wheelspin  
- braking behavior  

---

# 7. Steering Model

Front wheels rotate by a steering angle θ:

```
θ = steeringInput * maxSteeringAngle
```

To improve realism, the system supports **Ackermann steering geometry**, reducing tire scrub and enabling accurate turning radii.

---

# 8. Engine & Drivetrain Model

### **8.1 RPM Computation**

```
RPM = wheelAngularVelocity * gearRatio * finalDriveRatio * 60 / (2π)
```

### **8.2 Torque Curve**

The engine maps RPM → torque using a tunable response curve:

```
1000 RPM → 120 Nm  
2500 RPM → 210 Nm  
4000 RPM → 240 Nm  
6000 RPM → 210 Nm
```

### **8.3 Gearbox Model**

Features:

- multiple forward gears  
- clutch slip model  
- rev limiter  
- gear-dependent torque scaling  

---

# 9. Summation of Forces

Total longitudinal and lateral force on the vehicle:

```
F_total = 
    F_engine +
    F_brake +
    F_drag +
    F_rolling +
    F_longitudinal +
    F_lateral
```

Newton’s second law provides acceleration:

```
a = F_total / mass
```

Velocity & position integrate forward in time.

---

# 10. Orientation & Rotational Dynamics

Yaw, pitch, and roll arise from torque and inertia:

```
angularAcceleration = torque / inertia
angularVelocity += angularAcceleration * dt
orientationQuaternion = integrate(angularVelocity)
```

Quaternions ensure stability during dynamic maneuvers.

---

# 11. CAN-Compatible Output Signals

To unify the physics engine with data visualization, the simulator outputs values analogous to CAN telemetry:

| Physics Variable | Simulated CAN Equivalent |
|------------------|--------------------------|
| speed            | Vehicle Speed            |
| rpm              | Engine RPM               |
| gear             | Gear State               |
| steeringAngle    | Steering Sensor          |
| throttle         | Accelerator Position     |
| brakeForce       | Brake Pressure           |

This enables **frame diffing**, **frequency analysis**, and **ML pipeline compatibility**.

---

# 12. Real-Time Constraints

Target update rate: **60 Hz**

Stability techniques:

- fixed timestep  
- clamping of extreme forces  
- smoothing of sensor outputs  
- normalized quaternion updates  

The design prioritizes **performance** and **interpretability** over extreme realism.

---

# 13. Summary

This physics engine provides a computationally efficient and scientifically meaningful model of an embodied agent operating under realistic physical constraints.  
Its simplicity makes it:

- ideal for **cognitive modeling**  
- friendly for **machine learning datasets**  
- extensible to **autonomy research and drones**  
- suited for **interactive simulation & visualization**

This foundation supports both real-time visualization and rigorous experimental workflows.

---

# End of Document
