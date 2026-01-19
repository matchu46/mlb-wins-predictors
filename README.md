# MLB Team Analytics: Wins, Competitiveness, and Team Tiers

## Repository Overview
This repository contains two complementary baseball analytics projects that analyze Major League Baseball (MLB) team performance from different but related perspectives.

Together, these projects demonstrate how team-level statistics can be used to:
1. Quantitatively explain **why teams win games**
2. Qualitatively classify teams into **competitive tiers**

Both projects use the Lahman Baseball Database and emphasize interpretability, statistical rigor, and proper handling of temporal data.

---

## Data Source
- **Lahman Baseball Database (Teams table)**
- Unit of analysis: **Team-season**
- Seasons covered: **2000–2025**

---

## Project 1: What Predicts MLB Team Wins?

`project-1-wins-regression/`

### Objective
To identify which team-level offensive and pitching statistics are most strongly associated with MLB team win totals.

### Approach
- Linear regression modeling
- Comparison of component-based metrics (runs scored and allowed) versus aggregate metrics (run differential)
- Evaluation using MAE and R²

### Key Takeaways
- Runs scored and runs allowed are the dominant predictors of team wins.
- Power and plate discipline correlate with winning but contribute indirectly through total run production.
- Disaggregating offensive and defensive components explains wins better than a single composite statistic.

This project focuses on **explanation and interpretation** rather than pure prediction.

---

## Project 2: Classifying MLB Teams into Competitive Tiers

`project-2-tier-classification/`

### Objective
To classify MLB teams into **Contender**, **Average**, and **Rebuilding** tiers using team performance metrics.

### Approach
- Multinomial logistic regression
- Tier labels defined using historical win distributions (training period only)
- Proper temporal validation with out-of-sample predictions for 2022–2025
- Evaluation using precision, recall, F1-score, and confusion matrices

### Key Takeaways
- Runs scored and runs allowed are the strongest drivers of team tier classification.
- Power and plate discipline contribute directionally but play a secondary role.
- The model separates Contender and Rebuilding teams with high precision, while most ambiguity occurs among Average teams.

This project focuses on **categorization and decision-oriented analysis** rather than exact win prediction.

---

## How the Projects Fit Together

| Project | Question Answered | Modeling Type |
|-------|------------------|--------------|
| Project 1 | *Why do teams win games?* | Regression |
| Project 2 | *How competitive is a team?* | Classification |

Project 1 provides a **quantitative explanation** of win drivers, while Project 2 translates those insights into a **practical competitive framework**. Together, they reflect how analytics is used both for understanding performance and for supporting strategic decision-making.

---

## Tools Used
- Python
- pandas
- scikit-learn
- matplotlib
- seaborn

---

## Notes
These projects prioritize analytical clarity and defensible conclusions over model complexity. All claims are directly supported by model outputs and evaluation metrics.
