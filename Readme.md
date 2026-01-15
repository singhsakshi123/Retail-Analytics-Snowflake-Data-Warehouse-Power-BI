# 🏬 Global Superstore Data Warehouse (Snowflake) + Power BI Dashboards

## 📌 Project Overview
This project builds an **end-to-end analytics solution** for a global retail business by designing a **Snowflake data warehouse** and connecting it to **Power BI dashboards** for scalable and trusted reporting.

Instead of building dashboards directly on raw transactional data, this solution creates a **dimensional model (star schema)** with clean business logic in SQL, enabling fast, consistent, and reliable insights across:
- Sales & profitability
- Product performance
- Customer behavior
- Shipping & delivery efficiency


## 🎯 Business Problem
The business had thousands of transactions across regions, customer segments, and shipping modes, but decision-making was inefficient because:
- KPIs were inconsistently calculated across reports (profit margin, AOV, late delivery rate, etc.)
- Dashboards built on raw data were slow and difficult to scale
- Shipping and customer insights were not cleanly linked to sales outcomes
- No centralized analytics layer existed for consistent reporting


## ✅ Solution Implemented
A scalable analytics architecture was designed using best practices:

- Built a **Snowflake data warehouse** using **dimensional modeling**
- Structured data flow using separate schemas:
  - `RAW_STAGE` → raw ingestion (source truth)
  - `TRANSFORM` → cleaned + business logic
  - `DW` → final analytics-ready tables
- Implemented multiple fact tables aligned to business processes
- Centralized KPI logic in **Snowflake SQL**, not Power BI
- Used Power BI only for dashboarding and interaction


## 🗂️ Data Model (Star Schema)
### Dimensions
- `DIM_DATE` (supports both order & ship date analysis)
- `DIM_CUSTOMER`
- `DIM_PRODUCT`
- `DIM_GEOGRAPHY`
- `DIM_SHIPPING`

### Fact Tables
- `FACT_SALES` (order-product transaction level)
- `FACT_SHIPPING` (order-level delivery performance)
- `FACT_CUSTOMER_MONTHLY` (customer × month aggregation)
- `FACT_PRODUCT_MONTHLY` (product × month aggregation)

This design avoids incorrect aggregations and supports fast analytics at multiple levels.


## 🔄 ETL Pipeline (Snowflake SQL)
The ETL is implemented through modular SQL scripts:

- **Database + Schema setup**
- **Raw staging load**
- **Dimension builds**
- **Fact table builds**
- **Validation checks** (row counts, distinct orders, shipping sanity checks)
- **Final DW load** (clean tables for BI consumption)


## 📊 Power BI Dashboards
Each dashboard maps directly to a business process and a Snowflake fact table:

### 1️⃣ Sales Dashboard
Tracks revenue and profitability trends across categories, regions, and time.
- Powered by: `FACT_SALES`

### 2️⃣ Product Performance Dashboard
Highlights top products, margin drivers, and underperforming sub-categories.
- Powered by: `FACT_PRODUCT_MONTHLY`

### 3️⃣ Customer Insights Dashboard
Analyzes customer segments, average order value, repeat behavior, and profitability.
- Powered by: `FACT_CUSTOMER_MONTHLY`

### 4️⃣ Shipping & Delivery Performance Dashboard
Monitors late deliveries, ship mode efficiency, and logistics cost behavior.
- Powered by: `FACT_SHIPPING`


## 💡 Key Insights Enabled
- Identify categories with **high sales but weak profit margins**
- Detect regions and ship modes responsible for **late deliveries**
- Separate customer segments that drive **volume vs true profitability**
- Highlight products that appear strong in revenue but lose value due to **discounting**
- Improve trust since all KPIs are standardized in Snowflake (single source of truth)


## 🛠️ Tech Stack
- **Programming / Query Language:** SQL  
- **Cloud Data Warehouse:** Snowflake  
- **Visualization / BI:** Power BI  
- **Data Modeling:** Dimensional Modeling (Star Schema)  


## 📊 Dashboard Visuals

<div align="center">
  <img src="Visuals/Sales Dashboard.png" width="450"/>
  <img src="Visuals/Product Performance.png" width="450"/>
</div>

<div align="center">
  <img src="Visuals/Customer Insights.png" width="450"/>
  <img src="Visuals/Shipping & Delivery Performance.png" width="450"/>
</div>
