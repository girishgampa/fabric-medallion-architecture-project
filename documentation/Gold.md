# Gold Layer

## Overview

The Gold layer represents the business-ready data warehouse built on top of the Silver layer following the Medallion Architecture.

Unlike the Silver layer, where the focus was on data cleaning and transformation, the Gold layer focuses on dimensional modeling by creating Fact and Dimension tables. These tables are optimized for reporting, analytics, and Power BI dashboards.

---

## Objectives

- Build a Star Schema
- Create Dimension tables
- Create Fact tables
- Prepare data for Power BI
- Enable business reporting and KPI generation

---

# Gold Layer Architecture

Silver Layer
      │
      ▼
Dimension Tables
- dim_customer
- dim_product
- dim_seller
- dim_category
- dim_date

Fact Tables
- fact_sales
- fact_payments
- fact_reviews

      │
      ▼
Power BI

---

# Design Principles

- Gold layer performs business modeling, not data cleaning.
- All cleansing and datatype conversions were completed in the Silver layer.
- Dimension tables store descriptive attributes.
- Fact tables store measurable business events.
- Relationships are implemented using a Star Schema.

# Gold Layer Tables

## Dimension Tables

Dimension tables provide descriptive attributes used for filtering, grouping, and slicing business metrics in Power BI reports.

---

## 1. dim_customer

The **Customer Dimension** stores customer-related information required for customer segmentation and geographical analysis.

| Column | Description |
|---------|-------------|
| customer_id | Unique customer identifier |
| customer_city | Customer city |
| customer_state | Customer state |

### Business Purpose

- Analyze sales by customer location
- Customer segmentation
- Power BI slicers and filters

---

## 2. dim_product

The **Product Dimension** contains descriptive information about products.

| Column | Description |
|---------|-------------|
| product_id | Unique product identifier |
| product_category_name | Product category |
| product_description_length | Product description length |
| product_photos_qty | Number of product images |
| product_weight_g | Product weight (grams) |
| product_length_cm | Product length (cm) |
| product_height_cm | Product height (cm) |
| product_width_cm | Product width (cm) |

### Business Purpose

- Product analysis
- Product performance reporting
- Revenue by product/category

---

## 3. dim_category

The **Category Dimension** stores English translations for product categories.

| Column | Description |
|---------|-------------|
| product_category_name | Original category name |
| product_category_name_english | English category name |

### Business Purpose

- Improve report readability
- Business-friendly category names

---

## 4. dim_seller

The **Seller Dimension** contains seller information.

| Column | Description |
|---------|-------------|
| seller_id | Unique seller identifier |
| seller_city | Seller city |
| seller_state | Seller state |

### Business Purpose

- Seller performance analysis
- Revenue by seller location

---

## 5. dim_date

The **Date Dimension** supports time intelligence and date-based reporting.

| Column | Description |
|---------|-------------|
| date | Calendar date |
| day | Day of month |
| day_name | Day name |
| week | Week number |
| month | Month number |
| month_name | Month abbreviation |
| quarter | Quarter |
| year | Year |

### Business Purpose

- Monthly revenue analysis
- Time intelligence
- Year-over-Year reporting
- Dashboard filtering

---

## 1. fact_sales

The **Sales Fact Table** is the central fact table in the Gold layer.

Each record represents **one order item**, making it the primary source for sales, customer, product, delivery, and review analytics.

---

### Primary Keys

| Column | Description |
|---------|-------------|
| order_id | Unique order identifier |
| order_item_id | Unique order item identifier |
| customer_id | Customer identifier |
| product_id | Product identifier |
| seller_id | Seller identifier |

---

### Order Information

| Column | Description |
|---------|-------------|
| order_purchase_timestamp | Date and time when the order was placed |
| order_purchase_date | Date component of the purchase timestamp |
| order_status | Original order status from the source system |
| order_approved_at | Date and time when the order was approved |

---

### Sales Metrics

| Column | Description |
|---------|-------------|
| price | Product selling price |
| freight_value | Shipping cost charged for the order item |
| total_item_cost | Total cost of the order item (Price + Freight) |

---

### Delivery Information

| Column | Description |
|---------|-------------|
| shipping_limit_date | Deadline for the seller to ship the order |
| order_delivered_carrier_date | Date and time the carrier received the order |
| order_delivered_customer_date | Date and time the customer received the order |
| order_estimated_delivery_date | Estimated delivery date provided at purchase |
| delivery_status | Current delivery status of the order |
| delivery_days | Number of days taken for delivery |
| delivery_performance | Delivery performance classification (Early, On Time, Late, Not Delivered) |

---

### Customer Review Metrics

| Column | Description |
|---------|-------------|
| avg_review_score | Average customer review score for the order |
| review_count | Total number of reviews received for the order |

---

### Business Purpose

The **fact_sales** table is the primary analytical fact table used throughout the project. It combines sales transactions with delivery and customer review metrics to support comprehensive business reporting.

It enables analysis of:

- Revenue and sales performance
- Customer purchasing behavior
- Product performance
- Seller performance
- Delivery efficiency
- Customer satisfaction
- Executive KPI reporting

> **Design Note**
>
> Customer review metrics (`avg_review_score` and `review_count`) were aggregated into `fact_sales` to simplify reporting and reduce unnecessary joins. The original `fact_reviews` table is retained in the semantic model for future analysis but is hidden from report view.



# Star Schema

The Gold layer follows a **Star Schema** optimized for analytical workloads and Power BI reporting.

```text
                    dim_customer
                          │
                    dim_seller
                          │
dim_category ── dim_product ──┐
                              │
                         fact_sales
                              │
                          dim_date

fact_payments (Standalone Fact)

fact_reviews (Source for Review Aggregation)
```

---

# Power BI Integration

The Gold layer serves as the source for the **Microsoft Fabric Semantic Model** and the **Power BI Executive Dashboard**.

Business users can analyze:

- 📈 Revenue trends
- 💰 Sales performance
- 📦 Product category performance
- 👥 Customer insights
- 🏪 Seller performance
- ⭐ Customer reviews
- 🚚 Delivery performance
- 💳 Payment method distribution

---

## Gold Layer Summary

✔️ Business-ready dimensional model

✔️ Star Schema implementation

✔️ Optimized for Microsoft Fabric Semantic Model

✔️ Interactive Power BI reporting

✔️ Supports KPI generation and executive dashboards
