# NBA Talent Acquisition Decision Support System

A data-driven decision support system for NBA player acquisition built with Python, Power BI, and OLS regression. Designed to help front offices identify undervalued players, assess team positional gaps, and make financially sustainable roster decisions.

Built by Sharon Smith, Brittany Isabell, and Jose F. Barquero Jimenez — ETSU Decision Support Systems, Spring 2026.

---

## What This Does

Most NBA teams look at stats. This system asks a different question: which players are worth acquiring *given their salary, their trajectory, and your team's specific gaps?*

We built a DSS that answers that question across 434 players using seven KPIs, two interactive Power BI dashboards, and a full ETL pipeline merging three datasets.

---

## The Two Dashboards

### Team Scout Report
Select any of the 30 NBA teams. The dashboard shows:
- Positional Need Score for every position — where are the gaps?
- Current roster performance with PER, WS, BPM, VORP, salary, and trajectory flags
- Offensive vs Defensive impact scatter plot by position
- Team-level KPI gauges benchmarked against league averages

### Acquisition Candidates
Filter by position, salary gap tier, cost per win tier, and age. The dashboard shows:
- Which players are undervalued vs overpriced (Salary Gap chart)
- PER vs Win Shares scatter plot — top right is your target
- Full acquisition candidate table with KPI scores, market gap, value tier, and trajectory
- Step-by-step guide built into the dashboard for non-technical users

---

## The Seven KPIs

| KPI | What it measures |
|-----|-----------------|
| PER | Overall player efficiency, normalized to league average of 15.0 |
| Win Shares / VORP | Cumulative wins contributed; value above replacement level |
| Cost Per Win | Salary per Win Share — identifies financially efficient players |
| Box Plus/Minus | Context-adjusted two-way impact per 100 possessions |
| Performance Trajectory | Age-curve analysis — rising, peak, or declining? |
| Positional Need Score | Weighted gap between a team's position group and league average |
| Salary vs Market Value Gap | OLS regression residual — who is under or overpaid? |

---

## How We Built It

**Three data sources:**
- NBA Player Salaries 2024-25 (Kaggle) — 563 rows, salary data
- Basketball Reference Advanced Stats 2024-25 — 736 rows, all advanced metrics
- NBA Per-Game Stats 2024 (Kaggle) — 528 rows, counting stats

**ETL pipeline in Python:**
- Merged three datasets on player name with accent normalization
- Handled mid-season trades by deduplicating on highest games played row
- Cleaned salary strings, removed league average rows, resolved column collisions
- Final unified dataset: 434 players with complete records across all seven KPIs

**KPI calculations in Excel then visualized in Power BI:**
- OLS regression (R² = 0.550, n = 355) to predict market salary from PER, WS, USG%, Age
- Positional Need Score using weighted z-scores by position
- Performance Trajectory using age-cohort peer averages from a dynamic reference table

---

## Files in This Repo

| File | Description |
|------|-------------|
| `NBA_DSS_DataPrep_Refined.ipynb` | Full Python ETL pipeline |
| `NBA_DSS_UnifiedDf_Sample.csv` | Sample of the unified dataset (100 rows) |
| `NBA_DSS_UnifiedDf_Formulas.xlsx` | Full dataset with KPI formulas |
| `NBA_TalentAcquisition_DSS.pbix` | Power BI dashboard file |
| `dashboard_acquisition_candidates.png` | Screenshot — Acquisition Candidates view |
| `dashboard_team_scout_report.png` | Screenshot — Team Scout Report view |
| `NBA_DSS_DataPreparationReport.pdf` | Full data preparation report |
| `Presentation_NBA_DSS.pdf` | Final presentation slides |

**To open the dashboard:** Download Power BI Desktop (free) and open the .pbix file.

---

## Tools Used

- Python (Pandas, NumPy)
- Microsoft Excel
- Power BI Desktop
- OLS Regression
- Data sources: Kaggle, Basketball Reference

---

## About

I'm a data analyst who finds the story behind the numbers. This project sits at the intersection of sports analytics, business intelligence, and data storytelling — using real NBA data to answer real acquisition questions.

Connect with me on [LinkedIn](https://www.linkedin.com/in/sharon-smith-analyst)
