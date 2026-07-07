# 📖 Data Dictionary – Online Retail Dataset

> **Purpose:**  
> This document provides a comprehensive description of the Online Retail dataset used throughout the AnalystLab Africa Data Analytics Internship. It serves as a reference for understanding the dataset, its business context, column definitions, relationships, and data quality considerations before performing analysis.

---

# 📌 Dataset Information

| Attribute | Details |
|------------|---------|
| **Dataset Name** | Online Retail |
| **Business Domain** | Retail / E-commerce |
| **Dataset Type** | Transactional Sales Data |
| **Source** | UCI Machine Learning Repository |
| **Business Process** | Customer Sales Transactions |
| **Approximate Records** | 541,909 Rows |
| **Number of Columns** | 8 |
| **Granularity** | One row represents one product purchased (or returned) within a single invoice. |

---

# 📚 Business Context

The dataset contains transactional records from a UK-based online retail company specializing in unique gift items. It captures customer purchases, product information, transaction details, pricing, and customer locations.

The primary objective of analyzing this dataset is to gain insights into customer purchasing behavior, product performance, sales trends, and business growth to support data-driven decision-making.

---

# 🏗️ Business Entities

The dataset represents four major business entities.

| Entity | Description |
|---------|-------------|
| **Customer** | Individuals purchasing products from the company. |
| **Product** | Items sold by the retailer. |
| **Transaction (Invoice)** | A customer purchase containing one or more products. |
| **Time** | The date and time when each transaction occurred. |

---

# 🔄 Entity Relationship

```text
Customer
    │
    │ places
    ▼
Invoice (Transaction)
    │
    │ contains
    ▼
Products
    │
    │ purchased on
    ▼
Invoice Date
```

### Interpretation

- One customer can have many invoices.
- One invoice can contain multiple products.
- Each row represents one product line within a transaction.

---

# 📋 Column Dictionary

---

## 1️⃣ InvoiceNo

| Property | Description |
|----------|-------------|
| **Business Name** | Invoice Number |
| **Column Name** | InvoiceNo |
| **Data Type** | Text |
| **Business Entity** | Transaction |
| **Description** | Unique identifier assigned to each sales transaction. |
| **Business Purpose** | Groups multiple purchased products into a single customer order. |
| **Example** | 536365 |
| **Missing Values** | No |
| **Special Notes** | Invoice numbers beginning with **"C"** indicate cancelled transactions (returns). |

---

## 2️⃣ StockCode

| Property | Description |
|----------|-------------|
| **Business Name** | Product Code |
| **Column Name** | StockCode |
| **Data Type** | Text |
| **Business Entity** | Product |
| **Description** | Unique code assigned to each product. |
| **Business Purpose** | Identifies products sold by the company. |
| **Example** | 85123A |
| **Missing Values** | No |
| **Special Notes** | Used as the primary key in the Product Dimension table. |

---

## 3️⃣ Description

| Property | Description |
|----------|-------------|
| **Business Name** | Product Description |
| **Column Name** | Description |
| **Data Type** | Text |
| **Business Entity** | Product |
| **Description** | Name of the product sold. |
| **Business Purpose** | Provides readable product information for reporting and analysis. |
| **Example** | WHITE HANGING HEART T-LIGHT HOLDER |
| **Missing Values** | Yes |
| **Special Notes** | Missing descriptions should be reviewed during data cleaning. |

---

## 4️⃣ Quantity

| Property | Description |
|----------|-------------|
| **Business Name** | Quantity Purchased |
| **Column Name** | Quantity |
| **Data Type** | Whole Number |
| **Business Entity** | Transaction |
| **Description** | Number of units purchased in a transaction. |
| **Business Purpose** | Measures sales volume for each product. |
| **Example** | 6 |
| **Missing Values** | No |
| **Special Notes** | Negative values usually indicate returned products or cancelled orders. |

---

## 5️⃣ InvoiceDate

| Property | Description |
|----------|-------------|
| **Business Name** | Invoice Date |
| **Column Name** | InvoiceDate |
| **Data Type** | Date & Time |
| **Business Entity** | Time |
| **Description** | Date and time when the transaction occurred. |
| **Business Purpose** | Enables time-based analysis such as daily, monthly, quarterly, and yearly sales trends. |
| **Example** | 01/12/2010 08:26 |
| **Missing Values** | No |
| **Special Notes** | Used to build the Date Dimension table. |

---

## 6️⃣ UnitPrice

| Property | Description |
|----------|-------------|
| **Business Name** | Unit Price |
| **Column Name** | UnitPrice |
| **Data Type** | Decimal Number |
| **Business Entity** | Transaction |
| **Description** | Price of a single product unit. |
| **Business Purpose** | Used to calculate sales revenue. |
| **Example** | 2.55 |
| **Missing Values** | No |
| **Special Notes** | Zero or negative values should be investigated during data cleaning. |

---

## 7️⃣ CustomerID

| Property | Description |
|----------|-------------|
| **Business Name** | Customer ID |
| **Column Name** | CustomerID |
| **Data Type** | Text (or Whole Number) |
| **Business Entity** | Customer |
| **Description** | Unique identifier assigned to each customer. |
| **Business Purpose** | Tracks customer purchases and supports customer segmentation. |
| **Example** | 17850 |
| **Missing Values** | Yes |
| **Special Notes** | Missing values usually represent anonymous customers. |

---

## 8️⃣ Country

| Property | Description |
|----------|-------------|
| **Business Name** | Customer Country |
| **Column Name** | Country |
| **Data Type** | Text |
| **Business Entity** | Geography |
| **Description** | Country where the customer is located. |
| **Business Purpose** | Supports geographic sales and customer analysis. |
| **Example** | United Kingdom |
| **Missing Values** | No |
| **Special Notes** | Used for regional performance reporting. |

---

# ⚙️ Derived Columns

The following columns are commonly created during data preparation and analysis.

| Derived Column | Purpose |
|----------------|---------|
| **Sales** | Calculates revenue (`Quantity × UnitPrice`). |
| **Order Status** | Identifies completed and cancelled transactions. |
| **Year** | Annual trend analysis. |
| **Quarter** | Quarterly performance reporting. |
| **Month** | Monthly sales analysis. |
| **Month Name** | Improves report readability. |
| **Weekday** | Daily purchasing pattern analysis. |

---

# 🔑 Keys and Relationships

| Table | Primary Key |
|--------|-------------|
| **Dim Customer** | CustomerID |
| **Dim Product** | StockCode |
| **Dim Date** | Date |
| **Fact Sales** | InvoiceNo + StockCode (transaction line) |

---

# 📊 Business Metrics

Using this dataset, the following key performance indicators (KPIs) can be calculated.

## 💰 Sales Metrics

- Total Revenue
- Total Orders
- Total Quantity Sold
- Average Order Value
- Average Selling Price

---

## 👥 Customer Metrics

- Total Customers
- Repeat Customers
- Customer Purchase Frequency
- Top Customers by Revenue

---

## 📦 Product Metrics

- Best-Selling Products
- Lowest-Selling Products
- Product Revenue
- Product Return Rate

---

## 🌍 Geographic Metrics

- Revenue by Country
- Customers by Country
- Orders by Country

---

## 📅 Time Metrics

- Sales by Year
- Sales by Quarter
- Sales by Month
- Monthly Growth
- Seasonal Sales Trends

---

# 🧹 Data Quality Assessment

The following data quality issues were identified during the initial exploration.

| Issue | Impact |
|-------|--------|
| Missing Customer IDs | Prevents customer-level analysis for some transactions. |
| Missing Product Descriptions | Reduces product identification accuracy. |
| Cancelled Transactions | Invoice numbers beginning with **"C"** represent returns. |
| Negative Quantities | Usually indicate returned products. |
| Zero or Negative Unit Prices | Require investigation before revenue analysis. |
| Duplicate Records | Must be handled carefully when creating dimension tables. |

---

# 💼 Business Value

The Online Retail dataset enables organizations to answer important business questions such as:

- Which products generate the highest revenue?
- Who are the most valuable customers?
- Which countries contribute the most sales?
- What are the monthly and yearly sales trends?
- Which products experience the highest return rates?
- How do customer purchasing behaviors change over time?

Answering these questions supports better inventory management, customer relationship strategies, marketing campaigns, and business decision-making.

---

# 📝 Summary

The Online Retail dataset is a transactional retail dataset designed for analyzing customer behavior, product performance, sales trends, and business growth. By transforming the raw data into a well-structured star schema with fact and dimension tables, analysts can build interactive dashboards, perform advanced analytics, and generate actionable business insights.

---

> **"A well-documented dataset is the foundation of reliable analysis. Understanding the data before performing analysis leads to more accurate insights and better business decisions."**