# Odontogenic Pathology Classification from Microscopic Images

This repository presents a complete computational pipeline for the preprocessing, outlier removal, and deep learning–based classification of microscopic images corresponding to odontogenic pathologies.

The study focuses on the following five classes:
- Ameloblastoma (A)
- Dentigerous Cyst (D)
- Keratocyst Odontogenic Cyst (K)
- Orthokeratinized Odontogenic Cyst (O)
- Dental Follicle (DF)

The proposed methodology ensures geometric consistency in pattern extraction, improves data quality through outlier removal, and achieves robust classification using transfer learning.

---

## Repository Structure

```
├── GORLIN_image_preprocessing.ipynb
├── Cores_A_D_K_S_O.ipynb
├── Clasificación_A_D_K_O_D.ipynb
└── README.md
```

---

## 1. Image Preprocessing and Pattern Extraction  
**Notebook:** `GORLIN_image_preprocessing.ipynb`

This notebook implements a geometric preprocessing pipeline designed to extract a consistent and well-defined region of interest (ROI) from microscopic images.

### Objective
To ensure consistent pattern extraction and reduce variability caused by differences in image scale, background information, and acquisition conditions.

### Methodology
The preprocessing pipeline consists of the following steps:

1. Image resizing to 25% of the original resolution using bilinear interpolation to reduce computational cost while preserving the main geometric structures.
2. Conversion to grayscale followed by Gaussian filtering to suppress noise and small intensity fluctuations.
3. Edge detection using the Canny algorithm.
4. Detection of circular structures via the Hough Circle Transform.
5. Selection of the most prominent circle (largest radius) corresponding to the main anatomical structure.
6. Computation and extraction of a square region inscribed within the detected circle.

The extracted square region defines the final pattern used for subsequent analysis.

---

## 2. Outlier Removal Using Principal Component Analysis (PCA)  
**Notebook:** `Cores_A_D_K_S_O.ipynb`

This notebook performs outlier detection and removal to improve dataset consistency and robustness.

### Objective
To remove samples that significantly deviate from the main data distribution and may negatively affect model training.

### Methodology
- Feature vectors derived from the preprocessed images are projected into a low-dimensional PCA space.
- Samples located far from the central distribution are identified as outliers.
- Only inlier samples are retained for subsequent stages.

---

## 3. Deep Learning Classification  
**Notebook:** `Clasificación_A_D_K_O_D.ipynb`

This notebook implements the final classification stage using a convolutional neural network.

### Model
- DenseNet121 architecture
- Pretrained on ImageNet
- Fine-tuned for multi-class classification of odontogenic pathologies

### Key Characteristics
- Transfer learning to exploit generic visual features
- End-to-end training on standardized and cleaned image data
- Multi-class prediction across the five pathological categories

---

## Requirements

- Python 3.8 or later
- NumPy
- OpenCV
- scikit-learn
- TensorFlow / Keras
- Matplotlib

---

## Citation
If you use this code in your research, please cite the corresponding publication.

---

## Contact
Carlos Acuña Ocampo
carlos.acunaocampo@tec.mx
