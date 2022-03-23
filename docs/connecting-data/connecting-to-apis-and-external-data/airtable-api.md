# Connecting to Airtable

### Creating an Airtable account 
Set up an account with [Airtable](airtable.com). 

__Costs__  
There are several different types of accounts. There is a free version, a $10 and $20 version. You can check [HERE](https://airtable.com/wspBcisr7QHMSSfml/workspace/plans?ref=bp.skp2021hpub) for details and comparison.


__Rate Limits__  
The Airtable API is limited to 5 requests per second per base. If you exceed this rate, you will receive a 429 status code and will need to wait 30 seconds before subsequent requests will succeed.

## Airtable Data Source Form
To set up a data source connection for Airtable, you will need to have:

- A unique name for your data source connection to be used in queries.
- The Base ID.
- The API Key generated Through your Airtable account.



### Form

![Airtable Form][image-1]


### Base ID
You can access your Base at [https://airtable.com/](https://airtable.com/).

![Finding your base][image-2] 

You can find the Base ID in Hoghlighted section of the Base URL


`https://airtable.com/`<mark>YOUR_BASE_ID</mark>`/tblPI1Mclv7pqrqDq/viwCAMdqRwJpFOlxl?blocks=hide`

### API Key

To generate your API Key you can access your [account](https://airtable.com/account) where you will have the option to generate an API Key


![Generate API Key][image-4]


## Endpoints


### Table

| Endpoint | URL Params | Optional | Description |
| -------- | ---------- | -------- | ----------  |
| tables   | TableName  | priority<br>sources<br>tags<br>unaggregated<br>exclude_aggregate<br>page|Returns the table and it's cells 
                 



### Query Page Sidebar

![Airtable Endpoints][image-3]

## Sample Queries

Suppose that my Airtable API data source was called `myairtableapi` and you have a table called `Form Responses 1`. In the table there are several columns including ID and fields. In order to access the values in the fields column you have to query their keys specifically as so.

### Get Tables Endpoint

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