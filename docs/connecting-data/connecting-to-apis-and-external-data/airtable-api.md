# Connecting to Airtable

## Airtable Data Source Form
To set up a data source connection for JIRA, you will need to have:

- A unique name for your data source connection to be used in queries.
- The Base ID.
- The API Key generated Through your Airtable account.

### Form

![Airtable Form][image-1]


### Base ID
You can access your Base at [https://airtable.com/](https://airtable.com/).

![Finding your base][image-3] 

You can find the Base ID in Hoghlighted section of the Base URL


`https://airtable.com/`<mark>YOUR_BASE_ID</mark>`/tblPI1Mclv7pqrqDq/viwCAMdqRwJpFOlxl?blocks=hide`

### API Key

To generate your API Key you can access your [account](https://airtable.com/account) where you will have the option to generate an API Key


![Generate API Key][image-6]


## Endpoints


### Table

| Endpoint | URL Params | Optional | Description |
| -------- | ---------- | -------- | ----------  |
| <br><br>tables   | <br><br>TableName  | priority<br>sources<br>tags<br>unaggregated<br>exclude_aggregate<br>page|Returns the table and it's cells 
                 



### Query Page Sidebar

![Airtable Endpoints][image-2]

## Sample Queries

Suppose that my JIRA API data source was called `myjiraapi`

### Get Board Endpoint

```sql
SELECT *
FROM `myjiraapi`.`/board/:boardId`
WHERE `boardId`='1'
LIMIT 100
```

### Get All Boards Endpoint

```sql
SELECT *
FROM `myjiraapi`.`/board`
LIMIT 100
```

### Get Epics Endpoint

```sql
SELECT *
FROM `myjiraapi`.`/board/:boardId/epic`
WHERE `boardId`='1'
LIMIT 100
```

### Get Issues Endpoint

```sql
SELECT *
FROM `myjiraapi`.`/board/:boardId/issue`
WHERE `boardId`='1'
LIMIT 100
```

### Get Projects Endpoint

```sql
SELECT *
FROM `myjiraapi`.`/board/:boardId/project`
WHERE `boardId`='1'
LIMIT 100
```


[image-6]: ../../../img/api/airtable/airtable-generate-api.png
[image-4]: ../../../img/api/jira-find-email.png
[image-3]: ../../../img/api/airtable/airtable-base.png
[image-1]: ../../../img/api/airtable/airtable-form.png
[image-2]: ../../../img/api/airtable-endpoint.png