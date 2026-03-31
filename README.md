# Heart Attack Risk Analysis & Prediction
 
## Project Overview
 
Cardiovascular disease is the **#1 cause of death globally**. This project builds a machine learning classification pipeline to predict individual heart attack risk *before* symptoms appear, shifting healthcare from reactive treatment to proactive prevention.

## Dataset
 
**8,763 patient records | 26 features | Binary target: Heart Attack Risk (1 = High, 0 = Low)**
 
Features span four categories: clinical markers (cholesterol, blood pressure, heart rate, BMI, triglycerides), lifestyle factors (smoking, alcohol, exercise, diet, sedentary hours), medical history (diabetes, family history, prior heart problems, medication use), and demographics (age, sex, income, country, continent).
 
📎 **Source:** [Heart Attack Risk Prediction Dataset — Kaggle](https://www.kaggle.com/datasets/iamsouravbanerjee/heart-attack-prediction-dataset)
 
## Exploratory Data Analysis
 
**Univariate Highlights**
- Age is broadly distributed (18 to 90) with no skew toward older patients
- Cholesterol (120 to 400 mg/dL) and BMI (17 to 40) show flat, uniform distributions
- Diet is evenly split across Healthy, Average, and Unhealthy (~2,900 each)
- Exercise Hours Per Week is uniformly spread (0 to 20 hrs) with no behavioral clustering
 
**Bivariate Analysis**
 
No individual feature crossed the p < 0.05 significance threshold against heart attack risk. Cholesterol came closest (p = 0.07), followed by Diabetes (p = 0.11) and Sleep Hours (p = 0.14), pointing to the inherently multifactorial nature of heart attack risk.
 
## Model Workflow
 
1. **Data Collection and Definition:** 8,763 patient records across 26 clinical, lifestyle, and demographic features; target variable: Heart Attack Risk (binary)
2. **Exploratory Data Analysis:** Univariate statistics (distribution, skewness, kurtosis) and bivariate testing (t-tests for continuous features, chi-square for categorical) against the target variable
3. **Data Cleaning and Preprocessing:** Parsed blood pressure string into Systolic_BP and Diastolic_BP via SQL transformation; dropped Patient ID; converted binary columns to categorical; clipped outliers in Sedentary Hours, Triglycerides, and Exercise Hours Per Week
4. **Feature Selection:** Permutation Feature Importance run on top models to identify and exclude low-impact features; tested with and without top 10 excluded features
5. **Model Training:** Six classification algorithms compared: Logistic Regression, Averaged Perceptron, Neural Network, Decision Forest, Boosted Decision Tree, and Support Vector Machine
6. **Cross-Validation:** k=10 fold validation to confirm model stability and generalizability
7. **Hyperparameter Tuning:** across key parameters including number of trees, max depth, learning rate, and minimum samples per leaf
8. **Final Evaluation:** Scored and evaluated on held-out test set; assessed via Accuracy, Recall, Precision, F1, AUC, and Confusion Matrix
 
## Modeling & Evaluation
 
Six classification algorithms were compared including Logistic Regression, Averaged Perceptron, Neural Network, Decision Forest, Boosted Decision Tree, and Support Vector Machine. **Two-Class Boosted Decision Tree** was selected as the final model as it delivered the best overall performance across accuracy, precision, F1 score, and AUC.
 
| Algorithm | Accuracy | Recall | F1 | AUC |
|---|---|---|---|---|
| Two-Class Boosted Decision Tree | 0.61 | 0.143 | 0.209 | 0.509 |

The model was further evaluated using 10-fold cross-validation and hyperparameter tuning to assess stability and generalization.
 
## Final Model Performance
 
| Metric | Value |
|---|---|
| **Accuracy** | ~61% |
| **Recall** | ~14% |
| **AUC** | ~0.51 |
| **Algorithm** | Two-Class Boosted Decision Tree |
 
The model highlights the challenge of predicting complex health outcomes using static features and emphasizes the need for richer longitudinal and clinical data.
 
## Key Findings
 
- No individual feature showed statistical significance at p < 0.05, suggesting that heart attack risk is influenced by multiple interacting factors rather than any single variable
- **Cholesterol** had the lowest p-value (0.07), making it the strongest individual signal in the dataset
- Conventional risk factors like BMI, sedentary behavior, and age showed no significant standalone association
- Model accuracy plateaued at ~61% across all tuning strategies, suggesting dataset size and balance are the primary limiting factors
- A larger, more balanced dataset and longitudinal patient data would likely yield meaningful improvement
 
## Tech Stack
 
| | Tool |
|---|---|
| **ML Platform** | Azure Machine Learning Studio (Designer) |
| **Algorithms** | Two-Class Boosted Decision Tree, Decision Forest, Logistic Regression, Neural Network, SVM |
| **Pipeline Steps** | SQL Transformation, Edit Metadata, Clip Values, Cross-Validation, Tune Model Hyperparameters, Permutation Feature Importance |
| **EDA** | Excel |
 
## Team
 
| Name | Email |
|------|-------|
| Disha Shetty | dishas23@uw.edu |
| Jaza Lodhi | jazal@uw.edu |
| Akshit Mahajan | akshit98@uw.edu |
| Orlantha Coleman | ocoleman@uw.edu |
| Shubhanshi Jain | shubh075@uw.edu |
 
## Disclaimer
 
This project is intended for **academic and educational purposes only**. The model is not validated for clinical use and should not be used to make real medical decisions. Always consult a qualified healthcare professional for medical advice.

## License
 
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
 
© 2026 Disha Shetty, Jaza Lodhi, Akshit Mahajan, Orlantha Coleman, Shubhanshi Jain
