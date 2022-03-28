---
description: How to Connect DataDistillr to the People Data Labs API
---

# People Data Labs API

## Creating a People Data Labs account
Set up an account with [People Data Labs](https://www.peopledatalabs.com/signup).

### Costs


### Rate Limits
Rate limits are defined on a per-minute, per-key or per-endpoint basis. We use a fixed-window rate limiting strategy, so if your API key's rate limit is `100` requests per minute, those `100` api calls can be made at any interval within the 60-second window.

| HEADER NAME                       | ASSOCIATED APIS                                                                                                                                                        | DESCRIPTION                                                                                       |
|-----------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
| `Retry-After`                     | `All`                                                                                                                                                                  | The number of seconds left until the current rate limit window resets.                            |
| `X-RateLimit-Limit`               | `All`                                                                                                                                                                  | The maximum number of requests you're permitted to make per minute.                               |
| `X-RateLimit-Remaining`           | `All`                                                                                                                                                                  | **DEPRECATED. Do not use.**<br>The number of requests remaining in the current rate limit window. |
| `X-RateLimit-Reset`               | `All`                                                                                                                                                                  | The time at which the current rate limit window resets in UTC epoch seconds.                      |
| `X-TotalLimit-Limit`              | [Person Enrichment API](https://docs.peopledatalabs.com/docs/enrichment-api)<br>[Bulk Person Enrichment API](https://docs.peopledatalabs.com/docs/bulk-enrichment-api) | The maximum number of API requests that return a `200` you're able to make.                       |
| `X-TotalLimit-Remaining`          | [Person Enrichment API](https://docs.peopledatalabs.com/docs/enrichment-api)<br>[Bulk Person Enrichment API](https://docs.peopledatalabs.com/docs/bulk-enrichment-api) | The number of API requests that return a `200` you have remaining.                                |
| `X-SearchLimit-Remaining`         | [Person Search API](https://docs.peopledatalabs.com/docs/search-api)                                                                                                   | The number of retrievable records from the Search API that you have remaining.                    |
| `X-EnrichCompanyLimit-Remaining`  | [Company Enrichment API](https://docs.peopledatalabs.com/docs/company-enrichment-api)                                                                                  | The number of API requests that return a `200` you have remaining.                                |


If your account has a limit on the number of `200` API calls that you're able to make, once `x-totallimit-remaining` reaches zero, all succeeding api requests will return 403 errors, and once `x-ratelimit-remaining` reaches zero, all succeeding requests made will return 429 errors until the current rate limit window resets. If you'd like to increase your account's `x-totallimit-limit` or `x-ratelimit-limit`, please contact your account manager or reach out to us at [support@peopledatalabs.com](support@peopledatalabs.com).

#### The API Dashboard

All accounts are given access to a [dashboard](https://www.peopledatalabs.com/main), which will allows you to manage your API keys, view usage and test new endpoints (when they are available.)

## How to Connect DataDistillr to People Data Labs
To set up a data source connect for People Data Labs, you will need to have:

- A unique name for your data source connection to be used in queries
- An API token generated through your People Data Labs account


### Data Source Form
To locate the JIRA form, follow the steps in [Connecting Your Data to DataDistillr](../../). When you get to the window to choose the data source type, select API as shown below.

<figure markdown>
  ![Data Source Wizard][image-9]{ width="100%" }
</figure>

On the API screen, select People Data Labs from the list of API forms.

<figure markdown>
  ![List of APIs][image-3]{ width="100%" }
</figure>

The following form will appear. Instructions can be found below on how to find the information required to fill each field on the People Data Labs API form.

Once you have filled out all the fields, press the green 'Save' button, and your API will be connected!


<figure markdown>
  ![People Data Labs Form][image-5]{ width="100%" }
</figure>


### Name
Enter any name that will help you recognize this data source within your query window.

Acceptable characters include:

- lowercase alphanumeric characters
- underscores


### API Key
An API key is generated within your account page. The following steps will navigate you to its location. Once created, copy the key and enter it in the People Data Labs form.

!!! example "Steps for getting the API key"

    === "1. Home page"
    
        Click the **API Keys** button

        ![Home page][image-1]

    === "2. Account settings"

        ![API keys][image-2]



## Endpoints
The APIs reside at `api.peopledatalabs.com`. All API requests must be made over HTTPS. Calls made over standard HTTP will fail. API requests without proper authentication (a valid API key) will also fail.

The table below shows a list of endpoints available to connect within the DataDistillr application. If you need to connect to any endpoints not listed in the table below, please use the [Custom API](../../) Form.

| Endpoint                       | Required  | Optional                                                                                                                                                                                                                                                                                                                 | Description                                                                                                         |
|--------------------------------|-----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| `/person/enrich`               |           | name<br>first_name<br>last_name<br>middle_name<br>location<br>street_address<br>locality<br>region<br>country<br>postal_code<br>company<br>school<br>phone<br>email<br>email_hash<br>profile<br>lid<br>birth_date<br>min_likelihood<br>required<br>data_included<br>include_if_matched<br>titlecase<br>pretty<br>api_key | Find the single best profile matching some attributes about a particular person.                                    |
| `/person/retrieve/{person_id}` | person_id | titlecase<br>pretty<br>api_key                                                                                                                                                                                                                                                                                           | Directly lookup a specific profile using its PDL ID.                                                                |
| `/person/identify`             |           | name<br>first_name<br>last_name<br>middle_name<br>location<br>street_address<br>locality<br>region<br>country<br>postal_code<br>company<br>school<br>phone<br>email<br>email_hash<br>profile<br>lid<br>birth_date<br>min_likelihood<br>required<br>data_included<br>include_if_matched<br>titlecase<br>pretty<br>api_key | Find the best selection of profiles associated with a particular set of attributes for a person or related persons. |
| `/person/search`               |           | query<br>sql<br>size<br>scroll_token<br>dataset<br>data_include<br>titlecase<br>pretty<br>api_key                                                                                                                                                                                                                        | Find all the profiles for any number of persons that satisfy some search criteria.                                  |


### Nav Tree
The endpoints above will display as follows in the nav tree once your API has successfully connected.

<figure markdown>
  ![People Data Labs Endpoints][image-7]{ width="100%" }
</figure>



## Sample Queries
The following queries are intended to help you get started, and make life simpler querying within your API.

For the following examples, suppose that my People Data Labs API data source was called `mypdlapi` and I want to query an endpoint. The endpoint goes after the People Data Labs data source name like so: ``#!sql FROM `mypdlapi`.`<ENDPOINT>` ``.

### Enrich
You can use the `v5/person/enrich` endpoint to enrich data on a person:

The person enrichment API provides a one-to-one match, providing up-to-date information on a unique individual.

```sql
SELECT *
FROM `mypdlapi`.`/person/enrich`
WHERE `first_name`='John'
AND `last_name`='Doe'
AND `postal_code`='11111'
AND `phone`='555-123-4567'
LIMIT 100
```

### Retrieve
The Person Retrieve API allows you to use a PDL Person ID (like `qEnOZ5Oh0poWnQ1luFBfVw_0000`) to get back the data associated with that ID. A PDL ID is a unique and permanent identifier for each record in our dataset, and so this endpoint allows you to directly retrieve the data for the exact record you are interested in.

```sql
SELECT *
FROM `mypdlapi`.`/person/retrieve/:person_id`
WHERE `person_id`='qEnOZ5Oh0poWnQ1luFBfVw_0000'
LIMIT 100
```

### Identify
The Identify API allows you to use broad search inputs to recover multiple records from our person dataset. In particular, this endpoint enables functionality such as searching by just single identifying attribute (such as name, email, phone number, company, school, or location) in addition to using any combination of these attributes

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
We provide a `v5/person/search` endpoint, which allows you to write queries (in Elasticsearch or SQL format) against our dataset and return any profiles that match those queries:

PDL's Search API is perfect for finding specific segments of people that you need in order to power your projects and products.

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
[image-3]: ../../img/api/peopledatalabs/choose-form-peopledatalabs-light.png
[image-4]: ../../img/api/peopledatalabs/choose-form-peopledatalabs-dark.png
[image-5]: ../../img/api/peopledatalabs/peopledatalabs-form-light.png
[image-6]: ../../img/api/peopledatalabs/peopledatalabs-form-dark.png
[image-7]: ../../img/api/peopledatalabs/peopledatalabs-nav-tree-light.png
[image-8]: ../../img/api/peopledatalabs/peopledatalabs-nav-tree-dark.png
[image-9]: ../../img/api/data-source-wizard-api-light.png