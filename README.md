# 📊 Supply Chain Performance & Business Optimization Dashboard

🔗 **Power BI Dashboard:**  
[https://app.powerbi.com/groups/me/reports/YOUR_REPORT_ID/ReportSection?experience=power-bi](https://app.powerbi.com/groups/me/reports/b30197cc-efa4-436b-982a-487ad6019827/c047e7bb3d07670d06ae?experience=power-bi)

<p align="center">
  <img src="dashboard1.png" alt="Dashboard 1" width="900">
</p>

<p align="center">
  <img src="dashboard2.png" alt="Dashboard 2" width="900">
</p>

---

# 📌 Project Overview

This End-to-End Business Optimization Dashboard demonstrates a real-world data analytics workflow where data is transferred from a **MySQL Test Environment** to a **Microsoft SQL Server Production Environment**, transformed using **Power Query**, analyzed with **DAX**, and visualized using **Power BI**.

The project simulates an enterprise ETL process used by organizations to migrate, clean, validate, and analyze production data for business decision-making.

---

# 🎯 Problem Statement

Organizations often maintain separate **Test** and **Production** databases.

Before production deployment, data must be:

- Extracted from multiple sources
- Cleaned and transformed
- Validated
- Migrated to the production database
- Visualized through interactive dashboards

This project demonstrates the complete workflow from database migration to business reporting.

---

# 🏗️ Architecture

```text
             MySQL (Test Database)
                     │
                     ▼
         Data Cleaning & Validation
                     │
                     ▼
          Microsoft SQL Server
          (Production Database)
                     │
                     ▼
          Power Query Transformation
                     │
                     ▼
               Data Modeling
                     │
                     ▼
               DAX Measures
                     │
                     ▼
             Interactive Power BI
```

---

# ⚙️ Tech Stack

- Power BI Desktop
- Microsoft SQL Server
- MySQL Community Server
- Power Query
- DAX
- SQL
- Data Modeling

---

# 📂 Data Sources

The project uses two relational tables stored in MySQL.

Example:

- Demand Table
- Availability Table

The tables are joined inside SQL Server before being imported into Power BI.

---

# 🔄 ETL Process

## Step 1

Download and install

- MySQL Community Server
- MySQL Workbench
- Microsoft SQL Server

---

## Step 2

Create a Test Database inside MySQL.

---

## Step 3

Import the CSV dataset into MySQL.

---

## Step 4

Create a Production Database in SQL Server.

---

## Step 5

Move the validated data from

```
MySQL (Test)
        ↓
SQL Server (Production)
```

---

## Step 6

Join both tables using

```sql
LEFT JOIN
```

Create a final production table.

---

## Step 7

Connect SQL Server with Power BI.

```
Get Data
      ↓
SQL Server
      ↓
Load Data
```

---

## Step 8

Transform the data using Power Query.

Examples

- Remove null values
- Rename columns
- Change data types
- Clean inconsistent values
- Remove duplicates

---

## Step 9

Create a clean data model.

---

## Step 10

Create DAX Measures.

---

# 📐 DAX Measures

### Total Days

```DAX
Total Days = DISTINCTCOUNT(Table[Date])
```

---

### Total Demand

```DAX
Total Demand = SUM(Table[Demand])
```

---

### Total Availability

```DAX
Total Availability = SUM(Table[Availability])
```

---

### Average Demand Per Day

```DAX
Avg Demand =
DIVIDE([Total Demand],[Total Days])
```

---

### Average Availability Per Day

```DAX
Avg Availability =
DIVIDE([Total Availability],[Total Days])
```

---

### Supply Shortage

```DAX
Supply Shortage =
SUMX(
Table,
MAX(
Table[Demand]-Table[Availability],
0
))
```

---

### Profit

```DAX
Profit =
SUMX(
FILTER(Table,
Table[Availability]>=Table[Demand]),
(Table[Availability]-Table[Demand])*Table[Unit Price]
)
```

---

### Loss

```DAX
Loss =
SUMX(
FILTER(Table,
Table[Availability]<Table[Demand]),
(Table[Demand]-Table[Availability])*Table[Unit Price]
)
```

---

### Average Daily Loss

```DAX
Average Daily Loss =
DIVIDE([Loss],[Total Days])
```

---

# 📈 Dashboard 1

### Supply Analysis

KPIs

- Average Demand Per Day
- Average Availability Per Day
- Total Supply Shortage

Provides insights into demand vs available inventory.

---

# 📊 Dashboard 2

### Profit & Loss Analysis

KPIs

- Total Profit
- Total Loss
- Average Daily Loss

Helps identify operational losses and profitability.

---

# 💡 Business Insights

- Compare demand and supply.
- Identify shortages.
- Monitor production efficiency.
- Track daily operational performance.
- Analyze total business loss.
- Measure overall profitability.
- Support production planning.
- Improve inventory management.

---

# 📸 Dashboard Preview

## Dashboard 1

![Dashboard 1](dashboard1.png)

---

## Dashboard 2

![Dashboard 2](dashboard2.png)

---

# 📁 Repository Structure

```
Supply-Chain-Performance-Dashboard
│
├── Dashboard.pbix
├── Dataset
│     ├── Demand.csv
│     ├── Availability.csv
│
├── SQL
│     ├── MySQL.sql
│     ├── SQLServer.sql
│
├── Images
│     ├── dashboard1.png
│     ├── dashboard2.png
│
└── README.md
```

---

# 🚀 Future Improvements

- Power BI Service Deployment
- Incremental Refresh
- Scheduled Refresh
- Row-Level Security (RLS)
- Azure SQL Integration
- Data Gateway Configuration
- Real-Time Dashboard
- KPI Alerts

---

# 👨‍💻 Author

**Harsh Kumar**

### Skills

- Power BI
- SQL Server
- MySQL
- DAX
- Power Query
- Data Modeling
- Business Intelligence
- Data Analytics

---

## ⭐ If you found this project helpful, don't forget to Star this repository.
