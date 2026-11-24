#  E-Commerce Sales Insights Dashboard
### Power BI Capstone Project | Anshuk Chaturvedi | KIIT | B.Tech CSE 2023-27

---

## 🧾 Project Overview

This is a 5-page interactive Power BI dashboard built to analyze e-commerce sales data across product categories, regions, and sales channels for the years **2023 and 2024**. The goal was to turn raw transaction data into clear, actionable business insights — covering everything from revenue trends and profitability to geographic performance and order operations.

---

## 🗂️ Files in This Repository

| File | Description |
|------|-------------|
| `EcommerceSalesInsights_Dashboard.pbix` | Main Power BI dashboard file |
| `Ecommerce_Sales_Dataset.xlsx` | Source dataset (3 sheets: Orders, Customers, Targets) |
| `ProjectDoc_LowPlag_AnshukChaturvedi.pdf` | Full project documentation PDF |

---

## 🎯 Problem Statement

Most e-commerce businesses collect huge amounts of transaction data but struggle to make sense of it quickly. Managers can't easily answer questions like:
- Which product categories are actually profitable?
- Are we hitting our monthly sales targets?
- Does giving discounts hurt our profit margins?
- Which cities and regions are underperforming?

This dashboard solves all of that in one place.

---

## 📁 Dataset Description

A custom synthetic dataset was built to simulate a realistic Indian e-commerce business.

| Table | Rows | Description |
|-------|------|-------------|
| Orders | 2,000 | All transactions with sales, profit, discount, channel, status |
| Customers | 1,276 | Customer profiles with age, gender, tier, lifetime spend |
| Targets | 168 | Monthly sales targets per category for 2023–2024 |

**Categories:** Electronics, Clothing, Home & Kitchen, Sports, Books, Beauty, Toys  
**Regions:** North, South, East, West, Central  
**Cities:** Delhi, Mumbai, Chennai, Bangalore, Kolkata, Pune, Hyderabad + more  
**Channels:** Website, Mobile App, Marketplace, Social Media  

---

## 🖥️ Dashboard Pages

| Page | Title | Key Visuals |
|------|-------|-------------|
| 1 | Executive Overview | 4 KPI Cards, Bar Chart, Line Chart, Year Slicer |
| 2 | Channel & Segment | Donut Chart, Matrix, Stacked Bar, Category Slicer |
| 3 | Profitability Analysis | Waterfall Chart, Scatter Plot, KPI Cards, Quarter Slicer |
| 4 | Geographic Insights | India Map, City Bar Chart, Region Slicer |
| 5 | Operations & Orders | Funnel Chart, Detail Table, Return Rate KPI, Slicers |

---

## 🧮 DAX Measures

All 9 custom measures written for this project:

```dax
Total Sales = SUM(Orders[Net_Sales])

Total Profit = SUM(Orders[Profit])

Total Orders = COUNTROWS(Orders)

Profit Margin % = DIVIDE([Total Profit], [Total Sales], 0) * 100

Avg Order Value = DIVIDE([Total Sales], [Total Orders], 0)

Return Rate % = DIVIDE(
    CALCULATE(COUNTROWS(Orders), Orders[Order_Status] = "Returned"),
    [Total Orders], 0) * 100

Sales vs Target = [Total Sales] - SUM(Targets[Sales_Target])

YTD Sales = TOTALYTD([Total Sales], Orders[Order_Date])

MoM Growth % =
VAR CurrentMonth = [Total Sales]
VAR PrevMonth = CALCULATE([Total Sales], DATEADD(Orders[Order_Date], -1, MONTH))
RETURN DIVIDE(CurrentMonth - PrevMonth, PrevMonth, 0) * 100
```

---

## 🔗 Data Model Relationships

```
Orders ──── (Customer_ID) ────► Customers   [Many-to-One]
Orders ──── (Category)    ────► Targets     [Many-to-Many]
```

---

## 💡 Key Insights from the Data

- **Electronics** dominates with 65%+ of total revenue due to high unit prices
- **South & North** regions lead in sales; Central region is the weakest
- Discounts above **25%** consistently lead to reduced or negative profit margins
- All **4 sales channels** contribute almost equally (~25% each)
- **Return rate is 20.85%** — highest in Electronics and Clothing
- Monthly actuals **fall short of targets** every month — targets may be set too aggressively

---

## 🛠️ Tech Stack

- **Microsoft Power BI Desktop** — Dashboard & visualizations
- **Power Query Editor** — Data transformation
- **DAX** — Custom KPI measures
- **Microsoft Excel** — Data source
- **Python (pandas, openpyxl)** — Dataset generation

---

## 🚀 How to Open This Project

1. Download and install [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free)
2. Clone or download this repository
3. Open `EcommerceSalesInsights_Dashboard.pbix` in Power BI Desktop
4. If prompted, update the data source path to point to `Ecommerce_Sales_Dataset.xlsx`
5. Click **Refresh** to load all data

---

## 👤 Author

**Anshuk Chaturvedi**  
Roll No: 23051575  
B.Tech Computer Science Engineering (2023–2027)  
Kalinga Institute of Industrial Technology (KIIT)

---

> *Capstone Project — April 2026*
