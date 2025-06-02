# 🦷 Dental Caries & Periapical Lesion Detection using YOLOv8

This repository contains a complete pipeline for training a YOLOv8-based object detection model to identify **dental caries** and **periapical lesions** in dental radiographs.

---

## 📐 Model Architecture & Reasoning

We used the [Ultralytics YOLOv8](https://docs.ultralytics.com) object detection architecture:
- Variant: `YOLOv8m` (Medium)
- Chosen for its trade-off between accuracy and training efficiency
- Pretrained on COCO for better convergence on small medical dataset

---

## 🗂️ Dataset & Preprocessing

- Source: Roboflow project ([ADR version 7](https://universe.roboflow.com/new-workspace-oorwh/adr))
- Format: YOLOv8 (includes train/val/test split)
- Classes: 
  - `Dental Caries`
  - `Periapical Lesion`

### Preprocessing:
- Cropped out black borders from X-rays
- Applied **CLAHE** (Contrast Limited Adaptive Histogram Equalization)
- Resized to 640×640 with padding
- Converted to grayscale (1-channel input)

---

## ⚙️ Training Strategy & Hyperparameters

```yaml
Model:       YOLOv8m
Epochs:      30
Batch size:  16
Image size:  640x640
Patience:    15 (early stopping)
Pretrained:  True
Optimizer:   SGD
Losses:      Box + Class + DFL
