📊 E-Commerce Analytics Using SQL & Python
🔍 Project Summary:

An end-to-end data analytics project that explores E-commerce sales using SQL for data extraction and Python for analysis and visualization. It highlights how business insights—like top customers, revenue growth, and payment trends—can be derived from real transactional data.

🚀 Project Overview

This project focuses on analyzing E-commerce sales and payment data to identify top-spending customers, annual revenue trends, and business insights.
It demonstrates how SQL and Python work together to transform raw data into clear, data-driven decisions.

🧠 Objectives

Analyze yearly revenue and payment patterns.

Identify the top 3 customers for each year.

Visualize customer spending and business performance.

Build an end-to-end workflow — from SQL queries to final insights.

🗃️ Tools & Technologies

SQL → Data Extraction & Aggregation

Python (Pandas, Seaborn, Matplotlib) → Data Processing & Visualization

MySQL Database → Data Source

Jupyter Notebook → Analysis & Reporting

📈 Key Features

Extracted and analyzed real-time order and payment data.

Ranked customers using SQL’s DENSE_RANK() function.

Visualized yearly top customers and payment trends using Seaborn.

Derived meaningful insights to support data-driven decision-making.

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

📊 Insights Derived

The top 3 customers in each year contribute significantly to total revenue.

Year-over-year payment trends show strong business growth.

Payment data highlights the most-used transaction methods and customer preferences.

⚙️ How to Run This Project

Clone this repository:

git clone https://github.com/abhishekmishra224/ecommerce-sql-python.git
cd ecommerce-sql-python


Install dependencies:

pip install pandas seaborn matplotlib mysql-connector-python


Configure your database connection in the notebook.

Run the Jupyter Notebook:

jupyter notebook SQL-Python-Ecommerce-Project.ipynb


Execute all cells in order to generate SQL results and visualizations.

📸 Visualizations Include

Top Customers by Year (Bar Chart)

Revenue Trends (Line Chart)

Payment Distribution (Pie/Bar Chart)

📘 Learnings

Writing optimized SQL queries for real datasets.

Using Python for cleaning, merging, and analyzing business data.

Designing visual stories that communicate trends effectively.

Applying data analytics to real-world business scenarios.

👨‍💻 Author

Abhishek Mishra
📍 B.Tech in Cloud Computing Engineering | VIT Bhopal
🔗 LinkedIn

💻 GitHub

📧 abhishekk6278@gmail.com
