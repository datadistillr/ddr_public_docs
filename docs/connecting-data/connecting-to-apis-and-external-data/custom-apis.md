---
description: How to Connect DataDistillr to a Simple API
---

# Custom APIs

Let's start with connecting this simple Fantasy Football API:
[https://www.fantasyfootballdatapros.com/api/players/2019/1](https://www.fantasyfootballdatapros.com/api/players/2019/1){target="_blank"}.

This API returns fantasy football players for a given year. The data is returned in JSON format and is completely static.

### __Connecting to an API__

Let's look at how you could connect this API to DataDistillr. First, follow the section on how to 
[connect to a data source](../../). When you get to the window to choose the data source type, select _API_ as shown below.

![Select API from the available choices][image-1]

DataDistillr comes prepopulated with API configurations for popular APIs such as ServiceNow, SalesForce, Google
Analytics and others. In our case, we will need to select _Custom API_, as shown below.

![Select Custom API][image-2]

### __Name Your Connection__

The next step is to give your connection a unique name. This name will appear in queries and should describe what the
API is and only include alphanumeric characters and underscores.

#### __Understanding DataDistillr's API Namespaces__

Once you have created your connection, DataDistillr allows you to define endpoints for the API.  This may seem silly
for an API with only one option, but consider something like GitHub or a banking API. There are likely multiple datasets
which you'd like to access. Defining multiple endpoints per connection allows you to have logical, clean queries.

For example, let's say that you wanted to connect to GitHub's API, which has datasets for accessing repositories,
organizations, people and more. By defining multiple endpoints, you will end up with queries like this:

```sql
SELECT *
FROM github.repos

SELECT *
FROM github.orgs
```

For our example here, give your API a name, and then click on the _Add_ button by the endpoints, as shown below.

![Add your API][image-3]

### __Adding an Endpoint__

Now you are ready to add an endpoint to your API connection.  For our simple example, the only fields you will need to
fill out are the **endpoint name, the URL, the request method (`GET`), and the data format,** as shown below.

![Adding an Endpoint][image-4]

Now, click _Save_ and you are ready to query!

### __Querying Your APIs__

Now that you've added your data, you can query your data. In the query editor, you will see your endpoint listed,
but if you want to type in a query, or use this endpoint in a pre-existing query, you can run a query like this:

```sql
SELECT *
FROM fantasyfootball.players
```


[image-1]: ../../img/api/select-api-form.png
[image-2]: ../../img/api/custom/CustomAPI_v0.7.2.png
[image-3]: ../../img/api/custom/custom-API-form.PNG
[image-4]: ../../img/api/custom/API-endpoint-form.PNG
