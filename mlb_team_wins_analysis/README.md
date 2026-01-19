# MLB Team Wins Analysis: What Statistics Best Predict Success?

## Project Overview
This project analyzes Major League Baseball (MLB) team-season data to identify which performance metrics are most strongly associated with team win totals. Using historical team statistics, the analysis focuses on understanding *why* teams win games rather than simply predicting outcomes.

The project emphasizes clear feature engineering, statistical modeling, and careful interpretation of results.

---

## Data Source
- **Lahman Baseball Database (Teams table)**
- Seasons analyzed: **2000–2024**
- Unit of analysis: **Team-season**

Key statistics used include:
- Wins (W)
- Runs scored (R)
- Runs allowed (RA)
- Home runs (HR)
- Walks (BB)
- Strikeouts (SO)

---

## Research Question
**Which team-level offensive and pitching statistics best predict MLB team wins?**

---

## Methodology

### 1. Data Preparation
- Filtered to modern-era seasons (2000 onward).
- Selected core offensive and pitching statistics.
- Created **run differential (R − RA)** as a derived feature.
- Removed incomplete records to ensure consistency.

### 2. Exploratory Analysis
- Computed pairwise correlations between wins and team statistics.
- Compared simple correlations to regression results to identify overlapping effects and multicollinearity.

### 3. Modeling
Two linear regression models were evaluated:

**Model A — Component-based model**
- Features: R, RA, HR, BB, SO
- Purpose: Explain wins using offensive and defensive components.

**Model B — Aggregate model**
- Feature: Run Differential only
- Purpose: Test whether a single composite metric can explain wins.

### 4. Evaluation
- Random train/test split (80/20)
- Metrics:
  - Mean Absolute Error (MAE)
  - R² (coefficient of determination)

---

## Model Performance

| Model | Features Used | MAE (Wins) | R² |
|-----|--------------|-----------|----|
| Model A | R, RA, HR, BB, SO | ~4.9 | ~0.85 |
| Model B | Run Differential | ~5.8 | ~0.45 |

**Key takeaway:**  
Disaggregated offensive and pitching components explain team wins substantially better than a single composite statistic.

---

## Key Findings

- **Runs scored (R) and runs allowed (RA) are the strongest predictors of team wins**, as demonstrated by their dominant regression coefficients and the high explanatory power of Model A.
- **Power (HR) and plate discipline (BB)** show strong correlation with wins but contribute limited marginal explanatory power once total runs are included, indicating their impact is largely indirect.
- **Run differential alone is insufficient** to fully explain win totals across teams and seasons, highlighting the importance of separating offensive and defensive components.
- Multicollinearity between offensive statistics explains why some variables lose apparent importance in multivariate models despite strong pairwise correlations.

---

## Visualizations
- **Predicted vs. Actual Wins** scatter plot
- **Regression coefficient bar chart**, illustrating relative feature importance

All figures are exported for use in documentation and reporting.

---

## Tools Used
- Python
- pandas
- scikit-learn
- matplotlib

---

## Notes
This project prioritizes interpretability and statistical reasoning over model complexity. The goal is to provide clear, defensible insights into team performance rather than optimize predictive accuracy through advanced machine learning techniques.
