#  Business 360 – Sales, Profit & Performance Dashboard

Business 360 is an **end-to-end Sales Analytics project** that provides a complete view of business performance across **sales, profit, quantity, orders, margins, customers, products, regions, and payment modes** using **Power BI, SQL, and Python**.

This project is designed for **Data Analyst / Business Analyst** roles and focuses on real-world business KPIs and decision-making insights.

---

## 🔹 Project Objective
To build a **360° interactive dashboard** that helps stakeholders:
- Monitor overall business performance
- Identify top & bottom products and customers
- Analyze category, region, and city-wise sales
- Understand discount impact on profit margins
- Track trends by month, week, and year

---

## 🔹 Tools & Technologies
- **Power BI** – Dashboard design, DAX measures
- **SQL** – Data aggregation & analysis
- **Python (Pandas)** – Data cleaning & transformation
- **Excel / CSV** – Raw data source

---

## 🔹 Key KPIs
| KPI | Value |
|----|------|
| Total Sales | 534M |
| Total Profit | 80M |
| Profit Margin | 15% |
| Total Quantity | 15K |
| Total Orders | 5K |

Month-over-month (LM) comparison is included for all KPIs.
![business1](https://github.com/dstar211/Business-360-/blob/main/business%20360%201.jpg)
---

## 📊 Dashboard Pages & Insights 


### 1️⃣ Sales Overview Page
**Key Features**
- Total Sales, Profit, Quantity, Orders & Profit Margin
- City-wise total sales with highest profit product
- Region-wise sales contribution
- Top & Bottom customers by sales
- Weekly insights: Avg Discount vs Profit Margin

**Business Insights**
- Sales are well distributed across regions, with **North & East contributing the highest**
- High discounts on specific days reduce profit margins
- A small number of customers contribute significantly to total sales

---
![business](https://github.com/dstar211/Business-360-/blob/main/business%202.jpg)


### 2️⃣ Product & Category Performance Page
**Key Features**
- Top 10 products by total profit and profit margin
- Top & Bottom sub-category sales
- Category-wise sales and average discount
- Category quantity vs total orders
- Best-selling category by month

**Business Insights**
- **Home Decor and Furniture** generate the highest sales
- Some products show high sales but lower margins due to discounts
- Monthly trends highlight peak sales periods for specific categories

--- 
![business](https://github.com/dstar211/Business-360-/blob/main/buiness%203.jpg)

### 3️⃣ Yearly, Regional & Payment Analysis Page
**Key Features**
- Year-wise sales & profit comparison
- Top & Bottom categories by sales
- Region-wise profit and quantity analysis
- Payment mode contribution (COD, Net Banking, etc.)
- Monthly sales & quantity trends

**Business Insights**
- Strong growth observed in recent years
- **North region** leads in profit contribution
- Sales are evenly split across payment modes, reducing dependency risk

---
![business](https://github.com/dstar211/Business-360-/blob/main/business%204.jpg)

## 🔄 Project Workflow
```text
Raw Data (Excel / CSV)
        ↓
SQL (Joins, Aggregations, Grouping)
        ↓
Python (Cleaning, Feature Engineering)
        ↓
Power BI (DAX Measures & Visuals)
        ↓
Interactive Business 360 Dashboard

/* OBJECTIVE: Calculate Net Sales and Profit Margin by Region 
  PROJECT: Business 360 
*/

SELECT 
    dim_customer.region,
    ROUND(SUM(fact_sales.net_sales), 2) AS total_net_sales,
    ROUND(AVG(fact_sales.margin_pct), 4) AS avg_margin
FROM 
    gdb041.fact_sales_monthly AS fact_sales
JOIN 
    gdb041.dim_customer AS dim_customer
    ON fact_sales.customer_code = dim_customer.customer_code
WHERE 
    fact_sales.fiscal_year = 2021
GROUP BY 
    dim_customer.region
ORDER BY 
    total_net_sales DESC;
