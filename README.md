# FMCG Sales Analytics on Databricks

### SQL-Driven Analytical Platform for FMCG Sales Intelligence, KPI Engineering & Natural-Language Analytics

[![Databricks](https://img.shields.io/badge/Databricks-SQL-orange?style=for-the-badge\&logo=databricks)](https://www.databricks.com/)
[![SQL](https://img.shields.io/badge/SQL-Analytics-blue?style=for-the-badge\&logo=postgresql)](https://en.wikipedia.org/wiki/SQL)
[![Genie AI](https://img.shields.io/badge/Databricks-Genie_AI-purple?style=for-the-badge)](https://www.databricks.com/product/ai)
[![GitHub](https://img.shields.io/badge/Source-GitHub-black?style=for-the-badge\&logo=github)](https://github.com/syedsaud15)

> **A Databricks-based FMCG analytics solution that converts transactional sales data into structured business intelligence through analytical SQL, KPI engineering, interactive dashboards, and natural-language data exploration with Genie AI.**

---

## 01 · Executive Summary

This project implements an **FMCG sales analytics solution on Databricks** designed to bridge the gap between raw sales information and business decision-making.

The analytical layer is built around **SQL-driven business logic**, where sales data is transformed into reusable analytical outputs covering KPIs, category performance, brand performance, ranking, comparison, and business-level summaries.

The resulting analytical layer feeds two consumption interfaces:

```text
                         ┌──────────────────────┐
                         │      Sales Data       │
                         └──────────┬───────────┘
                                    │
                                    ▼
                         ┌──────────────────────┐
                         │   Databricks SQL     │
                         │ Analytical Layer     │
                         └──────────┬───────────┘
                                    │
                         ┌──────────┴──────────┐
                         │                     │
                         ▼                     ▼
                ┌──────────────────┐  ┌──────────────────┐
                │   Dashboards     │  │    Genie AI      │
                │ Visual Analytics  │  │ Natural Language │
                └────────┬─────────┘  └────────┬─────────┘
                         │                     │
                         └──────────┬──────────┘
                                    ▼
                         ┌──────────────────────┐
                         │ Business Intelligence│
                         │ & Decision Support   │
                         └──────────────────────┘
```

The repository contains the analytical SQL implementation, dashboard evidence, Genie AI interaction examples, and project documentation.

---

# 02 · Problem Definition

FMCG sales environments generate high-volume transactional information across multiple business dimensions such as:

* Products
* Brands
* Categories
* Sales values
* Business KPIs

Raw transactional data is not directly optimized for business decision-making.

A business stakeholder typically needs answers to questions such as:

* What is the current sales position?
* Which category contributes the most sales?
* Which brands are outperforming others?
* What are the major KPIs?
* How does one segment compare with another?
* Can business users explore the data without writing SQL?

The engineering objective of this project is therefore:

> **Create a structured analytical layer that converts sales data into reusable business metrics and exposes those metrics through both visual and natural-language interfaces.**

---

# 03 · Solution Architecture

```text
┌─────────────────────────────────────────────────────────────────────┐
│                         FMCG DATA DOMAIN                            │
└───────────────────────────────┬─────────────────────────────────────┘
                                │
                                ▼
┌─────────────────────────────────────────────────────────────────────┐
│                         DATABRICKS                                  │
│                                                                     │
│   ┌─────────────────────────────────────────────────────────────┐   │
│   │                    SQL ANALYTICAL LAYER                     │   │
│   │                                                             │   │
│   │  • Aggregations                                             │   │
│   │  • KPI calculations                                         │   │
│   │  • Category analysis                                        │   │
│   │  • Brand analysis                                           │   │
│   │  • Ranking & comparison                                     │   │
│   │  • Business-oriented analytical queries                    │   │
│   └──────────────────────────────┬──────────────────────────────┘   │
│                                  │                                  │
│                    ┌─────────────┴─────────────┐                    │
│                    │                           │                    │
│                    ▼                           ▼                    │
│       ┌────────────────────────┐   ┌────────────────────────────┐   │
│       │  Databricks Dashboard  │   │       Databricks Genie      │   │
│       │                        │   │                             │   │
│       │  KPI Visualization     │   │  Natural Language Queries  │   │
│       │  Category Analysis     │   │  Business Questions        │   │
│       │  Brand Analysis        │   │  Analytical Responses      │   │
│       └────────────┬───────────┘   └─────────────┬───────────────┘   │
│                    │                             │                   │
└────────────────────┼─────────────────────────────┼───────────────────┘
                     │                             │
                     └──────────────┬──────────────┘
                                    ▼
                         ┌──────────────────────┐
                         │  Business Insights   │
                         └──────────────────────┘
```

---

# 04 · Engineering Design

The project separates the solution into three conceptual layers.

### Layer 1 — Analytical Computation

SQL acts as the primary computation layer.

Business logic is expressed through SQL queries rather than being embedded directly into dashboard visualizations.

This separation makes analytical calculations easier to inspect, modify, and reproduce.

### Layer 2 — Analytical Consumption

The calculated metrics are consumed through Databricks dashboards.

The dashboard focuses on:

* KPI monitoring
* Category comparison
* Brand performance
* Sales analysis

### Layer 3 — Conversational Consumption

Genie AI provides an alternative interaction model.

Instead of requiring a stakeholder to understand the underlying SQL implementation, users can ask questions using natural language.

This creates two complementary consumption patterns:

```text
Traditional Analytics
        │
        └── SQL → Dashboard → Visual Insight

Conversational Analytics
        │
        └── Question → Genie AI → Analytical Response
```

---

# 05 · Technology Architecture

| Layer                    | Technology            | Responsibility                      |
| ------------------------ | --------------------- | ----------------------------------- |
| Analytics Platform       | Databricks            | Central analytical environment      |
| Query Engine             | Databricks SQL        | Analytical computation              |
| Business Logic           | SQL                   | KPI and sales analysis              |
| Visualization            | Databricks Dashboards | Business reporting                  |
| Conversational Analytics | Genie AI              | Natural-language exploration        |
| Version Control          | Git / GitHub          | Source and documentation management |

---

# 06 · Analytical Domain Model

The project analyzes the FMCG sales domain across multiple analytical dimensions.

```text
                         FMCG SALES DOMAIN
                                │
               ┌────────────────┼────────────────┐
               │                │                │
               ▼                ▼                ▼
           CATEGORY           BRAND            SALES
               │                │                │
               ▼                ▼                ▼
        Category KPIs     Brand Performance   Sales KPIs
               │                │                │
               └────────────────┼────────────────┘
                                ▼
                         Business Analysis
```

### Core analytical dimensions

**Category**

Used to understand sales contribution and relative category performance.

**Brand**

Used to compare brand-level performance and identify leading brands.

**Sales**

Used as the primary quantitative measure for KPI generation and business comparison.

---

# 07 · KPI Engineering

The dashboard is built around a defined KPI layer rather than isolated visualizations.

### KPI Set

| KPI              | Analytical Purpose           |
| ---------------- | ---------------------------- |
| Total Sales      | Overall sales performance    |
| Average Sales    | Sales-level central tendency |
| Total Brands     | Brand portfolio coverage     |
| Total Categories | Category portfolio coverage  |

These KPIs establish the top-level analytical context before users move into category and brand-level analysis.

---

# 08 · Analytical Query Design

The repository contains a dedicated SQL implementation:

```text
SQL/
└── FMCG_Sales_Queries.sql
```

The SQL layer is the core analytical asset of the repository.

The query implementation supports analysis including:

### Aggregation

Transforming granular sales information into business-level summaries.

### Grouped Analysis

Analyzing sales across dimensions such as:

```sql
GROUP BY category
```

and:

```sql
GROUP BY brand
```

### KPI Computation

Generating reusable business metrics from the underlying sales data.

### Ranking

Identifying high-performing brands and categories.

### Comparative Analysis

Comparing business segments using aggregated sales measures.

---

# 09 · Analytical Processing Pattern

The project follows a repeatable analytical pattern:

```text
Raw / Source-Level Sales Information
                │
                ▼
        Business Dimensions
                │
                ▼
        SQL Aggregation Layer
                │
                ▼
        KPI / Metric Generation
                │
                ▼
       Analytical Result Sets
                │
        ┌───────┴────────┐
        ▼                ▼
    Dashboard         Genie AI
        │                │
        └───────┬────────┘
                ▼
        Business Insights
```

This design keeps the analytical computation conceptually separate from the presentation layer.

---

# 10 · Dashboard Engineering

The dashboard acts as the **visual consumption layer** for the analytical outputs.

## Dashboard responsibilities

### Executive KPI Layer

Provides immediate visibility into:

* Total Sales
* Average Sales
* Total Brands
* Total Categories

### Category Analytics

Enables analysis of:

* Sales contribution by category
* Category-level comparison
* Relative category performance

### Brand Analytics

Enables analysis of:

* Brand-level sales
* Top-performing brands
* Brand comparison

The repository includes dashboard evidence under:

```text
Dashboard Screenshots/
```

---

# 11 · Genie AI Analytics Layer

One of the distinguishing components of this project is the use of **Databricks Genie AI** as a conversational analytical interface.

The objective is not to replace SQL.

Instead:

```text
SQL
 │
 ├── Defines analytical logic
 │
 └── Establishes the business data layer
             │
             ▼
         Genie AI
             │
             ▼
      Natural Language
             │
             ▼
       Business Answer
```

This provides a self-service analytics experience on top of the structured analytical environment.

---

# 12 · Example Business Questions

The implemented Genie AI workflow supports questions such as:

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

These examples demonstrate the transition from:

**manual query construction**

to:

**natural-language analytical exploration.**

---

# 13 · Business Findings

The current analytical results identify:

### Highest-performing category

**Beverage** generated the highest sales among the analyzed categories.

### Leading brand

**Nescafe** is identified as the top-performing brand in the current analysis.

### KPI visibility

The dashboard consolidates the major sales KPIs into a single analytical interface.

### Conversational analytics

Genie AI allows users to interrogate the analytical data using natural-language questions.

---

# 14 · Repository Architecture

```text
FMCG-Sales-Analytics-Databricks/
│
├── Dashboard Screenshots/
│   └── Dashboard evidence and visual outputs
│
├── Genie AI Screenshots/
│   └── Conversational analytics examples
│
├── SQL/
│   └── FMCG_Sales_Queries.sql
│
└── README.md
```

The repository intentionally keeps the analytical implementation separate from visual evidence.

---

# 15 · Engineering Decisions

## Why Databricks SQL?

Databricks SQL provides a centralized environment for executing analytical SQL workloads and exposing results to downstream analytical experiences.

## Why SQL-first analytical logic?

SQL is well suited for:

* Aggregation
* Filtering
* Grouping
* KPI calculations
* Ranking
* Business-oriented analytical transformations

Keeping this logic explicit also makes the analytical implementation inspectable.

## Why Dashboard + Genie AI?

These interfaces solve different problems.

| Interface | Primary User              | Interaction    |
| --------- | ------------------------- | -------------- |
| Dashboard | Analyst / Business User   | Visual         |
| Genie AI  | Business User             | Conversational |
| SQL       | Data / Analytics Engineer | Programmatic   |

Together they provide multiple access patterns to the same analytical domain.

---

# 16 · Data Quality Considerations

For an analytical system, metric correctness depends on the quality of the underlying data.

Relevant validation considerations include:

* Null handling
* Duplicate records
* Invalid category values
* Invalid brand values
* Numeric field consistency
* Aggregation correctness
* KPI reconciliation
* Unexpected sales values

A production extension of this project should formalize these checks into an automated data-quality layer.

---

# 17 · Performance Considerations

For larger FMCG datasets, analytical performance can be improved through:

* Query optimization
* Predicate filtering
* Appropriate aggregation strategies
* Partition-aware processing where applicable
* Reducing unnecessary scans
* Reusing analytical datasets
* Monitoring query execution behavior

The current repository focuses on the analytical implementation rather than presenting unverified production-scale performance benchmarks.

---

# 18 · Security Considerations

No credentials or secrets should be embedded inside the repository.

A production deployment should additionally consider:

* Workspace access control
* Table-level permissions
* Credential management
* Secret management
* Environment separation
* Auditability
* Controlled access to analytical datasets

---

# 19 · Reproducibility

The analytical implementation is version-controlled through GitHub.

The core SQL artifact is located at:

```text
SQL/FMCG_Sales_Queries.sql
```

A Databricks environment with access to the relevant data objects is required to reproduce the analytical execution.

The dashboard and Genie AI folders provide visual evidence of the implemented analytical experience.

---

# 20 · Local Repository vs Analytical Platform

This distinction is important.

```text
GitHub Repository
       │
       ├── SQL implementation
       ├── Documentation
       └── Visual evidence
              │
              ▼
        Databricks Workspace
              │
              ├── SQL execution
              ├── Dashboard
              └── Genie AI
```

GitHub acts as the **version-controlled project layer**, while Databricks provides the **execution and analytical environment**.

---

# 21 · Current Scope

### Implemented

* [x] Databricks SQL analytical layer
* [x] FMCG sales KPI analysis
* [x] Category-level analysis
* [x] Brand-level analysis
* [x] Databricks Dashboard
* [x] Genie AI analytical interaction
* [x] SQL source-code organization
* [x] Dashboard screenshots
* [x] Genie AI screenshots
* [x] GitHub-based documentation

### Not Claimed as Current Implementation

The following are intentionally **not represented as implemented architecture** unless added to the repository:

* [ ] Automated ingestion pipeline
* [ ] Bronze / Silver / Gold architecture
* [ ] Delta Lake pipeline
* [ ] PySpark transformation layer
* [ ] Automated orchestration
* [ ] CI/CD deployment
* [ ] Automated data-quality framework
* [ ] Production monitoring

This distinction keeps the documentation technically accurate rather than artificially inflating the architecture.

---

# 22 · Production Evolution Roadmap

The current SQL analytics solution can evolve into a broader data engineering architecture:

```text
                  CURRENT
                    │
                    ▼
              Databricks SQL
                    │
                    ▼
               Dashboard
                    │
                    ▼
                Genie AI


                  FUTURE
                    │
                    ▼
            Data Ingestion Layer
                    │
                    ▼
             Bronze / Raw Layer
                    │
                    ▼
            Silver / Cleansed Layer
                    │
                    ▼
              Gold / Analytics
                    │
                    ▼
             Databricks SQL
                    │
          ┌─────────┴─────────┐
          ▼                   ▼
      Dashboard            Genie AI
```

Potential future engineering additions include:

1. Automated ingestion
2. Incremental processing
3. Data-quality validation
4. Medallion architecture
5. Delta-based storage
6. Workflow orchestration
7. Data lineage
8. CI/CD
9. Monitoring and alerting
10. Role-based access control

---

# 23 · Engineering Takeaways

This project demonstrates practical implementation across three complementary areas:

### Data Engineering

* Databricks
* SQL-based analytical processing
* Structured analytical workflows
* Reproducible source management

### Analytics Engineering

* KPI design
* Business metric computation
* Dimensional analysis
* Analytical query development

### AI-Assisted Analytics

* Databricks Genie AI
* Natural-language data exploration
* Self-service business analytics

---

# 24 · Why This Project Matters

The value of the project is not simply the dashboard.

The engineering workflow demonstrates how:

```text
BUSINESS REQUIREMENT
        ↓
ANALYTICAL MODEL
        ↓
SQL BUSINESS LOGIC
        ↓
KPI ENGINEERING
        ↓
VISUAL ANALYTICS
        ↓
CONVERSATIONAL ANALYTICS
        ↓
BUSINESS DECISION SUPPORT
```

This represents the transition from **data processing to usable analytical products**.

---

# 25 · Project Evidence

### Dashboard

Project dashboard screenshots:

```text
Dashboard Screenshots/
```

### Genie AI

Natural-language analytics examples:

```text
Genie AI Screenshots/
```

### SQL

Complete analytical implementation:

```text
SQL/FMCG_Sales_Queries.sql
```

---

# 26 · Getting Started

## Prerequisites

* Databricks workspace
* Databricks SQL access
* Access to the relevant FMCG sales data
* Git
* GitHub

## Clone

```bash
git clone https://github.com/syedsaud15/FMCG-Sales-Analytics-Databricks.git

cd FMCG-Sales-Analytics-Databricks
```

## Open SQL

```text
SQL/FMCG_Sales_Queries.sql
```

Review the SQL implementation and adapt referenced data objects to the target Databricks environment where required.

## Explore Outputs

Review:

```text
Dashboard Screenshots/
Genie AI Screenshots/
```

---

# 27 · Project Metadata

| Property             | Value                           |
| -------------------- | ------------------------------- |
| Domain               | FMCG / Retail Analytics         |
| Platform             | Databricks                      |
| Primary Language     | SQL                             |
| Analytics Engine     | Databricks SQL                  |
| Visualization        | Databricks Dashboards           |
| Conversational Layer | Databricks Genie AI             |
| Version Control      | Git / GitHub                    |
| Repository           | FMCG-Sales-Analytics-Databricks |

---

# 28 · Author

## Syed Saud Alam

**Data Engineer | Cloud Data Engineering | Big Data | Databricks | SQL**

GitHub:
https://github.com/syedsaud15

LinkedIn:
https://www.linkedin.com/in/syed-saud-dev/

---

# 29 · Final Engineering Summary

> **FMCG Sales Analytics on Databricks demonstrates how structured SQL engineering can transform sales data into reusable business metrics and expose those metrics through both dashboard-driven and natural-language analytical experiences.**

The project combines:

**Databricks + SQL + KPI Engineering + Business Analytics + Dashboards + Genie AI**

to create a unified analytical workflow from **sales data to business insight**.

---

### ⭐ If you find this project useful

Consider starring the repository and exploring the SQL implementation.

**Built by Syed Saud Alam**
