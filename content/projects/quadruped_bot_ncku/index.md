---
title: "Collaborative Robotic System for Automated Retrieval and Transport"
date: 2023-06-04
description: "A collaborative dual-robot system for automated object retrieval and transport using bio-inspired mechanisms."
summary: "This system integrates a bio-inspired retrieval robot with a PID-controlled transport platform. Featuring a Theo Jansen linkage, a SCARA arm, and data-backed stress analysis, it demonstrates a complete workflow for automated material handling."
slug: "robot-retrieval"
tags: ["robotics"]
---

## Project Overview
This project presents an integrated robotic solution designed for automated material handling. The system consists of two specialized robots: a **Retrieval Robot** for precise object manipulation and a **Transportation Robot** for long-distance delivery. The workflow includes object detection, grasping, temporary storage, and automated unloading.

---

## Mechanical Design & Innovation

### 1. Bio-inspired Mobility (Theo Jansen Linkage)
The Retrieval Robot utilizes a modified **Theo Jansen linkage** (Strandbeest) for its movement. 
- **Optimization:** We extended the wheelbase to increase stability and create more space for the internal chassis.
- **Involute Gear System:** To prevent interference found in standard circular gears, we designed custom **Involute Gears** with a 35:25 gear ratio, ensuring constant velocity and higher load capacity.

![Mechanism Design - Theo Jansen Linkage](Linkage.jpg)

### 2. SCARA Robotic Arm & Gripper
A 4-DOF SCARA (Selective Compliance Assembly Robot Arm) was implemented for its superior balance.
- **Precision:** Driven by NEMA 17 stepper motors and A4988 drivers.
- **Efficiency:** The center-heavy design ensures the robot remains stable during rapid arm movements.
![Mechanism Design - Involute Gears](SCARA.jpg)

### 3. Transportation Unit (LEGO EV3 Platform)
The delivery phase is handled by a custom LEGO EV3 robot featuring:
- **PID Control:** Advanced line-following logic for smooth navigation.
- **Automatic Tilting:** A dual-motor tipping mechanism for depositing items into the target zone.

---

## Technical Specifications & Data

### System Components
| Category | Component | Specification |
| :--- | :--- | :--- |
| **Micro-controllers** | Arduino UNO (x2) | Main control & Arm kinematics |
| **Actuators** | JGA25-370 Motors | High-torque DC motors for legs |
| **Stepper Motors** | NEMA 17 | Used for SCARA arm precision |
| **Communication** | HC-05 Bluetooth | App Inventor interface connectivity |
| **Sensors** | Ultrasonic & Touch | Obstacle avoidance & Trip counting |

| | |
|--|--|
| <img src=circuit_base.jpg> | <img src=circuit_arm.jpg>|


### Structural Analysis (FEA Results)
We conducted Finite Element Analysis (FEA) using SolidWorks to ensure structural integrity under a total weight of approximately 8kg.

| Metric | Value | Result |
| :--- | :--- | :--- |
| **Max Load Applied** | 90 N | Passed |
| **Maximum Displacement** | 0.00177 mm | Highly Rigid |
| **Safety Factor** | Optimized | Structural Safety Confirmed |

![FEA Stress Analysis Result](FEA_arm.jpg)

---

## Software Architecture
The system integrates multiple programming environments to achieve seamless coordination:
1. **C++/Arduino:** Low-level control for motors and sensors.
2. **App Inventor:** A custom Android GUI for real-time manual override and monitoring.
3. **EV3 Logic:** Automated PID line-following and unloading sequences.

---

## Team Contributions

* **Chih-Yu Su:** System Integration, Arduino Programming, Documentation.
* **Duo-Xun Zhang:** Mechanical Design, CAD Modeling (SolidWorks), Presentation.
* **Jing-Wen Qiu:** Mechanical Design, CAD Modeling (SolidWorks), Assembly.
* **Wei-Ting Chen:** Mechanical Design, CAD Modeling (SolidWorks), Assembly.
* **Wei-Yun Shi:** Transportation Robot Logic (EV3), Hardware Testing.
* **Yu-Ting Chen:** Assembly, Sourcing, Budgeting, and Aesthetics.

---

## Conclusion
This project successfully demonstrates the integration of mechanical linkage design, FEA simulation, and multi-platform software control. By overcoming challenges such as gear interference and stepper motor jitter, our team delivered a robust automated system.

<img src="group.jpg" width="50%" />

---
