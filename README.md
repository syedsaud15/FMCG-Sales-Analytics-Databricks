# 🛒 FMCG Sales Analytics Dashboard using Databricks

> **End-to-end FMCG sales analytics solution built on Databricks SQL, combining analytical SQL, interactive dashboards, KPI-driven reporting, and Databricks Genie AI for natural-language business analysis.**

---

## 📌 Project Overview

The **FMCG Sales Analytics Dashboard** is a business-focused analytics solution developed using **Databricks SQL** to transform FMCG sales data into actionable business insights.

The project focuses on analyzing sales performance across **categories, brands, and key business metrics**, while providing an interactive analytical layer through **Databricks Dashboards**.

The solution also integrates **Databricks Genie AI**, enabling users to interact with the analytical data using natural-language questions instead of writing SQL queries manually.

The repository contains the analytical SQL layer, dashboard outputs, Genie AI analysis examples, and supporting project documentation.

---

## 🎯 Business Objective

FMCG organizations generate large volumes of transactional sales data across products, brands, and categories. Converting this raw information into decision-ready insights requires a reliable analytical layer and intuitive reporting interface.

This project addresses that requirement by providing a centralized analytics solution capable of answering questions such as:

* What is the overall sales performance?
* Which product category generates the highest sales?
* Which brands are performing best?
* What are the key sales KPIs?
* How do different categories and brands compare?
* Can business users query sales data using natural language?

The objective is to move from **raw sales information → analytical SQL → business KPIs → interactive decision support**.

---

## 🏗️ Solution Architecture

```text
                    FMCG Sales Data
                           │
                           ▼
                 ┌───────────────────┐
                 │    Databricks     │
                 │    SQL Layer      │
                 └─────────┬─────────┘
                           │
                           │ SQL Transformations
                           ▼
                 ┌───────────────────┐
                 │ Analytical Result │
                 │      Dataset      │
                 └─────────┬─────────┘
                           │
             ┌─────────────┴─────────────┐
             │                           │
             ▼                           ▼
   ┌───────────────────┐       ┌───────────────────┐
   │ Databricks        │       │ Databricks        │
   │ Dashboards        │       │ Genie AI          │
   └─────────┬─────────┘       └─────────┬─────────┘
             │                           │
             ▼                           ▼
     KPI & Visual Analytics      Natural Language
                                  Business Queries
             │                           │
             └─────────────┬─────────────┘
                           ▼
                  Business Insights
```

---

## ⚙️ Technology Stack

| Technology                | Purpose                                       |
| ------------------------- | --------------------------------------------- |
| **Databricks**            | Cloud data and analytics platform             |
| **Databricks SQL**        | Analytical querying and data preparation      |
| **SQL**                   | Business logic and analytical transformations |
| **Databricks Dashboards** | Interactive business reporting                |
| **Databricks Genie AI**   | Natural-language data exploration             |
| **GitHub**                | Source-code and project documentation         |

---

## 🔄 Analytical Workflow

The project follows a structured analytical workflow:

### 1. Data Access

Sales data is accessed within the Databricks analytical environment.

### 2. SQL Analysis

SQL queries are used to calculate business metrics and aggregate sales information across relevant dimensions.

### 3. KPI Generation

The analytical layer produces key performance indicators including:

* Total Sales
* Average Sales
* Total Brands
* Total Categories
* Category-level sales
* Brand-level sales

### 4. Dashboard Development

The resulting analytical datasets are used to create interactive Databricks dashboards for visual business analysis.

### 5. Natural Language Analytics

Databricks Genie AI provides an additional interface through which users can ask business questions using natural language.

---

# 📊 Analytics Layer

The SQL layer contains the analytical queries used to derive business metrics and reporting datasets.

The analysis covers:

### Category Analysis

* Total sales by category
* Category performance comparison
* Identification of high-performing categories

### Brand Analysis

* Brand-wise sales performance
* Top-performing brands
* Comparative brand analysis

### KPI Analysis

The dashboard provides centralized monitoring of important business metrics:

```text
Total Sales
Total Brands
Total Categories
Average Sales
```

---

# 📈 Dashboard

The Databricks dashboard provides an interactive analytical interface for monitoring FMCG sales performance.

### Dashboard capabilities

* Executive-level KPI monitoring
* Category performance analysis
* Brand performance analysis
* Comparative sales analysis
* Interactive business visualizations

Dashboard screenshots are available in:

```text
Dashboard Screenshots/
```

---

# 🤖 Databricks Genie AI

A key component of the project is the integration of **Databricks Genie AI** for natural-language analytics.

Instead of manually writing SQL, business users can ask questions such as:

```text
What is the total sales?
```

```text
What is the average sales?
```

```text
Which category has the highest sales?
```

```text
Show the top 5 brands by sales.
```

Genie AI converts these natural-language requests into data-driven analytical responses.

This creates an additional **self-service analytics layer** on top of the structured SQL analysis.

Genie AI examples are available in:

```text
Genie AI Screenshots/
```

---

# 🔍 Key Business Insights

Based on the analysis performed in the project:

* **Beverage** is the highest-performing category by sales.
* **Nescafe** is identified as a top-performing brand.
* KPI-level reporting enables quick monitoring of overall sales performance.
* Genie AI enables natural-language exploration of the analytical data.

> These insights are derived from the project's analytical output and are intended to demonstrate how the dashboard can support business decision-making.

---

# 📂 Repository Structure

```text
FMCG-Sales-Analytics-Databricks/
│
├── Dashboard Screenshots/
│   └── Dashboard visualization outputs
│
├── Genie AI Screenshots/
│   └── Natural-language analytics examples
│
├── SQL/
│   └── FMCG_Sales_Queries.sql
│
└── README.md
```

---

# 🧩 SQL Engineering

The SQL layer is responsible for converting the underlying sales information into analytical outputs.

The query set demonstrates:

* Aggregation
* Grouping
* KPI calculations
* Category-level analysis
* Brand-level analysis
* Business-oriented filtering
* Analytical ranking and comparison

All SQL implementation is maintained under:

```text
SQL/FMCG_Sales_Queries.sql
```

---

# 🧠 Engineering Highlights

This project demonstrates practical experience with:

* Databricks SQL
* Analytical SQL development
* Business KPI engineering
* Dimensional sales analysis
* Dashboard-oriented data preparation
* Self-service analytics
* Natural-language data exploration
* Business intelligence workflows

---

# 🔐 Configuration & Security

The project does not require hard-coded credentials or secrets in the repository.

When implementing the solution in a Databricks environment, authentication and workspace access should be handled through the appropriate Databricks authentication mechanisms rather than embedding credentials inside SQL files or notebooks.

---

# 🚀 How to Explore the Project

## Prerequisites

You should have access to:

* A Databricks workspace
* Databricks SQL
* Appropriate permissions to query the underlying data
* Access to Databricks Dashboards
* Databricks Genie AI access where available

## Steps

### 1. Clone the repository

```bash
git clone https://github.com/syedsaud15/FMCG-Sales-Analytics-Databricks.git
```

### 2. Open the SQL directory

```text
SQL/
└── FMCG_Sales_Queries.sql
```

### 3. Execute the analytical queries

Run the SQL statements inside a Databricks SQL environment after adapting the referenced objects to your workspace/data environment where required.

### 4. Review the dashboard

Use the dashboard screenshots in:

```text
Dashboard Screenshots/
```

### 5. Explore Genie AI

Review the examples inside:

```text
Genie AI Screenshots/
```

---

# 📌 Project Outcomes

The project demonstrates how a Databricks-based analytical workflow can combine:

```text
Sales Data
     ↓
Analytical SQL
     ↓
Business KPIs
     ↓
Interactive Dashboard
     ↓
Genie AI
     ↓
Business Insights
```

The result is a unified analytics experience supporting both **traditional SQL-driven analysis** and **natural-language business exploration**.

---

# 🔮 Future Enhancements

Potential extensions to the project include:

* Automated ingestion pipelines
* Bronze / Silver / Gold data architecture
* Delta Lake-based storage
* Incremental data processing
* Data quality validation
* Automated dashboard refresh
* Historical sales trend analysis
* Customer-level analytics
* Time-series sales analysis
* Advanced KPI monitoring
* Data governance and lineage
* CI/CD integration for Databricks assets

---

# 🏆 Skills Demonstrated

**Data Engineering**

* Databricks
* SQL
* Analytical data processing
* Data transformation
* Data modeling concepts

**Analytics & BI**

* KPI development
* Sales analytics
* Business intelligence
* Dashboard development
* Category and brand analysis

**AI-Assisted Analytics**

* Databricks Genie AI
* Natural-language querying
* Self-service analytics

**Engineering Practices**

* Git/GitHub
* Structured project organization
* Reproducible SQL workflows
* Technical documentation

---

# 👨‍💻 Author

**Syed Saud Alam**

Data Engineer | Big Data | Cloud Data Engineering | Databricks

**GitHub:**
https://github.com/syedsaud15

**LinkedIn:**
https://www.linkedin.com/in/syed-saud-alam

---

## ⭐ Project Focus

> **Turning FMCG sales data into business-ready intelligence using Databricks SQL, interactive dashboards, and Genie AI.**
