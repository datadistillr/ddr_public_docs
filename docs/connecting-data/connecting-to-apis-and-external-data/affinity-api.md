---
description: How to Connect DataDistillr to the Affinity API
---

# Connecting to Affinity

## First Steps with Affinity

[Contact](https://www.affinity.co/request-demo){target=_blank} Affinity for a free demo and to create an account.


???+ cost "Cost"

    This is a paid API. [Contact](https://www.affinity.co/request-demo){target=_blank} Affinity for pricing.

???+ rlimit "Rate Limits"

    Your account plan tier will limit the number of requests each API key can make per month. Current rate limits are 
    available in [Affinity's documentation](https://api-docs.affinity.co/#rate-limits){target=_blank}.

## How to Connect DataDistillr to Affinity
To set up a data source connect for Affinity, you will need to have:

- A [unique name](#name) for your data source connection to be used in queries
- An [API key](#api-key) generated through your Affinity account


### Data Source Form
To locate the Affinity form, follow the steps in [Connecting Your Data to DataDistillr](../../). When you get to the
window to choose the data source type, select API as shown below.

<figure markdown>
  ![Data Source Wizard][image-9]{ width="100%" }
</figure>

On the API screen, select Affinity from the list of API forms.

<figure markdown>
  ![List of APIs][image-3]{ width="100%" }
</figure>

The following form will appear. Instructions are below on how to find the information required for each field on the
Affinity API form.

Once you have filled out all the fields, press the green 'Save' button, and your API will be connected!


<figure markdown>
  ![Affinity Form][image-5]{ width="100%" }
</figure>


### Name
Enter any name that will help you recognize this data source within your query window.

!!! info "Acceptable characters include"

    - lowercase alphanumeric characters
    - underscores


### API Key
The API key is generated within your account's settings page. Head over to the
[Affinity docs](https://support.affinity.co/hc/en-us/articles/360032633992-How-to-obtain-your-API-Key){target=_blank}
to learn how to generate your API Key. Once created, copy the key and enter it in the Affinity form.

## Endpoints
The table below shows a list of endpoints available to connect within the DataDistillr application. If you need to
connect to any endpoints not listed in the table below, please use the
[Custom API](../../connecting-to-apis-and-external-data/custom-apis) Form or [Contact Us](../../getting-help.md) for
assistance.


| Endpoint         | URL Parameters           | Required  | Optional                                                        | Description                                                                                                         |
|------------------|--------------------------|-----------|-----------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| `lists`          |                          |           |                                                                 | Returns a collection of all the lists visible to you                                                                |
| `list`           | list_id                  | person_id |                                                                 | Gets the details for a specific list given the existing list id                                                     |
| `list_entry`     | list_id<br>list_entry_id |           |                                                                 | Find the best selection of profiles associated with a particular set of attributes for a person or related persons. |
| `fields`         |                          |           | list_id<br>value_type<br>with_modified_names                    | Find all the profiles for any number of persons that satisfy some search criteria.                                  |
| `field_values`   |                          |           | person_id<br>organization_id<br>opportunity_id<br>list_entry_id | Find all the profiles for any number of persons that satisfy some search criteria.                                  |


### Nav Tree
The endpoints above will display as follows in the nav tree once your API has successfully connected.

<figure markdown>
  ![Affinity Endpoints][image-7]{ width=100% }
</figure>


## Sample Queries
The following queries are intended to help you get started, and make life simpler querying within your API.

For the following examples, suppose that my Affinity API data source was called `myaffinityapi` and I want to query an
endpoint. In the `FROM` clause, the endpoint goes after the Affinity data source name:

!!! example "FROM Clause"

    ```sql
    FROM `myaffinityapi`.`<ENDPOINT>`
    ```

### Lists
 
You can use the `lists` endpoint to retrieve a list of all endpoints available to you.

```sql
SELECT *
FROM `myaffinityapi`.`lists`
LIMIT 100
```

### List

Gets the details for a specific list given the existing list id

```sql
SELECT *
FROM `myaffinityapi`.`list`
WHERE `person_id`='qEnOZ5Oh0poWnQ1luFBfVw_0000'
LIMIT 100
```

### List Entry

Each list comprises a number of entries. Each list entry has a creator, a list that it belongs to, and the underlying
entity it represents depending on the type of the list (people, organizations or opportunities).

```sql
SELECT *
FROM `myaffinityapi`.`list_entry`
WHERE `list_id`='12345'
AND `list_entry_id`='54321'
LIMIT 100
```

### Fields

Returns all fields based on the parameters provided. Pass the `list_id` to only fetch fields that are specific to that
list. Otherwise, all global and list-specific fields will be returned. Pass the `value_type` to fetch fields of specific
value types. Otherwise, all fields of any type will be returned. Pass the `with_modified_names` flag to return the 
fields such that the names have the list name prepended to them.

```sql
SELECT *
FROM `myaffinityapi`.`fields`
WHERE `list_id`=12345
AND `value_type`=3
LIMIT 100
```

### Field Values

Field values are displayed in Affinity as the data in the cells of an Affinity spreadsheet. This endpoint returns all
field values attached to a person, organization, opportunity, or list_entry.

```sql
SELECT *
FROM `myaffinityapi`.`fields`
WHERE `person_id`=12345
LIMIT 100
```


[image-3]: ../../img/api/affinity/affinity-select-api.jpeg
[image-5]: ../../img/api/affinity/affinity-form.png
[image-7]: ../../img/api/affinity/affinity-endpoints.png
[image-9]: ../../img/api/data-source-wizard-api-light.png