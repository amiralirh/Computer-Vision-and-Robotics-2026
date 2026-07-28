# Surgical Tracking & Kinematic Safety System

## 📌 Project Overview
This project develops an advanced Multi-Object Tracking (MOT) pipeline and a Kinematic Safety Dashboard for robotic cataract surgery. Utilizing the **Cataract-LMM dataset**, the system tracks surgical instruments in real-time and evaluates their motion trajectories using robotics control theory. 

The core objective is to bridge Computer Vision and Robotic Control by identifying spatial hazards, analyzing high-frequency tremors, and quantifying the control effort required by a teleoperated surgical robot (e.g., slave manipulator).


## 🚀 Core Modules & Technical Contributions

### 1. Strategic Data Engineering & Geometry
- **Video-Level Splitting:** Implemented strict video-level Train/Val/Test splits (70-15-15) to eliminate inter-frame data leakage, a common pitfall in tracking datasets.
- **Dynamic Polar Coordinate Transformation:** Mapped Cartesian instrument tip coordinates to a patient-centric Polar Coordinate system $(r, \theta)$, dynamically anchored to the moving pupil centroid for anatomy-relative tracking.

### 2. Multi-Object Tracking (MOT) Architecture
- **Tracking-by-Detection Pipeline:** Integrated a high-performance object detector (e.g., YOLO/Faster R-CNN) with a robust data association algorithm (e.g., ByteTrack/DeepSORT) to track instruments.
- **Tracking Metrics Analysis:** Evaluated the system using strict MOT metrics including **MOTA**, **IDF1**, **MT/ML**, and **ID Switches**, supplemented by Precision-Recall curves and FPS benchmarking across different input resolutions.

### 3. Robotic Kinematics & Control Assessment
- **Spatial Hazard Detection:** Defined dynamic safe zones based on Cornea and Pupil masks, triggering warnings when Euclidean distances breached predefined safety thresholds.
- **Tremor & Signal Filtering:** Applied low-pass filters (Savitzky-Golay / Kalman Filter) to raw visual predictions to compute smooth 1st to 3rd order derivatives (Velocity, Acceleration, Jerk), successfully identifying high-frequency tremors.
- **Control Effort Metric:** Designed a novel kinematic metric based on trajectory planning theory—utilizing the integral of squared acceleration ($\int a^2 dt$) and dimension-less jerk—to quantify actuator wear, energy consumption, and motion smoothness of the robotic arm.

### 4. Interactive Surgical HUD (Heads-Up Display)
Rendered a professional, real-time alerting dashboard overlay on the surgical video featuring:
- **Fading Trajectory Tails:** Visualizing the last 30 frames of instrument motion.
- **Context-Aware Color Coding:** Green for safe states, Orange for spatial boundary proximity, and Red for critical kinematic instability.
- **Timeline Dashboard:** A 1D synchronized timeline plotting linear velocity and highlighting temporal regions where spatial or kinematic warnings were triggered.


## 🛠️ Tech Stack & Dependencies
* **Tracking & CV:** `PyTorch`, `Ultralytics` (YOLO), `OpenCV`, `py-motmetrics`
* **Signal Processing & Math:** `SciPy` (Savitzky-Golay), `FilterPy` (Kalman Filter), `NumPy`
* **Visualization:** `Matplotlib`, `Seaborn`

