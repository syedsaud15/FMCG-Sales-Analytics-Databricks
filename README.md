# FMCG Sales Analytics on Databricks

<p align="center">

### From Sales Data → Analytical SQL → Business KPIs → Interactive Analytics → Natural-Language Insights

<br>

<a href="https://github.com/syedsaud15/FMCG-Sales-Analytics-Databricks">
<img src="https://img.shields.io/badge/Repository-GitHub-181717?style=flat-square&logo=github" alt="GitHub">
</a>
<a href="https://www.databricks.com/">
<img src="https://img.shields.io/badge/Platform-Databricks-EF3E42?style=flat-square&logo=databricks" alt="Databricks">
</a>
<img src="https://img.shields.io/badge/SQL-Analytics-336791?style=flat-square&logo=postgresql" alt="SQL">
<img src="https://img.shields.io/badge/Genie%20AI-Conversational%20Analytics-7B61FF?style=flat-square" alt="Genie AI">

</p>

> **An analytical FMCG sales solution built on Databricks SQL that transforms sales data into business-ready KPIs, category and brand intelligence, interactive dashboard insights, and natural-language analytical exploration through Databricks Genie AI.**

---

## 1. Executive Overview

FMCG businesses operate across large product portfolios, brands, and categories where decision-making depends on understanding sales performance quickly and accurately.

This project implements a **Databricks-based analytical workflow** for turning FMCG sales information into a structured business intelligence layer.

The core analytical logic is implemented in SQL and covers:

* Sales aggregation
* KPI computation
* Category-level analysis
* Brand-level analysis
* Comparative analysis
* Ranking-oriented analysis
* Business-oriented analytical queries

The resulting analytical outputs are consumed through two different interfaces:

**Visual analytics**

→ Databricks Dashboard

**Conversational analytics**

→ Databricks Genie AI

The architecture intentionally separates **analytical computation** from **analytical consumption**.

```text
                         FMCG SALES DATA
                                │
                                ▼
                    ┌───────────────────────┐
                    │    DATABRICKS SQL     │
                    │                       │
                    │ Analytical Queries    │
                    │ KPI Calculations      │
                    │ Category Analysis     │
                    │ Brand Analysis        │
                    │ Ranking & Comparison  │
                    └───────────┬───────────┘
                                │
                       Analytical Outputs
                                │
                 ┌──────────────┴──────────────┐
                 │                             │
                 ▼                             ▼
      ┌────────────────────┐       ┌────────────────────┐
      │ Databricks         │       │ Databricks         │
      │ Dashboard           │       │ Genie AI           │
      │                     │       │                    │
      │ Visual Analytics    │       │ Natural Language   │
      │ KPI Monitoring      │       │ Data Exploration  │
      │ Brand/Category      │       │ Business Questions│
      └──────────┬─────────┘       └──────────┬─────────┘
                 │                            │
                 └─────────────┬──────────────┘
                               ▼
                    ┌──────────────────────┐
                    │ Business Insights    │
                    │ & Decision Support    │
                    └──────────────────────┘
```

---

# 2. Business Problem

A sales dataset contains information, but information alone does not provide a decision-making interface.

Business stakeholders typically need answers to questions such as:

* What is the overall sales position?
* What is the average sales value?
* Which category contributes the most sales?
* Which brands are performing strongly?
* How do categories compare?
* How do brands compare?
* Can the business explore the data without manually writing SQL?

The engineering problem is therefore not simply to create a dashboard.

It is to establish a **reusable analytical layer** that can answer business questions consistently and expose the resulting metrics through accessible analytical interfaces.

---

# 3. Project Objective

The project has four primary objectives:

### Objective 01 — Centralize analytical logic

Implement sales analysis through structured SQL rather than embedding business calculations independently inside individual visualizations.

### Objective 02 — Engineer reusable KPIs

Convert sales information into measurable business indicators such as total sales, average sales, brand count, and category count.

### Objective 03 — Enable dimensional analysis

Provide analytical views across FMCG dimensions such as:

* Category
* Brand
* Sales performance

### Objective 04 — Provide multiple consumption interfaces

Support both:

```text
Traditional BI
SQL → Dashboard → Visual Insight
```

and:

```text
Conversational BI
Question → Genie AI → Analytical Response
```

---

# 4. Scope of the Current Implementation

The current repository focuses specifically on the **analytical and consumption layer**.

### Implemented

* Databricks SQL analysis
* FMCG sales KPI analysis
* Category analysis
* Brand analysis
* Dashboard-based analytics
* Genie AI natural-language analysis
* SQL source-code organization
* Analytical evidence through screenshots
* GitHub-based version control

### Intentionally outside the current implementation

The repository does **not** currently claim to implement:

* Automated ingestion
* Streaming ingestion
* Bronze/Silver/Gold pipelines
* PySpark ETL
* Delta Lake pipeline orchestration
* Airflow orchestration
* CI/CD deployment
* Automated data-quality framework
* Production monitoring

These are documented separately as possible architectural extensions rather than being presented as existing functionality.

This distinction keeps the project technically defensible.

---

# 5. System Architecture

## Current Architecture

```text
┌──────────────────────────────────────────────────────────────┐
│                       SOURCE SALES DATA                      │
└──────────────────────────────┬───────────────────────────────┘
                               │
                               ▼
┌──────────────────────────────────────────────────────────────┐
│                       DATABRICKS SQL                         │
│                                                              │
│  ┌────────────────────────────────────────────────────────┐  │
│  │                 ANALYTICAL LOGIC                       │  │
│  │                                                        │  │
│  │  • Aggregations                                        │  │
│  │  • KPI calculations                                    │  │
│  │  • Category analysis                                   │  │
│  │  • Brand analysis                                      │  │
│  │  • Ranking                                             │  │
│  │  • Comparisons                                         │  │
│  └─────────────────────────┬──────────────────────────────┘  │
└────────────────────────────┼─────────────────────────────────┘
                             │
                             ▼
                  ┌─────────────────────┐
                  │ Analytical Outputs  │
                  └──────────┬──────────┘
                             │
                ┌────────────┴────────────┐
                │                         │
                ▼                         ▼
       ┌─────────────────┐       ┌─────────────────┐
       │   Dashboard     │       │    Genie AI     │
       │                 │       │                 │
       │ KPI Monitoring  │       │ Natural Language│
       │ Category Views  │       │ Questions       │
       │ Brand Views     │       │ Analysis        │
       └────────┬────────┘       └────────┬────────┘
                │                         │
                └────────────┬────────────┘
                             ▼
                    BUSINESS CONSUMPTION
```

---

# 6. Architectural Boundaries

A key design principle of the project is keeping responsibilities distinct.

| Layer          | Responsibility                              |
| -------------- | ------------------------------------------- |
| Source Data    | Provides sales information                  |
| Databricks SQL | Performs analytical computation             |
| KPI Logic      | Defines measurable business indicators      |
| Dashboard      | Presents analytical results visually        |
| Genie AI       | Enables conversational exploration          |
| GitHub         | Maintains version-controlled project assets |

This avoids treating the dashboard itself as the data-processing layer.

---

# 7. Analytical Model

The project operates around three primary analytical dimensions.

```text
                    FMCG SALES
                        │
          ┌─────────────┼─────────────┐
          │             │             │
          ▼             ▼             ▼
       CATEGORY        BRAND         SALES
          │             │             │
          ▼             ▼             ▼
     Category KPI   Brand KPI     Sales KPI
          │             │             │
          └─────────────┼─────────────┘
                        ▼
                 Business Analysis
```

### Category

Used to determine how sales are distributed across product categories.

### Brand

Used to compare brand-level performance and identify leading brands.

### Sales

Used as the core quantitative measure for KPI generation and comparative analysis.

---

# 8. KPI Engineering

The dashboard provides a compact KPI layer for high-level business monitoring.

| KPI                  | Purpose                                     |
| -------------------- | ------------------------------------------- |
| **Total Sales**      | Measures overall sales performance          |
| **Average Sales**    | Provides an aggregate sales-level indicator |
| **Total Brands**     | Measures the number of brands represented   |
| **Total Categories** | Measures category coverage                  |

The KPI layer acts as the entry point into deeper category and brand analysis.

```text
                 KPI Layer
                    │
       ┌────────────┼────────────┐
       ▼            ▼            ▼
   Sales Level   Brand Level  Category Level
       │            │            │
       └────────────┼────────────┘
                    ▼
             Business Insight
```

---

# 9. SQL Engineering Layer

The repository contains a dedicated analytical SQL artifact:

```text
SQL/
└── FMCG_Sales_Queries.sql
```

The SQL file is the primary implementation asset of the project.

It contains the analytical query work required to support the FMCG sales analysis.

The repository therefore follows a simple separation:

```text
SQL Implementation
        │
        ▼
Analytical Results
        │
        ├──────────────► Dashboard
        │
        └──────────────► Genie AI
```

---

# 10. Analytical Query Patterns

The SQL implementation is oriented around common analytical engineering patterns.

### Aggregation

Converting detailed sales information into business-level summaries.

### Grouped Analysis

Calculating metrics across dimensions such as category and brand.

### KPI Computation

Deriving high-level metrics from sales data.

### Ranking

Identifying high-performing brands and categories.

### Comparative Analysis

Comparing performance across business dimensions.

These patterns are fundamental to analytical workloads because they transform transactional-level information into decision-oriented datasets.

---

# 11. Business Metric Flow

A typical metric follows this conceptual path:

```text
Source Sales Records
        │
        ▼
Filtering / Selection
        │
        ▼
Dimensional Grouping
        │
        ▼
Aggregation
        │
        ▼
Business Metric
        │
        ▼
Dashboard / Genie AI
```

The same underlying analytical logic can therefore support multiple consumption experiences.

---

# 12. Dashboard Layer

The Databricks Dashboard represents the **visual consumption layer**.

It provides an interactive view of the analytical outputs.

### Dashboard focus areas

#### KPI Monitoring

Provides a high-level snapshot of:

* Total Sales
* Average Sales
* Total Brands
* Total Categories

#### Category Intelligence

Supports:

* Sales by category
* Category comparison
* Category performance analysis

#### Brand Intelligence

Supports:

* Brand-wise sales
* Top-performing brands
* Brand comparison

Dashboard evidence is available under:

```text
Dashboard Screenshots/
```

---

# 13. Genie AI Layer

Databricks Genie AI provides a conversational interface over the analytical environment.

The purpose is to reduce the dependency on manually constructed SQL for exploratory business questions.

Conceptually:

```text
Business User
      │
      │ Natural-language question
      ▼
┌──────────────────────┐
│      Genie AI        │
└──────────┬───────────┘
           │
           ▼
    Analytical Context
           │
           ▼
     Data-driven Answer
```

This creates a second analytical access pattern alongside the dashboard.

---

# 14. Example Analytical Questions

The project demonstrates natural-language questions such as:

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

The purpose of these interactions is to demonstrate **self-service analytical exploration**, not to replace the underlying SQL layer.

---

# 15. Key Findings

The current analytical output identifies:

### Category Performance

**Beverage** is the highest-performing category in the analyzed dataset.

### Brand Performance

**Nescafe** is identified as a top-performing brand in the current analysis.

### KPI Visibility

The dashboard consolidates important sales indicators into a single analytical view.

### Conversational Access

Genie AI enables users to explore business questions using natural language.

---

# 16. Repository Structure

```text
FMCG-Sales-Analytics-Databricks/
│
├── Dashboard Screenshots/
│   └── Dashboard implementation evidence
│
├── Genie AI Screenshots/
│   └── Conversational analytics evidence
│
├── SQL/
│   └── FMCG_Sales_Queries.sql
│
└── README.md
```

The repository is intentionally lightweight because the project currently centers on the analytical SQL layer and Databricks-based analytical outputs.

---

# 17. Evidence-Based Documentation

The repository contains visual evidence for the two primary consumption layers.

### Dashboard Evidence

```text
Dashboard Screenshots/
```

Demonstrates the visual analytics implementation.

### Genie AI Evidence

```text
Genie AI Screenshots/
```

Demonstrates natural-language analytical interactions.

### SQL Evidence

```text
SQL/FMCG_Sales_Queries.sql
```

Contains the analytical implementation.

Together, these three assets represent:

```text
IMPLEMENTATION
     │
     ├── SQL
     │
     ├── Dashboard
     │
     └── Genie AI
```

---

# 18. Engineering Decisions

## Why Databricks?

Databricks provides a unified environment for data processing and analytical workloads, allowing SQL-based analytics and downstream analytical experiences to exist within the same platform.

## Why SQL as the analytical language?

The primary workload is analytical rather than application-oriented.

SQL provides direct and expressive constructs for:

* Aggregation
* Grouping
* Filtering
* Ranking
* Business metric computation

## Why separate SQL from the dashboard?

Business logic embedded directly inside visualization configuration becomes harder to inspect and maintain.

Maintaining the analytical logic as SQL makes the calculations:

* Visible
* Version-controlled
* Reviewable
* Reusable

## Why Dashboard + Genie AI?

They solve different consumption problems.

| Interface | Strength                   |
| --------- | -------------------------- |
| SQL       | Engineering control        |
| Dashboard | Visual monitoring          |
| Genie AI  | Conversational exploration |

---

# 19. Data Quality Considerations

Metric accuracy depends on the quality of the source data.

For a production evolution of this solution, the following checks should be introduced:

### Structural validation

* Required columns exist
* Expected data types are present
* Schema changes are detected

### Record-level validation

* Null checks
* Duplicate detection
* Invalid dimension values
* Invalid numeric values

### Analytical validation

* KPI reconciliation
* Aggregation consistency
* Unexpected sales-value detection
* Category/brand completeness

The current repository does not claim to contain an automated data-quality framework.

---

# 20. Performance Considerations

As data volume grows, analytical SQL should be reviewed for:

* Unnecessary data scans
* Expensive repeated aggregations
* Inefficient filtering
* High-cardinality grouping
* Repeated computation of identical metrics

Potential future optimization strategies include:

* Query optimization
* Reusable analytical datasets
* Appropriate physical data organization
* Incremental analytical processing
* Workload monitoring

No unsupported performance benchmark is claimed by this project.

---

# 21. Security Considerations

The repository does not require credentials to be committed to source control.

A production deployment should additionally implement:

* Least-privilege access
* Workspace-level access control
* Dataset/table permissions
* Secret management
* Environment isolation
* Audit logging

The GitHub repository should remain free of:

```text
API keys
Passwords
Tokens
Connection strings
Cloud credentials
```

---

# 22. Reproducibility

The analytical implementation is version-controlled through GitHub.

To reproduce the analytical work:

1. Clone the repository.
2. Open the SQL implementation.
3. Execute the required queries in an appropriate Databricks environment.
4. Provide access to the corresponding sales data objects.
5. Recreate or inspect the dashboard and Genie AI analytical experience.

The repository provides the SQL implementation and visual evidence; the execution environment remains Databricks.

---

# 23. Reproduction Workflow

```text
Clone Repository
       │
       ▼
Open SQL/FMCG_Sales_Queries.sql
       │
       ▼
Connect to Databricks
       │
       ▼
Resolve Required Data Objects
       │
       ▼
Execute Analytical Queries
       │
       ▼
Validate Analytical Results
       │
       ├───────────────┐
       ▼               ▼
   Dashboard        Genie AI
       │               │
       └───────┬───────┘
               ▼
        Business Analysis
```

---

# 24. Current Architecture vs Future Architecture

The current solution is intentionally focused.

### Current

```text
Sales Data
    ↓
Databricks SQL
    ↓
Analytical Outputs
    ├── Dashboard
    └── Genie AI
```

### Potential Production Evolution

```text
External Sources
       │
       ▼
Ingestion Layer
       │
       ▼
Raw / Bronze
       │
       ▼
Cleansed / Silver
       │
       ▼
Business / Gold
       │
       ▼
Analytical SQL
       │
   ┌───┴────┐
   ▼        ▼
Dashboard  Genie AI
```

Possible future engineering additions:

* Automated ingestion
* Incremental processing
* Data-quality automation
* Medallion architecture
* Delta-based storage
* Workflow orchestration
* Lineage
* CI/CD
* Monitoring
* Governance

These are **future architectural directions**, not claims about the current repository.

---

# 25. Engineering Maturity Roadmap

| Capability              | Current |  Future |
| ----------------------- | :-----: | :-----: |
| SQL Analytics           |    ✅    |    —    |
| KPI Engineering         |    ✅    |    —    |
| Category Analysis       |    ✅    |    —    |
| Brand Analysis          |    ✅    |    —    |
| Databricks Dashboard    |    ✅    |    —    |
| Genie AI                |    ✅    |    —    |
| Automated Ingestion     |    —    | Planned |
| Data Quality Automation |    —    | Planned |
| Pipeline Orchestration  |    —    | Planned |
| CI/CD                   |    —    | Planned |
| Monitoring              |    —    | Planned |
| Governance              |    —    | Planned |

This makes the repository's current engineering boundary explicit.

---

# 26. Project Strengths

### Analytical separation

The project separates business logic from dashboard presentation.

### Multiple consumption modes

Users can consume insights visually or conversationally.

### Reusable SQL layer

The analytical SQL is maintained as a version-controlled project asset.

### Business-oriented design

The analysis is organized around questions that business users actually ask.

### Honest architecture

The documentation distinguishes implemented capabilities from future enhancements.

---

# 27. What This Project Demonstrates

This project demonstrates practical experience in:

### Data & Analytics Engineering

* Databricks
* Databricks SQL
* SQL analytics
* KPI engineering
* Aggregation
* Dimensional analysis
* Business metric design

### Business Intelligence

* Dashboard design
* KPI monitoring
* Category analytics
* Brand analytics
* Business insight generation

### AI-Assisted Analytics

* Databricks Genie AI
* Natural-language querying
* Self-service analytics

### Engineering Practices

* Version control
* Structured repository organization
* Reproducible analytical logic
* Technical documentation
* Architecture boundary definition

---

# 28. Technology Stack

| Technology                | Role                                  |
| ------------------------- | ------------------------------------- |
| **Databricks**            | Analytical platform                   |
| **Databricks SQL**        | Query and analytical processing       |
| **SQL**                   | Business logic and metric computation |
| **Databricks Dashboards** | Visual analytics                      |
| **Databricks Genie AI**   | Conversational analytics              |
| **Git**                   | Version control                       |
| **GitHub**                | Source-code hosting and documentation |

---

# 29. Getting Started

## Prerequisites

* Databricks workspace
* Databricks SQL access
* Access to the required FMCG sales data
* Git

## Clone

```bash
git clone https://github.com/syedsaud15/FMCG-Sales-Analytics-Databricks.git

cd FMCG-Sales-Analytics-Databricks
```

## Analytical SQL

Open:

```text
SQL/FMCG_Sales_Queries.sql
```

Execute the relevant queries in the Databricks environment after mapping the referenced data objects to the target workspace.

## Review Evidence

Dashboard implementation:

```text
Dashboard Screenshots/
```

Genie AI implementation:

```text
Genie AI Screenshots/
```

---

# 30. Project Assets

| Asset                        | Purpose                           |
| ---------------------------- | --------------------------------- |
| `SQL/FMCG_Sales_Queries.sql` | Core analytical implementation    |
| `Dashboard Screenshots/`     | Dashboard evidence                |
| `Genie AI Screenshots/`      | Conversational analytics evidence |
| `README.md`                  | Technical documentation           |

---

# 31. Repository

**GitHub**

https://github.com/syedsaud15/FMCG-Sales-Analytics-Databricks

---

# 32. Author

## Syed Saud Alam

**Data Engineer | Cloud Data Engineering | Big Data | Databricks | SQL**

GitHub:
https://github.com/syedsaud15

LinkedIn:
https://www.linkedin.com/in/syed-saud-dev/

---

# 33. Final Engineering Perspective

The project demonstrates a practical analytical pattern:

```text
                  DATA
                   │
                   ▼
            SQL COMPUTATION
                   │
                   ▼
           BUSINESS METRICS
                   │
          ┌────────┴────────┐
          ▼                 ▼
     VISUAL BI        CONVERSATIONAL BI
          │                 │
          ▼                 ▼
      DASHBOARD          GENIE AI
          │                 │
          └────────┬────────┘
                   ▼
             BUSINESS INSIGHT
```

The core engineering principle is simple:

> **Build the analytical logic once, then make the resulting business intelligence accessible through multiple consumption patterns.**

This repository represents that principle using **Databricks SQL, KPI engineering, interactive dashboards, and Genie AI-powered natural-language analytics**.
