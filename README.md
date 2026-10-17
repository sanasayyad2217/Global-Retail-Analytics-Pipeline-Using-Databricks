
# Global Retail Analytics Pipeline Using Databricks

An end-to-end retail data engineering project using **Databricks, PySpark, Spark SQL, and Delta Lake**. This project follows the **Medallion Architecture** to ingest, clean, transform, and analyze Global Superstore data.

## Workflow Architecture

![Global Superstore ETL Pipeline Workflow](https://github.com/sanasayyad2217/Global-Retail-Analytics-Pipeline-Using-Databricks/blob/main/ETLIMAGE.png)

## Project Overview

This project implements a three-layer ETL pipeline:

- **Bronze Layer:** Ingests raw Global Superstore CSV data into a Delta table.
- **Silver Layer:** Cleans data, standardizes column names, handles missing values, converts data types, and removes duplicates.
- **Gold Layer:** Creates 16 analytical tables for business intelligence and reporting.

## Technology Stack

- Databricks
- Python
- PySpark
- Spark SQL
- Delta Lake
- CSV

## Data Source

**Dataset:** Global Superstore CSV

Source path in Databricks:

`/Volumes/etlpipelines/default/sana/Global-Superstore - Copy.csv`

## Architecture and Data Flow

```text
Global Superstore CSV
        |
        v
Bronze Layer
etlpipelines.default.bronze_global_superstore
        |
        v
Silver Layer
etlpipelines.default.silver_global_superstore
        |
        v
Gold Layer
etlpipelines.goldetl
        |
        v
Business Analytics and Reporting
```

## Gold Layer Tables

The Gold layer contains 16 analytical tables.

| No. | Table Name | Purpose |
|---:|---|---|
| 1 | `gold_overall_kpis` | Overall business KPIs |
| 2 | `gold_yearly_sales` | Yearly sales and growth |
| 3 | `gold_monthly_sales` | Monthly sales trends |
| 4 | `gold_region_market` | Regional and market performance |
| 5 | `gold_country_state` | Country, state, and city analysis |
| 6 | `gold_product_performance` | Product sales and profitability |
| 7 | `gold_category_subcategory` | Category performance |
| 8 | `gold_customer_performance` | Customer sales and profit |
| 9 | `gold_segment_performance` | Customer segment analysis |
| 10 | `gold_shipping_performance` | Shipping cost and delivery analysis |
| 11 | `gold_order_priority` | Order priority analysis |
| 12 | `gold_discount_analysis` | Discount impact analysis |
| 13 | `gold_profitability_analysis` | Profitability analysis |
| 14 | `gold_top_products` | Top products by category |
| 15 | `gold_customer_retention` | One-time and repeat customers |
| 16 | `gold_order_details` | Detailed order-level records |

## Key Features

- End-to-end ETL pipeline using Medallion Architecture
- Raw data ingestion and Delta table creation
- Data cleaning and transformation with PySpark
- SQL-based analytical aggregations
- Sales, profit, discount, and shipping analysis
- Customer retention analysis
- Product ranking using window functions
- Data validation and Gold table row-count checks
- Analytics-ready datasets for dashboards and reporting

## How to Run

1. Upload the Global Superstore CSV file to a Databricks Volume.
2. Run the Bronze layer notebook to ingest the source data.
3. Run the Silver layer notebook to clean and transform the data.
4. Run the Gold layer script to generate all 16 analytical tables.
5. Validate the tables and execute SQL queries for business insights.

**Note:** Ensure the source path, catalog, schema, and column names match your Databricks environment.

## Example SQL Queries

### Overall Business KPIs

```sql
SELECT *
FROM etlpipelines.goldetl.gold_overall_kpis;
```

### Best-Performing Regions

```sql
SELECT *
FROM etlpipelines.goldetl.gold_region_market
ORDER BY total_sales DESC;
```

### Loss-Making Products

```sql
SELECT
    product_id,
    product_name,
    total_sales,
    total_profit
FROM etlpipelines.goldetl.gold_product_performance
WHERE total_profit < 0
ORDER BY total_profit;
```

### Monthly Sales Trends

```sql
SELECT *
FROM etlpipelines.goldetl.gold_monthly_sales
ORDER BY order_year, order_month;
```

## Learning Outcomes

This project demonstrates practical skills in:

- Data engineering and ETL pipeline development
- Databricks and PySpark
- Spark SQL and Delta Lake
- Data quality and transformation
- Business analytics and KPI development
- Building scalable, analytics-ready data layers

## Author

**Sana Sayyad**

## GitHub Repository

[Global Retail Analytics Pipeline Using Databricks](https://github.com/sanasayyad2217/Global-Retail-Analytics-Pipeline-Using-Databricks)
