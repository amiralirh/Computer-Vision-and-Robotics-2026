# Visual Perception for Robotic Surgery: Multi-Label Tool Detection

## 📌 Project Overview
This project develops a robust Visual Perception module for autonomous surgical robotics, focusing on the real-time detection and tracking of surgical instruments (e.g., Phaco probes, Choppers) in real-world **Cataract Surgery** videos. 

Moving beyond controlled environments, this pipeline addresses critical clinical challenges such as severe class imbalance, multi-tool occlusion, motion blur, and specular reflections from surgical microscopes. The ultimate goal is to provide a reliable, low-latency perception loop for autonomous or semi-autonomous robotic intervention.


## 🚀 Core Modules & Technical Contributions

### 1. Advanced EDA & Data Engineering
- **Multi-Label Formulation:** Framed the detection task as a Multi-Label Classification problem (handling concurrent tool appearances) using appropriate loss functions like **Focal Loss** to counteract severe class imbalances.
- **Robust Augmentation:** Implemented state-of-the-art augmentation strategies including **CutMix, Mixup, and RandAugment** to fortify the model against surgical artifacts (microscope glares, tool occlusions, and blood/tissue obstructions).

### 2. Deep Neural Network Architecture & Optimization
- **Transfer Learning:** Leveraged modern ImageNet-pretrained architectures (e.g., *ResNet, EfficientNet, ConvNeXt*) adapted for medical domains where data is highly constrained.
- **Hyperparameter Search:** Utilized the **Optuna** framework to systematically optimize learning rates, weight decay, and optimizers (AdamW vs. SGD with Momentum), meticulously analyzing the Bias-Variance tradeoff.

### 3. Explainable AI (XAI) & Interpretability
- Avoided the "black box" pitfall of medical AI by integrating **Grad-CAM** to generate thermal heatmaps, proving the network relies on the actual geometric structures of the tools rather than spurious background artifacts.
- Visualized high-dimensional extracted feature spaces using **t-SNE** to validate inter-class separability.
- Evaluated performance beyond misleading Accuracy metrics, utilizing **Precision, Recall, F1-Score, PR-AUC**, and comprehensive Confusion Matrices.

### 4. Cross-Validation & Inference Acceleration
- **Stratified K-Fold:** Transitioned from standard splitting to Stratified K-Fold cross-validation to ensure equitable distribution of rare surgical phases across folds, quantifying model variance and robustness.
- **Model Soups vs. Ensemble Learning:** Addressed the critical robotic constraint of **Real-time Inference Latency**. Instead of traditional ensemble methods that degrade throughput, implemented **Model Soups** (averaging weights of fine-tuned models) to achieve ensemble-level accuracy without ANY computational overhead during deployment.


## 🛠️ Tech Stack & Frameworks
* **Deep Learning:** `PyTorch` / `Torchvision`
* **Optimization:** `Optuna`
* **XAI & Metrics:** `Captum`  `Scikit-learn`
* **Data Processing:** `Pandas`, `NumPy`, `OpenCV`, `Albumentations`

