<div align="center">

# 🛒 Customer Shopping Behavior Analysis

**Uncovering shopping trends, customer segments & revenue drivers through data**

![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge&logo=python&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-336791?style=for-the-badge&logo=postgresql&logoColor=white)
![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

[Overview](#-overview) •
[Dataset](#-dataset) •
[Project Structure](#-project-structure) •
[Key Insights](#-key-insights) •
[Setup](#-getting-started) •
[SQL Queries](#-sql-analysis) •
[Dashboard](#-power-bi-dashboard)

</div>

---

## 📌 Overview

A leading retail company wants to better understand its customers' shopping behavior to improve sales, customer satisfaction, and long-term loyalty. This project analyzes **3,900 customer transactions** to uncover which factors — discounts, reviews, seasons, or payment preferences — drive consumer decisions and repeat purchases.

### 🎯 Business Question

> *"How can the company leverage consumer shopping data to identify trends, improve customer engagement, and optimize marketing and product strategies?"*

### 🛠️ Tech Stack

| Layer | Tool |
|---|---|
| Data Cleaning & Transformation | Python (Pandas) |
| Database & Querying | PostgreSQL |
| Visualization & Dashboard | Power BI |
| Version Control | Git & GitHub |

---

## 📊 Dataset

The dataset contains **3,900 records** with **18 features** capturing customer demographics, purchase details, and behavioral attributes.

<details>
<summary>📋 <b>Click to view all columns</b></summary>
<br>

| # | Column | Description |
|---|---|---|
| 1 | `customer_id` | Unique customer identifier |
| 2 | `age` | Customer age |
| 3 | `gender` | Male / Female |
| 4 | `item_purchased` | Product name |
| 5 | `category` | Clothing, Footwear, Accessories, Outerwear |
| 6 | `purchase_amount_usd` | Transaction amount in USD |
| 7 | `location` | U.S. state |
| 8 | `size` | Product size (S, M, L, XL) |
| 9 | `color` | Product color |
| 10 | `season` | Fall, Winter, Spring, Summer |
| 11 | `review_rating` | Rating from 1.0 to 5.0 |
| 12 | `subscription_status` | Yes / No |
| 13 | `shipping_type` | Express, Standard, Free Shipping, etc. |
| 14 | `discount_applied` | Yes / No |
| 15 | `promo_code_used` | Yes / No |
| 16 | `previous_purchases` | Number of prior purchases |
| 17 | `payment_method` | Credit Card, PayPal, Cash, etc. |
| 18 | `frequency_of_purchases` | Weekly, Monthly, Quarterly, etc. |

</details>

---

## 📁 Project Structure

```
customer-shopping-behavior-analysis/
│
├── 📄 README.md                                        # Project documentation
├── 📄 requirements.txt                                 # Python dependencies
├── 📄 .gitignore                                       # Git ignore rules
│
├── 📂 data/
│   └── customer_shopping_behavior.csv                  # Raw dataset
│
├── 📂 notebooks/
│   └── Customer_Shopping_Behaviour.ipynb               # Data cleaning & transformation
│
├── 📂 sql/                               
│   └── Answers.sql                                     # SQL analysis queries
│
├── 📂 dashboard/
│   └── dashboard.pdf           # Power BI dashboard 
│
└── 📂 reports/
    └── Customer_Shopping_Behavior_Report.pdf  # Full project report
    └── Customer_Shopping_Behavior_Project_Description.pdf  # Full project description
```

---

## 🔍 Key Insights

<details>
<summary>💰 <b>Revenue & Spending</b></summary>
<br>

- **Total Revenue:** ~$233K across 3,900 transactions
- **Average Order Value:** $59.76
- **Male customers** generate ~68% of total revenue while making up the majority of the customer base
- **Clothing** is the top revenue category (~$0.10M), followed by Accessories (~$0.07M)

</details>

<details>
<summary>👥 <b>Customer Segments</b></summary>
<br>

- Customers segmented into **New** (1 purchase), **Returning** (2–10), and **Loyal** (10+) groups
- Young Adults and Middle-aged customers contribute the most revenue (~$62K and ~$59K respectively)
- Subscription rate is **27%** across the customer base

</details>

<details>
<summary>🏷️ <b>Discounts & Promotions</b></summary>
<br>

- **43%** of purchases had a discount applied
- `discount_applied` and `promo_code_used` columns were found to be identical — the redundant column was dropped
- Customers who used discounts still spent above the average purchase amount in many cases

</details>

<details>
<summary>📦 <b>Products & Seasons</b></summary>
<br>

- **Blouse, Shirt, and Dress** are the top revenue-generating items
- Revenue is fairly **evenly distributed across all four seasons**
- **Medium (M)** is the most popular size, contributing ~45% of revenue

</details>

---

## 🐍 Data Preparation (Python)

The Jupyter notebook handles data cleaning and feature engineering:

<details>
<summary>📝 <b>Click to view transformations performed</b></summary>
<br>

1. **Missing Values** — Imputed `review_rating` nulls with category-wise median
2. **Column Renaming** — Standardized column names to `snake_case`
3. **Feature: `age_group`** — Binned ages into 4 quartile-based groups: Young Adult, Adult, Middle-aged, Senior
4. **Feature: `purchase_frequency_days`** — Mapped text frequencies to numeric days (e.g., Weekly → 7, Monthly → 30)
5. **Redundancy Removal** — Dropped `promo_code_used` (identical to `discount_applied`)
6. **Database Export** — Loaded cleaned data into PostgreSQL via SQLAlchemy

</details>

---

## 🗃️ SQL Analysis

Ten business-driven SQL queries were written to extract insights from the PostgreSQL database:

<details>
<summary>📝 <b>Click to view all 10 queries</b></summary>
<br>

| # | Query | Purpose |
|---|---|---|
| Q1 | Revenue by Gender | Compare male vs. female total spending |
| Q2 | Discount + High Spenders | Customers who used discounts but spent above average |
| Q3 | Top 5 Rated Products | Products with highest average review ratings |
| Q4 | Standard vs. Express Shipping | Compare average purchase amounts by shipping type |
| Q5 | Subscriber vs. Non-Subscriber | Compare spend and revenue between subscriber groups |
| Q6 | Top 5 Discount Products | Products with highest % of discounted purchases |
| Q7 | Customer Segmentation | Segment customers into New, Returning, and Loyal |
| Q8 | Top 3 Products per Category | Most purchased items within each category |
| Q9 | Repeat Buyers & Subscriptions | Do repeat buyers also tend to subscribe? |
| Q10 | Revenue by Age Group | Revenue contribution by age group |

</details>

---

## 📊 Power BI Dashboard

An interactive dashboard was built in Power BI with filters for Category, Season, Gender, Location, and Age.

<div align="center">

![Customer Shopping Behavior Dashboard](dashboard.pdf)

</div>

### Dashboard Highlights

- **KPI Cards** — Total Revenue, Total Orders, Avg Order Value, Avg Rating, Subscription %, Discount Use %
- **Bar Charts** — Revenue by Item, Category, Payment Method
- **Donut Charts** — Revenue by Size, Customers by Gender
- **Line Chart** — Revenue trend by Age Group
- **Map Visual** — Revenue distribution by U.S. location
- **Interactive Filters** — Slice data by Category, Season, Gender, Location, and Age range

---

## 🚀 Getting Started

### Prerequisites

- Python 3.x
- PostgreSQL (for SQL analysis)
- Power BI Desktop (for dashboard)

### Installation

```bash
# Clone the repository
git clone https://github.com/YOUR_USERNAME/customer-shopping-behavior-analysis.git
cd customer-shopping-behavior-analysis

# Install Python dependencies
pip install -r requirements.txt
```

### Run the Notebook

```bash
jupyter notebook notebooks/Customer_Shopping_Behaviour.ipynb
```

---

## 📝 Project Report

A comprehensive project report is included in the [`reports/`](reports/) folder, covering:

- Problem statement and business context
- Data preparation methodology
- SQL analysis results
- Dashboard walkthrough
- Key findings and business recommendations

---

## 📜 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

<div align="center">

</div>
