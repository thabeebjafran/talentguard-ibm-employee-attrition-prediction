# TalentGuard — IBM Employee Attrition Prediction & Retention Strategy

Predictive model that flags employees most likely to leave IBM, paired with a targeted retention strategy that cuts projected attrition by nearly a third.

## Business Problem

IBM's 2022 employee attrition rate was **16.14%** — high enough to put sustained pressure on hiring costs, team continuity, and institutional knowledge. HR needed a way to move from reactive ("who already left") to proactive ("who is likely to leave next, and why") so retention budget could be targeted instead of spread thin.

## Dataset

1,470 employee records from IBM's HR Analytics attrition dataset — demographics, compensation, job role, tenure, performance ratings, and attrition outcome.

## Approach

1. **Data preparation** — encoded categorical variables, converted overtime to binary, checked correlations against attrition.
2. **Feature selection** — narrowed to the strongest, least collinear predictors (checked via VIF): **Monthly Income, Overtime, and Stock Option Level**.
3. **Logistic regression model** — trained on a 70/30 split to predict attrition probability per employee, evaluated with a confusion matrix, classification report, ROC curve, and KS-statistic (38.9 — solid separation between leavers and stayers).
4. **Risk flagging** — lowered the decision threshold to 0.3 (rather than the default 0.5) to proactively surface at-risk *current* employees, not just replicate past outcomes.
5. **Retention strategy design** — built three targeted interventions based on the top predictive drivers:
   - **Overtime:** restrict to Job Level 1–2 and only when urgent
   - **Salary:** tiered raises based on performance rating and job involvement
   - **Stock options:** awarded based on performance, involvement, and tenure
6. **Impact simulation** — reran the trained model on the adjusted employee profiles to quantify the retention lift.

## Key Findings

- **1,205 active employees** were scored; the model flagged **148 (12.2%)** as high attrition risk under current conditions.
- **100% of predicted leavers work overtime** — the single strongest behavioral signal.
- **67.6% of predicted leavers earn under $5,000/month.**
- **52.7% of predicted leavers hold no stock options.**
- Overtime, salary, and stock option level are the three variables strategy can realistically move — and the three the model weights most heavily.

## Results

Applying the targeted retention strategy and re-scoring the workforce:

| Metric | Before | After | Change |
|---|---|---|---|
| Predicted attrition rate | 12.2% (148 employees) | 8.8% (106 employees) | **−3.4 pts** |
| Overtime-linked churn | baseline | — | **−28.3%** |
| Low/mid-salary churn | baseline | — | significant drop |
| No-stock-option churn | baseline | — | **−55.1%** |

Net effect: **overall predicted attrition drops from 12.2% to 8.8%** — without a blanket raise or company-wide policy change, just by targeting the interventions at the employees the model flags.

## Recommendations

- **COO / HR Leadership:** adopt the flagged-risk list as the primary input for retention budget allocation instead of exit interviews alone.
- **People Ops:** cap overtime for Job Level 1–2 employees to urgent cases only.
- **Compensation:** tie salary increases to performance rating + job involvement rather than flat annual raises.
- **Total Rewards:** extend stock option eligibility further down the tenure/performance curve — it's the highest-leverage lever in the model.

## Repository Contents

| File | Description |
|---|---|
| `TalentGuard_Attrition_Modeling.ipynb` | Full notebook — cleaning, feature selection, logistic regression, evaluation, and strategy simulation |
| `TalentGuard_IBM_Dashboard.twbx` | Interactive Tableau dashboard (attrition drivers, risk segments) |
| `IBM_Attrition_Prediction_Strategy_Presentation.pptx` | Stakeholder-facing deck — problem, model, findings, strategy, recommendations |
| `attrition_predictions_and_strategy_output.xlsx` | Per-employee attrition predictions and post-strategy outcomes |

> Note: the raw source CSV is excluded from this repo to keep it lightweight — it's the public IBM HR Analytics Employee Attrition dataset, widely available on Kaggle.

## Tools Used

`Python` (pandas, scikit-learn, statsmodels, seaborn) · `Logistic Regression` · `Tableau` · `Excel` · `PowerPoint`

## Author

**Thabeeb Jafran** — [LinkedIn](#) · [Portfolio](#)
