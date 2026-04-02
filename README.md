# 📊 Sales Performance Analysis Dashboard

> Turning raw sales data into actionable business insights using Power BI & DAX

---

## 🚀 Project Summary
This project simulates a real-world sales analytics scenario where business stakeholders need visibility into revenue performance, customer behavior, and operational inefficiencies.

Using a structured data model and interactive dashboards, this solution identifies **growth trends, revenue leakage, and optimization opportunities**.

---

## 🎯 Problem Statement
Businesses often struggle with:
- Lack of clarity on **true revenue (after returns & discounts)**
- Increasing **return rates impacting profitability**
- Difficulty identifying **high-performing vs loss-making regions**
- Limited visibility into **customer buying patterns**

👉 This dashboard solves these problems with clear, actionable insights.

---

## 🧠 Key Business Questions Answered

- How is revenue trending over time?
- What percentage of revenue is lost due to returns and discounts?
- Which regions contribute most to profit vs loss?
- When do customers purchase the most?
- How external factors (like temperature) influence sales?

---

## 📌 Key KPIs

| KPI | Description |
|-----|------------|
| Total Orders | Total number of unique orders |
| Gross Sales | Total revenue before deductions |
| Net Sales | Revenue after discounts and returns |
| Return Rate % | Percentage of returned orders |
| Erosion % | Revenue loss due to discounts & returns |
| AOV | Average revenue per order |
| Loss % | Regional loss contribution |

---

## 🏗️ Data Model Design

- Implemented a **Star Schema**
- Fact Tables:
  - Fact Sales
  - Fact Returns  
- Dimension Tables:
  - Date
  - Region
  - Product
  - Temperature  

👉 Custom relationship created using:
```DAX
Temperature Key = 
RELATED('Sales Territory'[Sales Territory Region]) 
& RELATED(Dates[Month Number Of Year])
```

---

## ⚙️ DAX Measures (Core Logic)

```DAX
Gross Sales = SUM('Fact Sales'[Sales Amount])
Total Discount = SUM('Fact Sales'[Discount Amount])
Total Return Amount = SUM('Fact Returns'[Return Amount])

Net Sales = [Gross Sales] - [Total Discount] - [Total Return Amount]

Return Rate = DIVIDE([Total Return],[Total Order])

Erosion Amount = [Total Discount] + [Total Return Amount]
Erosion % = DIVIDE([Erosion Amount], [Gross Sales])

AOV = DIVIDE([Net Sales],[Total Order])

Loss % = DIVIDE([Erosion Amount],[Gross Sales])

Total Order = DISTINCTCOUNT('Fact Sales'[Sales Order Number])

day_type = IF(WEEKDAY(Dates[Date],2) <= 5, "WeekDay","WeekEnd")
```

---

## 📊 Analysis Performed

- 📈 Year-over-Year Sales Growth Analysis  
- 🔄 Return Rate & Revenue Erosion Analysis  
- 🌍 Regional Performance Benchmarking  
- 📅 Time-Based Sales Trend (Monthly & Weekly)  
- 🌡️ External Factor Analysis (Temperature Impact)  

---

## 🔍 Key Insights

- 📈 **Strong Revenue Growth:** Sales increased significantly over time  
- ⚠️ **Rising Return Rate:** Major contributor to revenue loss  
- 💸 **Erosion Impact:** Discounts + returns reduce overall profitability  
- 🌍 **Regional Gap:** High sales regions also show higher loss %  
- 📅 **Peak Season:** June–July shows highest sales activity  
- 🗓️ **Customer Behavior:** Weekdays outperform weekends  
- 🌡️ **Temperature Effect:** Warm conditions drive higher sales  

---

## 💡 Business Recommendations

- 🎯 Focus promotions during **peak months (June–July)**  
- ⚠️ Reduce return rates via **quality checks & better product info**  
- 📍 Optimize strategies for **high-loss regions**  
- 🗓️ Allocate resources more on **weekday demand peaks**  

---

## 🛠️ Tools & Technologies

- **Power BI**
  - Data Modeling (Star Schema)
  - Advanced DAX Measures
  - Interactive Dashboard Design
  - 
- **CSV Files**
  - Source data storage  

- **GitHub**
  - Documentation & version control  

---

## 📈 Business Value Delivered

- Improved visibility into **true revenue performance**
- Identified **hidden revenue leakage**
- Enabled **data-driven decision making**
- Highlighted **optimization opportunities across regions & time**

---

## ⭐ Support

If you found this project useful, please consider giving it a ⭐  
It helps others discover the project and supports my work!
