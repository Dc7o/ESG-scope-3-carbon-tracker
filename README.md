# ESG-scope-3-carbon-tracker
# ESG Scope 3 Carbon Tracker

## Overview
End-to-end ESG reporting pipeline that tracks, models, and reports 
Scope 3 greenhouse gas emissions across a 20-supplier network using 
SQL, Python, and Tableau — built as a capstone project aligned with 
GHG Protocol standards.

## Business Problem
A manufacturing company needs to identify which suppliers are driving 
the most Scope 3 emissions, quantify the key drivers, and produce 
ESG-ready insights for investor disclosure.

## Project Architecture
## Tools & Technologies
| Tool | Purpose |
|---|---|
| MySQL Workbench | Schema design, CTEs, window functions |
| Python (statsmodels) | Simple and Multiple Linear Regression |
| Tableau Desktop | Interactive ESG dashboard |
| pandas / numpy | Data manipulation |
| matplotlib / seaborn | Diagnostic plots |

## Project Phases
| Phase | Description | Status |
|---|---|---|
| Phase 1 | SQL — schema, joins, CTEs, window functions | ✅ Complete |
| Phase 2 | Python — regression analysis (Block 1 & Block 2) | ✅ Complete |
| Phase 3 | Tableau — interactive dashboard | 🔄 In Progress |
| Phase 4 | ESG report output | 🔄 Pending |

## Dataset
- 20 suppliers across 10 countries (2024)
- 4 tables: suppliers, emission_factors, activity_data, transport_logs
- 240 activity records and 240 transport records
- Emission factors aligned with GHG Protocol Category 1–6

## Regression Results

### Block 1 — Simple Linear Regression
- **Dependent Variable:** Total tCO₂e
- **Independent Variable:** Transport Risk Score
- **R² = 0.40** — risk score explains 40% of emissions variance
- **p = 0.003** — statistically significant

### Block 2 — Multiple Linear Regression (Enter Method)
- **Independent Variables:** Transport risk score, distance, 
  spend, supplier tier
- **R² = 0.74** — model explains 74% of emissions variance
- **ΔR² = 0.34** — Block 2 significantly improved over Block 1
- **Sig. F Change = 0.016** — improvement is statistically significant

### Significant Predictors
| Variable | Coefficient | p-value | Interpretation |
|---|---|---|---|
| transport_risk_score | +214,541 | 0.0007 | Strongest driver of emissions |
| total_spend_usd | +0.011 | 0.030 | Higher spend = higher emissions |

## Key Insights
- Transport mode is the single biggest lever for reducing Scope 3 emissions
- Switching suppliers from air/road to rail/sea has the highest emission reduction potential
- Top 3 suppliers (ColdChain Inc, ElectroParts Ltd, CleanChem SA) account for disproportionate emissions
- Tier classification was not significant at n=20 — would likely become significant with larger sample

## Regression Equation
Y = -849,703.79
+ 214,540.85 × (transport_risk_score)
+ 28.87      × (avg_distance_km)
+ 0.011      × (total_spend_usd)
+ 38,099.57  × (tier_2 dummy)
+ 77,595.14  × (tier_3 dummy)
  ## Repository Structure
📁 ESG-scope-3-carbon-tracker/
├── 📁 data/
│     └── esg_spss.csv
├── 📁 sql/
│     └── phase1_esg_sql.sql
├── 📁 python/
│     └── esg_regression_spss_style.py
└── 📁 outputs/
└── esg.png

## Author
Dhvani — Data Analytics | ESG Reporting | Python | SQL | Tableau
