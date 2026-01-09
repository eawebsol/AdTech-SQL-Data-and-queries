# 🚀 AdTech SQL Practice - Data Analyst Interview Prep

[![SQL](https://img.shields.io/badge/SQL-BigQuery-blue)](https://cloud.google.com/bigquery)
[![T-SQL](https://img.shields.io/badge/SQL-T--SQL-red)](https://docs.microsoft.com/en-us/sql/)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)

A comprehensive SQL practice repository for **Data Analyst - AdTech** roles, featuring realistic datasets and 20 carefully crafted queries covering all essential concepts.

## 📋 Table of Contents

- [Overview](#overview)
- [Job Role Context](#job-role-context)
- [Dataset Structure](#dataset-structure)
- [Query Coverage](#query-coverage)
- [Getting Started](#getting-started)
- [Key Concepts Covered](#key-concepts-covered)
- [Query Index](#query-index)
- [Performance Optimization Tips](#performance-optimization-tips)
- [Contributing](#contributing)

## 🎯 Overview

This repository contains:
- **5 realistic AdTech tables** with 5,000+ rows of sample data
- **20 progressive SQL queries** from basic to advanced
- **Dual syntax support**: BigQuery (primary) and T-SQL (notes)
- **Detailed explanations** for each query
- **Real-world business applications** and use cases

Perfect for preparing for **Data Analyst positions** in AdTech, programmatic advertising, or digital marketing analytics.

## 💼 Job Role Context

**Target Role**: Data Analyst – AdTech (2-3 Years Experience)

**Key Responsibilities**:
- Analyze AdTech data (ads.txt, programmatic delivery, campaign performance)
- Build scalable data pipelines using GCP tools
- Write complex SQL queries in BigQuery
- Create dashboards in Looker Studio
- Deliver actionable insights

**Required Skills**:
- Strong SQL proficiency (BigQuery)
- Experience with AdTech datasets
- GCP data pipeline experience
- Data visualization (Looker Studio)
- Understanding of digital advertising concepts

## 📊 Dataset Structure

### Tables Overview

| Table Name | Records | Description |
|------------|---------|-------------|
| `ads_txt` | 1,000 | Ad inventory and authorized sellers |
| `campaign_performance` | 810 | Campaign metrics (impressions, clicks, conversions, revenue) |
| `programmatic_delivery` | 1,500 | Ad delivery data (fill rates, latency, status) |
| `ad_spend` | 855 | Cost data (spend, budget, CPC, CPM) |
| `impressions` | 2,000 | Impression-level data (bids, wins, engagement) |

### Entity Relationship Diagram

```
┌─────────────────┐
│   ads_txt       │
│─────────────────│
│ ad_id (PK)      │
│ domain          │
│ seller_account  │
│ status          │
└─────────────────┘

┌──────────────────────┐      ┌────────────────────┐
│ campaign_performance │──────│ programmatic_      │
│──────────────────────│      │    delivery        │
│ performance_id (PK)  │      │────────────────────│
│ campaign_id          │◄─────│ campaign_id        │
│ performance_date     │      │ date               │
│ impressions          │      │ delivery_status    │
│ clicks               │      │ impressions_deliv. │
│ conversions          │      │ fill_rate          │
│ revenue              │      └────────────────────┘
│ cost                 │
└──────────────────────┘
        │
        │
        ▼
┌──────────────────────┐      ┌────────────────────┐
│    ad_spend          │      │   impressions      │
│──────────────────────│      │────────────────────│
│ spend_id (PK)        │      │ impression_id (PK) │
│ campaign_id          │      │ campaign_id        │
│ date                 │      │ timestamp          │
│ daily_spend          │      │ is_clicked         │
│ platform             │      │ is_converted       │
│ avg_cpc              │      │ bid_price          │
└──────────────────────┘      └────────────────────┘
```

## 🎓 Query Coverage

### 10 Key Concept Areas (20 Queries Total)

1. **Basic Filtering & Aggregation** (Q1-Q2)
   - DISTINCT, GROUP BY, SUM, COUNT, ORDER BY

2. **JOINs & Relationships** (Q3-Q4)
   - INNER JOIN, LEFT JOIN, multi-table joins

3. **CTEs (Common Table Expressions)** (Q5-Q6)
   - WITH clauses, nested CTEs, data pipeline patterns

4. **Subqueries & EXISTS** (Q7-Q8)
   - NOT EXISTS, NOT IN, correlated subqueries

5. **Time-Series Analysis** (Q9-Q10)
   - Window functions, LAG, moving averages, trend detection

6. **Data Quality & Anomaly Detection** (Q11-Q12)
   - NULL handling, statistical analysis, Z-scores, outlier detection

7. **Advanced Aggregations** (Q13-Q14)
   - Multiple dimensions, ranking, HAVING clauses

8. **Complex Business Logic** (Q15-Q16)
   - ARPU, CPC, ROAS, ROI calculations

9. **Data Transformation & Pivoting** (Q17)
   - CASE WHEN pivoting, cross-tabulation

10. **Optimization & Best Practices** (Q18-Q20)
    - Partition pruning, benchmark analysis, comprehensive dashboards

## 🚀 Getting Started

### Prerequisites

**Option 1: BigQuery (Recommended)**
- Google Cloud Platform account
- BigQuery project created
- Basic familiarity with BigQuery Console

**Option 2: SQL Server**
- SQL Server 2016 or later
- SQL Server Management Studio (SSMS)
- Adapt queries using T-SQL notes provided

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/yourusername/adtech-sql-practice.git
cd adtech-sql-practice
```

2. **Set up the database**

**For BigQuery:**
```sql
-- Create a new dataset
CREATE SCHEMA `your-project.adtech_practice`;

-- Run the table creation script
-- Execute: data_creation_script.sql
```

**For SQL Server:**
```sql
-- Create a new database
CREATE DATABASE AdTechPractice;
GO

USE AdTechPractice;
GO

-- Run the adapted table creation script
-- Note: Adjust GENERATE_UUID() to NEWID(), GENERATE_ARRAY() to number tables
```

3. **Verify data load**
```sql
-- Check record counts
SELECT 'ads_txt' AS table_name, COUNT(*) AS row_count FROM ads_txt
UNION ALL
SELECT 'campaign_performance', COUNT(*) FROM campaign_performance
UNION ALL
SELECT 'programmatic_delivery', COUNT(*) FROM programmatic_delivery
UNION ALL
SELECT 'ad_spend', COUNT(*) FROM ad_spend
UNION ALL
SELECT 'impressions', COUNT(*) FROM impressions;
```

Expected output:
```
table_name              | row_count
------------------------|----------
ads_txt                 | 1000
campaign_performance    | ~810
programmatic_delivery   | 1500
ad_spend               | ~855
impressions            | 2000
```

4. **Start practicing!**
- Open `query_solutions.sql`
- Try writing queries yourself before checking solutions
- Review explanations for each query

## 🔑 Key Concepts Covered

### SQL Fundamentals
- ✅ SELECT, WHERE, GROUP BY, HAVING, ORDER BY
- ✅ DISTINCT, LIMIT/TOP
- ✅ Aggregate functions: SUM, AVG, COUNT, MIN, MAX
- ✅ String functions and formatting

### Advanced SQL
- ✅ **Window Functions**
  - ROW_NUMBER(), RANK(), DENSE_RANK()
  - LAG(), LEAD()
  - Moving averages with ROWS BETWEEN
  - PARTITION BY and ORDER BY

- ✅ **Common Table Expressions (CTEs)**
  - Single and nested CTEs
  - Recursive CTEs
  - Data pipeline patterns

- ✅ **JOINs**
  - INNER JOIN
  - LEFT/RIGHT JOIN
  - CROSS JOIN
  - Self-joins
  - Multi-table joins with multiple conditions

- ✅ **Subqueries**
  - Correlated subqueries
  - EXISTS / NOT EXISTS
  - IN / NOT IN
  - Scalar subqueries

### Data Quality & Analysis
- ✅ NULL handling (COALESCE, IFNULL, NULLIF)
- ✅ Statistical analysis (mean, standard deviation, Z-scores)
- ✅ Anomaly detection algorithms
- ✅ Data validation techniques

### AdTech-Specific Metrics
- ✅ **Performance Metrics**
  - CTR (Click-Through Rate)
  - Conversion Rate
  - Fill Rate
  - Delivery Rate

- ✅ **Cost Metrics**
  - CPC (Cost Per Click)
  - CPM (Cost Per Mille)
  - Cost Per Conversion
  - CPA (Cost Per Acquisition)

- ✅ **ROI Metrics**
  - ROAS (Return on Ad Spend)
  - ROI (Return on Investment)
  - ARPU (Average Revenue Per User)
  - Profit Margin

### Date & Time Operations
- ✅ DATE_SUB / DATEADD
- ✅ DATE_TRUNC / DATEPART
- ✅ CURRENT_DATE / GETDATE
- ✅ Time-series analysis
- ✅ Rolling windows

## 📖 Query Index

### Quick Reference

| # | Query Name | Difficulty | Key Concepts | Business Use Case |
|---|------------|------------|--------------|-------------------|
| 1 | Unique Ad IDs | ⭐ Easy | DISTINCT, WHERE | Ad inventory audit |
| 2 | Revenue per Campaign | ⭐ Easy | GROUP BY, SUM | Campaign profitability |
| 3 | Delivery Efficiency Join | ⭐⭐ Medium | INNER JOIN, HAVING | Delivery quality monitoring |
| 4 | Multi-table Analysis | ⭐⭐ Medium | Multiple JOINs | Comprehensive campaign view |
| 5 | Top Performing Impressions | ⭐⭐⭐ Hard | CTE, ROW_NUMBER | Impression optimization |
| 6 | Multi-level CTE Pipeline | ⭐⭐⭐ Hard | Nested CTEs | Performance classification |
| 7 | Zero Revenue Campaigns | ⭐⭐ Medium | NOT EXISTS | Underperformer identification |
| 8 | Alternative NOT IN | ⭐⭐ Medium | NOT IN, Subquery | Campaign filtering |
| 9 | Trend Analysis | ⭐⭐⭐ Hard | Moving averages, LAG | Performance trends |
| 10 | Declining Performance | ⭐⭐⭐ Hard | Window functions | Early warning system |
| 11 | Missing Value Handling | ⭐⭐ Medium | COALESCE, NULLIF | Data quality |
| 12 | Anomaly Detection | ⭐⭐⭐⭐ Expert | Z-scores, Statistics | Quality assurance |
| 13 | Ad Group Metrics | ⭐⭐ Medium | Multiple GROUP BY | Granular analysis |
| 14 | Top Ad Formats | ⭐⭐ Medium | RANK, LIMIT | Format optimization |
| 15 | ARPU Calculation | ⭐⭐⭐ Hard | User-level metrics | User value analysis |
| 16 | Cost Per Click | ⭐⭐ Medium | Cost metrics | Budget efficiency |
| 17 | Status Pivoting | ⭐⭐ Medium | CASE WHEN pivot | Regional performance |
| 18 | Query Optimization | ⭐⭐ Medium | Partition pruning | Performance tuning |
| 19 | Benchmark Comparison | ⭐⭐⭐ Hard | Self-join, Benchmarks | Relative performance |
| 20 | Campaign Health Dashboard | ⭐⭐⭐⭐ Expert | Comprehensive metrics | Executive reporting |

### Difficulty Legend
- ⭐ **Easy**: Basic SQL concepts, 1-2 tables
- ⭐⭐ **Medium**: Intermediate concepts, 2-3 tables, some complexity
- ⭐⭐⭐ **Hard**: Advanced concepts, multiple techniques combined
- ⭐⭐⭐⭐ **Expert**: Complex business logic, multiple advanced concepts

## ⚡ Performance Optimization Tips

### BigQuery Best Practices

#### 1. Partition Filtering
```sql
-- ✅ Good: Uses partition pruning
WHERE performance_date >= '2024-01-01'
  AND performance_date < '2025-01-01'

-- ❌ Bad: Scans entire table
WHERE EXTRACT(YEAR FROM performance_date) = 2024
```

#### 2. Column Selection
```sql
-- ✅ Good: Select only needed columns
SELECT campaign_id, impressions, clicks

-- ❌ Bad: Wastes bandwidth and processing
SELECT *
```

#### 3. Filter Order
```sql
-- ✅ Good: Filter before aggregation
WHERE status = 'active'
GROUP BY campaign_id

-- ❌ Bad: Aggregates unnecessary data
GROUP BY campaign_id
HAVING status = 'active'
```

#### 4. Approximation Functions
```sql
-- ✅ Good: Fast for large datasets
SELECT APPROX_COUNT_DISTINCT(user_id)

-- ❌ Slower: Exact count on billions of rows
SELECT COUNT(DISTINCT user_id)
```

#### 5. JOIN Optimization
```sql
-- ✅ Good: Largest table first, filtered early
FROM large_table
INNER JOIN small_table USING (id)
WHERE large_table.date >= '2024-01-01'

-- ❌ Bad: Small table first, no early filtering
FROM small_table
INNER JOIN large_table USING (id)
```

### T-SQL Best Practices

#### 1. Indexing
```sql
-- Create indexes on frequently joined/filtered columns
CREATE INDEX idx_campaign_date 
ON campaign_performance(campaign_id, performance_date);
```

#### 2. Query Hints
```sql
-- Use NOLOCK for read-only queries (reduces blocking)
SELECT * FROM campaign_performance WITH (NOLOCK)
WHERE campaign_id = 'camp_001';
```

#### 3. Statistics
```sql
-- Keep statistics up to date
UPDATE STATISTICS campaign_performance;
```

#### 4. Stored Procedures
```sql
-- Create stored procedures for repeated queries
CREATE PROCEDURE GetCampaignMetrics
    @StartDate DATE,
    @EndDate DATE
AS
BEGIN
    -- Query logic here
END;
```

## 📚 Learning Path

### Beginner (Week 1-2)
- [ ] Complete Q1-Q8 (Basic to Subqueries)
- [ ] Understand GROUP BY and aggregations
- [ ] Practice JOINs with 2-3 tables
- [ ] Master NULL handling

### Intermediate (Week 3-4)
- [ ] Complete Q9-Q14 (Time-series to Advanced Aggregations)
- [ ] Learn window functions thoroughly
- [ ] Understand CTEs and when to use them
- [ ] Practice performance optimization

### Advanced (Week 5-6)
- [ ] Complete Q15-Q20 (Complex Business Logic to Dashboards)
- [ ] Build custom metrics and KPIs
- [ ] Optimize queries for large datasets
- [ ] Create end-to-end analytics queries

### Interview Preparation
- [ ] Review all queries without looking at solutions
- [ ] Explain your approach out loud
- [ ] Practice writing queries in 15-20 minutes
- [ ] Understand the business context for each query

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. **Add more queries**: Submit PRs with new AdTech scenarios
2. **Improve explanations**: Make concepts clearer
3. **Add visualizations**: Create dashboards with results
4. **Report issues**: Found a bug? Let us know!

### Contribution Guidelines

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/new-query`)
3. Commit your changes (`git commit -m 'Add new query for X'`)
4. Push to the branch (`git push origin feature/new-query`)
5. Open a Pull Request

## 📝 Additional Resources

### BigQuery Resources
- [BigQuery Documentation](https://cloud.google.com/bigquery/docs)
- [BigQuery SQL Reference](https://cloud.google.com/bigquery/docs/reference/standard-sql/query-syntax)
- [BigQuery Best Practices](https://cloud.google.com/bigquery/docs/best-practices)

### AdTech Learning
- [IAB Tech Lab Standards](https://iabtechlab.com/)
- [Google Ad Manager Documentation](https://support.google.com/admanager)
- [Programmatic Advertising Guide](https://www.iab.com/insights/programmatic-advertising-guide/)

### SQL Practice Platforms
- [LeetCode Database](https://leetcode.com/problemset/database/)
- [HackerRank SQL](https://www.hackerrank.com/domains/sql)
- [SQLZoo](https://sqlzoo.net/)

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Inspired by real-world AdTech data analyst interviews
- Dataset design based on industry-standard AdTech platforms
- Query patterns derived from production analytics workflows

## 📧 Contact

Questions? Suggestions? Reach out!

- GitHub Issues: [Create an issue](https://github.com/yourusername/adtech-sql-practice/issues)
- Email: your.email@example.com
- LinkedIn: [Your Profile](https://linkedin.com/in/yourprofile)

---

⭐ **Star this repo** if you found it helpful!

📚 **Fork it** to customize for your learning journey!

🚀 **Share it** with others preparing for AdTech data roles!

---

**Happy Querying! 🎯**
