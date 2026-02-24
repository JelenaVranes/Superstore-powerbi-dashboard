# 📊 Sales Insights Dashboard – Power BI Project

## 🧩 Overview
This project presents a sales performance analysis using **Power BI** and the **Superstore Sales** dataset. 
The goal is to deliver an executive-friendly dashboard that highlights revenue trends, profitability, top products, and customer behavior across regions and segments.

The dashboard enables:
- Tracking sales and profit over time 
- Monitoring key KPIs (Sales, Profit, Margin, YoY) 
- Analyzing product and sub-category performance 
- Understanding customer segments and regional distribution 
- Identifying seasonality and anomalies 

---

## 🗂 Dataset
Dataset: **Superstore Sales** (public). 
Typical columns include:
- `Order Date`, `Ship Date`
- `Category`, `Sub-Category`
- `Region`, `State`
- `Segment`
- `Customer Name`
- `Sales`, `Profit`, `Quantity`, `Discount`

A copy of the dataset is available in the **/data** folder.

---

## 🔧 Data Preparation & Modeling

### Power Query (Data Cleaning)
- Validated data types (dates, numbers, text)
- Removed duplicates where applicable
- Created a dedicated **Date** table (Year, Month, Quarter)
- Standardized column names where needed

### Data Model
Implemented a star schema:
- **FactSales** (fact table)
- **DimDate**, **DimCustomer**, **DimProduct**, **DimRegion** (dimensions)

Relationships:
- `FactSales[Order Date]` → `DimDate[Date]` (Many-to-One)
- Additional relationships to dimensions depending on the dataset structure

---

## 🧮 DAX Measures
Core measures used in the report:

```DAX
Total Sales = SUM(FactSales[Sales])

Total Profit = SUM(FactSales[Profit])

Profit Margin = DIVIDE([Total Profit], [Total Sales])

YoY Sales = 
CALCULATE([Total Sales], DATEADD(DimDate[Date], -1, YEAR))

YoY Sales % = 
DIVIDE([Total Sales] - [YoY Sales], [YoY Sales])

Avg Discount = AVERAGE(FactSales[Discount])

Sales vs Profit Delta = [Total Sales] - [Total Profit]
Show more lines
________________________________________
📈 Report Pages
1) Sales Overview
•	KPIs: Total Sales, Total Profit, Profit Margin, YoY Sales %
•	Sales Trend (monthly)
•	Sales by State (map)
•	Sales by Category (bar)
•	Slicers: Year, Region, Category
2) Product Performance
•	Top 10 Products by Sales
•	Profit by Sub-Category
•	Sales vs Profit (scatter)
•	Discount impact (Avg Discount card)
•	Sales by Category, Sub-Category and Product Name (Decomposition Tree)
3) Customer Insights
•	Top Customers by Revenue (table)
•	Sales by Segment
•	Sales by State
________________________________________
🖼 Screenshots
Visuals are included in the /visuals folder:
•	overview.png
•	product_performance.png
•	customer_insights.png
________________________________________
💡 Sample Insights (illustrative)
•	Technology category drives the highest revenue share, with strong YoY growth.
•	Excessive discounts reduce profit margin significantly for certain sub-categories.
•	Corporate segment shows the strongest profitability.
•	Sales show strong Q4 seasonality.
Note: Your insights will vary depending on filters and chosen time windows.
________________________________________
🧠 Tech Stack
•	Power BI Desktop
•	Power Query
•	DAX
•	GitHub
________________________________________
📥 How to Use
1.	Download the .pbix file from /pbix.
2.	Open it in Power BI Desktop.
3.	Ensure the dataset in /data is connected (update source if needed).
________________________________________
📬 Contact
If you’d like to connect or discuss improvements, feel free to reach out via GitHub Issues or Discussions.


