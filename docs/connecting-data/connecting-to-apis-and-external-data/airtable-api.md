---
description: How to Connect DataDistillr to the Airtable API
---

# Connecting to Airtable

## Getting Started with Airtable
Set up an account with [Airtable](https://www.airtable.com/){target=_blank}.

???+ cost "Costs" 

    There are both free and [paid](https://airtable.com/pricing){target=_blank} options for this API.


???+ rlimit "Rate Limits"  

    Airtable limits the number of requests each API key can make per second. Current rate limits are available in Airtable's [documentation](https://support.airtable.com/hc/en-us/articles/203313985-Public-REST-API#:~:text=Is%20there%20a%20rate%20limit,requests%20per%20second%2C%20per%20base.){target=_blank}.

## How to Connect DataDistillr to Airtable
To set up a data source connection for Airtable, you will need to have:

- A [unique name](#name) for your data source connection to be used in queries.
- The [Base ID](#base-id-project-path) (Called 'Project Path' on the form).
- The [API Key](#api-key) generated through your Airtable account.



### Data Source Form

To locate the Airtable form, follow the steps in [Connecting Your Data to DataDistillr](../../). When you get to the window to choose the data source type, select API as shown below.&#x20;

![Select API from the available choices][image-5]

On the API screen, select Airtable from list of API forms as shown in the image below.

![Select Airtable API from available choices][image-6]

The following form will appear. Instructions are below on how to find the information required to fill each field on the Airtable API form.

Once you have filled out all the fields, press the green 'Save' button, and your API will be connected!

![Airtable Form][image-1]

### Name

Enter any name that will help you recognize this data source from within your query window. &#x20;

!!! info "Acceptable characters include"

    * lowercase alphanumeric characters
    * underscores

### Base ID (Project Path)

=== "1. Find your base"

    After [logging in](https://airtable.com/){target=_blank}, you can access your Base ID by navigating to 'Bases' along the top panel and clicking on your workspace as shown in the image below.
    
    ![Finding your base][image-2]
    
=== "2. Find your Base ID (Project Path)"

    OYou can find the Base ID (Called Project Path in our form) in the Highlighted section of the Base URL shown below, and enter this into the Airtable Data Source Form as the 'Project Path'.
    
    `https://airtable.com/`<mark>YOUR_BASE_ID</mark>`/tblPI1Mclv7pqrqDq/viwCAMdqRwJpFOlxl?blocks=hide`

### API Key

=== "1. Generate and copy API Key"

    To generate your API Key, navigate to your [Account overview](https://airtable.com/account){target=_blank} where you will have the option to generate an API Key as highlighted below. Copy this API Key and enter into the Airtable Form.

    ![Generate API Key][image-4]


## Endpoints

The table below shows a list of endpoints available to connect to within the DataDistillr application. If you need to connect to any endpoints not listed in the table below, please use the [Custom API](custom-apis.md) Form.

| Endpoint | URL Params | Optional                                                                 | Description                     |
|----------| ---------- |--------------------------------------------------------------------------|---------------------------------|
| `tables`   | TableName  | priority<br>sources<br>tags<br>unaggregated<br>exclude_aggregate<br>page | Returns the table and its cells |


### Nav Tree

The endpoint above will display as follows in the nav tree once your API has successfully connected.

![Airtable Endpoints][image-3]

## Sample Queries

The following queries are intended to help you get started, and make life simpler querying within your API.

For the following examples, suppose that my Airtable API data source was called `myairtableapi`, and I want to query an endpoint. The endpoint goes after the ClickUp data source name:

!!! example "FROM Clause"

    ```sql
    FROM `myairtableapi`.`<ENDPOINT>`
    ```

### Get Tables Endpoint

Suppose you have a table called `Form Responses 1`. In the table there are several columns including `ID` and `fields`. In order to access the values in the fields column you have to query their keys specifically as so.


```sql
SELECT AT.id AS ID,
AT.fields['Timestamp'] AS Times,
AT.fields['Name'] AS Name,
AT.fields['Email Address'] AS Address
FROM `myairtableapi`.`tables` AS AT
WHERE tableName='Form Responses 1'
```

[image-1]: ../../img/api/airtable/airtable-form.png
[image-2]: ../../img/api/airtable/airtable-base.png
[image-3]: ../../img/api/airtable/airtable-endpoint.png
[image-4]: ../../img/api/airtable/airtable-generate-api.jpeg
[image-5]: ../../img/api/add-api.png
[image-6]: ../../img/api/airtable/airtable-select-api.jpeg
