# Kidney CT Image Classification

**Biomedical Engineering | University of Sydney | 2026**

Multi-classifier comparison for four-class kidney CT classification (Normal, Cyst, Stone, Tumour) on the CT-KIDNEY-DATASET, evaluating classical machine learning approaches against deep learning via transfer learning.

## Overview

Standard CT kidney classification pipelines often rely on deep learning without benchmarking against classical approaches. This project evaluates both families of methods side-by-side on identical data, using an ablation-driven design process for the CNN architecture.

## Methods

| Model | Features | Approach |
|---|---|---|
| SVM-RBF | HOG + LBP | Classical ML |
| SVM-Linear | HOG + LBP | Classical ML |
| Random Forest | HOG + LBP | Classical ML |
| ResNet50 CNN | Raw image | Transfer learning + ablation |

**Ablation study covered:** backbone selection, classifier head architecture, unfreezing depth, and augmentation policy.

## Results

| Model | Test Accuracy | Notes |
|---|---|---|
| ResNet50 CNN | 1.0000 | Resolved Cyst–Tumour confusion |
| SVM-RBF | 0.9992 | Best classical model |
| SVM-Linear | ~0.999 | |
| Random Forest | ~0.999 | |

**Note on data leakage:** Results are evaluated at image level. Within-patient data leakage arising from image-level splitting likely inflates reported performance. True clinical generalisation is expected to be lower. Future work should prioritise patient-level cross-validation and Grad-CAM explainability for clinical interpretability.

## Dataset

[CT-KIDNEY-DATASET](https://www.kaggle.com/datasets/nazmul0087/ct-kidney-dataset-normal-cyst-tumor-and-stone) — 5,966-image subset across 4 classes.

## Tech Stack

`Python` `scikit-learn` `PyTorch` / `TensorFlow` `ResNet50` `HOG` `LBP` `Jupyter`

## Files

- `kidney_classification.ipynb` — Full pipeline: preprocessing, feature extraction, model training, evaluation
- `report.pdf` — Full project report

## Key Takeaways

- Classical ML with hand-crafted texture features (HOG+LBP) reached near-identical accuracy to deep learning at a fraction of the computational cost
- Ablation-driven CNN design produced counterintuitive results — augmentation and head depth empirically contradicted common defaults
- Critical evaluation of data leakage demonstrates awareness of real-world clinical deployment constraints
