---
description: Running your first query in DataDistillr
---

# 🏃 Running a Query

Now that you've setup a project, and uploaded an Excel file, you are ready to start querying data. From the project page, click on the query button and you will be taken to the query view.&#x20;

![The query button](<../img/Screen Shot 2021-11-16 at 9.29.36 PM.png>)

The screenshot below shows our query viewer; there's a lot here.

![Query Viewer](<../img/Screen Shot 2021-11-16 at 9.33.10 PM.png>)

### __Viewing the Schema__

Firstly, if you did everything from the preceding two pages, in the left column of the page you should have an upload data source in the nav tree with a few Excel files in it. If you click the arrow next to the file name, the file listing will expand and you will see the schema of the files that you uploaded.

DataDistillr automatically discovers the schema of your data, but there may be times where you need to correct it. You can read more about schema discovery in the schema section of the documentation.&#x20;

### __Running a Query__

If you click on the file name, a tab will open with a basic query that should look something like this:

```sql
SELECT * 
FROM demo_project_data.`/Dummy-Customers-1.xlsx`
LIMIT 1000
```

This is the most basic query you can run. This query will display all available fields in the dataset, and limit the results to 1000 records.

!!! info 
    DataDistillr uses SQL to access and query data. While many tools use SQL, most have their own dialect of SQL. For the most part, DataDistillr follows the ANSI standard, with additions to support data cleaning and dealing with complex data sets. You can read more about DataDistillr's SQL in the SQL Reference section. &#x20;


To Run this Query, you may press either the purple _Run_ button, or the gray _Run Query_ button as shown below. The differences in these buttons will be explained in more detail in the Additional Querying Options section.

![Run Query](<../img/Screen Shot 2021-11-23 at 8.54.05 AM.png>)

Now, let's modify this query slightly. Replace the pre-populated query with the query below:

```sql
SELECT ip_address, getCountryName(ip_address) AS country
FROM demo_project_data.`/Dummy-Customers-1.xlsx`
LIMIT 1000
```

Unlike the previous query, this query returns only two columns, the IP address and then a derived column which is the country name.

![Results View](<../img/Screen Shot 2021-11-16 at 10.43.31 PM.png>)

!!! info
    Enriching your data is extremely useful in data analysis. DataDistillr has many functions such as the one you saw above which can enrich artifacts such as phone numbers, IP Addresses, bank routing numbers, MAC addresses, state and country codes and much more. See the section: Enriching your Data for more!


Congratulations! You've taken your first step towards working with data with DataDistillr. As you will see, working with data with DataDistillr is simpler than many other analytics tools because it allows you to interact with many data types in exactly the same manner. 


Now, let's look at how you can present this data through visualization.&#x20;