#  Customer Churn Prediction — Telecom

##  Problem Statement

Telecom companies lose significant revenue when customers stop using their services (churn). This project builds a **Business Intelligence pipeline** to identify customers who are likely to churn, enabling the company to take proactive retention actions.

---

##  Objectives

- Analyze customer behavior using **Exploratory Data Analysis (EDA)**
- Perform **OLAP (Online Analytical Processing)** to slice churn data across business dimensions
- Build and compare **classification models** to predict churn
- Compute **business KPIs** such as churn rate and revenue at risk
- Provide actionable **business recommendations**

---

##  Dataset

| Property | Details |
|---|---|
| Source | [IBM Telco Customer Churn — Kaggle](https://www.kaggle.com/blastchar/telco-customer-churn) |
| Records | 7,043 customers |
| Features | 21 (demographics, services, contract, charges) |
| Target | `Churn` (Yes / No) |

**Key Features:**
- `tenure` — Number of months the customer has stayed
- `Contract` — Month-to-month, One year, Two year
- `MonthlyCharges` — Monthly billing amount
- `InternetService` — DSL, Fiber optic, No
- `TotalCharges` — Total amount charged

---

##  Tech Stack

![Python](https://img.shields.io/badge/Python-3.8+-blue?style=flat&logo=python)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?style=flat&logo=jupyter)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?style=flat&logo=pandas)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-ML-F7931E?style=flat&logo=scikit-learn)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-11557C?style=flat)
![Seaborn](https://img.shields.io/badge/Seaborn-Visualization-4C72B0?style=flat)

---

##  Project Pipeline

```
Raw Data (CSV)
      │
      ▼
Data Preprocessing
(Handle nulls, encode categoricals, scale features)
      │
      ▼
Exploratory Data Analysis (EDA)
(Churn distribution, tenure, charges, correlation heatmap)
      │
      ▼
OLAP & Data Cube Analysis
(Pivot: Contract × InternetService × TenureGroup)
      │
      ▼
Feature Selection
(Top 10 features by correlation with Churn)
      │
      ▼
Classification Models
(Logistic Regression | Decision Tree | Random Forest)
      │
      ▼
KPI Metrics
(Churn rate, Revenue at risk, Retention rate)
      │
      ▼
Conclusion & Business Recommendations
```

---

##  Results

### Model Comparison

| Model | Accuracy | ROC-AUC |
|---|---|---|
| **Logistic Regression** | **78.78%** | **0.8355**  |
| Decision Tree | 77.57% | 0.8140 |
| Random Forest | 76.72% | 0.8032 |

> **Best Model: Logistic Regression** with AUC = 0.8355

### Business KPIs

| KPI | Value |
|---|---|
| Overall Churn Rate | ~26.5% |
| Customers at Risk | ~1,869 |
| Revenue at Risk | ~$456,000 / month |
| Avg Tenure (Churned) | ~18 months |
| Avg Tenure (Retained) | ~38 months |

### OLAP Insight

| Segment | Churn Rate |
|---|---|
| Month-to-month + Fiber optic | > 40% 🔴 |
| One year + DSL | ~15% 🟡 |
| Two year + Any service | < 5% 🟢 |

---

##  Repository Structure

```
customer-churn-prediction/
│
├── WA_Fn-UseC_-Telco-Customer-Churn.csv   # Raw dataset
├── Customer_churn_Prediction_Telecom.ipynb # Main Jupyter notebook
│
├── outputs/
│   ├── eda_plots.png                       # EDA visualizations
│   ├── correlation_heatmap.png             # Feature correlation
│   ├── olap_cube_heatmap.png               # OLAP pivot heatmap
│   ├── confusion_matrices.png              # Model confusion matrices
│   ├── roc_curves.png                      # ROC curve comparison
│   ├── feature_importance.png              # Random Forest importance
│   └── kpi_metrics.png                     # Business KPI chart
│
└── README.md
```

---

##  How to Run

**1. Clone the repository**
```bash
git clone https://github.com/your-username/customer-churn-prediction.git
cd customer-churn-prediction
```

**2. Install dependencies**
```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

**3. Launch Jupyter Notebook**
```bash
jupyter notebook Customer_churn_Prediction_Telecom.ipynb
```

**4. Run all cells** — `Kernel → Restart & Run All`

---

##  Key Findings

- **1 in 4 customers** churns, costing the business over **$456K/month**
- **Month-to-month contracts** have 3× higher churn than two-year contracts
- **Fiber optic** customers churn more — suggesting pricing or quality issues
- **MonthlyCharges** and **TotalCharges** are the strongest churn predictors
- Customers with **tenure < 12 months** are at the highest risk
