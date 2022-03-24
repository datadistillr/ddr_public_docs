---
description: How to Connect DataDistillr to the People Data Labs API
---

# People Data Labs API

## Creating a People Data Labs account
Set up an account with [People Data Labs](https://www.peopledatalabs.com/signup).

### Costs


### Rate Limits


## How to Connect DataDistillr to People Data Labs
To set up a data source connect for People Data Labs, you will need to have:

- 


### Data Source Form


#### Name
Enter any name that will help you recognize this data source within your query window.

Acceptable characters include:
- lowercase alphanumeric characters
- underscores


#### API Key



## Endpoints
The table below shows a list of endpoints available to connect within the DataDistillr application. If you need to connect to any endpoints not listed in the table below, please use the [Custom API](../../) Form.

| Endpoint | Required | Optional | Description |
|----------|----------|----------|-------------|
|          |          |          |             |


### Nav Tree
The endpoints above will display as follows in the nav tree once your API has successfully connected.



## Sample Queries

The following queries are intended to help you get started, and make like simpler querying within your API.

### Endpoint 1

```sql
SELECT * 
FROM `table`
WHERE `column`='value'
```

### Endpoint 2


```sql
SELECT *
FROM `source`.`table`
WHERE `column`='value'
LIMIT 100
```

