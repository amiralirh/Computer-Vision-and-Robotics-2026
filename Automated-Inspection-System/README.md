# Industrial Automated Inspection System: Vision-Kinematics Pipeline

## 📌 Project Overview
This project implements an end-to-end industrial automated inspection cell using a **PRR (Prismatic-Revolute-Revolute) robotic arm** and an overhead RGB camera. The system integrates machine vision for object detection, mathematical kinematics for motion planning, and 3D simulation for validation. 

Additionally, the repository includes a standalone Forward Kinematics analysis for the **7-DoF KUKA LBR iiwa** collaborative robot.


## 🚀 System Architecture & Pipeline

### 1. Machine Vision (OpenCV)
- **Perspective Rectification:** Extracted corner fiducial markers to compute a Homography matrix, transforming the angled, distorted camera view into a standardized top-down (orthographic) metric projection.
- **Color Segmentation:** Converted the rectified image to the HSV color space to segment target discs (Red, Green, Blue) while robustly handling the red-spectrum wrap-around and optical vignetting.
- **Connected-Component Analysis:** Grouped pixels and extracted geometric centroids to precisely locate target coordinates in the robot's base frame.

### 2. Robot Kinematics (SymPy & NumPy)
- **Denavit-Hartenberg (DH) Modeling:** Formulated the DH parameters for the PRR robotic arm.
- **Symbolic & Numerical FK:** Derived the closed-form symbolic Forward Kinematics (FK) matrices using `SymPy` and validated them against high-speed numerical computations using `NumPy`.
- **Workspace Analysis:** Mapped and visualized the robot's reachable 3D workspace (a toroidal/donut-shaped volume defined by the arm lengths $L_2$ and $L_3$).
- **Numerical Search IK:** Implemented a Brute-Force Grid Search algorithm in the joint space to position the end-effector accurately over the detected vision targets without relying on analytical Inverse Kinematics.

### 3. Physics Simulation & Validation (PyBullet)
- **URDF Generation:** Procedurally generated the XML-based URDF model of the PRR robot and the inspection table directly within the pipeline.
- **Real-time Actuation:** Deployed the robot in the `PyBullet` physics engine, commanding it to reach the target discs based on the computed joint configurations.
- **Kinematic Verification:** Compared the simulated end-effector states (`getLinkState`) with the mathematical FK outputs, ensuring sub-millimeter precision and analyzing systematic offset errors.
- **Trajectory Animation:** Generated smooth, linearly interpolated joint trajectories and captured real-time simulation frames to create a GIF animation of the inspection process.


## 🛠️ Tech Stack & Dependencies
* **Python 3.x**
* **Computer Vision:** `OpenCV`, `NumPy`
* **Kinematics & Math:** `SymPy`, `SciPy`
* **Simulation:** `PyBullet`
* **Visualization:** `Matplotlib`, `imageio` (for GIF generation)

