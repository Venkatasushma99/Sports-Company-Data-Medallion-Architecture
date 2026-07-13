# Architecture

The solution follows the **Medallion Architecture** pattern:

```text
Source Files
     |
     v
Bronze Layer
Raw and historical source data
     |
     v
Silver Layer
Cleaned, validated and standardised data
     |
     v
Gold Layer
Business-ready dimensions and facts
     |
     v
Power BI / Reporting / Analytics
```

---

# Medallion Layers

## Bronze Layer

The Bronze layer stores raw data received from the source systems.

### Source Datasets

- Customers
- Products
- Gross Prices
- Orders

The data is stored with minimal transformation to maintain the original source values.

### Metadata Captured

- Ingestion Timestamp
- Source File Name
- Data Source
- Batch Identifier
- Record Creation Date

The Bronze layer provides a historical and auditable copy of the source data.

---

## Silver Layer

The Silver layer contains cleaned and standardised data.

### Transformations Performed

- Removing duplicate records
- Handling missing values
- Standardising column names
- Correcting data types
- Trimming unnecessary spaces
- Standardising customer and city names
- Cleaning product descriptions
- Validating customer and product identifiers
- Converting date columns into standard date formats
- Validating numeric price and quantity fields
- Applying business rules
- Rejecting or quarantining invalid records

The Silver layer provides reliable and reusable datasets for downstream processing.

---

## Gold Layer

The Gold layer contains business-ready datasets designed for analytics and reporting.

### Star Schema

#### Dimension Tables

- **dim_customers**
- **dim_products**
- **dim_prices**

#### Fact Table

- **fact_orders**

### Business Analytics Supported

- Customer Analysis
- Product Analysis
- Location Analysis
- Order Date Analysis
- Quantity Analysis
- Gross Price Analysis
- Revenue Analysis
