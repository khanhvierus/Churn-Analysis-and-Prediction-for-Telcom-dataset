#  Customer Churn Prediction: High-Recall Strategy

##  Project Objective
This project develops a machine learning solution to predict customer churn in the telecommunications industry. The primary goal was to achieve a **high Recall (0.77)** to ensure that the business can identify and retain as many at-risk customers as possible, minimizing revenue loss.

---

##  Methodology & Workflow

The project followed a rigorous data science lifecycle, from statistical cleaning to advanced gradient boosting optimization.

### 1️ Data Cleaning & Initial Pruning
* **Statistical Filtering:** Used Chi-Square tests to identify non-informative features.
* **A/B Testing Noise:** Dropped 4 interference variables (`Gender`, `Married`, `Phone_Service`, `Multiple_Lines`) after verifying they added noise rather than predictive power.

### 2️ Advanced Feature Engineering (FE)
Instead of relying on raw data, we engineered high-signal features:
* **Tenure_to_Monthly_Charge_Ratio:** (Top 1 Importance) Measures the financial weight relative to loyalty.
* **Avg_Monthly_Long_Distance:** Normalizes long-distance usage over time.
* **Total_Services:** Aggregates the customer's ecosystem engagement.
* **Data Integrity:** Reverted `Age` binning to raw numerical format to allow the model to find its own optimal split points.

### 3️ Intelligent Feature Selection (Gain-Based)
* **Information Gain:** Ranked features based on their actual contribution to error reduction rather than split frequency.
* **Elbow Method:** Conducted iterative testing (from Top 5 to Top 38 features) to find the "Sweet Spot" where F1-Score peaks before noise sets in.

### 4️ Model Optimization (LightGBM)
* **Algorithm:** Moved from Random Forest to **LightGBM** for superior handling of categorical data and imbalanced classes.
* **Heavyweight Tuning:** Executed a `RandomizedSearchCV` with 100 iterations, focusing on `scale_pos_weight` and `Regularization (L1/L2)` to stabilize the high-recall performance.

---

##  Performance Summary (Final Test Set)

The model was validated against a **hidden 15% Test Set** that it had never seen before.

| Metric | Class 1 (Churners) | Class 0 (Loyal) |
| :--- | :---: | :---: |
| **Precision** | **0.66** | 0.90 |
| **Recall** | **0.77** | 0.84 |
| **F1-Score** | **0.71** | 0.87 |
| **Accuracy** | \- | **0.82** |

###  Key Takeaways:
* **Proactive Retention:** Identifying **77% of churners** allows for highly effective marketing interventions.
* **Model Stability:** The consistency between Validation (0.73 F1) and Test (0.71 F1) confirms the model is robust and not overfitted.

---

##  Project Architecture (Pipeline)

The entire workflow is encapsulated in a production-ready **Scikit-learn Pipeline**:

```mermaid
graph TD
    A[Raw Data] --> B[Feature Engineering Wrapper]
    B --> C[ColumnTransformer: Encode/Scale]
    C --> D[Feature Selector: Top 38 Gain-based]
    D --> E[Tuned LightGBM Model]
    E --> F[Churn Prediction]
