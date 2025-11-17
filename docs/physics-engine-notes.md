# 🧮 Physics Engine Notes  
### Vehicle Dynamics Model for Real-Time CAN Bus Simulation

This document summarizes the physics concepts used to design a real-time vehicle simulation engine compatible with CAN bus signal visualization.  
It is written for clarity, reproducibility, and research purposes.

---

# 1. Overview

The physics engine models how a vehicle responds to:
- acceleration  
- braking  
- steering  
- suspension movement  
- friction and traction  
- mass distribution  
- wheel forces  

The goals of the physics engine are:
- **stable real-time performance**  
- **physically plausible movement**  
- **compatibility with CAN telemetry**  
- **smooth output for visualization (speed, RPM, orientation)**  

---

# 2. Coordinate System

We use a right-handed coordinate system:

- **X-axis** → right  
- **Y-axis** → up  
- **Z-axis** → forward  

Vehicle motion is primarily in the X–Z plane, with Y used for suspension movement.

---

# 3. Core Mathematical Concepts

### 3.1 Vectors
Used for velocity, acceleration, forces, wheel direction, etc.

### 3.2 Quaternions
Used for orientation to avoid gimbal lock.

### 3.3 Integration
The physics engine approximates continuous motion using:
- semi-implicit Euler  
- timestep `dt` from a stable clock (e.g., 60 Hz)

---

# 4. Vehicle Body Parameters

Example parameters:

```
mass: 1500 kg
wheelRadius: 0.34 m
wheelBase: 2.8 m
trackWidth: 1.6 m
inertiaTensor: { x: 400, y: 1200, z: 1300 }
dragCoefficient: 0.32
rollingResistance: 12.5
```

These parameters influence every subsystem.

---

# 5. Suspension Model (Raycast Vehicle)

Each wheel has a suspension strut modeled as:

```
F_spring = k * (restLength - currentLength)
F_damper = c * (compressionSpeed)
```

Where:
- `k` = spring stiffness  
- `c` = damping coefficient  

Suspension stabilizes the vehicle and impacts handling.

---

# 6. Wheel Physics

### 6.1 Longitudinal Slip (Acceleration/Braking)

Slip ratio:

```
slip = (wheelAngularVelocity * wheelRadius - vehicleForwardSpeed) / max(vehicleForwardSpeed, smallValue)
```

### 6.2 Traction Curve

Slip ratio feeds into a traction force curve (simplified Pacejka model):

```
F_long = tractionCurve(slip) * normalForce
```

This defines:
- grip  
- wheelspin  
- braking effectiveness  

---

# 7. Steering Model

Front wheels rotate by steering angle θ:

```
θ = steeringInput * maxSteeringAngle
```

The vehicle uses **Ackermann steering geometry** for realistic turning.

---

# 8. Engine & Drivetrain

### 8.1 RPM Model

```
RPM = wheelAngularVelocity * gearRatio * finalDriveRatio * 60 / (2π)
```

### 8.2 Torque Curve

Engine torque is mapped from an RPM → Torque curve:

```
1000 RPM → 120 Nm
2500 RPM → 210 Nm
4000 RPM → 240 Nm
6000 RPM → 210 Nm
```

### 8.3 Gearbox

- gear ratios  
- final drive  
- clutch slip model  
- rev limiter  

---

# 9. Force Summation

Total force on the vehicle:

```
F_total = 
    F_engine 
  + F_brake
  + F_drag
  + F_rolling
  + F_longitudinal
  + F_lateral
```

Acceleration:

```
a = F_total / mass
```

Velocity integration:

```
v = v + a * dt
```

Position integration:

```
x = x + v * dt
```

---

# 10. Orientation & Rotation

Angular velocity is computed from torque:

```
angularAcceleration = torque / inertia
angularVelocity += angularAcceleration * dt
orientationQuaternion = integrate(angularVelocity)
```

This controls:
- pitch  
- yaw  
- roll  

---

# 11. CAN-Compatible Output Signals

The simulation generates signals compatible with CAN visualization:

| Sim Variable    | CAN Equivalent             |
|-----------------|----------------------------|
| `speed`         | Vehicle Speed              |
| `rpm`           | Engine RPM                 |
| `gear`          | Gear Position              |
| `steeringAngle` | Steering Sensor Value      |
| `throttle`      | Accelerator Pedal Position |
| `brakeForce`    | Brake Pressure             |

These can be streamed directly to the frontend.

---

# 12. Real-Time Constraints

Simulation target: **60 updates per second**

Stability maintained by:

- fixed timestep loop  
- clamped forces  
- interpolation smoothing  
- normalized quaternions  

---

# 13. Summary

This physics engine captures the essential dynamics necessary for:
- vehicle research  
- real-time visualization  
- CAN bus signal interpretation  
- cognitive systems modeling  
- machine learning experiments  

It is fully compatible with both synthetic and hardware-based CAN data pipelines.

---

# End of Document
