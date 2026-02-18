# 🩺 Medical Cost Analysis: Advanced Statistical Modeling

## 📌 Project Overview
This project focuses on modeling annual medical insurance costs using the **Medical Cost Personal Dataset**.The objective was to move beyond simple prediction and perform a deep econometric analysis, identifying where standard linear models fail and implementing advanced **Generalized Linear Models (GLM)** to handle non-normal data distribution.

---

## 🛠️ Data Engineering & Quality Control
Before modeling, I implemented a rigorous data preparation pipeline to ensure the reliability of the results:
* **Outlier Management:** Identified 139 outliers using Boxplot analysis.
* **Influential Observations:** Used **Cook’s Distance** (threshold $4/n$) to remove 87 points that disproportionately impacted model stability.
* **Feature Engineering:** Converted categorical variables (sex, smoker, region) into factors for regression compatibility.

---

## 🔬 The Modeling Journey

### 1. The Baseline: Multiple Linear Regression (RL)
Initially, a multiple linear regression was performed to establish a baseline.
* **Hypothesis Testing:** Conducted global significance tests (F-statistic: 524.2, $p < 2.2e-16$) which confirmed the regression was useful.
* **Diagnostics:** Residual analysis revealed major violations of the Gauss-Markov assumptions, specifically **Heteroscedasticity** (funnel-shaped residuals) and **Non-Normality** (Shapiro-Wilk test $p < 2.2e-16$).

### 2. Variable Selection
I utilized automated selection methods to find the most parsimonious model:
* **Stepwise Selection:** Used the **Akaike Information Criterion (AIC)** to balance model fit and complexity.
* **Multicollinearity Check:** Verified model integrity using **Variance Inflation Factors (VIF)**, ensuring all values were $< 5$.

### 3. The Optimized Solution: Gamma GLM
To address the asymmetrical nature of medical costs, I implemented a **Generalized Linear Model**:
* **Distribution:** Gamma distribution was chosen to handle positive and right-skewed data.
* **Link Function:** Log-link was applied to model multiplicative effects of features.
* **Performance:** The Gamma GLM outperformed the Linear model, achieving a lower AIC (20,947 vs. 21,267).

---

## 📊 Key Results (GLM Gamma)
The final model identifies the following multiplicative impacts on medical charges:
* **Smoking Status:** Multiplies costs by **4.58x**.
* **Age:** Increases costs by **3.6%** for every year.
* **Children:** Each additional child adds **~8.7%** to the predicted cost.
* **BMI:** Each unit increase in BMI results in a **1.2%** increase in charges.

---
## 🧰 Tech Stack
* **Software:** R.
* **Methodologies:** OLS Regression, ANOVA, Cook's Distance, Gamma GLM, AIC/BIC Comparison.