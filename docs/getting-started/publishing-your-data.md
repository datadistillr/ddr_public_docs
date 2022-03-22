# 📰 Publishing Your Data

In this final installment of the quick start tutorial, you will learn how to take any dataset you've created, and publish it so that you can access it programmatically. &#x20;

!!! info "Why Publish Data?"
    

    DataDistillr is a great tool for exploring data, but sometimes there will be situations in which DataDistillr cannot do everything you need, such as machine learning. In this case, we have made it easy for you to do your data exploration in DataDistillr, then publish your dataset and easily move it into a Pandas, PySpark or R dataframe for machine learning.


### __Publishing Data__

After you've run a query, in the top bar, you will see a button labeled _Manage API Access._ Click on that button as shown below.

![Manage API Access Button](<../img/Screen Shot 2021-11-23 at 11.46.54 PM.png>)

### __API Management Screen__

The API Management Screen is where you can control access to the various datasets you have created.

!!! warning
    When you publish a dataset, anyone with the access information can view the data. Exercise caution in exposing data, and make sure you protect the access tokens to prevent unauthorized access.


### __Create an API Access Client__

Since this is your first project, you will have to create an API Access Client. Enter a name and enable the API app.&#x20;

![Create an API client](<../img/Screen Shot 2021-11-24 at 12.10.39 AM.png>)

#### __Understanding API Permissions__

When you create an API Access Client, all of your projects and queries within those projects will be visible. You can set permissions for each of these to allow or disallow API access to your datasets. Allow, and deny are self-explanatory. When the permission is set to _inherit_, the dataset will inherit the permission from the project.

!!! info
    Users will have to have an access token in order to access the data. Publishing a data set does not automatically make the data visible to the world.&#x20;

You can expand a project tab and see all the queries in a project. From there, you can set the access permissions for every dataset resulting from a query, as well as view API usage statistics.

![API Access Management](<../img/Screen Shot 2021-11-23 at 11.52.23 PM.png>)

### __Accessing Published Data__

Once you've published your data, you can access this data programmatically. To retrieve the access tokens, as well as code snippets, click on the <code>&lt;/&gt;</code> icon next to the permissions. DataDistillr will generate code snippets similar to the examples below, prepopulated with your API key and data set ids, so all you will have to do is copy and paste this code into your Python or R scripts.

=== "Python"

    ```python
    import pandas as pd
    import requests

    url = "https://app.datadistillr.io/v1/results/<dataset id>"
    api_key = "<YOUR API KEY HERE>"
    headers = {"Authorization": api_key}

    response = requests.get(url, headers=headers)
    data = pd.DataFrame(response.json()['results'], columns=response.json()['summary']['columnNames'])
    ```

=== "Python with DataDistillr SDK" 

    ```python
    import datadistillr.datadistillr as ddr

    url = "https://app.datadistillr.io/v1/results/<dataset id>"
    auth_token = "<YOUR API KEY HERE>"
    dataframe = ddr.datadistillr.get_dataframe(url, auth_token)
    ```

=== "R" 

    ```r
    library(dplyr)
    library(httr)
    library(data.table)

    URL <- "https://app.datadistillr.io/v1/results/<dataset id>"
    AUTH_HEADER <- "<YOUR API KEY>"

    response <- GET(URL, add_headers(Authorization = AUTH_HEADER))
    content <- content(response, as = "parsed", type = "application/json")
    data <- data.frame(rbindlist(content$results))
    colnames(data) <- content$summary$columnNames
    ```

That's it!