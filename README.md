# Financial Loan Analysis

An end-to-end data analysis project on a bank's 2021 loan portfolio, using **Python and Power BI** to clean the data, calculate key lending KPIs, and build an interactive dashboard for tracking loan performance and risk.

---

## Problem Statement

A bank issues thousands of personal loans a year, but leadership has no single, consolidated view of how the loan book is performing. This project analyzes the loan portfolio to answer:

- How much capital has been funded, and how much has been recovered?
- What share of the portfolio is **"Good"** (Current / Fully Paid) vs **"Bad"** (Charged Off)?
- How is the average interest rate and DTI (debt-to-income) trending?
- How does loan performance vary by **term, employment length, and state**?
- What does month-over-month loan issuance and recovery look like across the year?

**Goal:** Clean and analyze the raw loan data, then deliver an interactive Power BI dashboard that lets stakeholders monitor portfolio health at a glance and drill down by grade, purpose, and state.

---

## Dataset

**Source file:** `financial_loan_dataset.csv`
**Size:** 38,576 loan records | 24 columns
**Period:** Loans issued January 2021 – December 2021

Key fields: `loan_status`, `loan_amount`, `total_payment`, `int_rate`, `dti`, `term`, `grade`, `sub_grade`, `purpose`, `emp_length`, `home_ownership`, `verification_status`, `address_state`, `issue_date`, `last_payment_date`, `next_payment_date`.

---

## Tools & Tech Stack

| Stage | Tool | What it was used for |
| ----- | ---- | --------------------- |
| 1. Data Cleaning & KPI Calculation | **Python** (pandas, numpy, matplotlib, seaborn) | Structured cleaning, null/duplicate handling, type fixes, KPI computation, EDA visuals |
| 2. Dashboard | **Power BI** | Interactive executive dashboard with KPI cards, trends, and drill-downs |

---

## Data Cleaning (Python)

Performed in `finance_project_python.ipynb`:

- Loaded the raw CSV and inspected shape, dtypes, and structure (`df.info()`, `df.head()`)
- Checked for duplicate records (none found)
- Checked for missing values — dropped the small number of records with a null `emp_title`
- Standardized categorical values — e.g. merged `'Source Verified'` into `'Verified'` in `verification_status`
- Converted date columns (`issue_date`, `last_credit_pull_date`, `last_payment_date`, `next_payment_date`) from string to proper `datetime` format
- Reviewed unique values across all categorical columns to catch inconsistencies before analysis

---

## 📊 KPI Calculations (Python)

The notebook computes the core lending KPIs directly from the cleaned data:

- **Total Loan Applications**
- **Total Funded Amount** (sum of `loan_amount`)
- **Total Received Amount** (sum of `total_payment`)
- **Average Interest Rate**
- **Average DTI**
- **Good Loans** (`Current` + `Fully Paid`) — application count, funded amount, received amount
- **Bad Loans** (`Charged Off`) — application count, funded amount, received amount

A pie chart of total amount received by loan `term` (36 vs 60 months) was also generated as part of the exploratory analysis.

---

## Power BI Dashboard

The dashboard has two pages, filterable by **Grade**, **Purpose**, and **Address State**.

### Page 1 — Summary

![Summary Page](Screenshot%202026-09-22%20225210.png)


- KPI cards: Total Loan Applications, Total Funded Amount, Total Received Amount, Average Interest Rate, Average DTI (each with MTD and MoM change)
- **Good Loan vs Bad Loan** donut charts with application count, funded amount, and received amount for each
- A breakdown table by `loan_status` (Current / Charged Off / Fully Paid) showing applications, funded amount, received amount, avg interest rate, and avg DTI

### Page 2 — Overview

![Overview Page](Screenshot%202026-09-22%20225234.png)

- Total Received Amount trend **by month** (Jan → Dec)
- Total Received Amount **by state** (map view)
- Total Received Amount **by term** (36 vs 60 months, pie chart)
- Total Received Amount **by employment length** (bar chart)


---

## Key Insights

- The portfolio recovered **more than it funded overall** ($473.1M received vs $435.8M funded), driven largely by interest and fully-paid loans, though Charged Off loans recovered only a fraction of what was funded ($37M received vs $66M funded).
- **86% of loans are performing well** (Current/Fully Paid), while **~14% have been charged off** — a useful baseline default rate for the portfolio.
- **36-month term loans make up 62.3%** of total received amount vs **37.7% for 60-month loans** — shorter-term loans dominate the book.
- Borrowers with **10+ years of employment** contribute the highest received amount by far ($126M), roughly 2.5x the next-highest employment length bracket.
- Charged-off loans carry a **notably higher average interest rate (13.88%) and DTI (14.00%)** than Fully Paid loans (11.64% int rate, 13.17% DTI) — pricing does track risk, though not enough to fully offset losses.

---

## Project Structure

```
Financial-Loan-Analytics/
│
├── README.md
├── LICENSE
├── financial_loan_dataset.csv
├── finance_project_python.ipynb
├── Screenshot 2026-09-22 225210.png   # Power BI summary page
└── Screenshot 2026-09-22 225234.png   # Power BI overview page
```


---

## How to Reproduce

1. Clone this repo:
   ```bash
   git clone https://github.com/atharvbajpai-web/Financial-Loan-Analytics.git
   cd Financial-Loan-Analytics
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Open `finance_project_python.ipynb` and run all cells to clean the data and generate the KPIs.
4. (Optional) Open the Power BI dashboard once added, point it to the cleaned data, and hit Refresh.

---

## 🙋 About This Project

Built as a data analyst portfolio project to demonstrate the full analytics workflow — from raw data cleaning and KPI derivation in Python to a polished, interactive Power BI dashboard.
