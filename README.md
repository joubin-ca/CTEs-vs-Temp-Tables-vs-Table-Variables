# CTEs vs Temp-Tables vs Table-Variables
Choosing the Right Tool for Intermediate Data in T-SQL

There are several ways to hold intermediate data for processing in T-SQL.

Consideration that needed to make are:
- Performance Optimization options
- Temporary Storage (or not)
- Reuse across batches

## Common Table Expressions (CTEs) - WITH

## Temporary Tables - #temptable

## Table Variables - DECLARE @varTableName TABLE

## "Staging" tables
Even though a staging table is a permanent structure in SQL, we can view it as a staging area for data preparation for operations such as:
- ETL
- Data Cleansing
- Bulk Imports
- Reporting Preparations
