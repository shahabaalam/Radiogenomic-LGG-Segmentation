# A Deep Learning Approach to Radiogenomic Characterization of Lower-Grade Gliomas Through FLAIR Image Segmentation

This repository contains code for segmenting FLAIR abnormalities in lower-grade glioma (LGG) MRI images using a U-Net based deep learning architecture. The goal is to facilitate radiogenomic analyses by automatically extracting tumor shape features that may correlate with genomic subtypes and clinical outcomes.

---

## Table of Contents

- [Introduction](#introduction)
- [Dataset](#dataset)
- [Model Architecture](#model-architecture)
- [Installation](#installation)
- [Model Evaluation](#model-evaluation)
- [License](#license)

---

## Introduction

This project implements a deep learning pipeline that includes:

- Data loading and preprocessing with augmentation.
- U-Net architecture for semantic segmentation of FLAIR MRI images.
- Training, evaluation, and visualization of segmentation results.
- Post-processing to extract radiogenomic features from the segmented tumor regions.

By combining imaging features with genomic data, this work aims to aid in the radiogenomic characterization of lower-grade gliomas.

---

## Dataset

**LGG Segmentation Dataset**

The dataset consists of brain MRI images (FLAIR sequences) along with manually annotated segmentation masks of FLAIR abnormalities. Key details include:

- **Source:**  
  Images were obtained from The Cancer Imaging Archive (TCIA).

- **Patient Cohort:**  
  Data from 110 patients from The Cancer Genome Atlas (TCGA) lower-grade glioma collection, with available genomic cluster data.

- **Associated Publications:**
  - _Buda, M., Saha, A., & Mazurowski, M. A. (2019). Association of genomic subtypes of lower-grade gliomas with shape features automatically extracted by a deep learning algorithm. Computers in Biology and Medicine._
  - _Mazurowski, M. A., Clark, K., Czarnek, N. M., Shamsesfandabadi, P., Peters, K. B., & Saha, A. (2017). Radiogenomics of lower-grade glioma: algorithmically-assessed tumor shape is associated with tumor genomic subtypes and patient outcomes in a multi-institutional study with The Cancer Genome Atlas data. Journal of Neuro-Oncology._

---

## Model Architecture

The core of this project is based on a U-Net architecture which includes:

- **Encoder:** Convolutional blocks with ReLU activations, batch normalization, and max pooling.
- **Bottleneck:** A deep convolutional layer block to capture high-level features.
- **Decoder:** Transposed convolutions with skip connections to recover spatial resolution.
- **Output:** A 1x1 convolution with sigmoid activation to generate binary segmentation masks.

Loss function and metrics include:

- **Dice Loss:** To optimize segmentation overlap.
- **Dice Coefficient & IoU:** For evaluating segmentation performance.

---

## Installation

1. **Clone the repository:**

   ```bash
   git clone https://github.com/shahabaalam/Radiogenomic-LGG-Segmentation.git
   cd Radiogenomic-LGG-Segmentation
   ```

---

## **Model Evaluation**

The trained U-Net model was evaluated on the train, validation, and test sets with the following results:

### **Training Metrics**

- **Train Loss:** -0.9044
- **Train Accuracy:** 99.81%
- **Train IoU (Intersection over Union):** 82.76%
- **Train Dice Coefficient:** 90.44%

### **Validation Metrics**

- **Valid Loss:** -0.8844
- **Valid Accuracy:** 99.79%
- **Valid IoU (Intersection over Union):** 79.42%
- **Valid Dice Coefficient:** 88.43%

### **Test Metrics**

- **Test Loss:** -0.9050
- **Test Accuracy:** 99.79%
- **Test IoU (Intersection over Union):** 82.76%
- **Test Dice Coefficient:** 90.50%

### **Confusion Matrix**

```plaintext
[[25443941    27487]
 [   39067   245153]]
```

### **Classification Report**

| Class      | Precision | Recall | F1-Score | Support    |
| ---------- | --------- | ------ | -------- | ---------- |
| Background | 1.00      | 1.00   | 1.00     | 25,471,428 |
| Object     | 0.90      | 0.86   | 0.88     | 284,220    |

- **Overall Accuracy:** 100%
- **Macro Average:**
  - Precision: 0.95
  - Recall: 0.93
  - F1-Score: 0.94
- **Weighted Average:**
  - Precision: 1.00
  - Recall: 1.00
  - F1-Score: 1.00

---

## License

This project is licensed under the [MIT License](LICENSE).

---
