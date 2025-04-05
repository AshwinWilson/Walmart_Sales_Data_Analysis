
# 🏬 Walmart Sales Data Analysis

This end-to-end data analytics project focuses on uncovering **key business insights** from Walmart sales data using **Python**, **Pandas**, **SQLite**, and **SQL**. It simulates a real-world data analysis pipeline, ideal for aspiring or professional data analysts.

---

## 🔧 1. Project Environment Setup

**Tools Used:**  
Visual Studio Code (VS Code), Python 3.8+, SQLite (or optional MySQL/PostgreSQL)

**Goal:**  
Set up a clean and structured workspace for smooth development and collaboration.

<pre>
project/
│-- data/           # Raw and processed datasets
│-- notebooks/      # Jupyter Notebooks for EDA and analysis
│-- sql_queries/    # All SQL scripts used in the project
│-- README.md       # Project documentation
│-- requirements.txt# Required Python libraries
</pre>

---

## 📥 2. Dataset Acquisition

- **Data Source:** [Walmart Sales Dataset on Kaggle](https://www.kaggle.com/)
- **Storage:** Save the dataset in the `data/` folder for easy access and versioning.

---

## 📦 3. Install Required Libraries

Install the necessary Python packages:

```bash
pip install pandas numpy sqlalchemy sqlite3
```

For optional MySQL or PostgreSQL support:

```bash
pip install mysql-connector-python psycopg2
```

---

## 🔍 4. Exploratory Data Analysis (EDA)

Understand the dataset's structure and initial quality:

```python
df.info()
df.describe()
df.head()
```

---

## 🧹 5. Data Cleaning

- **Remove Duplicates:** Eliminated duplicate rows to ensure accurate analysis.
- **Handle Missing Values:** Dropped or imputed missing values based on significance.
- **Fix Data Types:** Converted fields like `date` to `datetime`, and `unit_price` to `float`.
- **Currency Formatting:** Removed `$` signs using regex:
  ```python
  df['unit_price'] = df['unit_price'].replace(r'[\$,]', '', regex=True).astype(float)
  ```
- **Validation:** Confirmed data consistency and fixed formatting issues.

---

## ⚙️ 6. Feature Engineering

Created a `total_amount` column for easier revenue and profit analysis:

```python
df['total_amount'] = df['unit_price'] * df['quantity']
```

---

## 🗃️ 7. Load Cleaned Data into SQLite

```python
import sqlite3
conn = sqlite3.connect("walmart_sales.db")
df.to_sql("walmart", conn, if_exists="replace", index=False)
```

---

## 📊 8. SQL-Based Business Analysis

### 1️⃣ Total Revenue by Branch
```sql
SELECT Branch, ROUND(SUM(unit_price * quantity), 2) AS total_revenue
FROM walmart
GROUP BY Branch
ORDER BY total_revenue DESC;
```

### 2️⃣ Monthly Sales Trend by Category
```sql
SELECT strftime('%Y-%m', date) AS month, category,
       ROUND(SUM(unit_price * quantity), 2) AS total_sales
FROM walmart
GROUP BY month, category
ORDER BY month, total_sales DESC;
```

### 3️⃣ Revenue by Payment Method
```sql
SELECT payment_method, COUNT(*) AS total_transactions,
       ROUND(SUM(unit_price * quantity), 2) AS total_sales
FROM walmart
GROUP BY payment_method
ORDER BY total_sales DESC;
```

### 4️⃣ Average Transaction Value per Branch
```sql
SELECT Branch, ROUND(AVG(unit_price * quantity), 2) AS avg_transaction_value
FROM walmart
GROUP BY Branch
ORDER BY avg_transaction_value DESC;
```

### 5️⃣ Estimated Profit by Category
```sql
SELECT category,
       ROUND(SUM(unit_price * quantity * profit_margin), 2) AS estimated_profit
FROM walmart
GROUP BY category
ORDER BY estimated_profit DESC;
```

### 6️⃣ Peak Hours by Quantity Sold
```sql
SELECT strftime('%H', time) AS hour,
       SUM(quantity) AS total_quantity
FROM walmart
GROUP BY hour
ORDER BY total_quantity DESC;
```

### 7️⃣ Top-Selling Cities
```sql
SELECT City,
       ROUND(SUM(unit_price * quantity), 2) AS total_sales
FROM walmart
GROUP BY City
ORDER BY total_sales DESC;
```

### 8️⃣ High-Rated Categories
```sql
SELECT category,
       ROUND(AVG(rating), 2) AS avg_rating
FROM walmart
GROUP BY category
ORDER BY avg_rating DESC;
```

---

## 📈 9. Results and Insights

### 🔹 **Sales Insights**
- Identified **top-performing product categories** by total revenue.
- Found branches with the **highest overall sales**, indicating key performing regions.
- Analyzed **preferred payment methods** across customer demographics.

### 🔹 **Profitability**
- Estimated **profit margins by category and location**.
- Pinpointed the **most profitable store branches** for strategic investment.

### 🔹 **Customer Behavior**
- Tracked **customer satisfaction** through average ratings.
- Highlighted **peak shopping hours** to optimize staffing and inventory.
- Identified **payment preferences** across branches and customer segments.

---

## 🚀 10. Future Enhancements

- **Interactive Dashboard**: Integrate Power BI or Tableau for real-time visual insights.
- **Data Enrichment**: Include customer profiles, marketing campaign data, and seasonal trends.
- **Automation**: Build an **automated data pipeline (ETL)** to support real-time analysis.

---

## ✅ Outcome

This project simulates the work of a real-world **data analyst** — from raw data ingestion and cleaning to SQL-based business intelligence reporting. It's ideal for showcasing analytical thinking, SQL querying, data preprocessing, and insight generation in a business context.
