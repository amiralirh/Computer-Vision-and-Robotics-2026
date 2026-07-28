# Surgical Robot Kinematics & Pose Analysis

## 📌 Project Overview
This project focuses on the advanced kinematic modeling, spatial transformations, and pose estimation of a **6-DoF Serial Surgical Robot** designed for high-precision maneuvers in confined spaces. The core objective is to analyze coordinate frame chains, handle mathematical singularities (Gimbal Lock), and reconstruct corrupted spatial data robustly.

This project was developed as part of the *Robotics and Machine Vision* coursework at K. N. Toosi University of Technology (Spring 2026).

## 🚀 Key Features & Analytical Modules

### 1. Singularity & Gimbal Lock Analysis
- Analytically evaluated the orientation of the surgical end-effector $\{E\}$ relative to the camera frame $\{C\}$ using Fixed Angles (Roll-Pitch-Yaw).
- Proved the loss of rotational degrees of freedom (degeneracy) when pitch angle $\beta = \frac{\pi}{2}$ and demonstrated the difference in behavior when using moving Euler angles ($u-v-w$).

### 2. Homogeneous Transformations & Frame Chaining
- Computed the complex spatial relationship between the End-Effector $\{E\}$ and Target Tissue $\{T\}$ by chaining transformation matrices: ${}^{0}T_{C}$, ${}^{0}T_{E}$, and ${}^{C}T_{T}$.
- Extracted the equivalent rotation angle ($\theta$) and axis of rotation ($\mathbf{k}$) using eigenvalues and the trace of the Special Orthogonal group $SO(3)$ matrix.

### 3. Robust Pose Reconstruction (Numerical Stability)
- Developed a robust algorithm to reconstruct corrupted transformation matrices derived from noisy sensor data.
- Enforced orthonormality and $SO(3)$ constraints using vector cross-products ($\mathbf{u} \times \mathbf{v} = \mathbf{w}$) and Least Squares fitting to find the closest valid geometric matrix.

### 4. Kinematic-based Skill Assessment
- Designed an evaluation metric to differentiate between *Expert* and *Novice* surgeons based on **Angular Jitter**.
- Proved the geometric invariance of the relative rotation matrix $R_{\text{rel}} = R(t)^T R(t+\Delta t)$ and computed the "Incompetence Score" by analyzing rotational deviations over time.

## 🛠️ Code Implementations
The repository includes robust implementations in **Python/MATLAB**:
* **`robust_rpy_extractor`**: Converts a $3 \times 3$ rotation matrix to Roll-Pitch-Yaw angles using `atan2`, meticulously handling edge cases ($\cos\beta = 0$) to prevent angular jumps.
* **`pose_reconstruction`**: Takes a corrupted homogeneous transformation matrix, rectifies it to valid $SO(3)$ space, and calculates the inverse transform without direct $4 \times 4$ determinants.
* **`skill_assessment`**: Evaluates a 3D array of $N$ transformation matrices and returns the positional/angular jitter score.

## 📊 Mathematical Highlights
The analysis extensively utilizes:
* Taylor series expansion for infinitesimal rotations to demonstrate non-commutativity limits.
* Eigenvector analysis for Universal Joint mappings.
* Orthonormal projection and reflection error handling in rotational spaces.

