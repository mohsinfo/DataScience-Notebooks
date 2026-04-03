# 🫀 Arrhythmia Classification with Machine Learning

> **Can machine learning reliably detect irregular heartbeats — and reduce the burden on manual ECG diagnosis?**

This project builds a multi-class classification model to detect arrhythmia from physiological and ECG measurements, using the UCI Arrhythmia dataset. The focus is on handling extreme class imbalance and high dimensionality — two of the hardest real-world challenges in clinical ML.

---

## 📊 Key Results

| Metric | Value |
|---|---|
| Final model | **Random Forest** (tuned via GridSearchCV) |
| Test set accuracy | **81%** |
| Cross-validation mean accuracy | **82.27%** |
| Classes classified | 16 arrhythmia types |
| Features in raw dataset | 279 |
| Features selected | Top 20 |
| Best hyperparameters | `max_depth=20`, `min_samples_split=5`, `n_estimators=100` |

> **Clinical impact:** An 82% cross-validated accuracy across 16 arrhythmia types from ECG data can help triage patients faster, flag high-risk cases for cardiologist review, and reduce time spent on routine normal readings.

---

## 🔍 The Problem

Manual ECG interpretation is time-intensive and requires specialist expertise. With 16 distinct arrhythmia classes and a dataset of only 452 samples across 279 features, this project tackles three compounding challenges simultaneously:

- **Extreme high dimensionality** — 279 features, 452 samples (p >> n)
- **Severe class imbalance** — some arrhythmia types have very few examples
- **Multi-class classification** — not just "normal vs abnormal" but 16 distinct conditions

---

## 🔄 Pipeline Overview

```
UCI Arrhythmia dataset (452 samples, 279 features, 16 classes)
       ↓
  Feature selection — top 20 most informative features
  (QRS duration, Heart rate, ECG_91, ECG_100, ECG_112... and more)
       ↓
  Class balancing — Random Oversampling + SMOTE
       ↓
  Baseline model — Logistic Regression
       ↓
  Model selection — Random Forest
       ↓
  Hyperparameter tuning — GridSearchCV
  (Best: max_depth=20, min_samples_split=5, n_estimators=100)
       ↓
  5-fold cross-validation — Mean accuracy: 82.27%
       ↓
  Test set evaluation — 81% accuracy
```

---

## 🏆 Top 20 Selected Features

| Feature | Description |
|---|---|
| QRS duration | Duration of the QRS complex |
| Heart rate | Beats per minute |
| ECG_91, ECG_100, ECG_112 | ECG amplitude measurements |
| ECG_113, ECG_114, ECG_124 | ECG amplitude measurements |
| ECG_137, ECG_149, ECG_197 | ECG amplitude measurements |
| ECG_220, ECG_228, ECG_230 | ECG amplitude measurements |
| ECG_238, ECG_240, ECG_241 | ECG amplitude measurements |
| ECG_248, ECG_251 | ECG amplitude measurements |

---

## 💡 Key Findings

- **Feature reduction is critical** — dropping from 279 to top 20 features reduced noise significantly; most ECG signal is concentrated in a small subset of measurements
- **SMOTE outperformed random oversampling** for minority arrhythmia classes — generating synthetic samples that better represent rare class boundaries
- **Cross-validation confirms generalizability** — 82.27% mean accuracy across 5 folds, showing the model isn't just overfitting to the test set
- **GridSearchCV found the right depth** — `max_depth=20` balances complexity and overfitting for this dataset size

---

## 📋 Classification Report Summary

The model achieves balanced precision and recall across classes, with macro and weighted averages both near 81%, confirming the model handles minority arrhythmia types reasonably well — not just the common ones.

---

## 🗂️ Dataset

**Source:** [UCI Arrhythmia Dataset](https://archive.ics.uci.edu/dataset/5/arrhythmia)  
452 patient records · 279 features · 16 arrhythmia classes · labeled for supervised learning

Features include: heart rate, QRS duration, PR interval, T-wave measurements, and other cardiological ECG attributes.

---

## 📁 Repository Structure

```
Arrhythmia-Detection/
├── Arrhythmia Data.ipynb   # Full pipeline: EDA → feature selection → SMOTE → GridSearchCV → evaluation
├── arrhythmia.data         # Raw dataset
├── arrhythmia.names        # Feature descriptions
└── README.md
```

---

## 🛠️ Tech Stack

`Python` `pandas` `scikit-learn` `imbalanced-learn` `SMOTE` `GridSearchCV` `matplotlib` `seaborn`

---

## 🚀 Run Locally

```bash
pip install numpy pandas scikit-learn imbalanced-learn matplotlib seaborn jupyter
jupyter notebook "Arrhythmia Data.ipynb"
```

---

## 🔮 Future Work

- Experiment with deep learning (1D-CNN) on raw ECG signal data for improved pattern detection
- Extend to real-time ECG stream classification using a lightweight deployed model
- Incorporate explainability (SHAP values) to surface which features drive each arrhythmia prediction
