# MLB Team Tier Classification (Contender, Average, Rebuilding)

## Project Overview
This project classifies Major League Baseball (MLB) teams into competitive tiers—**Contender**, **Average**, and **Rebuilding**—using team-level performance statistics. Rather than predicting exact win totals, the goal is to model team competitiveness in a way that reflects how teams are commonly evaluated in real-world baseball analysis.

The project emphasizes interpretability, proper temporal validation, and evidence-based conclusions.

---

## Data Source
- **Lahman Baseball Database (Teams table)**  
- Seasons analyzed: **2000–2025**
- Unit of analysis: **Team-season**

Key statistics used include:
- Runs scored (R)
- Runs allowed (RA)
- Home runs (HR)
- Walks (BB)
- Strikeouts (SO)

---

## Tier Definition
Teams are labeled using historical win distributions from the **training period only (2000–2021)**:

- **Contender**: Top 25% of teams by wins  
- **Average**: Middle 50%  
- **Rebuilding**: Bottom 25%

This approach avoids information leakage and ensures that tier definitions are not influenced by future seasons.

---

## Methodology

1. **Feature Engineering**
   - Constructed team-level predictors from offensive and pitching statistics.
   - Wins were used only to define tiers, not as model inputs.

2. **Model**
   - Multinomial Logistic Regression
   - Chosen for interpretability and suitability for multi-class classification.

3. **Evaluation**
   - Stratified train/validation split using data from **2000–2021**
   - Model performance evaluated with precision, recall, F1-score, and a confusion matrix.

4. **Out-of-Sample Predictions**
   - Final model trained on all data through 2021.
   - Tier predictions generated for **2022–2025**.
   - Predictions for 2025 should be interpreted as in-season projections.

---

## Model Performance (Validation Set)

- **Overall accuracy:** ~80%
- **Macro F1-score:** ~0.80

Key observations:
- The model distinguishes **Contender** and **Rebuilding** teams with high precision.
- Most misclassifications occur within the **Average** tier, reflecting the inherent ambiguity of mid-tier teams.

---

## Key Findings

- **Runs scored (R) and runs allowed (RA) are the strongest drivers of team tier classification**, with coefficient magnitudes substantially larger than those of other features in the logistic regression model.
- **Power (HR) and plate discipline (BB)** contribute directionally to tier predictions but play a **secondary role** relative to overall run production and prevention.
- The classification model effectively separates **Contender** and **Rebuilding** teams, while ambiguity is concentrated among **Average** teams.

---

## Results & Visualizations

- **Predicted team tiers for 2022–2025**
- **Tier distribution by season**, showing how league competitiveness changes over time
- **Franchise-level tier timelines**, illustrating competitive cycles for individual teams
- **Validation confusion matrix**, highlighting where classification errors occur

All outputs are saved as CSV files and figures for reproducibility.

---

## Tools Used
- Python
- pandas
- scikit-learn
- matplotlib
- seaborn

---

## Notes
This project prioritizes analytical rigor and interpretability over model complexity. The focus is on producing defensible insights rather than maximizing predictive performance through black-box methods.
