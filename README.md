# 🧬 Breast Cancer Tumor Classification  
**By Jasmine Justin & Katharina Dowlin**  
**Dataset**: [Breast Cancer Wisconsin (Diagnostic) Dataset – Kaggle](https://www.kaggle.com/datasets/uciml/breast-cancer-wisconsin-data)

---

## 📌 Project Overview

This project investigates whether machine learning can accurately classify breast tumors as **benign** or **malignant** based on physical characteristics extracted from imaging. The goal is to reduce reliance on invasive diagnostics by using predictive models that are efficient, interpretable, and aligned with clinical findings.

We approached this binary classification task using the following machine learning models:

- Logistic Regression  
- Random Forest  
- Support Vector Machine (SVM)  
- Boosting algorithms (XGBoost, LightGBM, CatBoost)

---

## 💡 Motivation

Research into tumor classification helps improve early detection and reduce unnecessary interventions. Although benign tumors are non-cancerous, some are linked to higher risk of developing breast cancer. Additionally, overdiagnosis and overtreatment are significant concerns in mammography.

AI and machine learning have shown promise in surpassing traditional methods in diagnostic accuracy. Our project aligns with ongoing research exploring AI’s role in clinical diagnostics.

---

## 📊 Dataset Description

- **Source**: University of Wisconsin
- **Type**: Diagnostic tabular data
- **Classes**: `Benign`, `Malignant`
- **Features**:  
  - 30 numerical features (e.g., radius, perimeter, texture, area, smoothness)

We applied supervised learning using these features to predict tumor classification.

---

## 🧼 Data Preprocessing & Feature Engineering

### ✔ Cleaning
- Removed missing/null values from the dataset.

### 📈 Correlation & Multicollinearity
- Found 13+ features with correlation > 0.85.
- Calculated VIF (Variance Inflation Factor) for each feature.
  - Example: `radius_mean` had a VIF of 3806.

### 🔍 Feature Reduction
- Iteratively removed features with highest VIF until all VIFs < 5.
- Final model used **13 features** describing tumor size, shape, texture, and symmetry.

---

## 🤖 Models & Results

All models were trained on an 80/20 train-test split. Evaluation metrics include:

- Accuracy
- Precision
- Recall
- F1 Score
- ROC-AUC
- Confusion Matrix

---

### 📈 Logistic Regression

- **Accuracy**: 94.7%  
- **Recall (Malignant)**: 0.91  
- **Precision (Malignant)**: 0.95  
- **F1 Score**: 0.93  
- Strong performance with minimal preprocessing. Great balance of simplicity and accuracy.

---

### 🌲 Random Forest

- **Top Features**:
  - `area_worst` (35.6%)
  - `perimeter_se`, `symmetry_worst`, `concavity_se`, `texture_mean`
- **Initial Overfitting**:
  - Solved by limiting tree depth to 5, using 100 estimators, and setting min samples for splits.
- **Clinically Aligned**:
  - Malignant tumors tend to be larger and more irregular.

---

### 💻 Support Vector Machine (SVM)

- **Accuracy**: 95%  
- **Precision (Malignant)**: 1.00  
- **Recall (Malignant)**: 0.86  
- **F1 Score (Malignant)**: 0.92  
- Excellent precision, slightly lower recall for malignant cases.

---

### 🚀 Boosting Models

#### ✅ XGBoost
- **Accuracy**: 98%  
- **Precision (Malignant)**: 1.00  
- **Top Features**:  
  - `area_worst`, `texture_mean`, `symmetry_worst`, `concavity_se`

#### 🔦 LightGBM
- **Accuracy**: 97%

#### 🐈 CatBoost
- **Accuracy**: 96%

All models consistently ranked **tumor size and symmetry** as top predictors of malignancy.

---

## 📊 Visualizations

### 📉 ROC Curves
All models achieved **AUC = 0.99**, indicating near-perfect class separation.

### 🔍 Confusion Matrices

| Model        | Misclassified Malignant | Misclassified Benign |
|--------------|--------------------------|-----------------------|
| XGBoost      | 2                        | 0                     |
| LightGBM     | 3                        | 0                     |
| Random Forest| 3                        | 0                     |
| Logistic Reg | ~4                       | ~2                    |
| SVM          | 6                        | 0                     |

---

## 🧠 Discussion

Our initial hypothesis was that features like **smoothness**, **area**, and **texture** would be most predictive. Surprisingly, **shape-based features** (e.g., worst area, perimeter, concavity) were more influential.

These findings align with clinical knowledge that malignant tumors are more irregular and complex than benign ones.

---

## ✅ Conclusion

- **XGBoost** was the best-performing model with **98% accuracy** and **perfect precision**.
- All models achieved **AUC scores of 0.99**.
- Results validate the role of machine learning in enhancing diagnostic accuracy in breast cancer detection.

---

## 🔭 Future Work

- Incorporate additional patient data (age, genetic markers, family history).
- Combine models into ensembles to improve robustness.
- Validate models on **real-world noisy data**.
- Extend project to use imaging data directly via deep learning (CNNs, etc.).

---

## 📚 References

1. Wang, X., et al. (2021). [A Deep Learning-Based Radiomics Model for Breast Lesion Classification](https://www.frontiersin.org/articles/10.3389/fonc.2021.629321/full), *Frontiers in Oncology*.  
2. Akram, M., et al. (2023). [A Computer-Aided Diagnosis System for Breast Cancer Classification](https://www.mdpi.com/2077-0383/12/4/1582), *Journal of Clinical Medicine*.  
3. Sasso, S. (2023). *Benign Breast Disease Can Double Your Risk of Breast Cancer*, Health.com.  
4. Oaklander, M. (2015). *Many DCIS Breast Cancer Patients Don’t Need Treatment*, TIME.  
5. Molteni, M. (2021). *With Breast Cancer, the Best Treatment May Be No Treatment*, WIRED.

---

> 💡 *If you'd like to contribute, feel free to fork this repository and submit a pull request!*

