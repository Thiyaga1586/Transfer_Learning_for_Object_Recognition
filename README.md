# Transfer Learning for Object Recognition (Caltech-101)

## Overview

This project implements transfer learning for multi-class object classification using the Caltech-101 dataset. Two pretrained convolutional neural networks **MobileNetV2** and **ResNet50** are evaluated under frozen feature extraction and fine-tuning strategies.

The objective is to analyze performance trade-offs between lightweight and deep architectures while following a complete end-to-end deep learning pipeline.

---

## Dataset

- **Dataset:** Caltech-101  
- **Categories:** 101 object classes  
- **Images:** ~8,600  
- **Split:** 80% training / 20% validation  
- **Image Size:** 224 × 224  

---

## Methodology

### Models Used

- **MobileNetV2** (ImageNet pretrained)  
- **ResNet50** (ImageNet pretrained)  

### Training Strategies

#### 1. Frozen Feature Extraction
- All pretrained layers frozen  
- Only classification head trained  

#### 2. Fine-Tuning
- Early layers frozen  
- Deeper layers unfrozen  
- Lower learning rate applied  

### Configuration

- **Optimizer:** Adam  
- **Loss Function:** Sparse Categorical Crossentropy  
- **Regularization:** Dropout  
- **Callbacks:** EarlyStopping, ReduceLROnPlateau, ModelCheckpoint  

---

## Results (Frozen Mode)

| Model        | Validation Accuracy | Validation Loss |
|--------------|--------------------|-----------------|
| MobileNetV2  | 93.87%             | 0.212           |
| ResNet50     | 94.14%             | 0.217           |

### Observations

- Both models achieve strong generalization (>93%).  
- ResNet50 provides slightly higher accuracy.  
- MobileNetV2 trains significantly faster.  

---

## Accuracy Comparison Plot

![Accuracy Comparison](Images/accuracy_comparison_graph.png)

---

## Analysis

- Transfer learning is highly effective for small datasets.  
- Frozen models already provide strong performance due to ImageNet feature reuse.  
- Fine-tuning improves task-specific adaptation.  
- MobileNetV2 offers better computational efficiency.  
- ResNet50 offers marginally better accuracy.  

---

## Pipeline

Dataset Preparation → Pretrained Model Loading → Feature Extraction → Fine-Tuning → Evaluation  

---

## Conclusion

Pretrained CNNs transfer effectively to Caltech-101. ResNet50 slightly outperforms MobileNetV2 in accuracy, while MobileNetV2 provides superior efficiency. The project highlights the trade-off between performance and computational cost in practical computer vision systems.
