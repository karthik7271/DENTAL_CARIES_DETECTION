# 🦷 GOCRICIT

**Comprehensive Analysis of Object Detection and Image Segmentation on Dental X-ray Images Using YOLOv8 and Deep Learning Models**  
*Author: Karthik Ragulan | Date: April 14, 2025*

---

## 📖 Project Overview

GOCRICIT is a deep learning pipeline that automates the detection and segmentation of cavities from dental X-rays. It leverages:

- **YOLOv8** for object detection (cavity localization)
- **U-Net** and **DeepLabV3+** for semantic segmentation (cavity boundaries)

The system improves clinical diagnostics by enhancing both detection precision and segmentation accuracy.

---

## 📂 Dataset

- Total Images: 300 dental X-rays
- Annotations:
  - **Bounding Boxes** for cavity detection
  - **Binary Masks** for segmentation
- Preprocessing:
  - Resizing
  - Normalization
  - Data Augmentation with `albumentations`

---

## 🧠 Methodology

### 🔹 Object Detection

- Model: `YOLOv8`
- Architecture: CSPDarknet + PANet + YOLO Head
- Loss Function: Binary Cross-Entropy + IoU Loss
- Optimizer: `AdamW`
- Epochs: 500

### 🔹 Image Segmentation

- Models: `U-Net`, `DeepLabV3+` (with ResNet & MiT-B5 encoders)
- Input Size: 256×256
- Loss Function: `0.6 × DiceLoss + 0.4 × BCEWithLogitsLoss`
- Optimizer: `Adam`
- Early Stopping & Model Checkpointing
- Metrics: Dice Score

---

## 🚧 Challenges and Solutions

| Challenge              | Solution                                                             |
|------------------------|----------------------------------------------------------------------|
| Small dataset          | Used data augmentation + additional images from online sources       |
| Poor annotations       | Switched to tighter, manually labeled bounding boxes                 |
| Overfitting            | Applied dropout, early stopping, and image augmentation              |
| Lack of negative cases | Future work includes adding healthy teeth for binary classification  |

---

## 📈 Results

- **YOLOv8 Accuracy** improved significantly with tighter annotations
- **Best Dice Score** (Validation): `0.60`
- Visual results show effective cavity isolation from noisy backgrounds

---

## 🔬 Future Work

- Explore **Transformer-based detection models** (e.g., DETR, DINO)
- Include **healthy X-rays** for binary classification
- Enhance segmentation using **tooth contour-aware labels**
- Integrate **YOLOv8Seg** for simultaneous detection & segmentation

---

## 🛠 Tech Stack

- Python
- PyTorch
- segmentation_models.pytorch
- Albumentations
- Matplotlib & Seaborn

---

## 📚 References

1. Bochkovskiy et al., YOLOv4: arXiv:2004.10934
2. Ronneberger et al., U-Net: MICCAI 2015
3. Chen et al., DeepLabV3+: ECCV 2018
4. Loshchilov & Hutter, ICLR 2019
5. Gonzalez & Woods, *Digital Image Processing*
6. Shorten & Khoshgoftaar, *Journal of Big Data*, 2019

---
