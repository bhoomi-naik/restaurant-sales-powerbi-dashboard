# NAIKS Restaurant — Sales Analytics Dashboard

<div align="center">

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)
![Power Query](https://img.shields.io/badge/Power%20Query-217346?style=for-the-badge&logo=microsoft&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)

**An end-to-end Business Intelligence dashboard built with real restaurant transaction data**

</div>

---

## Dashboard Preview

> Add your dashboard_preview.png to the repository and it will appear here

![Dashboard Preview](dashboard_preview.png)

---

## Project Summary

| Detail | Info |
|---|---|
| Business | NAIKS Restaurant |
| Data Period | April 1–26, 2026 |
| Dataset Size | 197 transactions x 8 columns |
| Tool | Microsoft Power BI Desktop (May 2026) |
| Dataset Type | Real-world data |
| Time to build | 1 day (beginner to completion) |

---

## Business Problem

The restaurant owner had raw transaction data but no visibility into:
- Which days generate the most revenue?
- Which menu items are top performers?
- Do customers prefer Full or Half plates?
- What is the average daily revenue?

This dashboard answers all these questions in one interactive view.

---

## Dataset Columns

| Column | Data Type | Description |
|---|---|---|
| Date | Date | Transaction date |
| Item Name | Text | Menu item ordered |
| Quantity | Whole Number | Plates ordered |
| Amount | Decimal | Total bill (Price x Qty) |
| Price Per Plate | Decimal | Unit price |
| Plate Type | Text | Full or Half plate |
| Month | Text | Month name |
| Day | Text | Day name |

> Note: Restaurant is closed every Monday — reflected in the data.

---

## Technical Implementation

### Data Preparation — Power Query
- Imported raw Excel data into Power Query Editor
- Fixed all column data types precisely
- Verified 100% data quality — zero nulls, zero errors across all columns
- Disabled Auto Date/Time for clean date field handling

### Data Modelling
- Created dedicated Date Table using DAX CALENDAR function
- Added 6 helper columns to Date Table: Year, Month Number, Month Name, Day of Week Number, Day Name, Is Closed flag
- Established One-to-Many (1:*) relationship between Date Table and sales table
- Built dedicated _Measures table for organized DAX management

### DAX Measures

```dax
-- Total Revenue
Total Revenue = SUM(restaurant_sales[Amount])

-- Total Orders
Total Orders = COUNTROWS(restaurant_sales)

-- Average Daily Revenue (accurate per-day calculation)
Avg Daily Revenue = 
AVERAGEX(
    VALUES('Date Table'[Date]),
    [Total Revenue]
)

-- Best Single Day Revenue
Best Revenue Day = 
MAXX(
    VALUES('Date Table'[Date]),
    [Total Revenue]
)

-- Total Quantity Sold
Total Quantity = SUM(restaurant_sales[Quantity])

-- Average Order Value (safe division)
Avg Order Value = 
DIVIDE(
    [Total Revenue],
    [Total Orders],
    0
)
```

---

## Dashboard Features

### KPI Cards

| Metric | Value |
|---|---|
| Total Revenue | Rs. 2,74,405 |
| Total Orders | 197 |
| Avg Daily Revenue | Rs. 34,301 |
| Best Revenue Day | Rs. 1,45,685 |

### Visualizations

| Chart | Type | Insight |
|---|---|---|
| Daily Revenue Trend | Line Chart | Daily pattern with Monday closures visible |
| Revenue by Item | Bar Chart | Top performing menu items ranked |
| Full vs Half Plate | Donut Chart | Customer plate preference split |
| Revenue by Day of Week | Column Chart | Best and worst performing days |

### Interactive Features
- Plate Type Slicer — filter entire dashboard by Full or Half plate
- Automatic Tooltips — hover over any data point for exact values
- Cross-filtering — click any visual to filter all other visuals
- Dark professional theme — enterprise-grade design

---

## Key Business Insights

### 1. Saturday Revenue Dominance
Saturday generates Rs. 1,45,685 — approximately 4.2x the average daily revenue of Rs. 34,301. The restaurant is heavily weekend-dependent. This creates both an opportunity (maximize Saturday capacity) and a risk (bad weather or holidays significantly impact weekly revenue).

### 2. Seafood Menu Dominance
3 of the top 5 revenue items are seafood dishes:

| Rank | Item | Category |
|---|---|---|
| 1 | King Fish Thali | Seafood |
| 2 | Bombay Duck Fry | Seafood |
| 3 | Mutton Masala | Meat |
| 4 | Chicken Masala | Meat |
| 5 | Pomfret Thali | Seafood |

NAIKS is clearly a coastal seafood-specialty restaurant. Marketing should lead with seafood identity.

### 3. Full Plate Overwhelming Preference
Full plates account for 97.68% of total revenue (Rs. 2,68,050) vs Half plates at just 2.32% (Rs. 6,360). The restaurant could consider repositioning half plates as appetizers or combo add-ons rather than standalone meals.

### 4. Mid-Week Revenue Gap
Wednesday and Thursday significantly underperform compared to Friday and Saturday. Mid-week promotions, combo offers, or loyalty discounts could smooth revenue distribution and improve overall monthly performance.

### 5. Revenue Concentration Risk
The top 2 items likely dominate total revenue — creating supply chain risk if key seafood items face seasonal unavailability or price increases.

### 6. Monday Closure Validated
Data analysis confirms zero transactions on all Mondays — validating the business rule and ensuring time intelligence calculations correctly account for closed days.

---

## Challenges and Solutions

| Challenge | Solution Applied |
|---|---|
| Auto Date/Time creating unwanted hierarchies | Disabled via File > Options > Data Load |
| Day names sorting alphabetically not chronologically | Used Sort by Column with Day of Week Number |
| DateTime format showing in tooltips | Fixed column type in Power Query |
| Missing Payment Mode column | Replaced with Plate Type analysis using available data |
| Line chart showing hierarchy levels | Disabled Auto Date/Time and rebuilt X-axis field |

---

## How to View This Dashboard

1. Download NAIKS_DB.pbix from this repository
2. Install Power BI Desktop — free from microsoft.com/power-bi
3. Open the .pbix file
4. Interact with the Plate Type slicer to filter all visuals
5. Hover over any chart for detailed tooltips
6. Click any chart segment to cross-filter other visuals

---

## Skills Demonstrated

Microsoft Power BI | DAX | Power Query | Data Modelling | Time Intelligence | KPI Design | Data Visualization | Business Intelligence | ETL | Dashboard Design | Data Cleaning | Analytical Thinking | Date Table Architecture | Relationship Modelling

---

## Repository Structure

```
restaurant-sales-powerbi-dashboard/
│
├── NAIKS_DB.pbix                              -- Power BI dashboard file
├── dashboard_preview.png                      -- Dashboard screenshot
├── README.md                                  -- This file
└── NAIKS_Restaurant_Dashboard_Case_Study.md   -- Detailed case study
```

---

## About

Built as part of a Data Analytics Portfolio to demonstrate end-to-end Power BI development skills for Data Analyst and Data Science internship applications.

Connect with me:
- LinkedIn: [Add your LinkedIn URL]
- Email: [Add your email]
- Portfolio: [Add your portfolio URL]

---

<div align="center">

If you found this project useful, please star this repository.

Built with real data | Designed for business impact | April 2026

</div>
