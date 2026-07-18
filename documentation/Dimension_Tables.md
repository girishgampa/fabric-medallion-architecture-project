# Dimension Tables

## Overview

Dimension tables contain descriptive attributes that provide context for business metrics stored in fact tables. They are used for filtering, grouping, and slicing data in Power BI reports.

The project follows a Star Schema design, where dimension tables are connected to the central `fact_sales` table.

---

# Dimension Tables

## 1. dim_customer

Stores customer information used for customer and geographical analysis.

| Column | Description |
|---------|-------------|
| customer_id | Unique customer identifier |
| customer_city | Customer city |
| customer_state | Customer state |

**Business Use Cases**

- Sales by state
- Sales by city
- Customer segmentation

---

## 2. dim_product

Stores descriptive information about products.

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

**Business Use Cases**

- Product performance
- Category analysis
- Product characteristics

---

## 3. dim_category

Maps Portuguese product categories to English.

| Column | Description |
|---------|-------------|
| product_category_name | Original category name |
| product_category_name_english | English category name |

**Business Use Cases**

- Business-friendly reporting
- Category filtering

---

## 4. dim_seller

Stores seller information.

| Column | Description |
|---------|-------------|
| seller_id | Unique seller identifier |
| seller_city | Seller city |
| seller_state | Seller state |

**Business Use Cases**

- Seller performance
- Sales by seller location

---

## 5. dim_date

Supports time intelligence and trend analysis.

| Column | Description |
|---------|-------------|
| date | Calendar date |
| day | Day of month |
| day_name | Day name |
| week | Week number |
| month | Month number |
| month_name | Month name |
| quarter | Quarter |
| year | Year |

**Business Use Cases**

- Monthly sales
- Quarterly trends
- Year-over-Year analysis
- Time filtering

---

# Summary

The Gold layer contains five dimension tables that provide descriptive attributes for reporting and analytical queries. These dimensions enable flexible filtering, grouping, and drill-down capabilities in Power BI dashboards.
