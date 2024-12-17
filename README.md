# Pizza-Sales-Dashboard-Analysis
![image](https://github.com/user-attachments/assets/9a3595c1-af27-4e64-a31c-1ec771ec2521)
## Overview
This project involves the development of a comprehensive Pizza Sales Dashboard, designed to analyze sales performance, identify revenue drivers, and provide actionable insights for business growth. The dashboard integrates SQL queries for data extraction and Power BI for visualization, enabling effective decision-making.


## Problem Statement
The objective is to monitor and analyze pizza sales performance, identify revenue trends, and derive insights to improve customer satisfaction and profitability. The dashboard addresses:
- Total revenue generated.
- Sales trends by day and month.
- Revenue contribution by pizza categories.
- Order volume and customer behavior.



## Steps Followed

1. **Data Extraction and Preparation:**
   - Used SQL to retrieve and aggregate data from the `pizza_sales` table.
   - Derived key metrics such as total revenue, total orders, and average order value using SQL queries.

2. **Data Cleaning and Transformation:**
   - Addressed missing and inconsistent data within SQL queries.
   - Utilized SQL functions like `SUM`, `COUNT`, and `AVG` for calculations.

3. **Data Modeling:**
   - Established relationships between tables in Power BI.
   - Created calculated columns and measures using DAX expressions for KPIs.

4. **Dashboard Design:**
   - Visualized data in Power BI using bar charts, line graphs, and pie charts.
   - Integrated filters for exploring data by day, month, and pizza category.

5. **Iterative Improvements:**
   - Incorporated stakeholder feedback to refine dashboard functionality and aesthetics.



## SQL Queries Used

### 1. Fetch All Sales Data:
```sql
SELECT * FROM pizza_sales;
```

Table 'pizza_sales' has 12 columns and 48,620 rows
![image](https://github.com/kethavath-sandeep/SQL-PowerBI-Project/blob/main/Pizza%20sales.png?raw=true)

### 2. Total Revenue:
```sql
SELECT SUM(total_price) AS total_revenue FROM pizza_sales;
```
![image](https://github.com/kethavath-sandeep/SQL-PowerBI-Project/blob/main/Total%20revenue%20(2).png?raw=true)

### 3. Average Order Value:
```sql
SELECT SUM(total_price)/COUNT(DISTINCT order_id) AS Avg_order_value FROM pizza_sales;
```
![image](https://github.com/kethavath-sandeep/SQL-PowerBI-Project/blob/main/Avg%20Order%20value.png?raw=true)

### 4. Total Pizzas Sold:
```sql
SELECT SUM(quantity) AS total_pizza_sold FROM pizza_sales;
```
![image](https://github.com/kethavath-sandeep/SQL-PowerBI-Project/blob/main/Total%20pizza%20sold.png?raw=true)

### 5. Total Orders:
```sql
SELECT COUNT(DISTINCT order_id) AS total_orders FROM pizza_sales;
```
![image](https://github.com/kethavath-sandeep/SQL-PowerBI-Project/blob/main/Total%20orders.png?raw=true)

### 6. Average Pizzas Per Order:
```sql
SELECT CAST(SUM(quantity) AS DECIMAL(10,2)) / COUNT(DISTINCT order_id) AS Avg_Pizzas_per_order FROM pizza_sales;
```
![image](https://github.com/kethavath-sandeep/SQL-PowerBI-Project/blob/main/Avg%20pizza%20per%20order.png?raw=true)

### 7. Orders by Day of the Week:
```sql
SELECT DATENAME(DW, order_date) AS order_day, COUNT(DISTINCT order_id) AS total_orders 
FROM pizza_sales
GROUP BY DATENAME(DW, order_date);
```
![image](https://github.com/kethavath-sandeep/SQL-PowerBI-Project/blob/main/Orders%20by%20day%20in%20week.png?raw=true)

### 8. Orders by Month:
```sql
SELECT DATENAME(MONTH, order_date) AS Month_Name, COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales
GROUP BY DATENAME(MONTH, order_date)
ORDER BY Total_Orders DESC;
```
![image](https://github.com/kethavath-sandeep/SQL-PowerBI-Project/blob/main/Orders%20by%20months.png?raw=true)

### 9. Revenue by Pizza Category:
```sql
SELECT pizza_category, SUM(total_price) AS total_revenue,
       SUM(total_price) * 100 / (SELECT SUM(total_price) FROM pizza_sales) AS PCT
FROM pizza_sales
GROUP BY pizza_category;
```
![image](https://github.com/kethavath-sandeep/SQL-PowerBI-Project/blob/main/Revenue%20by%20pizza%20catogery.png?raw=true)


## KPIs and Visualizations

### Key Metrics:
1. **Total Revenue:** Overall revenue from pizza sales.
2. **Average Order Value:** Average revenue per order.
3. **Total Pizzas Sold:** Total number of pizzas sold.
4. **Total Orders:** Total unique orders placed.
5. **Average Pizzas Per Order:** Average number of pizzas per order.
6. **Revenue by Pizza Category:** Contribution of each category to total revenue.
7. **Orders by Day and Month:** Trends in customer ordering behavior.

### Visualizations:
- **Bar Charts:** Revenue by pizza category, total orders by day and month.
- **Pie Charts:** Percentage revenue by pizza category.
- **Line Graphs:** Revenue and order trends over time.
- **Tables:** Summary of key metrics.

![image](https://github.com/user-attachments/assets/9a3595c1-af27-4e64-a31c-1ec771ec2521)

![image](https://github.com/user-attachments/assets/9a3595c1-af27-4e64-a31c-1ec771ec2521)

## Insights
1. **Revenue Drivers:** Identify top-performing pizza categories and focus promotional efforts on them.
2. **Order Trends:** Peak orders occur on weekends and specific months, which can guide marketing campaigns.
3. **Customer Behavior:** Average order size and value reveal purchasing patterns.
4. **Growth Opportunities:** Analyze underperforming days and categories to boost sales.



## Challenges Faced
1. **Data Quality Issues:** Addressed missing values and inconsistencies during SQL processing.
2. **Complex SQL Logic:** Ensured precise calculations for metrics like percentages and averages.
3. **Stakeholder Alignment:** Incorporated feedback to meet business requirements.




## Conclusion
The Pizza Sales Dashboard provides actionable insights into sales performance, enabling:
- Better marketing strategies based on sales trends.
- Enhanced decision-making through clear KPIs and visualizations.
- Improved profitability by identifying and addressing growth opportunities.


