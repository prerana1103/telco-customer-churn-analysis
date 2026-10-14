# Customer Churn Analysis

Analysed telecom customer behaviour data to identify the factors most strongly associated with customer churn, and translated the findings into concrete retention strategies.

## Overview

| | |
|---|---|
| **Dataset** | IBM/Kaggle *Telco Customer Churn* — 7,043 customers, 21 attributes (demographics, account, services, billing, churn label); overall churn 26.5% |
| **Tools** | Python — Pandas, NumPy, Matplotlib, Seaborn, SciPy |
| **Deliverables** | Jupyter notebook (full analysis), 7 exported charts, this report |

## What was done

- **Data cleaning:** checked for duplicate customer records (none found), coerced `TotalCharges` from text to numeric and imputed its 11 blank values (all tenure-0 customers) from tenure × monthly rate, standardised categorical/binary fields.
- **Feature engineering:** tenure buckets (0–12, 13–24, 25–48, 49–72 months), a `NumServices` engagement score (count of add-ons in use), and average monthly spend relative to tenure.
- **Exploratory analysis:** churn rate broken down by demographics, tenure, contract type, payment method, internet service type, add-on service adoption, and billing amounts, plus chi-square tests on the main categorical drivers and a correlation snapshot across numeric features.

## Key findings

1. **Contract type is the biggest driver** — month-to-month churn is ~43% vs ~11% (one-year) and ~3% (two-year); chi-square p < 1e-250.
2. **Risk is front-loaded** — ~47% churn in the first 12 months, falling to ~10% for customers beyond 4 years.
3. **Payment method matters** — electronic check ~45% vs ~15–19% for every other method.
4. **Fiber optic customers churn the most** (~42% vs ~19% DSL) despite paying the highest bills — a likely value/reliability expectations gap.
5. **Add-ons reduce churn** — among internet customers, churn falls from ~52% with no add-ons to ~5% with all six.
6. **Demographics** — seniors (~42% vs ~24%) and customers without a partner or dependents churn more; gender has no effect.

## Retention strategy recommendations

- Incentivise the move from month-to-month to annual contracts (discount or perk).
- Build a first-year onboarding/check-in program targeting the highest-risk tenure window.
- Offer a small credit for switching from electronic check to autopay.
- Investigate the fiber optic customer experience specifically (pricing perception vs. reliability).
- Proactively bundle/trial add-on services for new or at-risk customers to raise engagement.
- Design targeted outreach for senior citizens and single-account customers.

## Files in this project

```
churn_project/
├── README.md                                   ← this file
├── data/
│   └── telecom_customer_churn.csv               ← Kaggle Telco dataset (7,043 customers)
├── notebook/
│   ├── customer_churn_analysis.ipynb            ← full analysis notebook (run end-to-end)
│   └── customer_churn_analysis.html             ← static viewable version, no Jupyter needed
└── images/
    ├── 01_overall_churn_rate.png
    ├── 02_churn_by_demographics.png
    ├── 03_churn_by_tenure.png
    ├── 04_churn_by_contract_payment.png
    ├── 05_churn_by_service_usage.png
    ├── 06_charges_vs_churn.png
    └── 07_correlation_heatmap.png
```

## Note on the data

The dataset is the public IBM/Kaggle *Telco Customer Churn* file (`WA_Fn-UseC_-Telco-Customer-Churn.csv`, renamed `telecom_customer_churn.csv`). Findings are associations in observational data, not proven causes — e.g. fiber optic's high churn may reflect price, reliability, or the type of customer who picks fiber.
