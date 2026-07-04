# Project Lessons

## Lesson 1

Never assume the datatype of a column.

Always inspect:

- Schema
- Sample Data
- NULL values

before performing transformations.

---

## Lesson 2

Business understanding is more important than writing Spark code.

Before transforming any table ask:

- What does this table represent?
- What business process generated this data?
- What questions should this table answer?

---

## Lesson 3

Always validate every transformation.

Workflow:

Read
↓

Transform
↓

Validate
↓

Document
↓

Commit

---

## Lesson 4

NULL values do not always indicate bad data.

Sometimes NULL represents business reality.

Example:

Undelivered orders

still have

NULL delivery dates.

---

## Lesson 5

Understand the data model before writing code.

The Order Items table taught us:

- Composite Keys
- Fact Tables
- One row per purchased item
- Quantity represented using multiple rows

---

## Lesson 6

Always investigate unusual data instead of making assumptions.

Example:

Repeated product_id values

Instead of assuming duplicates, investigate the business meaning.

This led us to understand how quantities are stored in this dataset.


## Mistakes I Made

### Customers

- Used df instead of customers_df.

Lesson:
Always use descriptive DataFrame names.

---

### Orders

- Forgot notebook variables disappear after restarting Spark.

Lesson:
Always rebuild DataFrames from Delta tables.

---

### Orders

- Used incorrect timestamp format.

Lesson:
Always inspect sample data before parsing timestamps.

---

### Orders

- Compared timestamps instead of dates.


# Gold Layer Lessons

## Data Modeling

- Difference between Fact and Dimension tables.
- Importance of defining the grain before building a fact table.
- Difference between Natural Keys and Surrogate Keys.
- Composite keys are used when one column cannot uniquely identify a record.

---

## Star Schema

Learned how to design a Star Schema for reporting.

Dimensions

- Customer
- Product
- Seller
- Category
- Geography
- Date

Facts

- Sales
- Payments
- Reviews

---

## Data Warehouse Concepts

- Fact tables store measurable business events.
- Dimension tables store descriptive attributes.
- Gold layer focuses on business modeling rather than data transformation.

---

## Validation

Performed validation for

- Row Counts
- Primary Keys
- Business Keys
- Referential Integrity
- Data Types

---

## Best Practices

- Keep ZIP Codes as String because they are identifiers.
- Perform datatype conversions in Silver, not Gold.
- Keep Gold tables business-ready.
- Validate data before reporting.

Lesson:
Business rules are often different from technical implementations.
