# CTEs vs Temp-Tables vs Table-Variables
Choosing the Right Tool for Intermediate Data in T-SQL

There are several ways to hold intermediate data for processing in T-SQL.

Consideration that needed to make are:
- Performance Optimization options
- Temporary Storage (or not)
- Reuse across batches

## Common Table Expressions (CTEs) - WITH
### Syntax
```
WITH cte_name (col1, col2) AS
(
  SELECT ...
)
SELECT * FROM cte_name
```
### Scope
A single query only

### Pros
Clean and readable

### Cons
Not reusable

## Temporary Tables - #temptable

### Syntax
```
CREATE #tempTable_name (... col def here);
```

### Pros
- Save in tempdb
- Scoped to session
- Holds data across multiple queries within the session
- Can be updated, in the session
- Can be indexed

## Table Variables - DECLARE @varTableName TABLE
### Syntax
```
DECLARE @varTableName TABLE (... col def here);
```
### Scope
- Batch or stored proc

### Pros
- Lightweight
- Great for small datasets

## Derived/Inline tables
### Syntax
```
SELECT *
FROM (SELECT col1, col2 FROM AnotherTable)
AS yourInlineTable
```
### Scope
One-time ussage within a query

## "Staging" tables
Even though a staging table is a permanent structure in SQL, we can view it as a staging area for data preparation for operations such as:
- ETL
- Data Cleansing
- Bulk Imports
- Reporting Preparations
Knowing that it is used only for staging/transitional data for processing, it's really looked at as **how it's used**.

### Naming convention
Two options:
- Prefix with a differentiator such as "stg_" or "stage_"
- Place it within a schema name appropriately such as "etl" or "stg"

### Notes
The data in a staging table is cleaned up either after an operation or just before the next operation.
