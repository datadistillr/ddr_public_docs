---
description: Introducing background on SQL
---
# What Can SQL do?

This tutorial will give you a basic introduction to SQL, the standard language for accessing different data sources
within DataDistillr. 

Using SQL syntax will provide you with the ability to fully access your data, run analysis on your datasets, and
quickly present desired results. SQL can execute, retrieve, insert, update, delete, and create records in a data source.

## SQL Standard

SQL is an ANSI standard, but different versions of the SQL language exist. There are basic operators that must stay the
same (`SELECT`, `UPDATE`, `DELETE`, `INSERT`, `WHERE`), but there are some slight differences that can trip up even the
most talented analyst.

The SQL you will use to write queries in DataDistillr supports the ANSI standard, but includes special operators and
functions that enable users to drill into nested data formats. It is specifically formulated to query against complex
data: data made up of various types of records and fields, rather than discrete rows and columns.

## SQL Syntax

- SQL is **not case-sensitive** except inside of strings. It is a standard practice to capitalize clauses for clarity.

- The order of clauses matters. The order of precedence is: `SELECT`, `FROM`, `WHERE`, `LIMIT`. **Not all of these
clauses are required, details will be provided below.**

- To write a **comment** in SQL use `--`.

- The **semicolon** `;` is not part of a query. The database server uses it to separate two SQL statements.

Now that you have an understanding of SQL, you can follow this tutorial to [Practice Basic SQL](sql-practice.md). 