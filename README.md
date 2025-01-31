# **Contrastive Representation Learning**  

## **Overview**  
This project implements **Contrastive Learning** for self-supervised pretraining on the **MNIST dataset**, inspired by [SimCLR (Chen et al., 2020)](https://arxiv.org/pdf/2002.05709). The goal is to learn meaningful feature representations without labeled data, making it useful for scenarios where labeling is expensive (e.g., medical imaging).  

### **Key Concepts:**  
- **Self-Supervised Learning**: Learning representations without manual labels.  
- **Contrastive Learning**: Mapping similar images closer in feature space while pushing dissimilar ones apart.  
- **SimCLR-inspired Architecture**: Uses a base CNN encoder and a projection head for representation learning.  
- **Linear Classification Benchmark**: Evaluates pretraining effectiveness using a simple classifier.  

---

## **Project Structure**
```
📂 Contrastive-Representation-Learning
 ├── 📁 data/                     # MNIST dataset
 ├── 📁 models/                   # Model architectures
 ├── 📁 notebooks/                # Jupyter notebooks for experiments
 ├── train.py                     # Training script for contrastive learning
 ├── linear_eval.py               # Evaluates learned representations
 ├── utils.py                     # Utility functions
 ├── README.md                    # Project documentation
```

---

## **Implementation Details**  

### **1️⃣ Dataset & Augmentations**
- Dataset: **MNIST (subset of 5,000 images)**
- Augmentations:
  - **RandomHorizontalFlip**
  - **RandomResizedCrop**
  - **Color Jitter**
  - **Gaussian Blur**
  - **Random Grayscale**
- Normalization:  
  - Mean: **0.1307**, Std: **0.3081** (MNIST standard)

### **2️⃣ Model Architecture**  
- **Base Encoder:** Simple CNN  
- **Projection Head:** 2-layer MLP  
- **Loss Function:** NT-Xent (Normalized Temperature-scaled Cross-Entropy)  

### **3️⃣ Training Strategy**  
- **Batch Size:** 256  
- **Optimization:** Adam  
- **Pretraining:** 500 epochs  
- **Linear Evaluation:** A classifier is trained on frozen representations  

---

## **Results**
| Model                  | Dataset Size | Test Accuracy |
|------------------------|-------------|--------------|
| Random Initialization  | Full MNIST   | 98.60%       |
| Contrastive Pretraining | 50% MNIST    | XX.XX%       |

---

## **How to Run**  
### **1️⃣ Setup Environment**  
```bash
pip install -r requirements.txt
```
### **2️⃣ Train Contrastive Model**  
```bash
python train.py
```
### **3️⃣ Evaluate with Linear Classifier**  
```bash
python linear_eval.py
```

---

## **Future Work**  
🔹 Experiment with deeper architectures (ResNet, Vision Transformers)  
🔹 Extend to more complex datasets (CIFAR-10, Chest X-rays)  
🔹 Implement other contrastive methods (MoCo, BYOL)  

