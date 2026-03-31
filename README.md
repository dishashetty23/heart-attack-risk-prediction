Heart Attack Risk Analysis & Prediction
 
## Project Overview
 
Cardiovascular disease is the **#1 cause of death globally**. This project builds a machine learning classification pipeline to predict individual heart attack risk *before* symptoms appear — shifting healthcare from reactive treatment to proactive prevention.

---
 
## Dataset
 
**8,763 patient records | 26 features | Binary target: Heart Attack Risk (1 = High, 0 = Low)**
 
Features span four categories: clinical markers (cholesterol, blood pressure, heart rate, BMI, triglycerides), lifestyle factors (smoking, alcohol, exercise, diet, sedentary hours), medical history (diabetes, family history, prior heart problems, medication use), and demographics (age, sex, income, country, continent).
 
📎 **Source:** [Heart Attack Risk Prediction Dataset — Kaggle](https://www.kaggle.com/datasets/iamsouravbanerjee/heart-attack-prediction-dataset)
 
---
 
## Exploratory Data Analysis
 
**Univariate Highlights**
- Age is broadly distributed (18–90) with no skew toward older patients
- Cholesterol (120–400 mg/dL) and BMI (17–40) show flat, uniform distributions
- Diet is evenly split across Healthy, Average, and Unhealthy (~2,900 each)
- Exercise Hours Per Week is uniformly spread (0–20 hrs) — no behavioral clustering
 
**Bivariate Analysis**
 
No individual feature crossed the p < 0.05 significance threshold against heart attack risk. Cholesterol came closest (p = 0.07), followed by Diabetes (p = 0.11) and Sleep Hours (p = 0.14) — pointing to the inherently multifactorial nature of heart attack risk.
 
---
 
## Model Workflow
 
1. **Data Collection & Definition** — 8,763 patient records across 26 clinical, lifestyle, and demographic features; target variable: Heart Attack Risk (binary)
2. **Exploratory Data Analysis** — Univariate statistics (distribution, skewness, kurtosis) + bivariate testing (t-tests for continuous features, chi-square for categorical) against the target variable
3. **Data Cleaning & Preprocessing** — Parsed blood pressure string into Systolic_BP and Diastolic_BP via SQL transformation; dropped Patient ID; converted binary columns to categorical; clipped outliers in Sedentary Hours, Triglycerides, and Exercise Hours Per Week
4. **Feature Selection** — Permutation Feature Importance run on top models to identify and exclude low-impact features; tested with and without top 10 excluded features
5. **Model Training** — Six classification algorithms compared: Logistic Regression, Averaged Perceptron, Neural Network, Decision Forest, Boosted Decision Tree, and Support Vector Machine
6. **Cross-Validation** — k=10 fold validation to confirm model stability and generalizability
7. **Hyperparameter Tuning** — Sweep across key parameters (max leaves, number of trees, learning rate, min samples per leaf) optimizing for Recall
8. **Final Evaluation** — Scored and evaluated on held-out test set; assessed via Accuracy, Recall, Precision, F1, AUC, and Confusion Matrix
 
---
 
## Modeling & Evaluation
 
Six classification algorithms were compared. **Decision Forest** and **Boosted Decision Tree** were selected based on the best balance of accuracy and recall — prioritized because missing a high-risk patient (false negative) carries far greater consequence than a false positive.
 
| Algorithm | Accuracy | Recall | F1 | AUC |
|---|---|---|---|---|
| Two-Class Decision Forest | 0.54 | 0.338 | 0.345 | 0.496 |
| Two-Class Boosted Decision Tree | 0.61 | 0.143 | 0.209 | 0.509 |
 
Both models were further validated with cross-validation (k=10) and hyperparameter tuning, with accuracy stabilizing at ~61% and recall peaking at ~34%.
 
---
 
## Final Model Performance
 
| Metric | Value |
|---|---|
| **Best Accuracy** | ~61% |
| **Best Recall** | ~34% |
| **AUC** | ~0.51 |
| **Algorithm** | Two-Class Boosted Decision Tree |
 
---
 
## Key Findings
 
- No single feature was statistically significant (p < 0.05), confirming heart attack risk is inherently multivariable
- **Cholesterol** had the weakest p-value (0.07) — the strongest individual signal in the dataset
- Conventional risk factors like BMI, sedentary behavior, and age showed no significant standalone association
- Model accuracy plateaued at ~61% across all tuning strategies, suggesting dataset size and balance are the primary limiting factors
- A larger, more balanced dataset and longitudinal patient data would likely yield meaningful improvement
 
---
 
## Tech Stack
 
| | Tool |
|---|---|
| **ML Platform** | Azure Machine Learning Studio (Designer) |
| **Algorithms** | Boosted Decision Tree, Decision Forest, Logistic Regression, Neural Network, SVM |
| **Pipeline Steps** | SQL Transformation, Edit Metadata, Clip Values, Cross-Validation, Tune Model Hyperparameters, Permutation Feature Importance |
| **EDA** | Excel |
 
---

## Team
 
| Name | Email |
|------|-------|
| Disha Shetty | dishas23@uw.edu |
| Jaza Lodhi | jazal@uw.edu |
| Akshit Mahajan | akshit98@uw.edu |
| Orlantha Coleman | ocoleman@uw.edu |
| Shubhanshi Jain | shubh075@uw.edu |
 
---
 
## Disclaimer
 
This project is intended for **academic and educational purposes only**. The model is not validated for clinical use and should not be used to make real medical decisions. Always consult a qualified healthcare professional for medical advice.
