Walmart Sales Data Analysis | SQL + Python
📌 Overview
This project is a complete end-to-end data analysis pipeline using SQL and Python to derive actionable business insights from Walmart sales data. It showcases real-world data analyst tasks, including data cleaning, transformation, loading into SQL databases, and writing complex queries to solve business problems.

💼 Key Skills Demonstrated
Data Cleaning & Preprocessing (Python, Pandas)

SQL Querying (MySQL & PostgreSQL)

Feature Engineering

EDA (Exploratory Data Analysis)

Business Intelligence Reporting

Data Pipeline Creation

🧰 Tools & Technologies
Languages: Python, SQL

Databases: MySQL, PostgreSQL

Libraries: pandas, numpy, sqlalchemy, mysql-connector-python, psycopg2

Others: Jupyter Notebook, Kaggle API, VS Code

🧱 Project Structure
bash
Copy
Edit
walmart-sales-analysis/
├── data/                 # Raw & cleaned datasets
├── notebooks/            # Python notebooks for analysis
├── sql_queries/          # SQL scripts for business questions
├── main.py               # Python script for data cleaning & loading
├── requirements.txt      # Python dependencies
└── README.md             # Project documentation
🔄 Workflow Summary
1. Data Acquisition
Pulled dataset using Kaggle API

Stored raw data locally for transformation

2. Data Cleaning (Python)
Removed duplicates and handled missing values

Converted data types (dates, prices)

Formatted currency and numerical fields

3. Feature Engineering
Added Total_Amount = Quantity × Unit_Price to streamline analysis

4. Load into SQL
Loaded cleaned data into MySQL and PostgreSQL using SQLAlchemy

Verified accuracy using test queries

5. SQL Business Analysis
Wrote SQL queries to address key business questions:

📈 Sales trends across branches and categories

🛍️ Top 5 best-selling product types
'''sq
query = """
SELECT product_name, SUM(quantity) AS total_units_sold
FROM walmart
GROUP BY product_name
ORDER BY total_units_sold DESC
LIMIT 5;
"""
pd.read_sql_query(query, conn)
'''


🕒 Peak shopping times by hour and weekday

💳 Payment method preferences

💰 Profit margins by branch

📊 Sample Insights
Replace with actual results from your analysis.

Branch B had the highest revenue contribution.

Health & Beauty was the top-performing category.

Evenings (6 PM – 9 PM) were the peak shopping hours.

E-wallets were the most preferred payment method.

✅ Getting Started
bash
Copy
Edit
git clone <your-repo-url>
cd walmart-sales-analysis
pip install -r requirements.txt
Set up your Kaggle API and follow the steps in main.py or the Jupyter notebooks.

📈 Outcome
This project demonstrates a full cycle of data analysis, from raw data handling to SQL-based business intelligence. It's designed to reflect the tasks a data analyst would perform in a real-world business environment.
