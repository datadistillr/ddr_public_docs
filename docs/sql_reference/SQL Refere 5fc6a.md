# SQL Reference

This tutorial will give you a basic introduction to SQL, a standard language for accessing different data sources within DataDistillr. Knowing SQL syntax will allow you full access to your data, run a dataset analysis, and present results faster.

### What Can SQL do?

- SQL can execute, retrieve, insert, update, delete, create records from a data source

## SQL Syntax

 SQL is not case sensitive except inside of a string. It is a standard practice to capitalize clauses for clarity.

<aside>
💡 The order of clauses matter in SQL.The following order of precedence: FROM, SELECT, LIMIT.

</aside>

To write a **comment** in SQL use ’ --’ 

The **semicolon (;)** is not part of a query. The database server uses it to separate two SQL statements.

<aside>
➡️ Let's practice some basic SQL; start off by downloading the two excel files [**here](https://docs.datadistillr.com/getting-started/connecting-a-data-source-and-uploading-a-file/)** at the bottom of the page.

</aside>

## **Querying Data**

The `SELECT` **-** Extracts data from a data source. A data source can be an excel, CSV, json, api.

When we are asking for data, we use a select statement. If we want to return the whole table, we use a *; if we wish to use specific columns from a table, you give the name of those columns. You can also do simple calculations within the select clause.

```sql
--Display all available fields in the dataset
SELECT * 
FROM `demo_project`.`/Dummy-Customers-1.xlsx`
```

![Screen Shot 2022-04-15 at 1.23.51 PM.png](SQL%20Refere%205fc6a/Screen_Shot_2022-04-15_at_1.23.51_PM.png)

<aside>
💡 The **LIMIT** clause constrains the number of rows returned by a SELECT statement.

</aside>

```sql
--Display the first 1000 rows from column firt_name and ip_address
SELECT first_name, ip_address
FROM demo_project_data.`/Dummy-Customers-1.xlsx`
LIMIT 1000
```

Breaking down the code: `FROM` the  demo_project_data.`/Dummy-Customers-1.xlsx`  `SELECT` the first 1000 rows from the two columns (first name and ip address) to be viewed.

![Screen Shot 2022-04-15 at 1.28.37 PM.png](SQL%20Refere%205fc6a/Screen_Shot_2022-04-15_at_1.28.37_PM.png)

## **Sorting Data**

The `ORDER BY` ****clause sorts the result set based on specified criteria in ascending or descending orders. By default, it's in ascending order.  To change to descending just `DESC`

I want view a list of clients where clients are in ascending order based on last name

```sql
-- Display first and last name where its sorted based on last name
SELECT first_name,last_name
FROM `demo_project`.`/Dummy-Customers-1.xlsx` 
ORDER BY last_name
```

## **Filtering Data**

The `SELECT DISTINCT` clause filters any duplicate from the selected column or whole dataset and returns distinct values only.

```sql
--Display only company name
SELECT DISTINCT company_name
FROM demo_project_data.`/Dummy-Customers-1.xlsx`
```

![Screen Shot 2022-04-15 at 2.11.05 PM.png](SQL%20Refere%205fc6a/Screen_Shot_2022-04-15_at_2.11.05_PM.png)

 ****The ****`WHERE`  ****clause filters columns to extract only records that fulfill a specified condition.

```sql
--Select all customers from the company Kare
SELECT first_name,last_name, company_name
FROM demo_project_data.`/Dummy-Customers-1.xlsx`
WHERE company_name = 'Kare'
```

![Screen Shot 2022-04-15 at 2.13.29 PM.png](SQL%20Refere%205fc6a/Screen_Shot_2022-04-15_at_2.13.29_PM.png)

**Operators in the WHERE clause  to test if two expressions are the same.**

| Operators | Description | Example |
| --- | --- | --- |
| = | Equal | column = expression |
| > | Greater Than | column > expression |
| < | Less Than | column < expression |
| >= | Greater Than or Equal | column >= expression |
| <= | Less Than or Equal to | column <= expression |
| <> , != | Not Equal to | column != expression |

**SQL logical operators allows you to test if conditions are True or False based on conditions**

The `AND` ****operator filter records based on more than one condition and displays a record if all the conditions separated by AND are TRUE.

```sql
--Selects all customers who are from  Kare and their first name is Portia
SELECT first_name,last_name, company_name
FROM demo_project_data.`/Dummy-Customers-1.xlsx`
WHERE company_name = 'Kare' AND first_name = 'Portia'
```

![Screen Shot 2022-04-15 at 2.39.21 PM.png](SQL%20Refere%205fc6a/Screen_Shot_2022-04-15_at_2.39.21_PM.png)

The `OR`  ****operator filter records based on more than one condition and displays a record if any of the conditions separated by OR is TRUE.

```sql
--Select all customer who are from coompany Kare OR their name is Portia 
SELECT first_name,last_name, company_name
FROM demo_project_data.`/Dummy-Customers-1.xlsx`
WHERE company_name = 'Kare' OR first_name = 'Portia'
```

![Screen Shot 2022-04-15 at 2.40.44 PM.png](SQL%20Refere%205fc6a/Screen_Shot_2022-04-15_at_2.40.44_PM.png)

The `NOT` ****operator filter records based on more than one condition and displays a record if the condition(s) is NOT TRUE.

```sql
--Select all customer who are not from the company Kare should show 997 customers
SELECT first_name,last_name, company_name
FROM demo_project_data.`/Dummy-Customers-1.xlsx`
WHERE NOT company_name = 'Kare'
```

![Screen Shot 2022-04-15 at 2.42.03 PM.png](SQL%20Refere%205fc6a/Screen_Shot_2022-04-15_at_2.42.03_PM.png)

The `IN`  ****operator returns true if a value is in a set of values or false otherwise.

```sql
--IN operator is a shorthand for multiple OR operator
SELECT first_name,last_name, company_name
FROM demo_project_data.`/Dummy-Customers-1.xlsx`
WHERE company_name IN ('Kare','Tanoodle')
```

![Screen Shot 2022-04-15 at 2.50.41 PM.png](SQL%20Refere%205fc6a/Screen_Shot_2022-04-15_at_2.50.41_PM.png)

The `BETWEEN` operator selects values within a given inclusive range. The data type can be numbers, text, or dates.

```sql
-- Select customer who's ip adress are between '0.146.230.61' AND '123.110.196.5'
SELECT first_name,last_name, ip_address
FROM demo_project_data.`/Dummy-Customers-1.xlsx`
WHERE ip_address BETWEEN '0.146.230.61' AND '123.110.196.5'
```

![Screen Shot 2022-04-15 at 2.55.45 PM.png](SQL%20Refere%205fc6a/Screen_Shot_2022-04-15_at_2.55.45_PM.png)

## J**oining Multiple Tables**

DataDistillr allows you to link different datasource on the platform, this tutorial will show you how to linking tables together by using the `JOIN` clause which combines rows from two or more tables, based on a related column between them.

![Joins.png](SQL%20Refere%205fc6a/Joins.png)

The `AS`  clause allows you to give a temporary name to a table or column through aliases. This makes writing complex queries simpler.

```sql
-- Rename columns to make it pretty and easier to display
SELECT ip_address, getCountryName(ip_address) AS country
FROM demo_project_data.`/Dummy-Customers-1.xlsx`
LIMIT 1000
```

![Screen Shot 2022-04-15 at 3.05.35 PM.png](SQL%20Refere%205fc6a/Screen_Shot_2022-04-15_at_3.05.35_PM.png)

The `FULL OUTER JOIN` includes all rows from the joined tables whether or not the other table has the matching row

```sql
--Full join of two tables based on id number, should return everything
SELECT
	c1.first_name,
  c1.email,
  c2.first_name AS first_name1, 
  c2.email AS email2
FROM `demo_project`.`/Dummy-Customers-1.xlsx` as c1 
FULL OUTER JOIN `demo_project`.`/Dummy-Customers-2.xlsx` as c2 
ON c1.id = c2.id

```

![Screen Shot 2022-04-15 at 4.36.31 PM.png](SQL%20Refere%205fc6a/Screen_Shot_2022-04-15_at_4.36.31_PM.png)

The `INNER JOIN` returns rows if there is, at least, one row in both tables that matches the join condition. The inner join clause eliminates the rows that do not match with a row of the other table

For each row in column_name1, the inner join clause finds the matching rows in column_name2. If a row is matched, it is included in the final result set.

```sql
--Inner join both tables based company name
SELECT *
FROM `demo_project`.`/Dummy-Customers-1.xlsx` as customer1
INNER JOIN `demo_project`.`/Dummy-Customers-2.xlsx` as customer2
ON customer1.id = customer2.id
```

![Screen Shot 2022-04-15 at 5.10.57 PM.png](SQL%20Refere%205fc6a/Screen_Shot_2022-04-15_at_5.10.57_PM.png)

The query below shouldn't return anything because first names are not repeated in both tables

![Screen Shot 2022-04-15 at 4.42.51 PM.png](SQL%20Refere%205fc6a/Screen_Shot_2022-04-15_at_4.42.51_PM.png)

The `LEFT JOIN` clause returns all rows from the left table whether or not there is a matching row in the right table. 

```sql
--Left join tables based on the same fist name. Only 7 People have the same name
SELECT *
FROM `demo_project`.`/Dummy-Customers-1.xlsx` as customer1
LEFT JOIN `demo_project`.`/Dummy-Customers-2.xlsx` as customer2
ON customer1.first_name = customer2.fist_name
```

![Screen Shot 2022-04-15 at 5.13.33 PM.png](SQL%20Refere%205fc6a/Screen_Shot_2022-04-15_at_5.13.33_PM.png)

The `RIGHT JOIN` clause returns all rows from the right table whether or not there is a matching row in the left table. 

```sql
--Right join based on first name. Only 7 people have the same first name
SELECT *
FROM `demo_project`.`/Dummy-Customers-1.xlsx` as customer1
RIGHT JOIN `demo_project`.`/Dummy-Customers-2.xlsx` as customer2
ON customer1.first_name = customer2.first_name
```

![Screen Shot 2022-04-15 at 5.15.41 PM.png](SQL%20Refere%205fc6a/Screen_Shot_2022-04-15_at_5.15.41_PM.png)

## **Aggregate Functions**

The `MIN()` function returns the smallest value of the selected column.

```sql
-- smallest ip_address
SELECT MIN(ip_address)
FROM demo_project_data.`/Dummy-Customers-1.xlsx`
```

![Screen Shot 2022-04-15 at 5.18.07 PM.png](SQL%20Refere%205fc6a/Screen_Shot_2022-04-15_at_5.18.07_PM.png)

The `MAX()` function returns the largest value of the selected column.

```sql
-- Largest ip_address
SELECT MAX(ip_address)
FROM demo_project_data.`/Dummy-Customers-1.xlsx`
```

![Screen Shot 2022-04-15 at 5.19.05 PM.png](SQL%20Refere%205fc6a/Screen_Shot_2022-04-15_at_5.19.05_PM.png)

The `COUNT()` function returns the number of rows that matches a specified criterion.

```sql
-- Calculate the number of x in my column
SELECT COUNT(column_name)
FROM demo_project_data.`/Dummy-Customers-1.xlsx`
```

The `AVG()`function returns the average value of a numeric column. This calculates the average value of a set.

```sql
--Calculate the average  value of my column
SELECT AVG(column_name)
FROM demo_project_data.`/Dummy-Customers-1.xlsx`
```

The `SUM()`function returns the total sum of a numeric column only. This can be distinct values or all values within the column

```sql
-- Calculate the sum of the numeric column selected
SELECT SUM(column_name)
FROM demo_project_data.`/Dummy-Customers-1.xlsx` 
```