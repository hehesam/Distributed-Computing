# E-Commerce Data Analytics with PySpark

This project presents a comprehensive data processing and analytics pipeline for an E-commerce dataset using PySpark. It analyzes customer behavior, identifies sales trends, and predicts future revenue. The solution leverages PySpark's parallel processing capabilities across multiple configurations (local and cluster) to evaluate performance efficiency.

## 🧠 Authors

- Bahaar Khalilian  
- Hesam Mohebi

## 📁 Dataset Description

The dataset originates from a UK-based online retailer selling unique gifts. It covers transactions from **Jan 1, 2011 – Dec 31, 2011**, with a focus on UK customers.

- **Total Transactions**: 22,190  
- **Unique Customers**: 4,381 postcodes  
- **Total Records**: 406,830 rows (1 row = 1 item in a transaction)  
- **Average Transactions per Customer**: ~5  
- **Average Items per Transaction**: 18.3

## 📊 Project Goals

> “Design a comprehensive data processing and analytics solution to understand customer behavior, analyze sales trends, and predict future revenue.”

---

## 🔍 Part One: Customer Insights

### Query 1: Top Spending Customers
- Computes total spending per customer (`UnitPrice * Quantity`)
- Displays top 10 customers
- Highlights Pareto distribution (20% of customers → 80% of revenue)

### Query 2: Customer Behavior by Country
- Aggregates total spending and order count per country
- Computes average order size per country
- UK leads in volume, Netherlands shows highest avg order size

---

## 📈 Part Two: Sales Trends and Performance

### Query 3: Monthly Sales Trend
- Aggregates sales by month
- **Peak month**: November 2011
- Seasonal trend captured (holiday surge)

### Query 4: Most Expensive Invoices
- Groups by `InvoiceNo` and calculates total per invoice
- Highlights high-value transactions, mostly from the UK

---

## 🔮 Part Three: Forecasting and Future Planning

### Query 5: Sales Forecasting
- Uses PySpark MLlib’s Linear Regression model
- Predicts daily revenue for next 30 days
- Forecast shows steady increase in daily sales

---

## 🔢 Clustering Analysis

- Performs unsupervised clustering to segment transactions
- Identifies:
  - Low-value purchases (Cluster Purple)
  - High-value/bulk purchases (Cluster Cyan)
  - Product returns (Cluster Yellow)

---

## ⚙️ Runtime Performance Comparison

Performance is evaluated on:
- `local[2]` → 2 threads  
- `local[4]` → 4 threads  
- `local[*]` → all available cores  
- `cluster` → distributed mode

| Configuration | Average Runtime | Suitability |
|---------------|------------------|-------------|
| `local[2]`    | Fastest overall  | ✅ Best for small data |
| `local[4]`    | Slightly slower  | ⚠️ Display lag |
| `local[*]`    | Efficient        | ✅ Optimal local |
| `cluster`     | Slowest due to overhead | ❌ Not suitable for small data |

---

## 📦 Technologies Used

- Python 3.x  
- PySpark  
- MLlib (for regression & clustering)  
- Jupyter Notebook / Spark Shell

---

## 📁 Repository Structure

```bash
.
├── notebooks/
│   └── analysis_queries.ipynb         # Contains all 5 queries and plots
├── data/
│   └── online_retail_2011.csv         # E-commerce transaction dataset
├── src/
│   └── spark_processing.py            # PySpark functions & models

├── README.md
