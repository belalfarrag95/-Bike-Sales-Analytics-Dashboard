# 🚴 Bike Sales Analytics Dashboard

An interactive Power BI dashboard for analyzing bike sales performance, built with custom DAX time-intelligence measures, dynamic filtering, and a fully branded HTML/CSS visual design.

---

## 📊 Overview

This dashboard provides a 360° view of bike sales performance across products, categories, and time periods. It's built around three main report pages plus a custom-designed welcome screen, allowing stakeholders to explore revenue, orders, profit, and returns with month-over-month comparisons.

**Key Metrics Tracked:**
- 🛒 Total Orders: 56K
- 💰 Revenue: 24.91M
- 📈 Profit: 10.46M
- 📦 Quantities Sold: 84K
- 🔄 Returns: 1,809

---

## 🖼️ Dashboard Preview

### Welcome Page
![Welcome Page](screenshots/1_welcome_page.jpg)

### Summary Page
![Summary Page](screenshots/2_summary_page.jpg)

### Categories Page
![Categories Page](screenshots/3_categories_page.jpg)

### Returns Page
![Returns Page](screenshots/4_returns_page.jpg)

---

## ✨ Features

- **Custom Welcome Page** — Branded navigation screen with animated icons and section buttons (Summary, Categories, Returns)
- **Time Intelligence Measures** — Month-over-month comparisons using `PREVIOUSMONTH` and `DATEADD` DAX functions
- **Dynamic Filtering** — Interactive slicers for Year, Continent, Country, Category, and Subcategory
- **KPI Cards** — At-a-glance metrics for Orders, Revenue, Profit, Quantities, and Returns
- **Treemap & Bar Charts** — Category and subcategory breakdowns by orders
- **Drill-down Table** — Category → Subcategory → Product hierarchy with revenue and profit
- **Returns Analysis** — Dedicated page tracking returns by date, subcategory, and category with a donut chart
- **Forecast Visualization** — Trend line with forecast band on the Total Returns chart

---

## 🗂️ Data Model

The dataset follows a star schema with a central `Sales` fact table connected to `Products`, `Customers`, `Territories`, `Returns`, and a custom `Calendar` date table.

![Data Model](documentation/data_model.png)

**Tables:**
- `Calendar` (custom date table)
- `Sales` (fact table)
- `Returns` (fact table)
- `Products`
- `Product_Subcategories`
- `Product_Categories`
- `Customers`
- `Territories`

---

## 🧮 Key DAX Measures

![Measures List](documentation/measures_list.png)

```dax
Previous Month Revenue = 
CALCULATE(
    [TotalRevenue],
    PREVIOUSMONTH('Calendar'[Date])
)
```

```dax
Previous Month Orders = 
CALCULATE(
    [TotalOrders],
    DATEADD('Calendar'[Date], -1, MONTH)
)
```

```dax
TotalRevenue = 
SUMX(Sales, Sales[OrderQuantity] * Sales[ProductPrice])
```

Other measures include: `TotalOrders`, `TotalProfit`, `TotalQuantites`, `TotalReturns`, `ReturnQuantities`, `TotalCost`, and `avg product price`.

---

## 🛠️ Tools & Technologies

- **Power BI Desktop** — Data modeling & visualization
- **DAX** — Time intelligence & calculated measures
- **Power Query (M)** — Data cleaning & transformation
- **HTML/CSS Visuals** — Custom-branded welcome page and KPI elements

---

## 📁 Data Source

The dataset used for this project is sales data from a bicycle retail company, used strictly for educational and analytical/portfolio purposes.

---

## 📬 Contact

**Belal Farrag** — Data Analyst  
🔗 [LinkedIn](https://www.linkedin.com/in/belal-farrag-b976b01a4/)
