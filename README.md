# SQL-Portfolio

# 📦 SQL Data Cleaning & Inventory Valuation

## 🎯 Objective
As a Data Analyst Apprentice at Google, I understand the importance of data integrity before performing financial or operational analysis. 
The goal of this project was to take a raw, unstructured inventory dataset and transform it into a clean, queryable format to calculate the total dollar value of stock on hand.

## 🛠️ Skills & Tools Used
* **SQL Dialect:** Standard SQL (Compatible with MySQL / PostgreSQL)
* **Core Concepts:** Common Table Expressions (CTEs), Aggregate Functions (`SUM`, `GROUP BY`, `ORDER BY`), Data Type Casting.
* **Data Cleaning Techniques:** * Removing duplicate records (`DISTINCT`)
  * String manipulation and whitespace trimming (`TRIM`, `UPPER`)
  * Currency formatting and type conversion (`REPLACE`, `CAST`)
  * Handling missing/NULL values (`COALESCE`)

## 📊 The Business Problem
The initial dataset contained typical human-entry errors: 
* Duplicate product rows.
* Inconsistent capitalization and trailing spaces in product names.
* "Price" columns formatted as text strings with dollar signs (e.g., "$180").
* Missing inventory counts (NULLs).

Attempting to run mathematical aggregations on this raw data would result in errors or inaccurate total valuations.

## 🚀 The Solution
I engineered a SQL pipeline using a Common Table Expression (CTE) to create a clean, temporary view of the data. 
1. **Standardized Text:** Forced all product names and categories into consistent uppercase formats.
2. **Converted Data Types:** Stripped currency symbols and cast strings to decimal formats to allow for mathematical operations.
3. **Imputed Missing Data:** Replaced NULL stock counts with zeros using `COALESCE` to prevent calculation failures.
4. **Aggregated Valuation:** Multiplied the clean price by the clean stock count, grouping by category to find the total dollar value of the inventory.

## 💻 The Code
You can view the full SQL script used to build the schema, insert the messy data, and execute the cleaning/aggregation pipeline here: [Insert link to your inventory_cleaning.sql file here]
