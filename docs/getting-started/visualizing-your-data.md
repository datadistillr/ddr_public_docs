---
description: Creating a Quick Visualization
---

# 📊 Visualizing your Data

Now that you know how to execute a query in DataDistillr, let's create a visualization. In the query editor, enter the
following query:

```sql
SELECT getCountryName(ip_address) AS Country, COUNT(*) AS Customer_Count
FROM demo_project_data.`/Dummy-Customers-*.xlsx`
WHERE getCountryName(ip_address) <> 'Unknown'
GROUP BY Country
ORDER BY Customer_Count DESC
```

This query is an _aggregate query_ and will count the number of records by country name. This pattern of aggregation is
useful for summarizing data.

!!! info "Did You Notice the Asterisk?"
One powerful feature of DataDistillr is that it can query directories of files as if they were one big file. The query
above is actually executing over any files in the directory with the naming pattern `Dummy-Customers-n.xlsx`.

Next, click on the _Visualize_ button at the top of the screen to visualize the data.

![Visualization Button](<../img/getting-started/visualize-button.png>)

### __Visualization Options__

Next, you will see the visualization screen with options on the left as shown. For a more complete view of
DataDistillr's visualization capabilities, see the Visualization section of the documentation.

![Visualization Screen](<../img/getting-started/visualization-options.PNG>)

Fill in the left columns with the following options to generate the chart above:

- For _Graph Type_, select _Bar_
- Click the edit icon in _Transform_ and set the _Limit_ to _10_
- Double-click _Untitled_ to rename the graph and press _Save_
- For the X-Axis, select `Country`
- For the Y-Axis, select `Customer_Count`

You can export your data visualization as a jpeg or png by hovering over _Download_ in the top bar.

Congratulations! Now you are ready to publish your data.