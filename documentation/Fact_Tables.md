# Fact Tables

## Overview

Fact tables store measurable business events and numerical metrics used for reporting and analytics.

The project contains one primary fact table (`fact_sales`) and one supporting fact table (`fact_payments`).

---

# 1. fact_sales

The central fact table in the warehouse.

Each record represents one order item.

## Key Metrics

| Metric | Description |
|---------|-------------|
| price | Product price |
| freight_value | Shipping cost |
| total_item_cost | Product price + freight |
| avg_review_score | Average customer review score |
| review_count | Number of customer reviews |
| delivery_days | Delivery duration |
| delivery_performance | Delivery performance category |

## Related Dimensions

- dim_customer
- dim_product
- dim_category
- dim_seller
- dim_date

## Business Use Cases

- Revenue analysis
- Sales trends
- Customer analytics
- Product performance
- Delivery performance
- Executive KPIs

---

# 2. fact_payments

Stores payment transaction details for each order.

Because one order may contain multiple payment records, this table remains independent from `fact_sales`.

## Key Metrics

| Column | Description |
|---------|-------------|
| payment_type | Payment method |
| payment_installments | Number of installments |
| payment_value | Payment amount |

## Business Use Cases

- Payment method analysis
- Installment analysis
- Payment reporting

---

# Design Considerations

- `fact_sales` is the central analytical table.
- `fact_payments` is maintained separately to avoid many-to-many relationships.
- Customer review metrics are aggregated into `fact_sales` to simplify reporting.

---

# Summary

The project uses two fact tables:

| Fact Table | Purpose |
|------------|---------|
| fact_sales | Sales, delivery, and customer review analytics |
| fact_payments | Payment analysis |

Together, these tables support KPI generation, executive reporting, and interactive Power BI dashboards.
