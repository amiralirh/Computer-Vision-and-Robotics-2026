# Surgical Vision Deployment: Real-time Profiling & Failure Analysis

## 📌 Project Overview
This repository contains the practical implementation and empirical validation phase of the Surgical Visual Perception module. Transitioning from theoretical architecture design to real-world operational deployment, this project focuses on **PyTorch pipeline engineering, real-time inference benchmarking, and deep visual debugging** for robotic surgical assistants.

The primary objective is to deploy a multi-label classification network capable of tracking surgical instruments in cataract surgery while strictly satisfying the low-latency and hardware constraints of a real-time robotic control loop.


## 🚀 Core Implementations & Engineering

### 1. Custom Data Engineering & Augmentation
- **Optimized Data Pipeline:** Developed a custom PyTorch `Dataset` and `DataLoader` for Multi-hot encoded multi-label targets. Conducted performance profiling on batch loading speeds by tuning `num_workers` and `pin_memory`.
- **In-Loop CutMix/Mixup:** Implemented custom training loops integrating Mixup and CutMix data augmentations on-the-fly, dynamically interpolating multi-label targets and utilizing `BCEWithLogitsLoss` for robust gradient updates.

### 2. Edge Inference Benchmarking & Model Soups
- **Heavy vs. Edge Profiling:** Trained and benchmarked lightweight edge architectures (e.g., *MobileNetV3 / EfficientNet-B0*) against high-capacity models (e.g., *ResNet50 / ConvNeXt*).
- **Real-Time Benchmarking:** Developed a profiling script to rigorously measure **Inference Time (ms), Throughput (FPS), and GPU VRAM consumption** on test data, justifying the architectural choice for robotic control loops.
- **Model Soups Deployment:** Implemented the *Model Soups* technique (weight averaging across multiple checkpoints). This achieved the accuracy benefits of ensemble learning with **zero additional inference latency**, solving the critical throughput bottleneck in robotic applications.

### 3. Visual Debugging & Failure Analysis (XAI)
Moved beyond simple metrics to meticulously dissect the model's behavior on edge cases and clinical errors:
- **Feature Space Mapping:** Extracted penultimate layer embeddings and mapped them to 2D space using **t-SNE**, visualizing class entanglement and latent clustering.
- **Grad-CAM Failure Analysis:** Automated the extraction of False Positives (FP) and False Negatives (FN). Applied **Grad-CAM** to these failure cases to generate heatmaps, proving whether the network's mistakes were caused by surgical microscope glares, surgeon's hands, or similar background tissues.

## 🛠️ Tech Stack & Dependencies
* **Deep Learning Framework:** `PyTorch`, `Torchvision`
* **Performance Profiling:** `PyTorch Profiler`, `time`
* **XAI & Visualization:** `Captum` (Grad-CAM), `Scikit-learn` (t-SNE), `Matplotlib`
* **Hardware:** CUDA-enabled GPU (for VRAM & FPS Benchmarking)

