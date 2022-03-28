# Connecting to Airtable

## Creating an Airtable account
Set up an account with [Airtable](https://www.airtable.com/).

__Costs__  
There are several different types of accounts. There is a free version, a $10 and $20 version. You can check [HERE](https://www.airtable.com/pricing) for details and comparison.


__Rate Limits__  
The Airtable API is limited to 5 requests per second per base. If you exceed this rate, you will receive a 429 status code and will need to wait 30 seconds before subsequent requests will succeed.

## How to Connect DataDistillr to Airtable
To set up a data source connection for Airtable, you will need to have:

- A unique name for your data source connection to be used in queries.
- The Base ID (Called 'Project Path' on the form).
- The API Key generated through your Airtable account.



### Data Source Form

To locate the Airtable form, follow the steps in [Connecting Your Data to DataDistillr](../../). When you get to the window to choose the data source type, select API as shown below.&#x20;

![Select API from the available choices][image-5]

On the API screen, select Airtable from list of API forms as shown in the image below.

![Select Airtable API from available choices][image-6]

The following form will appear. Instructions can be found below on how to find the information required to fill each field on the Airtable API form.

Once you have filled out all the fields, press the green 'Save' button, and your API will be connected!

![Airtable Form][image-1]

### Name

Enter any name that will help you recognize this data source from within your query window. &#x20;

Acceptable characters include:

* lowercase alphanumeric characters
* underscores

### Project Path (Base ID)
You can access your Base ID at [https://airtable.com/](https://airtable.com/). Navigate to Bases along the top panel and click on your workspace as shown in the image below.

![Finding your base][image-2]

You can find the Project Path (Base ID) in the Highlighted section of the Base URL shown below, and enter this into the Airtable Data Source Form as the 'Project Path'.

`https://airtable.com/`<mark>YOUR_BASE_ID</mark>`/tblPI1Mclv7pqrqDq/viwCAMdqRwJpFOlxl?blocks=hide`

### API Key

To generate your API Key, navigate to your [Account overview](https://airtable.com/account) where you will have the option to generate an API Key as highlighted below. Copy this API Key and enter into the Airtable Form.


![Generate API Key][image-4]


## Endpoints

The table below shows a list of endpoints available to connect to within the DataDistillr application. If you need to connect to any endpoints not listed in the table below, please use the [Custom API](custom-apis.md) Form.

| Endpoint | URL Params | Optional                                                                 | Description                      |
|----------|------------|--------------------------------------------------------------------------|----------------------------------|
| tables   | TableName  | priority<br>sources<br>tags<br>unaggregated<br>exclude_aggregate<br>page | Returns the table and it's cells |


### Nav Tree

The endpoint above will display as follows in the nav tree once your API has successfully connected.

![Airtable Endpoints][image-3]

## Sample Queries

The following queries are intended to help you get started, and make life simpler querying within your API.

### Get Tables Endpoint

Suppose that my Airtable API data source was called `myairtableapi` and you have a table called `Form Responses 1`. In the table there are several columns including ID and fields. In order to access the values in the fields column you have to query their keys specifically as so.


```sql
SELECT AT.id AS ID,
AT.fields['Timestamp'] AS Times,
AT.fields['Name'] AS Name,
AT.fields['Email Address'] AS Address
FROM myairtableapi.`tables` AS AT
WHERE tableName='Form Responses 1'
```


[image-1]: ../../img/api/airtable/airtable-form.png
[image-2]: ../../img/api/airtable/airtable-base.png
[image-3]: ../../img/api/airtable/airtable-endpoint.png
[image-4]: ../../img/api/airtable/airtable-generate-api.png
[image-5]: ../../img/api/select-api-form.png
[image-6]: ../../img/api/airtable/select-Airtable-API.png
