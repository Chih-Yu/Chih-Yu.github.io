---
title: "Interaction between Human Body Pose and Robot Arm Using Deep Learning and Digital Twin"
date: 2024-06-07
description: "NCKU CSIE Project"
summary: "This project develops an intuitive human-robot interaction (HRI) system, replaces traditional keyboard-based control with natural, vision-based interaction."
slug: "Pose-RobotArm-HRI"
tags: ["robotics"]
---

[{{< icon github >}}](https://github.com/Chih-Yu/Pose-RobotArm-HRI)
[Project Poster (Chinese Version)](https://github.com/Chih-Yu/Pose-RobotArm-HRI/blob/main/%E6%B5%B7%E5%A0%B1BotAmr_%E5%BC%B5%E7%A6%95%E5%80%AB_%E8%98%87%E8%87%B4%E5%AE%87.pdf)

This project develops an intuitive human-robot interaction (HRI) system. By leveraging **Deep Learning (MediaPipe)** and **Digital Twin (PyBullet)** technologies, it maps human arm gestures captured via a depth camera to a physical robot arm in real-time. This replaces traditional keyboard-based control with natural, vision-based interaction.

## Team & Supervision
* Developers: Su Chih-Yu, Zhang Yi-Lun
* Advisor: Prof. Jenn-Jier James Lien

---

## System Architecture
The system follows a closed-loop control flow to ensure precision and safety:

![flowchart](image/flowchart.jpg)

1. **Vision Input**: An Intel® RealSense™ D435 captures RGB-D data.
2. **Pose Processing**: MediaPipe extracts 3D landmarks (x, y, z) of the user's arm joints.
3. **Signal Filtering**: A Kalman Filter is applied to eliminate jitter caused by involuntary human movement or sensor noise.
4. **Digital Twin Sync**: The filtered coordinates are sent to PyBullet for inverse kinematics calculation and motion path validation.
5. **Physical Execution**: Validated commands are transmitted via ROS to the TM Robot.

---

## Key Technical Modules

### 1. Vision & Depth Sensing (Intel® RealSense™)
The system utilizes infrared (IR) laser and RGB sensors to capture 3D spatial mapping ($X, Y, Z$). This allows the system to distinguish the user's distance and accurately map movements to the robot's coordinate system.

### 2. Gesture Estimation (MediaPipe)
The MediaPipe Pose model identifies key landmarks. We specifically focus on the Shoulder, Elbow, and Wrist joints to create a 3D mapping for the robot arm.

![mediapipe_mark](image/mediapipe_mark.jpg)

### 3. Motion Smoothing (Kalman Filter)
To counteract involuntary tremors and sensor noise, a discrete Kalman Filter is implemented to smooth the trajectory. The state update is governed by:

$$x_k = K_k \cdot z_k + (1 - K_k) \cdot x_{k-1}$$

**Where:**
* $x_k$: Current estimated position (Smooth output)
* $K_k$: Kalman Gain (Weight of the current measurement)
* $z_k$: Current measured position from sensors (Raw input)
* $x_{k-1}$: Previous estimated position



| Origin | Mapped & Filter |
| -------- | -------- | 
| ![kalman](image/kalman.png) | ![kalman2](image/kalman2.png) |

### 4. Digital Twin & Safety (PyBullet)
The **UR5/TM5** model in PyBullet acts as a safety buffer. It verifies movement within the robot's reach to prevent self-collision or singularities before physical execution.

![pybullet](image/pybullet.png)

---

## Applications & Results
* **Real-time Object Grabbing**: Guide the robot arm to pick up items via natural gestures.
* **Electric Wire Maze Game**: A high-precision test demonstrating low latency and fine-grained control.
* **Interactive UI**: A custom-built interface for calibration, data visualization, and mode switching (Grip, Free, Start Arm).

![ui](image/ui.png)

### Reference

[TechmanRobot Driver - GitHub](https://github.com/TechmanRobotInc)

[Intel® RealSense™ Library - Github](https://github.com/realsenseai/librealsense)

[Google Mediapipe](https://ai.google.dev/edge/mediapipe/solutions/guide?hl=zh-tw)