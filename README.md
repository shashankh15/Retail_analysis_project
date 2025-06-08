# Retail_analysis_project

# 🛍️ Retail Sales Analytics System

A real-world retail analytics dashboard built using **Power BI + SQL** on the popular Superstore dataset.  
This project simulates the work of a data analyst inside an MNC, analyzing revenue trends, return behavior, product performance, and customer segments.

---

## 📌 Project Objectives

- Analyze performance across regions, products, and customer types
- Visualize key business metrics: revenue, profit, returns, quantity, discount
- Detect return-related losses, delivery lags, and discount abuse
- Build a fully interactive Power BI dashboard with KPI cards, charts, and filters

---

## 🧠 Tools & Tech Stack

- **Power BI** – dashboard creation & visual storytelling
- **MySQL** – advanced queries for business logic
- **Excel / CSV** – data source (Superstore Dataset)
- **Data Modeling** – relationships, filters, top N logics

---

## 🔥 SQL Queries Used 

 1. 🏆 Top 5 Products by Revenue
```sql
SELECT 
  p.ProductName,
  SUM(od.Quantity * p.Price) AS Revenue
FROM OrderDetails od
JOIN Products p ON od.ProductID = p.ProductID
GROUP BY p.ProductName
ORDER BY Revenue DESC
LIMIT 5;


 2. 📍 Revenue by Region
sql
Copy
Edit
SELECT 
  o.Region,
  ROUND(SUM(od.Quantity * p.Price * (1 - od.Discount)), 2) AS TotalRevenue
FROM Orders o
JOIN OrderDetails od ON o.OrderID = od.OrderID
JOIN Products p ON od.ProductID = p.ProductID
GROUP BY o.Region
ORDER BY TotalRevenue DESC;


3. ⏱️ Avg Delivery Days per Region
sql
Copy
Edit
SELECT 
  Region,
  ROUND(AVG(DATEDIFF(DeliveryDate, OrderDate)), 2) AS AvgDeliveryDays
FROM Orders
GROUP BY Region;


4. 🧍 Revenue by Customer Segment
sql
Copy
Edit
SELECT 
  c.Segment,
  SUM(od.Quantity * p.Price * (1 - od.Discount)) AS SegmentRevenue
FROM Orders o
JOIN Customers c ON o.CustomerID = c.CustomerID
JOIN OrderDetails od ON o.OrderID = od.OrderID
JOIN Products p ON od.ProductID = p.ProductID
GROUP BY c.Segment
ORDER BY SegmentRevenue DESC;


5. 🔁 Return Rate by Region
sql
Copy
Edit
SELECT 
  o.Region,
  COUNT(r.OrderID) * 100.0 / COUNT(DISTINCT o.OrderID) AS ReturnRate
FROM Orders o
LEFT JOIN Returns r ON o.OrderID = r.OrderID
GROUP BY o.Region;


📊 Power BI Dashboard Highlights
6 KPI Cards: Revenue, Orders, Quantity, Discount, Profit Margin, AOV
Dynamic filters: Region, Segment, Category, Date Range

Visuals:
Bar: Revenue by Region
Pie: Segment Revenue
Line: Monthly Revenue Trends
Bar: Top 5 Product Sales
Clean layout, professional formatting, and business insights panel


💡 Key Business Insights
🔸 West region generates the most revenue but highest return rate
🔸 Corporate customers contribute over 50% of total revenue
🔸 Canon 2200 series alone generated ₹62K in sales
🔸 Discounts above 30% correlate with low-profit orders

🤝 Let's Connect!
If you found this project insightful or have feedback to share, feel free to connect or drop a ⭐ on this repo!

📬 Contact
📧 Email: hosmanishashank1517@gmail.com
💼 LinkedIn: www.linkedin.com/in/shashank-hosmani-7b31a6317
