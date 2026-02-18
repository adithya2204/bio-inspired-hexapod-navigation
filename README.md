# Ant Bot — Bio-Inspired Hexapod Navigation (Research Summary)

Ant Bot is a ROS 2-based hexapod simulation exploring bio-inspired locomotion and navigation strategies for multi-legged robots.  
The project investigates how insect-inspired behaviors such as tripod gait walking and path integration can be applied to autonomous robotic navigation in simulation.

The system is implemented in ROS 2 Humble and evaluated in a physics-based Gazebo environment using a custom URDF/Xacro robot model and closed-loop control pipeline.

---

## Research Focus

This work explores:

- Bio-inspired locomotion for hexapod robots  
- Robust gait coordination under directional control  
- Dead-reckoning-based navigation (path integration)  
- Stability during turning and full-rotation maneuvers  
- Simulation-driven evaluation of legged navigation strategies  

The objective is to study how insect navigation principles can be translated into control frameworks for autonomous legged systems.

---

## System Overview

### Tripod Gait Controller
A custom controller coordinating alternating leg tripods to ensure stable walking and directional control.

### Path Integration Navigation
The `ant_navigator` node enables random exploration followed by homing to the origin using heading estimation and yaw correction.

### Physics-Based Simulation
A complete URDF/Xacro robot model integrated with Gazebo plugins, IMU sensing, and ros2_control interfaces.

### Yaw Stabilization Logic
Additional correction mechanisms were introduced to reduce drift and vibration during full rotations and homing maneuvers.

---

## Experimental Observations

Simulation trials demonstrated:

- Stable tripod locomotion under directional commands  
- Successful return-to-origin behavior using path integration  
- Improved heading stability during rotations  
- Reduced drift after yaw realignment corrections  

![Start Position](Start%20position.png)

Representative navigation traces and heading-correction graphs are included in this repository.

---

## Demonstration

A full demonstration video is available here:  
**[https://drive.google.com/file/d/1WqY7ZmOZIHpbWZRTRdDwb_wMEqJCbax2/view?usp=sharing]**

The demo shows:

- Exploration phase  
- Heading estimation  
- Homing behavior  
- Yaw correction during return  

---

## Publication Status

The full implementation is currently private while the work is being prepared for academic publication.

Researchers interested in collaboration, validation, or technical discussion are welcome to contact me for access.

---

## Tools & Frameworks

- ROS 2 Humble  
- Gazebo Classic  
- Python (NumPy, transforms3d)  
- ros2_control  
- URDF/Xacro modeling  

---

## Hardware Platform

This project is based on a custom hexapod robotic platform developed for terrain navigation research.

The hardware platform overview is available here:

```bash
https://github.com/adithya2204/hexapod-terrain-platform
```

## Author

**Adithya Pothula**  
Robotics Researcher — Autonomous Navigation & Legged Systems  

GitHub: https://github.com/adithya2204  
Google Scholar: https://scholar.google.com/citations?hl=en&user=NI9WpkQAAAAJ

---


