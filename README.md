# 🤖 Computer Vision & Intelligent Robotics 

[![Python](https://img.shields.io/badge/Python-3.x-blue.svg)](https://www.python.org/)
[![PyTorch](https://img.shields.io/badge/PyTorch-Deep%20Learning-ee4c2c.svg)](https://pytorch.org/)
[![OpenCV](https://img.shields.io/badge/OpenCV-Vision-green.svg)](https://opencv.org/)
[![PyBullet](https://img.shields.io/badge/PyBullet-Simulation-yellow.svg)](https://pybullet.org/)

## 📌 About This Repository
Welcome! This repository is a curated collection of advanced academic and practical projects developed during the *Robotics and Machine Vision* coursework at K. N. Toosi University of Technology (Spring 2026). 

The projects demonstrate a comprehensive pipeline bridging **Visual Perception** (Deep Learning, Tracking, OpenCV) with **Robotic Control** (Kinematics, Dynamics, Simulation, and Safety Systems). The primary focus is on autonomous systems, industrial inspection, and surgical robotics.

---

## 📂 Project Showcase

### 1. [Surgical Robot Kinematics & Pose Analysis](./Surgical-Robot-Kinematics/)
A deep dive into the mathematical foundations of robotic manipulators. This project focuses on the spatial transformations of a 6-DoF surgical robot, handling edge cases in orientation tracking.
* **Key Concepts:** Denavit-Hartenberg (DH) Parameters, Gimbal Lock (Euler/RPY), Matrix Orthonormality, Skill Assessment via Angular Jitter.
* **Tech Stack:** `Python`, `NumPy`, `SciPy`, `SymPy`
* 🔗 **[View Project](./Surgical-Robot-Kinematics/)**

### 2. [Industrial Automated Inspection System](./Automated-Inspection-System/)
An end-to-end simulated industrial workcell. A PRR robotic arm autonomously inspects color-coded targets identified by an overhead camera, executing path planning based on numerical inverse kinematics.
* **Key Concepts:** Perspective Rectification (Homography), HSV Segmentation, Forward/Numerical Inverse Kinematics, Reachable Workspace Analysis.
* **Tech Stack:** `OpenCV`, `PyBullet`, `SymPy`, `Matplotlib`
* 🔗 **[View Project](./Automated-Inspection-System/)**

### 3. [Surgical Tool Perception: Deep Learning & XAI](./Surgical-Tool-Perception-CNN/)
A deep learning project focused on the multi-label classification of surgical instruments in real-world cataract surgery videos. It tackles clinical challenges like severe class imbalance and instrument occlusion.
* **Key Concepts:** Multi-label Classification, Transfer Learning, Hyperparameter Optimization, Stratified K-Fold Cross-Validation.
* **Tech Stack:** `PyTorch`, `Optuna`, `Pandas`, `Albumentations`
* 🔗 **[View Project](./Surgical-Tool-Perception-CNN/)**

### 4. [Surgical Vision Deployment & Profiling](./Surgical-Vision-Deployment/)
Transitioning from architecture design to operational deployment, this project focuses on PyTorch pipeline engineering, real-time inference benchmarking, and visual debugging for robotic control loops.
* **Key Concepts:** CutMix/Mixup Augmentations, Real-time Profiling (FPS/VRAM), Model Soups (Zero-latency ensemble), XAI (Grad-CAM, t-SNE).
* **Tech Stack:** `PyTorch Profiler`, `Captum`, `Scikit-learn`
* 🔗 **[View Project](./Surgical-Vision-Deployment/)**

### 5. [Surgical Tracking & Kinematic Safety System](./Surgical-Tracking-and-Safety-System/)
A sophisticated Multi-Object Tracking (MOT) pipeline integrated with a robotic control safety dashboard. It tracks surgical tools and evaluates their motion for spatial hazards and actuator wear.
* **Key Concepts:** Tracking-by-Detection (YOLO + SORT), Kinematic Hazard Detection, High-frequency Tremor Filtering, Control Effort Integration ($\int a^2 dt$), Surgical HUD Rendering.
* **Tech Stack:** `YOLO`, `ByteTrack`, `FilterPy`, `OpenCV`
* 🔗 **[View Project](./Surgical-Tracking-and-Safety-System/)**

---

## 🛠️ Core Skills & Technologies

* **Machine Vision & AI:** Image Processing (OpenCV), Object Detection & Tracking (YOLO, DeepSORT), CNN Architectures (ResNet, EfficientNet), Transfer Learning, XAI (Grad-CAM).
* **Robotics & Control:** Forward/Inverse Kinematics, Jacobian Analysis, Trajectory Planning, Signal Processing (Kalman/Savitzky-Golay Filters), Physics Simulation (PyBullet, URDF).
* **Software Engineering:** Object-Oriented Programming (OOP), Hardware Profiling (Latency/Throughput Optimization), Multi-processing/DataLoaders.

---

