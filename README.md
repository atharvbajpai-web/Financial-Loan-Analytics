# Financial Loan Analysis | Python + Power BI

An end-to-end analysis of **38,576 personal loans (2021)**: portfolio growth, loan quality, risk drivers and profitability, with a two-page Power BI dashboard and a written insights report.

## Problem
How can the lender grow its loan portfolio while controlling bad loans? See `01_Problem_Statement.docx`.

## Project structure
| Folder / file | What it contains |
|---|---|
| `01_Problem_Statement.docx / .pdf` | Business problem, objectives, key questions, KPI definitions |
| `02_Python_Analysis/Financial_Loan_Analysis.ipynb` | Cleaning, KPIs, charts and insights (pandas, matplotlib, seaborn) |
| `02_Python_Analysis/charts/` | All charts saved from the notebook |
| `03_Dashboard/` | Power BI dashboard – Page 1 Overview, Page 2 Summary |
| `04_Insights_Report.docx / .pdf` | Findings with charts, and recommendations |

To run the notebook, keep `financial_loan.csv` in the same folder as the notebook.

## Headline results
- **$435.8M** lent, **$473.1M** received; average interest rate 12.05%, average DTI 13.33%.
- Applications grew **85%** and money lent **116%** from January to December.
- **13.82%** of loans are bad. Charge-offs lost **$28.2M**, wiping out about 47% of the profit from fully paid loans.
- Charge-off rate rises from **5.7% (grade A) to 33.1% (grade G)**; 60-month loans default **25.0% vs 10.7%** for 36-month loans.
- **Small business** is the only purpose with a negative return (−2.8%); grades **B and C** generate about half of net profit.

## Tools
Python (pandas, NumPy, matplotlib, seaborn) · Power BI · Jupyter / Google Colab
