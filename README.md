📊 E-Commerce Analytics Using SQL & Python
-->This project dives deep into real-world E-commerce data to uncover insights about customer behavior, revenue patterns, and top-spending customers using a combination of SQL and Python. It demonstrates how data analysts turn raw transactional data into meaningful business intelligence.

🚀 Project Overview
-->The goal of this project is to analyze E-commerce sales and payment data using SQL queries for data extraction and Python for analysis and visualization.
It focuses on identifying the top 3 customers each year based on total spending, along with trends that can help businesses improve decision-making and customer retention.

🧠 Objectives
Analyze yearly revenue and payment trends.
Identify top-spending customers across different years.
Visualize business performance with clean, readable charts.
Build an end-to-end data pipeline — from SQL to insights.

🗃️ Tools & Technologies

SQL → Data Extraction & Aggregation
Python (Pandas, Seaborn, Matplotlib) → Data Processing & Visualization
Jupyter Notebook → Analysis & Reporting
MySQL Database → Data Source

📈 Key Features

Data Extraction: Fetched order and payment details directly from SQL database.
Customer Ranking: Used DENSE_RANK() to identify top 3 customers by payment each year.
Visualization: Created insightful bar charts and yearly comparisons using Seaborn.
Insight Generation: Highlighted customer contribution patterns and annual growth trends.

🧮 Example SQL Query
SELECT 
    years,
    customer_id,
    payment,
    d_rank
FROM (
    SELECT 
        YEAR(o.order_purchase_timestamp) AS years,
        o.customer_id,
        SUM(p.payment_value) AS payment,
        DENSE_RANK() OVER (
            PARTITION BY YEAR(o.order_purchase_timestamp)
            ORDER BY SUM(p.payment_value) DESC
        ) AS d_rank
    FROM orders o
    JOIN payments p
        ON p.order_id = o.order_id
    GROUP BY YEAR(o.order_purchase_timestamp), o.customer_id
) AS ranked
WHERE d_rank <= 3;

🧩 How to Run This Project

1.Clone this repository:
git clone https://github.com/abhishekmishra224/ecommerce-sql-python.git
cd ecommerce-sql-python

2.Install dependencies:
pip install pandas seaborn matplotlib mysql-connector-python

3.Configure your database connection in the notebook.

4.Run the Jupyter Notebook:
jupyter notebook SQL-Python-Ecommerce-Project.ipynb

5.Execute each cell sequentially to generate queries and visualizations.

📸 Visualizations Include
#Top Customers by Year (Bar Chart)
#Revenue Trends by Year
#Payment Distribution Overview

📘 Learnings
#Practical experience in SQL query optimization and data aggregation.
#Hands-on exposure to data visualization and storytelling using Python.
#Improved understanding of data-driven business insights and reporting.


👨‍💻 Author
Abhishek Mishra
📍 B.Tech in Cloud Computing Engineering | VIT Bhopal
🔗 LinkedIn
💻 GitHub
📧 abhishekk6278@gmail.com
