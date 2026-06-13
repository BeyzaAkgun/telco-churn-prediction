# 📡 Telecom Customer Churn Prediction

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python)
![XGBoost](https://img.shields.io/badge/XGBoost-green?logo=xgboost)
![SHAP](https://img.shields.io/badge/SHAP-Explainability-orange)
![Tableau](https://img.shields.io/badge/Tableau-Public-blue?logo=tableau)
![AUC](https://img.shields.io/badge/ROC--AUC-0.8377-brightgreen)

## 📌 Project Overview

Built an end-to-end machine learning pipeline to predict customer churn for a telecom company. The project identifies high-risk customers, explains the key drivers behind churn, and visualizes insights through an interactive Tableau dashboard — enabling data-driven retention strategies.

---

## 🔗 Live Dashboard

👉 [View Tableau Dashboard](https://public.tableau.com/app/profile/beyza.akg.n/viz/Book1_17812775873850/TelcoCustomerChurnDashboard)

---

## 📊 Dataset

- **Source:** [Telco Customer Churn — Kaggle](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)
- **Size:** 7,043 customers × 21 features
- **Target:** Churn (Yes/No) — 26.5% churn rate

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| Python | Core programming language |
| Pandas | Data manipulation & cleaning |
| Scikit-learn | Preprocessing & evaluation |
| XGBoost | Churn prediction model |
| SHAP | Model interpretability |
| Matplotlib / Seaborn | Data visualization |
| Tableau Public | Interactive dashboard |
| Google Colab | Development environment |

---

## 📁 Project Structure

```
telco-churn-prediction/
│
├── telco_churn_prediction.ipynb   # Main Colab notebook
├── telco_churn_tableau.csv        # Exported data for Tableau
├── README.md                      # Project documentation
└── images/                        # Charts and visualizations
    ├── eda_overview.png
    ├── model_evaluation.png
    ├── shap_importance.png
    └── shap_beeswarm.png
```

---

## ⚙️ Methodology

### 1. Exploratory Data Analysis
- Analyzed distributions of tenure, monthly charges, contract types
- Found month-to-month contracts and fiber optic users have highest churn rates
- Identified class imbalance (26.5% churn)

### 2. Feature Engineering
7 new features created from raw data:

| Feature | Description |
|---------|-------------|
| `tenure_group` | Customers grouped into 5 tenure buckets (0-1yr to 5-6yr) |
| `avg_monthly_spend` | TotalCharges / tenure |
| `charges_to_tenure` | MonthlyCharges / tenure ratio |
| `high_value_customer` | 1 if MonthlyCharges above median |
| `service_count` | Number of add-on services subscribed |
| `auto_payment` | 1 if automatic payment method |
| `risk_score` | Rule-based composite risk score |

### 3. Modeling
- Algorithm: **XGBoost Classifier**
- Handled class imbalance with `scale_pos_weight`
- Train/Test split: 80/20 stratified

### 4. Model Performance

| Metric | Score |
|--------|-------|
| ROC-AUC | **0.8377** |
| Accuracy | 75% |
| Churn Recall | 75% |
| Churn Precision | 52% |

### 5. SHAP Analysis
Top churn drivers identified:

1. 🥇 **risk_score** — strongest predictor overall
2. 🥈 **charges_to_tenure** — high charges relative to tenure
3. 🥉 **Contract** — month-to-month contracts drive churn
4. **tenure** — newer customers churn more
5. **MonthlyCharges** — higher bills correlate with churn

---

## 📈 Key Business Insights

- **43% of month-to-month customers** are at high churn risk
- **0-1 year tenure customers** have the highest churn rate (~30%)
- **High risk customers** pay on average **$74/month** vs $56 for low risk
- **2,192 customers** identified as High Risk — primary retention targets

---

## 💡 Retention Strategy Recommendations

1. **Offer contract upgrades** to month-to-month customers with discounts
2. **Target new customers** (0-12 months) with onboarding loyalty programs
3. **Review pricing** for fiber optic customers who show high churn
4. **Enable auto-pay incentives** — manual payment customers churn more

---

## 🚀 How to Run

1. Open `telco_churn_prediction.ipynb` in Google Colab
2. Run all cells in order
3. Kaggle API credentials required for data download

---

## 👤 Author

Made with ❤️ as a portfolio project demonstrating end-to-end ML for business problems.
