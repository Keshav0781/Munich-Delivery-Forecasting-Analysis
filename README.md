# Munich Delivery Operations — Forecasting & Performance Analysis

End-to-end data analytics case study using 4 years of daily delivery operations data from Munich (2022–2025). Covers SLA performance analysis, order volume forecasting, driver planning, and revenue impact quantification.

---

## Project Overview

This project analyses the operational performance of an on-demand food delivery platform in Munich. The analysis answers five core business questions using real daily operations data across 1,458 clean days.

**Tools Used:** Python, Jupyter Notebook, Statsmodels, Prophet, Scikit-learn, Matplotlib, Pandas

---

## Business Questions Answered

- **Q1** — How often is the 25-minute delivery target and service quality met?
- **Q2** — What is the impact of courier working hours on order fulfillment?
- **Q3** — Forecast order volume for the next 120 days (Jan–Apr 2026)
- **Q4** — Estimate required drivers for the next 90 days using city efficiency
- **Q5** — What assumptions and methodology were used for driver estimation?
- **Additional** — What is the financial cost of lost orders and what would fixing it unlock?

---

## Key Findings

| Finding | Value |
|---|---|
| 25-min SLA compliance | 57.5% (838 of 1,458 days) |
| Year-on-year decline | 68.4% in 2022 → 46.7% in 2025 |
| Working hours vs fulfillment correlation | +0.027 (R²=0.0008) |
| Best forecasting model | Holt-Winters ETS — MAPE 4.70% |
| Base forecast Jan–Apr 2026 | 5,498 orders/day |
| Required drivers (base) | 208 drivers/day |
| Friday peak drivers | 240 drivers/day |
| 4-year lost commission | €5.7 million |

---

## Forecasting Models Compared

| Model | MAPE | Result |
|---|---|---|
| Holt-Winters ETS | 4.70% | Winner |
| Ensemble (avg) | 5.66% | Good |
| Prophet | 5.95% | Good |
| SARIMA(1,1,1)(1,1,1,7) | 6.51% | Good |

All models evaluated on the same 120-day held-out test set (Sep–Dec 2025).

---

## Repository Structure

| File | Description |
|---|---|
| Case_Study.ipynb | Full analysis notebook |
| Presentation.pdf | Slide deck with findings |
| Summary.pdf | Written answers and methodology |
| munich_delivery_clean.csv | Cleaned dataset used for analysis |
| metrics_definition.pdf | KPI definitions and order lifecycle |
| requirements.txt | Python dependencies |
| README.md | Project documentation |

---

## Key Analysis Sections

**Data Cleaning**
1,461 raw records cleaned to 1,458 — removed dummy values, rebuilt broken fields, forward filled and interpolated missing values.

**SLA Analysis**
Mean delivery time of 24.71 minutes — just 0.29 minutes below the 25-minute target. Handling time gap of 2.19 minutes between compliant and non-compliant days is the primary operational lever.

**Working Hours vs Fulfillment**
Despite 75% more courier hours from lowest to highest working hour band — fulfillment rate moves by only 0.30 percentage points. Potential demand (corr −0.153) is the real driver.

**Order Volume Forecast**
Holt-Winters ETS selected with MAPE 4.70% on a 120-day test set. Damped trend applied to avoid over-extrapolation. Three planning scenarios — pessimistic 4,937, base 5,498, optimistic 6,059 orders/day.

**Driver Planning**
Formula: Required Drivers = Forecasted Orders ÷ (City Efficiency × Opening Hours). City efficiency stable at 2.147 orders/hr across all 48 months (std ±0.02).

**Revenue Impact**
Using JET 2023 AOV of €26.00 and 18% commission rate — €5.7M lost commission over 4 years. Each 1% fulfillment improvement = €112,000 additional annual commission.

---

## How to Run

1. Clone this repository
```bash
git clone https://github.com/Keshav0781/Munich-Delivery-Forecasting-Analysis.git
```

2. Install dependencies
```bash
pip install -r requirements.txt
```

3. Open the notebook
```bash
jupyter notebook Case_Study.ipynb
```

---

## Author

**Keshav Jha**
Data Scientist | Forecasting & Analytics
[LinkedIn](https://www.linkedin.com/in/your-linkedin) | [GitHub](https://github.com/Keshav0781)
