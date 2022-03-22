---
description: Creating a Quick Visualization
---

# 📊 Visualizing your Data

Now that you know how to execute a query in DataDistillr, we are going to create a visualization. In the query editor, enter the following query:

```sql
SELECT getCountryName(ip_address) AS Country, COUNT(*) AS Customer_Count
FROM demo_project_data.`/Dummy-Customers-*.xlsx`
WHERE getCountryName(ip_address) <> 'Unknown'
GROUP BY Country
ORDER BY Customer_Count DESC
```

This query is an _aggregate query_ and will count the number of records by country name. This pattern of aggregation is extremely useful for summarizing data.

!!! info "Did You Notice the Star?"
    Did you notice the asterisk in the file path? One very powerful feature of DataDistillr is that it can query directories of files as if they were one big file. The query above is actually executing over any files in the directory with the naming pattern `Dummy-Customers-n.xlsx`.


Next, we are going to visualize this data. Click on the _Visualize_ button at the top of the screen to visualize the data.

![Visualization Button](<../img/Screen Shot 2021-11-16 at 10.56.38 PM.png>)

### __Visualization Options__

Next, you will see the visualization screen with options on the left as shown below:

![Visualization Screen](<../img/Screen Shot 2021-11-23 at 9.25.36 AM.png>)

For _Graph Type_, select _Bar_. For _Limit_, enter _10_. Double click on the _Series_, enter the name of your data, and Press _Save_. Next, for the X-Axis, select `Country,` and for the Y-Axis, select `Customer_Count`. You should now have a visualization that looks something like the chart below:

![Customers by Country](<../img/Screen Shot 2021-11-23 at 9.27.46 AM.png>)

Congrats! You've created your first visualization using DataDistillr! For a more complete view of DataDistillr's visualization capabilities, please refer to the Visualization section of the documentation.&#x20;

Now, let's move on to publishing your data!