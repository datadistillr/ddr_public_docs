---
description: How to Connect DataDistillr to a Simple API
---

# Connection Basics

Let's start with connecting the most simple API possible.  There is a fantasy football API available here: [https://www.fantasyfootballdatapros.com/api/players/2019/1](https://www.fantasyfootballdatapros.com/api/players/2019/1){target="_blank"}.

This API returns fantasy football players for a given year.  The data is returned in JSON format and is completely static.  Let's look at how you could connect this API to DataDistillr.  First, follow the [earlier instructions about connecting to a data source](../../).  When you get to the window to choose the data source type, select API as shown below.&#x20;

![Select API from the available choices](../../img/Screen Shot 2021-11-19 at 1.46.04 PM.png)

### __Adding a Custom API__

DataDistillr comes prepopulated with API configurations for popular APIs such as ServiceNow, SalesForce, Google Analytics and others.  In our case, we will need to select _Custom API_, as shown below.&#x20;

![Select Custom API](<../../../img/Screen Shot 2021-11-19 at 1.48.27 PM.png>)

### __Name Your Connection__

The next step is to give your connection a unique name.  This name will appear in queries and should be descriptive of what the API is.  It also should only contain alphanumeric characters and underscores.

#### __Understanding DataDistillr's API Namespaces__

Once you have created your connection, DataDistillr allows you to define endpoints for the API.  This may seem silly for an API with only one option, but consider something like github, or a banking API.  There are likely multiple datasets which you'd like to access.  Defining multiple endpoints per connection allows you to have logical, clean queries.

For example, let's say that you wanted to connect to github's API, which has datasets for accessing repositories, organizations, people and more.  By defining multiple endpoints, you will end up with queries like this:

```sql
SELECT *
FROM github.repos

SELECT *
FROM github.orgs
```

For our example here, give your API a name, and then click on the Add button by the endpoints, as shown below.

![Add your API](<../../img/Screen Shot 2021-11-19 at 1.54.13 PM.png>)

### __Adding an Endpoint__

Now you are ready to add an endpoint to your API connection.  For our simple example, the only fields you will need to fill out are the endpoint name, the URL, the request method (`GET`) and the data format, as shown in the screenshot below.&#x20;

![Adding an Endpoint](<../../img/Screen Shot 2021-11-19 at 2.43.02 PM.png>)

Once you've done that, save your work and you are ready to query!

### __Querying Your APIs__

Now that you've added your data, you can query your data.  In the query veiw, you will see your endpoint listed, but if you want to type in a query, or use this endpoint in a pre-existing query, you can run a query like the one below:

```sql
SELECT * 
FROM fantasyfootball.players
```

Happy Distilling!
