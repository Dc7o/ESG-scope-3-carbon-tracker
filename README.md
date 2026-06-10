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
| Tableau Public | Interactive ESG dashboard |
| pandas / numpy | Data manipulation |
| matplotlib / seaborn | Diagnostic plots |

## Project Phases
| Phase | Description | Status |
|---|---|---|
| Phase 1 | SQL — schema, joins, CTEs, window functions | ✅ Complete |
| Phase 2 | Python — regression analysis (Block 1 & Block 2) | ✅ Complete |
| Phase 3 | Tableau — interactive dashboard | ✅ Complete |
| Phase 4 | ESG report output | ✅ Complete |

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
- **Independent Variables:** Transport risk score, distance, spend, supplier tier
- **R² = 0.74** — model explains 74% of emissions variance
- **ΔR² = 0.34** — Block 2 significantly improved over Block 1
- **Sig. F Change = 0.016** — improvement is statistically significant

### Significant Predictors
| Variable | Coefficient | p-value | Interpretation |
|---|---|---|---|
| transport_risk_score | +214,541 | 0.0007 | Strongest driver of emissions |
| total_spend_usd | +0.011 | 0.030 | Higher spend = higher emissions |

### Regression Equation
Y = -849,703.79
+ 214,540.85 × (transport_risk_score)
+ 28.87      × (avg_distance_km)
+ 0.011      × (total_spend_usd)
+ 38,099.57  × (tier_2 dummy)
+ 77,595.14  × (tier_3 dummy)
## Project Summary
This project builds an end-to-end ESG Scope 3 carbon tracking pipeline 
for a 20-supplier manufacturing network covering calendar year 2024. 
Data was structured in MySQL using GHG Protocol Category 1–6 
classifications, analysed in Python using Simple and Multiple Linear 
Regression, and visualised in Tableau Public.

## Key Findings
| Finding | Detail |
|---|---|
| Total Scope 3 emissions | 2,972,579 tCO₂e across 20 suppliers |
| Highest emitting supplier | ColdChain Inc — 414,898 tCO₂e |
| Lowest emitting supplier | ChemBase Inc — 35,170 tCO₂e |
| Top 3 suppliers share | ColdChain, ElectroParts, CleanChem SA = ~35% of total |
| Block 1 R² | 0.40 — transport risk score explains 40% of variance |
| Block 2 R² | 0.74 — five predictors explain 74% of variance |
| Significant drivers | Transport risk score (p=0.0007) and total spend (p=0.030) |
| Non-significant | Tier and distance — likely due to small sample n=20 |

## Conclusions
**1. Transport mode is the dominant Scope 3 lever**
Transport risk score is the single strongest predictor in both blocks. 
Suppliers using air and road freight generate significantly more 
emissions than those using rail and sea — independent of spend or distance.

**2. Spend volume amplifies emissions**
Total spend is significant (p=0.030). However the relationship is not 
proportional — emission intensity (tCO₂e per $1M spend) is a more 
meaningful KPI than raw emissions alone.

**3. Tier classification alone is insufficient**
Tier dummies were not statistically significant. Transport behaviour 
and spend matter more than tier classification in predicting emissions.

**4. Outlier suppliers require targeted engagement**
TechParts GmbH shows anomalously high emissions relative to its 
transport risk score — sitting well above the regression line. 
This supplier warrants direct investigation regardless of tier.

## Stakeholder Recommendations

**Procurement / Supply Chain Teams**
- Prioritise switching ColdChain Inc, ElectroParts Ltd and CleanChem SA 
  from air/road to rail/sea — top 3 account for 35% of total emissions
- Negotiate transport mode clauses into supplier contracts for top 5 emitters
- Require Scope 3 disclosure from all Tier 1 suppliers as a baseline condition

**ESG / Sustainability Reporting Teams**
- Adopt emission intensity (tCO₂e per $1M spend) as the primary supplier 
  KPI — it normalises for supplier size
- Use the regression equation to set science-based reduction targets per supplier
- Flag TechParts GmbH for a Scope 3 audit — emissions not explained by known predictors

**Finance / Risk Teams**
- Carbon pricing risk is concentrated in top 3 suppliers
- Model financial exposure under $50–$150/tonne carbon price scenarios
- Supplier diversification away from high air-freight reduces both 
  emission and supply chain risk simultaneously

**Leadership**
- Shifting top 5 emitters from air/road to rail/sea could reduce total 
  Scope 3 emissions by an estimated 20–30%
- Achievable without changing suppliers — only transport mode 
  contracts need renegotiation



