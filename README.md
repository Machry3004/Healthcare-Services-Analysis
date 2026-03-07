# Healthcare Services Analysis

A data analytics project built to analyze hospital revenue performance, patient admission patterns, and medical condition billing across 55,500 patient records using SQL, Power BI, Excel, and DAX.

---

## Tools and Tech Stack

| Tool | Purpose |
|---|---|
| PostgreSQL | Data storage and query execution |
| MS Excel | Initial data exploration and validation |
| Power Query | Data cleaning and transformation |
| Power BI | Dashboard and visualization |
| DAX | KPI measures and time intelligence |

---

## Problem Statement

A healthcare organization needed a centralized reporting system to track hospital revenue, understand which conditions and doctors drive the most billing, and monitor patient admission trends over time. Without a unified view, operational and financial decisions were being made without data backing. The goal was to build a report that identifies revenue drivers, highlights inefficiencies in length of stay, and tracks billing performance across time, conditions, and insurance providers.

---

## Dataset

| Attribute | Detail |
|---|---|
| Source | Kaggle — Healthcare Dataset |
| Records | 55,500 patient admissions |
| Columns | 15 |
| Period | May 2019 to May 2024 (5 years) |
| Key columns | billing_amount, medical_condition, insurance_provider, admission_type, date_of_admission, discharge_date, doctor, age_category, room_number |

---

## Dashboard Overview

### Dashboard 1 — Revenue Overview
Tracks total revenue, total admissions, average billing, and YoY growth. Includes revenue by admission type, monthly revenue trend, revenue and admissions combo chart, and revenue by medical condition.

![Revenue Overview](screenshots/healthcare_overview.png)

### Dashboard 2 — Stay and Capacity Analysis
Tracks average length of stay, rolling 3-month revenue, and revenue per day. Includes stay breakdown by admission type, total admissions by month, revenue per day by condition, and average stay by condition.

![Stay Analysis](screenshots/healthcare_stay_analysis.png)

### Dashboard 3 — Doctor and Provider Performance
Tracks previous month revenue, MoM billing growth, and revenue per day. Includes admission vs revenue scatter by condition, MoM billing growth trend, revenue by doctor, and revenue by insurance provider.

![Performance Dashboard](screenshots/healthcare_performance.png)

---

## Business Questions

**Dashboard 1 — Revenue Overview**

1. What is the total revenue generated across all patients?
2. What is the total number of patient admissions?
3. What is the average billing amount per patient?
4. How did revenue grow compared to the previous year (YoY)?
5. How is revenue distributed across Emergency, Elective, and Urgent admission types?
6. How does monthly revenue trend over time?
7. Which medical condition generates the highest total revenue?

**Dashboard 2 — Stay and Capacity Analysis**

8. What is the average length of hospital stay across all patients?
9. What is the rolling 3-month revenue?
10. How much revenue does the hospital generate per day of patient stay?
11. How does average length of stay differ across admission types?
12. How does total admission volume trend month by month?
13. Which medical condition has the highest revenue per day?
14. Which medical condition has the longest average hospital stay?

**Dashboard 3 — Doctor and Provider Performance**

15. What was the previous month's total revenue?
16. What is the Month-over-Month billing growth?
17. How does admission volume compare to revenue per medical condition?
18. Which doctor generates the highest total revenue?
19. Which insurance provider contributes the most revenue?

---

## Methodology

**Step 1 — Data Collection**
Dataset imported from Kaggle. Table created in PostgreSQL with correct data types across all 15 columns.

**Step 2 — Data Cleaning**
Handled in Excel and Power Query. Validated date formats for date_of_admission and discharge_date, standardized medical condition and insurance provider names, added age_category as a derived column.

**Step 3 — Data Modeling**
Built a Date Table in Power BI using CALENDAR() spanning from earliest admission to latest discharge. Established the date relationship for all time intelligence measures.

**Step 4 — Calculated Column**
Created Length_of_Stay as a calculated column using DATEDIFF on date_of_admission and discharge_date.

**Step 5 — SQL Query Writing**
Wrote 8 queries covering revenue by condition, insurance provider, doctor, admission type, age category, room, monthly trend, and average length of stay.

**Step 6 — DAX Measures**
Built measures for Total Revenue, Total Admissions, Avg Billing, Avg Length of Stay, Revenue per Day, Current Month Billing, MoM Growth, Previous Month Revenue, Previous Year Revenue, YoY Growth, Revenue % of Total, and Rolling 3M Revenue.

**Step 7 — Dashboard Building**
Built 3 dashboard pages in Power BI with slicers for Insurance Provider, Medical Condition, Admission Type, Test Result, Gender, and Date Year.

---

## Key Findings

1. The hospital generated **$1,417.4M in total revenue** across 55,500 admissions over 5 years, with an average billing amount of **$25,539 per patient**.
2. **YoY revenue growth is 20.37%**, confirming consistent year-over-year expansion in hospital billing volume and patient intake.
3. **Revenue is evenly distributed across all three admission types** — Elective ($477.6M, 33.7%), Urgent ($474.0M, 33.4%), and Emergency ($465.8M, 32.9%) — indicating no single admission category dominates billing.
4. **Diabetes is the highest revenue-generating condition** at $238.5M, followed closely by Obesity ($238.2M), Arthritis ($237.3M), and Hypertension ($235.7M) — all six conditions are within a $6.4M range, suggesting uniform resource consumption across conditions.
5. The **average length of stay is 15.51 days** across all patients, with minimal variation between Emergency (15.4 days), Elective (15.6 days), and Urgent (15.5 days) admission types.
6. **Revenue per day stands at $1.65K per patient** — consistent across all medical conditions, indicating standardized billing protocols regardless of condition type.
7. **Cigna is the top insurance provider** contributing $287.1M in revenue, though all five providers (Cigna, Medicare, Blue Cross, UnitedHealthcare, Aetna) are within a $8.3M range — indicating a well-diversified insurance revenue base with no single-provider dependency risk.

---

## Repo Structure

```
healthcare-services-analysis/
├── README.md
├── data/
│   └── healthcare_dataset.csv
├── sql/
│   └── Healthcare_Services_SQL_SCRIPTS.sql
├── dax/
│   └── Healthcare_DAX_Scripts.md
├── docs/
│   ├── Business_Requirements.md
│   └── Solutions.md
└── screenshots/
    ├── healthcare_overview.png
    ├── healthcare_stay_analysis.png
    └── healthcare_performance.png
```

---

## Files Included

| File | Description |
|---|---|
| healthcare_dataset.csv | Raw dataset — 55,500 patient records, 15 columns |
| Healthcare_Services_SQL_SCRIPTS.sql | 8 SQL queries covering all revenue and stay analysis |
| Healthcare_DAX_Scripts.md | 12 DAX measures for Power BI |
| Business_Requirements.md | All business questions the report answers |
| Solutions.md | Answers to every business question with results |

---

## Data Source

[Healthcare Dataset — Kaggle](https://www.kaggle.com)

Dataset covers patient admissions from May 2019 to May 2024. All patient names in the dataset are anonymized synthetic data. No real personally identifiable information is included.
