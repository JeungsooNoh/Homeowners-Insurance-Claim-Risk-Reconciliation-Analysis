# Homeowners Insurance Claim Risk Analysis

This project explores inconsistencies and risk patterns in homeowners insurance claims and payment records using real FEMA data and simulated billing data.

---

## Objective

To identify potentially problematic cases where:
- Insurance claims are paid despite insufficient or failed premium payments
- Customers were overcharged without receiving proper refunds
- Account data errors (NOC) or failed payments (NSF) occur

---

##  Data Sources

1. **Claim Data** (from FEMA OpenFEMA database)
   - Includes building and contents claims, ZIP code, date, and year of loss
   - Filtered to use only data from 2020–2023

2. **Payment Data** (simulated)
   - Includes expected premium, actual amount paid, refund flag, NSF/NOC signal, and refund amount

---

## Key Analysis

- Merged FEMA claims with payment records via unique `policy_id`
- Identified:
  - Overpaid customers who did not receive refunds
  - Customers who received refunds without overpaying
  - Claims paid even when payment was not made or failed
  - Total unrefunded overpayment amount

---

##  Summary Results

| Issue Type                     | Value     |
|-------------------------------|-----------|
| Overpaid without Refund        | 9 cases   |
| Refunded without Overpay       | 3 cases   |
| Total Overpaid (No Refund)     | $3,313    |
| NSF (Non-Sufficient Funds)     | 1 case    |
| NOC (Notice of Correction)     | 10%       |
| Refund Percentage              | 3.86%     |
| Suspicious Claim Cases         | 7 cases   |

---

## Notable Suspicious Pattern

> **"Claim paid but customer didn’t pay or failed to pay"**  
>  7 potential high-risk cases detected.

---

##  Tools Used

- Python (pandas, matplotlib)
- FEMA open data
- Custom data simulation

---

##  Project Files

- `notebook.ipynb` – full analysis
- `summary.csv` – summary of key metrics
- `suspicious_cases.csv` – suspicious policy details
