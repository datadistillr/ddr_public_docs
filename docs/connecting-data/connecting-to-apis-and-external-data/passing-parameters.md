---
description: This page explains how to pass parameters to APIs in a query
---

# Passing Parameters

Now that you've learned how to connect DataDistillr to an API to query external data sources, let's take it to the next
level and learn how to pass parameters to the API directly in the query. Depending on your API, these parameters can
either be passed as part of the URL or as query parameters. Let's first look at parameters in the URL using the GitHub
API: [https://docs.github.com/en/rest](https://docs.github.com/en/rest){target="_blank"}.

### __Parameters in the URL Path__

Many APIs will require you to specify arguments that are part of the URL path. For our example, we will retrieve an
organization's list of public projects. GitHub's API docs provide a base URL for all API calls of
[https://api.github.com](https://api.github.com){target="_blank"}. In the API docs, there is an explanation
for [how to query an organization's projects](https://docs.github.com/en/rest/reference/projects){target="_blank"}. As
you can see, GitHub specifies that the path is:

```
/orgs/{org}/projects
```

If we wanted to see the Apache Foundation's projects, we could thus, create the URL
[https://api.github.com/orgs/apache/projects](https://api.github.com/orgs/apache/projects){target="_blank"}, and we
would get that data. If you wanted that to be static, you could just use that URL, but what if you wanted to be able to
query an arbitrary organization?

To do that, simply follow the [Custom APIs](custom-apis.md) documentation to set up a connection to GitHub, add an
endpoint called
`projects` and use the URL: `https://api.github.com/orgs/{org}/projects` in Endpoint URL field in your configuration, as
shown below.

![Github Project Example Configuration](<../../img/api/endpoint-URL-with-parameter.png>)

Now, you can execute the following query to retrieve the Apache Foundation's projects:

```sql
SELECT *
FROM github.projects
WHERE org = 'apache'
```

Including `WHERE org='apache'` in the query passes that parameter into the API when the data is retrieved. You can
specify as many parameters as you want as long as the name in the curly braces `{}` is unique for each parameter.

!!! warning When you include URL path parameters in your API endpoint, your queries will fail if you do not include them
in the query `WHERE` clause. You can only use equality filters.

#### __Specifying a Default Value for URL Path Parameter__

You can specify a default parameter in the URL parameter as shown
here: `https://api.github.com/org/{org=apache}/projects`. If you do not include a WHERE clause in a query, `apache` will
be passed in the URL.

### __Passing Parameters as URL Query Options__

In addition to passing parameters in the URL, you can also pass parameters as part of the URL string. Sometimes these
are mandatory, sometimes not, but regardless, you can configure DataDistillr to pass these parameters in your API
queries. As an example, we will use an API for calculating sunrise/sunset times:
[https://sunrise-sunset.org/api](https://sunrise-sunset.org/api){target="_blank"}.

As an example, the URL below allows you to specify the latitude, longitude, and date for which you want the
sunrise/sunset times.

[https://api.sunrise-sunset.org/json?lat=36.7201600\&lng=-4.4203400\&date=2021-12-17](https://api.sunrise-sunset.org/json?lat=36.7201600\&lng=-4.4203400\&date=2021-12-17){target="_blank"}

The parameters are `lat`, `lng` and `date`. When configuring your API endpoint, simply add the required parameters to
the section labelled _Required Parameters_ section and any optional parameters to the _Optional Parameters_ section as
shown below.

![Adding Parameters to API Configuration](<../../img/api/parameters.PNG>)

Next, you can pass these parameters in query as shown below:

```sql
SELECT *
FROM api.sunrise
WHERE lat = 36.723
  AND lng = -4.420
```

You can combine parameters with the `AND` operator, but these queries will fail with an `OR` operator. Also, with query
parameters, you can only pass equality parameters. Parameters with any other comparison operator will fail.&#x20;