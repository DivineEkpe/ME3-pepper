# ME3 — Pepper Healthy vs Pepper Bacterial Spot Classifier

## Overview

This project trains a binary image classifier to distinguish **Healthy** bell pepper
leaves from leaves affected by **Bacterial Spot** disease using **transfer learning**
with MobileNetV2 pre-trained on ImageNet. The model is built with TensorFlow / Keras
and follows a two-phase training strategy: a feature-extraction phase (frozen base)
followed by a fine-tuning phase (top 30 layers unfrozen). The dataset ships as flat
class folders with no pre-made splits, so the notebook builds a stratified
70 / 15 / 15 train / val / test split at runtime.

---

## Running the App

```bash
cd ME3
streamlit run app.py
```

The app will open automatically at **http://localhost:8501**

**Streamlit Cloud URL:** **

---

## Dataset

A brief description of the dataset source is provided in [`dataset/README.md`](dataset/README.md).

**Dataset:** Plant Disease Classification (PlantVillage) — Kaggle  
**Classes:** `Healthy`, `Bacterial_Spot`  
**Split strategy:** 70% train · 15% val · 15% test (built at runtime)

---

## Environment Setup

### Requirements

Python **3.12** is recommended. All dependencies are pinned in [`requirements.txt`](requirements.txt).

### Install locally

```bash
# 1. Create and activate a virtual environment
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate

# 2. Install dependencies
pip install -r requirements.txt
```

### Key packages

| Package | Version | Purpose |
|---|---|---|
| `tensorflow` | 2.19.0 | Model training |
| `keras` | 3.15.0 | High-level API |
| `scikit-learn` | 1.8.0 | Evaluation metrics |
| `matplotlib` | 3.10.0 | Plotting |
| `seaborn` | 0.13.2 | Confusion matrix heatmap |
| `streamlit` | 1.60.0 | Web UI |

> **Note:** For faster training, use Google Colab with a T4 GPU runtime
> (`Runtime → Change runtime type → T4 GPU`).

---

## Project Structure

```
ME3/
├── dataset/
│   └── README.md          # Dataset source description
├── model/                 # Saved .keras model files
├── notebooks/
│   └── ME3.ipynb          # Full training pipeline
├── results/               # Plots, confusion matrices, learning curves
├── requirements.txt
├── CONTRIBUTORS.md
└── README.md              # This file
```

---

## Challenges & Solutions

| Challenge | Solution / Notes |
|---|---|
| No pre-made train/val/test splits | Built a stratified 70/15/15 split at runtime using `shutil.copy2` |
| Folder names use triple underscores (`Pepper__bell___healthy`) | Used substring matching (`'healthy' in base`, `'bacterial' in base`) instead of exact name comparison |
| Dataset contains many other plant disease classes | Keyword matching isolates only the two pepper classes |
| Subtle visual difference between healthy and early bacterial spot | Fine-tuning improves sensitivity to leaf texture and spot patterns |

---

## Possible Improvements

- Experiment with **EfficientNetB0** as an alternative base model
- Expand to multi-class plant disease detection across all PlantVillage classes
- Export the model to **TensorFlow Lite** for field use on mobile devices

---

## Results

> Full learning curves and confusion matrices are saved in `results/`.

## Contributors

See [CONTRIBUTORS.md](CONTRIBUTORS.md) for the full list of names, GitHub usernames, and registration numbers.

---
