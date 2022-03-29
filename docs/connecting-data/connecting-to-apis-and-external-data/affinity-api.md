---
description: How to Connect DataDistillr to the Affinity API
---

# Affinity API

### Rate Limits

Your account plan tier will limit the number of requests each API key can make per month. Current rate limits by plan tier are:
All API requests will be halted at 450K per user, per day. Your daily limit will reset the next day at 12AM (midnight) Pacific Time.

## How to Connect DataDistillr to Affinity
To set up a data source connect for Affinity, you will need to have:

- A [unique name](#name) for your data source connection to be used in queries
- An [API token](#api-key) generated through your Affinity account


### Data Source Form
To locate the Affinity form, follow the steps in [Connecting Your Data to DataDistillr](../../). When you get to the window to choose the data source type, select API as shown below.

<figure markdown>
  ![Data Source Wizard][image-9]{ width="100%" }
</figure>

On the API screen, select Affinity from the list of API forms.

<figure markdown>
  ![List of APIs][image-3]{ width="100%" }
</figure>

The following form will appear. Instructions can be found below on how to find the information required to fill each field on the Affinity API form.

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
The API key is generated within your account page. The following steps will navigate you to its location. Once created, copy the key and enter it in the Affinity form.


## Endpoints
The table below shows a list of endpoints available to connect within the DataDistillr application. If you need to connect to any endpoints not listed in the table below, please use the [Custom API](../../) Form.

| Endpoint          | Required  | URL Parameters           | Optional                                                        | Description                                                                                                         |
|-------------------|-----------|--------------------------|-----------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| `lists`           |           |                          |                                                                 | Returns a collection of all the lists visible to you                                                                |
| `list`            | person_id | list_id                  |                                                                 | Gets the details for a specific list given the existing list id                                                     |
| `list_entry`      |           | list_id<br>list_entry_id |                                                                 | Find the best selection of profiles associated with a particular set of attributes for a person or related persons. |
| `fields`          |           |                          | list_id<br>value_type<br>with_modified_names                    | Find all the profiles for any number of persons that satisfy some search criteria.                                  |
| `field_values`    |           |                          | person_id<br>organization_id<br>opportunity_id<br>list_entry_id | Find all the profiles for any number of persons that satisfy some search criteria.                                  |


### Nav Tree
The endpoints above will display as follows in the nav tree once your API has successfully connected.

<figure markdown>
    ![Affinity Endpoints][image-7]{ width=100% }
</figure>


## Sample Queries
The following queries are intended to help you get started, and make life simpler querying within your API.

For the following examples, suppose that my Affinity API data source was called `myaffinityapi` and I want to query an endpoint. In the `FROM` clause, the endpoint goes after the Affinity data source name.

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

### Identify
The Identify API allows you to use broad search inputs to recover multiple records from our person dataset. In particular, this endpoint enables functionality such as searching by just single identifying attribute (such as name, email, phone number, company, school, or location) in addition to using any combination of these attributes.

```sql
SELECT *
FROM `mypdlapi`.`/person/identify`
WHERE `first_name`='John'
AND `last_name`='Doe'
AND `postal_code`='11111'
AND `phone`='555-123-4567'
LIMIT 100
```

### Search
You can use the `v5/person/search` endpoint to write queries (in Elasticsearch or SQL format) against the dataset and return any profiles that match those queries. People Data Lab's Search API is perfect for finding specific segments of people that you need in order to power your projects and products.

```sql
SELECT *
FROM `mypdlapi`.`/person/search`
WHERE `first_name`='John'
AND `last_name`='Doe'
AND `postal_code`='11111'
AND `phone`='555-123-4567'
LIMIT 100
```

[image-1]: ../../img/api/peopledatalabs/people-data-labs-home-page.png
[image-2]: ../../img/api/peopledatalabs/people-data-labs-api-keys.png
[image-3]: ../../img/api/affinity/affinity-select-api.png
[image-4]: ../../img/api/peopledatalabs/choose-form-peopledatalabs-dark.png
[image-5]: ../../img/api/affinity/affinity-form.png
[image-6]: ../../img/api/peopledatalabs/peopledatalabs-form-dark.png
[image-7]: ../../img/api/affinity/affinity-endpoints.png
[image-8]: ../../img/api/peopledatalabs/peopledatalabs-nav-tree-dark.png
[image-9]: ../../img/api/select-api-form.png