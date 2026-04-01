# 🛒 Customer Shopping Behaviour — Analytics Project

> End-to-end data analytics project covering **EDA**, **SQL analysis**, **Python reporting**, and **Power BI dashboarding** on 3,900 customer shopping records.

---

## 📁 Project Structure

```
customer-behaviour-analytics/
│
├── customer_shopping_behavior.csv     # Raw dataset (3,900 rows × 18 columns)
├── customer_behaviour.ipynb           # Python EDA & data cleaning notebook
├── customer.sql                       # 10 SQL analytical queries
├── CUSTOMER.pbix                      # Power BI dashboard
└── Customer_Shopping_Report_INR.pdf   # Auto-generated analytics report (INR)
```
<img width="1920" height="1080" alt="Screenshot (1034)" src="https://github.com/user-attachments/assets/63a8063a-216e-4e7c-bfb9-e102afda3de8" />

---

## 📊 Dataset Overview

| Property | Detail |
|---|---|
| **File** | `customer_shopping_behavior.csv` |
| **Rows** | 3,900 customers |
| **Columns** | 18 features |
| **Currency** | USD (converted to INR @ ₹93.18) |

### Columns

| Column | Description |
|---|---|
| `Customer ID` | Unique customer identifier |
| `Age` | Customer age |
| `Gender` | Male / Female |
| `Item Purchased` | Product name |
| `Category` | Clothing / Footwear / Accessories / Outerwear |
| `Purchase Amount (USD)` | Transaction value in USD |
| `Location` | US State |
| `Size` | Product size (S/M/L/XL) |
| `Color` | Product color |
| `Season` | Season of purchase |
| `Review Rating` | Customer rating (1–5) |
| `Subscription Status` | Yes / No |
| `Shipping Type` | Standard / Express / Free / Next Day Air etc. |
| `Discount Applied` | Yes / No |
| `Promo Code Used` | Yes / No |
| `Previous Purchases` | Count of prior transactions |
| `Payment Method` | Credit Card / PayPal / Cash / Venmo etc. |
| `Frequency of Purchases` | Weekly / Fortnightly / Monthly etc. |

---

## 🐍 Python Notebook — `customer_behaviour.ipynb`

Covers the full **EDA and data preparation pipeline**:

- Data loading and shape inspection (`df.info()`, `df.describe()`)
- Null value detection and imputation (median fill by category for `Review Rating`)
- Column normalization (lowercase, underscores, rename)
- Feature engineering — `age_group` via `pd.qcut()` (Young Adult / Adult / Middle-aged / Senior)
- Exploratory visualizations

**Dependencies:**
```bash
pip install pandas numpy matplotlib seaborn
```

**Run:**
```bash
jupyter notebook customer_behaviour.ipynb
```

---

## 🗄️ SQL Analysis — `customer.sql`

10 business questions answered with SQL on the `customer_behaviour` table:

| # | Question | Technique |
|---|---|---|
| Q1 | Revenue by gender | `GROUP BY`, `SUM` |
| Q2 | Discount buyers above avg spend | Subquery, `WHERE` filter |
| Q3 | Top 5 products by avg rating | `GROUP BY`, `ORDER BY`, `LIMIT` |
| Q4 | Standard vs Express shipping spend | Conditional `GROUP BY` |
| Q5 | Subscriber vs non-subscriber spend | `GROUP BY`, `COUNT`, `AVG`, `SUM` |
| Q6 | Top 5 products by discount rate | `CASE WHEN`, percentage calc |
| Q7 | Customer segmentation (New/Returning/Loyal) | `CTE`, `CASE WHEN` |
| Q8 | Top 3 products per category | `CTE`, `ROW_NUMBER()`, `PARTITION BY` |
| Q9 | Repeat buyers & subscription overlap | `WHERE`, `GROUP BY` |
| Q10 | Revenue by age group | `GROUP BY`, `ORDER BY` |

**How to run** (SQLite example):
```bash
sqlite3 mydb.db
.mode csv
.import customer_shopping_behavior.csv customer_behaviour
.read customer.sql
```

---

## 📈 Power BI Dashboard — `CUSTOMER.pbix`

Interactive dashboard built in Power BI Desktop.

**To open:**
1. Install [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free)
2. Open `CUSTOMER.pbix`
3. If prompted for data source, re-point to `customer_shopping_behavior.csv`

---

## 📄 PDF Report — `Customer_Shopping_Report_INR.pdf`

Auto-generated multi-page analytics report with:

- KPI summary cover page (Total Revenue, Customers, Avg Rating, Subscriber Rate)
- One page per SQL query with data tables, charts, and insight callouts
- All monetary values displayed in **INR (₹)** at exchange rate **1 USD = ₹93.18**

**To regenerate the report**, run the Python generation script with `reportlab` and `matplotlib`:
```bash
pip install reportlab matplotlib pandas
python generate_report.py
```

---

## 🔑 Key Findings

| Finding | Value |
|---|---|
| Total Revenue | ₹2.17 Cr |
| Avg Purchase Value | ₹5,569 |
| Male Revenue Share | 67.7% |
| Loyal Customers (11+ purchases) | 79.9% |
| Non-subscribed Repeat Buyers | 72.4% |
| Top Age Group by Revenue | 55+ (29.8%) |
| Highest Rated Product | Gloves (3.86/5) |
| Highest Discount Rate Product | Hat (50%) |

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| Python (pandas, matplotlib) | EDA, data cleaning, PDF report generation |
| SQL (SQLite / PostgreSQL) | Business analytics queries |
| Power BI | Interactive dashboard |
| ReportLab | PDF report generation |
| Jupyter Notebook | Exploratory analysis |

---

## 🚀 Quick Start

```bash
# 1. Clone / download the project files
# 2. Install Python dependencies
pip install pandas numpy matplotlib seaborn reportlab jupyter

# 3. Run EDA notebook
jupyter notebook customer_behaviour.ipynb

# 4. Run SQL queries
sqlite3 shop.db
.import customer_shopping_behavior.csv customer_behaviour
.read customer.sql

# 5. Open Power BI dashboard
# Open CUSTOMER.pbix in Power BI Desktop

# 6. Generate PDF report
python generate_report.py
```

---

## 📌 Notes

- The dataset is entirely fictional / anonymized for educational purposes.
- SQL queries are written for standard SQL and tested on SQLite. Minor syntax adjustments may be needed for MySQL or PostgreSQL.
- Currency conversion uses the rate **1 USD = ₹93.18** (April 1, 2026).
