---
description: Running your first query in DataDistillr
---

# 🏃 Run a Query

Now that you've set up a project and uploaded an Excel file, you are ready to start querying data. From the project
page, click on the query button and you will be taken to the query editor.

![The query button](<../img/getting-started/query-button.png>)

See the query editor below. There's a lot to explore here!

![Query editor view](<../img/getting-started/query-editor.png>)

### **Viewing the Schema**

If you followed our tutorial for [Creating Your First Project](create-your-first-project.md) and
[Connecting a Data Source and Uploading a File](connecting-a-data-source-and-uploading-a-file.md), you should see two
Excel files in the left column under _Uploads_. If you click the arrow next to the file name, the listing will expand to
show the file schema.

!!! info

    DataDistillr automatically discovers the schema of your data, but there may be times where you need to correct it.
    You can read more about schema discovery in the schema section of the documentation.

### **Running a Query**

If you click on the file name, a tab will open with a basic query that should look something like this:

```sql
SELECT *
FROM demo_project_data.`/Dummy-Customers-1.xlsx` LIMIT 1000
```

This is a basic SQL query that displays all available fields in the dataset and limits the results to 1000 records.

!!! info DataDistillr uses SQL to access and query data. While many tools use SQL, most have their own dialect of SQL.
DataDistillr follows the ANSI standard, with additions to support data cleaning and dealing with complex data sets. Read
more about SQL in the [SQL Reference Guide](../sql-reference/sql-intro.md).

To Run this Query, you can press _Run_ or _Run Query_ as shown below. See the section: Additional Querying Options for
more information on the difference between these two buttons.

![Run Query](<../img/getting-started/run-query.png>)

Now, let's modify this query by replacing the pre-populated query with the query below:

```sql
SELECT ip_address, getCountryName(ip_address) AS country
FROM demo_project_data.`/Dummy-Customers-1.xlsx` LIMIT 1000
```

Unlike the previous query, this returns only two columns: ip_address and country (derived from the getCountryName()
function).

![Results View](<../img/getting-started/result-view.png>)

!!! info Enriching your data is extremely useful in data analysis. DataDistillr has many functions like the one above
that can enrich artifacts such as phone numbers, IP Addresses, bank routing numbers, MAC addresses, state, country
codes, and much more. See the section: Enriching your Data for more!

As you will see, working with data in DataDistillr is simpler than other analytics tools because it allows you to
interact with different data types in exactly the same manner.

Congratulations! Now you are ready to create data visualization using this dataset.