# employee-performance-outcomes-and-employee-segmentation-using-clustering-and-classification-.
#  Employee Attrition & Performance Prediction
### High Performer Classification and Employee Clustering (Machine Learning Project)

This repository contains a machine learning project focused on predicting **employee performance outcomes** and exploring **employee segmentation** using clustering techniques.  
The project demonstrates a complete ML workflow—from preprocessing and feature engineering to model evaluation and deployment scaffolding.

---

##  Project Overview

The primary objective of this project is to **classify employees as High Performers** based on HR-related attributes and to explore whether **natural groupings** exist among employees using clustering techniques.

The project is implemented in **Python (Jupyter Notebook)** using a real-world HR analytics dataset.

---

## Project Goals

- Create a binary target variable (**HighPerformer**) from employee performance ratings  
- Train a supervised classification model to predict high-performing employees  
- Apply dimensionality reduction for visualization  
- Perform unsupervised clustering to discover employee segments  
- Lay the groundwork for model deployment using a web interface

---

##  Dataset Overview

- **Dataset:** `WA_Fn-UseC_-HR-Employee-Attrition.csv`
- **Total Records:** 1,470 employees
- **Total Features:** 35
- **Missing Values:** None

### Key Statistics

| Metric | Value |
|------|------|
| Total Employees | 1,470 |
| Average Age | 36.92 |
| Average Years at Company | 7.01 |
| High Performers | ~15.4% |

### Feature Composition
- **Numerical Features:** 26  
- **Categorical Features:** 9  

---

##  Feature Engineering

### Target Variable: `HighPerformer`

A binary target variable was created:

- `1` → PerformanceRating > 3  
- `0` → PerformanceRating ≤ 3  

---

### Selected Features

| Feature Type | Feature Name | Description |
|-------------|-------------|-------------|
| Numerical | YearsAtCompany | Employee tenure |
| Numerical | TrainingTimesLastYear | Trainings completed last year |
| Numerical | PerformanceRating | Performance score (1–4) |
| Categorical | Department | Employee department |
| Categorical | JobRole | Employee job role |
| Categorical | Education | Education level (ordinal) |

---

##  Data Preprocessing

- One-hot encoding applied to categorical variables  
- `drop_first=True` used to reduce multicollinearity  
- Final dataset after encoding:
  - **17 numerical features**

---

##  Model Training & Evaluation

### Model
- **Support Vector Classifier (SVC)**
- **Kernel:** Linear

### Train–Test Split
- **Training:** 80%  
- **Testing:** 20%  
- **Random State:** 42  

---

###  Model Performance

| Metric | Score |
|------|------|
| Accuracy | 1.00 |
| Precision | 1.00 |
| Recall | 1.00 |
| F1-Score | 1.00 |

#### Confusion Matrix

| Actual / Predicted | 0 | 1 |
|-------------------|---|---|
| Actual 0 | 251 | 0 |
| Actual 1 | 0 | 43 |

>  **Important Note (Data Leakage)**  
> The perfect performance is unrealistic and occurs due to **data leakage**.  
> `PerformanceRating` was used both to **create the target variable** and as a **model input feature**, which must be avoided in real-world scenarios.

---

## Dimensionality Reduction

### Principal Component Analysis (PCA)

- Reduced feature space from 17 dimensions to **2 components**
- Used for visualization and exploratory analysis
- PCA visualization shows strong class separation

---

##  Unsupervised Learning

### K-Means Clustering

- **Number of clusters:** 3  
- Applied to encoded employee features  

The clusters suggest distinct employee groups. Further profiling is required to interpret cluster characteristics and their relationship with performance and attrition.

---

## 🚀 Deployment (Gradio – Placeholder)

A **Gradio UI scaffold** is included for future deployment.

```python
prediction = "No" if years_at_company > 5 else "Yes"
