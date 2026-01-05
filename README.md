# E-Commerce Subscription Prediction Analysis

**Date:** March 2025
**Authors:** Xiaohui Ma，Aastha Amin, Lucas Chin, Doan Nguyen, Brady Snyder

---

## 📖 Project Overview 
This project aims to understand the key drivers behind customer decisions to subscribe to premium e-commerce memberships. Using a dataset of e-commerce customer behavior, we developed a predictive statistical model to estimate the likelihood of subscription based on demographics and activity metrics. 

The primary objective was to determine the most appropriate statistical model (GLM) to predict subscription status and interpret the influence of various predictors.

## 📊 Dataset
The analysis utilizes the `E_commerce_subscription.csv` dataset.
* **Target Variable:** `Subscribed_Premium` (Binary: 1 = Yes, 0 = No)
* **Key Predictors:**
    * **Demographics:** Age, Income Level 
    * **Behavioral:** Average Cart Size, Website Visit Frequency, Marketing Emails Opened 
    * **Categorical:** Device Type, Loyalty Program Member 
* **Data Distribution:** The dataset is highly unbalanced, with approximately 94.67% of users subscribed and only 5.33% not subscribed.

## ⚙️ Methodology 

### 1. Exploratory Data Analysis (EDA)
We examined distributions and relationships between predictors and the response variable. Key observations included:
* Higher income levels and marketing engagement correlate with higher subscription rates. 
* Interaction effects were observed between device types and subscription status. 

### 2. Model Selection & Statistical Modeling
We employed a **Generalized Linear Model (GLM)** with a binomial distribution and logit link function (Logistic Regression). 

* **Stepwise Regression:** We utilized backward elimination starting from a complex model (up to 3-way interactions). 
* **Model Comparison:** Models were evaluated based on **AIC** (Akaike Information Criterion) and **BIC** (Bayesian Information Criterion). The final model showed a lower AIC (109.28) compared to the main effects model (115.49).
* **Multicollinearity Check:** Calculated Variance Inflation Factors (VIF). All predictors in the final model (after centering) had VIF < 5, indicating no significant multicollinearity. 
* **Significance Testing:** Conducted a Global Wald Test (p-value = 0.04) to confirm the collective significance of the coefficients.

### 3. Final Model Equation
The final model includes quadratic terms and interaction terms:
$$logit(Y) = \beta_0 + \beta_1(Age) + \beta_2(Income) + \beta_3(CartSize) + \beta_4(VisitFreq) + \beta_5(VisitFreq^2) + \dots + Interactions$$
*(See full model specification in the report)* 

## 📈 Results 

| Metric | Value |
| :--- | :--- |
| **Accuracy** | **94.0%**  |
| **AUC** | **0.904**  |
| **Sensitivity (TPR)** | 0.989  |
| **Specificity (TNR)** | 0.062  |

**Key Findings:**
* **Marketing Effectiveness:** Opening marketing emails significantly increases the odds of subscription (+29% per email).
* **Engagement Paradox:** While simple visit frequency showed a negative coefficient, significant interaction and quadratic terms suggest a complex non-linear relationship. 
* **Demographics:** Age has a slight negative impact on subscription likelihood (-6.1% per year). 

## ⚠️ Limitations & Future Work 
* **Class Imbalance:** The model suffers from a low True Negative Rate (6.2%) due to the scarcity of non-subscriber data (only ~5% of the dataset).
* **Future Improvement:** Techniques like **oversampling (SMOTE)** or undersampling should be applied to balance the classes and improve specificity. 

## 🛠 Tools Used
* **Language:** R (inferred from GLM/Summary output style)
* **Libraries:** `stats` (glm), `car` (vif), `ggplot2` (visualization)

---
*For more details, please refer to the full [Project Report](Final_Report.pdf).*
