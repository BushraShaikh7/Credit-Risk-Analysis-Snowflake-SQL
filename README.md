# Credit Risk Analysis — Snowflake SQL

**Dataset:** CS_TRAINING | 150,000 borrowers | Kaggle Give Me Some Credit  
**Tool:** Snowflake SQL  
**Purpose:** Identify which borrowers are most likely to default on a loan, using only SQL — no machine learning models.

---

## Background

Banks are legally required (ECOA, FCRA) to provide a specific, documented reason when denying a loan. This project explores which factors genuinely predict default and builds a data-backed case a lender could use in practice.

---

## Questions Answered

| # | Question | Key Finding |
|---|---|---|
| 1 | How many borrowers defaulted? | 10,026 of 150,000 — a 6.7% default rate |
| 2 | Does being 90 days late predict default? | One late payment = 33.7% default. Seven = 81.6% |
| 3 | Does high debt ratio predict default? | Weak predictor. High debt = 9% vs 5% for low debt |
| 4 | Do lower income borrowers default more? | Yes. Under $3k/month = 9% vs 5% for high income |
| 5 | Do older borrowers have more credit lines? | Yes. Over-50 average 9.2 lines vs 4.4 for under-30 |
| 6 | Once late payments exist, does income still matter? | Barely. All income groups converge around 40-43% |
| 7 | Does high credit utilisation predict default? | Over 80% utilisation = 21% default rate |
| 8 | What is the riskiest borrower profile? | Late payments + high utilisation = 41.6% default |
| 9 | What is the safest borrower profile? | No late payments + low utilisation = 1.8% default |
| 10 | How much money is at risk? | Riskiest group = $5.6M monthly debt exposure |
| 11 | Does age predict default? | Under-40 = 10.4% vs over-60 = 3.1% |

---

## Key Findings

- The gap between the safest and riskiest borrower profile is **23x**
- Late payment history is the single strongest predictor found
- Credit utilisation is the second strongest
- Combining both creates a group defaulting at 41.6% — six times the average
- Income and debt ratio are weak predictors when used alone
- Age is a meaningful signal but should not be used as a standalone reason for denial

---

## Data Quality Note

The `NumberOfTimes90DaysLate` column contains values of 96 and 98 which are almost certainly data errors or system placeholders. These rows should be investigated before being used in any real lending decision.

---

## Legal Context

Under ECOA (Equal Credit Opportunity Act) and FCRA (Fair Credit Reporting Act), a lender must provide a specific, documented reason for denying a loan. This analysis demonstrates how SQL-based exploratory analysis can surface defensible, evidence-backed risk factors.
