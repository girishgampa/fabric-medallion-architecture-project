# Semantic Model

## Overview

The Semantic Model was built using the Gold layer Delta tables.

It provides a business-friendly layer for Power BI reporting.

---

## Model Components

Dimension Tables

- dim_customer
- dim_product
- dim_category
- dim_seller
- dim_date

Fact Tables

- fact_sales
- fact_payments

---

## Relationships

- fact_sales → dim_customer
- fact_sales → dim_product
- fact_sales → dim_category
- fact_sales → dim_seller
- fact_sales → dim_date

---

## Measures

Examples

- Total Revenue
- Total Orders
- Average Review Score
- Average Delivery Days

---

## Design Considerations

- Star Schema
- One-to-Many relationships
- Hidden helper tables
- Optimized for Power BI
