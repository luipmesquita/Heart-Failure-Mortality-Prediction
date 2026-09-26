# Heart-Failure-Mortality-Prediction
Comparative machine learning analysis evaluating model parsimony (Full vs. Reduced feature sets) using Logistic Regression and Random Forest on heart failure mortality data.

# 🫀 Heart Failure Mortality Prediction: Model Parsimony & Comparative Evaluation

A machine learning study evaluating the trade-off between model complexity and predictive performance on heart failure mortality data.

This project explores whether a parsimonious model using only 4 clinically significant features can perform comparably to (or outperform) a full 12-feature model using **Logistic Regression** and **Random Forest Classifiers**.

---

## Key Highlights & Business/Clinical Impact

* **Parsimony & Noise Reduction:** Reducing features from 12 to 4 (`age`, `ejection_fraction`, `serum_creatinine`, and `time`) eliminated noise, resulting in higher predictive accuracy and better generalization across both algorithms.
* **Top Performing Model:** **Random Forest with Reduced Features** achieved the best overall performance with **MCC = 0.641**, **ROC-AUC = 0.911**, and **Accuracy = 85.0%**.
* **Clinical Utility:** The reduced model improved Recall for the high-risk class (mortality) from **58% to 63%**, reducing False Negatives while requiring 66% fewer clinical data points.
* **Metric Selection:** Emphasized **Matthews Correlation Coefficient (MCC)** over raw Accuracy due to target class imbalance (32% mortality / 68% survival).

---

## Comparative Performance Matrix

All models evaluated on an 80/20 stratified train-test split ($N=299$ total records, $N_{test}=60$).

| Model | Feature Set | Accuracy | MCC | ROC-AUC | Precision (Death) | Recall / Sensitivity (Death) | F1-Score (Death) |
| :--- | :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **Logistic Regression** | Full (12) | 0.817 | 0.556 | 0.859 | 0.79 | 0.58 | 0.67 |
| **Logistic Regression** | Reduced (4) | 0.817 | 0.599 | 0.864 | 0.73 | 0.58 | 0.65 |
| **Random Forest** | Full (12) | 0.833 | 0.599 | 0.908 | 0.85 | 0.58 | 0.69 |
| **Random Forest** | **Reduced (4)** | **0.850** | **0.641** | **0.911** | **0.86** | **0.63** | **0.73** |

---

##  Key Findings & Insights

1. **Feature Reduction Improves Performance:** Removing 8 secondary features increased MCC for both Logistic Regression (+0.043) and Random Forest (+0.042). This confirms that high feature dimensionality on small datasets can induce overfitting.
2. **Non-Linear Dynamics:** Random Forest consistently outperformed Logistic Regression across all metrics, indicating non-linear interactions between cardiac function (`ejection_fraction`), renal function (`serum_creatinine`), patient age, and follow-up time (`time`).
3. **Trade-off Analysis:** In clinical settings, high specificity prevents false alarms, but sensitivity (Recall) is paramount to avoid missing high-risk patients. The reduced Random Forest model successfully captured 12 out of 19 mortality cases in the test set without compromising precision (86%).

---

## Tech Stack & Dependencies

* **Language:** Python 3.x
* **Data Manipulation & Analysis:** `pandas`, `numpy`
* **Machine Learning:** `scikit-learn`
* **Data Visualization:** `matplotlib`, `seaborn`

---

## How to Run

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/teu-usuario/Heart-Failure-Mortality-Prediction.git](https://github.com/teu-usuario/Heart-Failure-Mortality-Prediction.git)
   cd Heart-Failure-Mortality-Prediction
