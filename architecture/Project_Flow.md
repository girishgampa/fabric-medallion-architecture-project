# Project Flow

## Overview

This document describes the end-to-end workflow of the **DP700 Microsoft Fabric Analytics Project**, from ingesting raw data to delivering interactive Power BI dashboards for business users.

The project follows the **Medallion Architecture** (Bronze, Silver, and Gold) to progressively refine raw data into trusted analytical datasets.

---

## End-to-End Workflow

```
Raw Dataset
     │
     ▼
Bronze Layer
(Raw Data Ingestion)
     │
     ▼
Silver Layer
(Data Cleaning & Transformation)
     │
     ▼
Gold Layer
(Business-Ready Data Model)
     │
     ▼
Semantic Model
(Star Schema & Relationships)
     │
     ▼
Power BI Dashboards
(Sales & Operations Analytics)
```

---

## Workflow Stages

### 1. Data Ingestion (Bronze Layer)

The raw Olist E-commerce dataset is ingested into the Microsoft Fabric Lakehouse without applying business transformations.

**Objectives**

- Preserve raw source data
- Maintain data integrity
- Enable data traceability
- Serve as the single source of truth

**Output**

- Bronze Delta Tables

---

### 2. Data Transformation (Silver Layer)

The Bronze data is cleaned, standardized, and transformed into consistent analytical tables.

Key transformations include:

- Data type conversions
- Standardized column names
- Duplicate handling
- Null value handling
- Derived columns
- Data quality validation

**Output**

- Clean Silver Tables

---

### 3. Business Modeling (Gold Layer)

The Silver tables are transformed into a business-friendly dimensional model.

This layer contains:

- Fact tables
- Dimension tables
- Business calculations
- Aggregated metrics

The Gold layer follows a **Star Schema** optimized for reporting and analytics.

**Output**

- Gold Fact Tables
- Gold Dimension Tables

---

### 4. Semantic Model

The Gold tables are connected through relationships to build a semantic model for Power BI.

The semantic model includes:

- Fact-to-dimension relationships
- Date intelligence
- Business measures (DAX)
- Optimized filtering and navigation

---

### 5. Dashboard Development

Interactive Power BI dashboards are created on top of the semantic model.

The project includes two dashboards:

### Sales Dashboard

Provides insights into:

- Revenue
- Orders
- Customers
- Product Categories
- Payment Methods
- Customer Reviews

### Operations Dashboard

Provides insights into:

- Delivery Performance
- Freight Cost
- Order Fulfillment
- Delivery Success Rate
- State-wise Delivery Analysis

---

## Technologies Used

| Technology | Purpose |
|------------|---------|
| Microsoft Fabric | Data Engineering Platform |
| Lakehouse | Centralized Data Storage |
| PySpark | Data Processing |
| Delta Tables | Reliable Data Storage |
| SQL Endpoint | Data Validation & Querying |
| Power BI | Data Visualization |
| DAX | Business Calculations |

---

## Summary

The project transforms raw e-commerce data into business-ready analytical datasets using Microsoft Fabric's Medallion Architecture. The final solution enables stakeholders to monitor sales performance and operational efficiency through interactive Power BI dashboards.
