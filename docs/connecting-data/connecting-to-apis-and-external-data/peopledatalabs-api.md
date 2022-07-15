---
description: How to Connect DataDistillr to the People Data Labs API
---

# Connecting to People Data Labs

## First Steps with People Data Labs

Set up an account with [People Data Labs][link-1]{target="_blank"}.

???+ cost There are both free and [paid][link-3]{target="_blank"} options for this API.

???+ rlimit "Rate Limits"
Your account plan tier will limit the number of requests each API key can make per minute. People Data
Lab's [documentation][link-5]{target="_blank"} contains information on these limits.

## How to Connect DataDistillr to People Data Labs

To set up a data source connection for People Data Labs, you will need to have:

- A [unique name](#name) for your data source connection to be used in queries
- An [API token](#api-key) generated through your People Data Labs account

### Data Source Form

To locate the People Data Labs form, follow the steps in [Connecting Your Data to DataDistillr](../../). When you get to
the window to choose the data source type, select API as shown below.

![Data Source Wizard][image-0]

On the API screen, select People Data Labs from the list of API forms.

<figure markdown>
  ![List of APIs][image-1]{ width="100%" }
</figure>

The following form will appear. Instructions are below on how to find the information required to fill each field on the
People Data Labs API form.

Once you have filled out all the fields, press the green 'Save' button, and your API will be connected!


<figure markdown>
  ![People Data Labs Form][image-3]{ width="100%" }
</figure>

### Name

Enter any name that will help you recognize this data source within your query window.

!!! info "Acceptable Characters Include"

    - lowercase alphanumeric characters
    - underscores

### API Key

The API key is generated within your account page. The following steps will navigate you to its location. Once created,
copy the key and enter it in the People Data Labs form under 'API Key'.

=== "1. Home Page"

    Click the **API Keys** button

    ![Home page][image-7]

=== "2. Account Settings"

    This page contains the settings for your API token. You can modify the token's nickname and generate a new key with
    **Roll This Key**.

    ![API keys][image-8]

## Endpoints

The table below shows a list of endpoints available to connect within the DataDistillr application. If you need to
connect to any endpoints not listed in the table below, please use the [Custom API](custom-apis.md) Form.

| Endpoint                       | Required  | Optional                                                                                                                                                                                                                                                                                                                 | Description                                                                                                         |
|--------------------------------|-----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| `/person/enrich`               |           | name<br>first_name<br>last_name<br>middle_name<br>location<br>street_address<br>locality<br>region<br>country<br>postal_code<br>company<br>school<br>phone<br>email<br>email_hash<br>profile<br>lid<br>birth_date<br>min_likelihood<br>required<br>data_included<br>include_if_matched<br>titlecase<br>pretty<br>api_key | Find the single best profile matching some attributes about a particular person.                                    |
| `/person/retrieve/{person_id}` | person_id | titlecase<br>pretty<br>api_key                                                                                                                                                                                                                                                                                           | Directly lookup a specific profile using its PDL ID.                                                                |
| `/person/identify`             |           | name<br>first_name<br>last_name<br>middle_name<br>location<br>street_address<br>locality<br>region<br>country<br>postal_code<br>company<br>school<br>phone<br>email<br>email_hash<br>profile<br>lid<br>birth_date<br>min_likelihood<br>required<br>data_included<br>include_if_matched<br>titlecase<br>pretty<br>api_key | Find the best selection of profiles associated with a particular set of attributes for a person or related persons. |
| `/person/search`               |           | query<br>sql<br>size<br>scroll_token<br>dataset<br>data_include<br>titlecase<br>pretty<br>api_key                                                                                                                                                                                                                        | Find all the profiles for any number of persons that satisfy some search criteria.                                  |

### Nav Tree

The endpoints above will display as follows in the nav tree once your API has successfully connected.

<figure markdown>
  ![People Data Labs Endpoints][image-5]{ width="100%" }
</figure>

## Sample Queries

The following queries are intended to help you get started, and make life simpler querying within your API.

For the following examples, suppose that my People Data Labs API data source was called `mypdlapi` and I want to query
an endpoint. In the `FROM` clause, the endpoint goes after the People Data Labs data source name.

!!! example "FROM Clause"

    ```sql
    FROM `mypdlapi`.`<ENDPOINT>`
    ```

### Enrich

You can use the `v5/person/enrich` endpoint to enrich data on a person. The person enrichment API provides a one-to-one
match, providing up-to-date information on a unique individual.

```sql
SELECT *
FROM `mypdlapi`.`/person/enrich`
WHERE `first_name` = 'John'
  AND `last_name` = 'Doe'
  AND `postal_code` = '11111'
  AND `phone` = '555-123-4567' LIMIT 100
```

### Retrieve

The Person Retrieve API allows you to use a PDL Person ID (like `qEnOZ5Oh0poWnQ1luFBfVw_0000`) to get back the data
associated with that ID. A PDL ID is a unique and permanent identifier for each record in our dataset, and so this
endpoint allows you to directly retrieve the data for the exact record you are interested in.

```sql
SELECT *
FROM `mypdlapi`.`/person/retrieve/:person_id`
WHERE `person_id` = 'qEnOZ5Oh0poWnQ1luFBfVw_0000' LIMIT 100
```

### Identify

The Identify API allows you to use broad search inputs to recover multiple records from our person dataset. In
particular, this endpoint enables functionality such as searching by just single identifying attribute (such as name,
email, phone number, company, school, or location) in addition to using any combination of these attributes.

```sql
SELECT *
FROM `mypdlapi`.`/person/identify`
WHERE `first_name` = 'John'
  AND `last_name` = 'Doe'
  AND `postal_code` = '11111'
  AND `phone` = '555-123-4567' LIMIT 100
```

### Search

You can use the `v5/person/search` endpoint to write queries (in Elasticsearch or SQL format) against the dataset and
return any profiles that match those queries. People Data Lab's Search API is perfect for finding specific segments of
people that you need in order to power your projects and products.

```sql
SELECT *
FROM `mypdlapi`.`/person/search`
WHERE `first_name` = 'John'
  AND `last_name` = 'Doe'
  AND `postal_code` = '11111'
  AND `phone` = '555-123-4567' LIMIT 100
```

[image-0]: ../../img/api/add-api.png "Data Source Menu"

[image-1]: ../../img/api/peopledatalabs/choose-form-peopledatalabs-light.jpeg "API Data Source selection"

[image-2]: ../../img/api/peopledatalabs/choose-form-peopledatalabs-dark.png "API Data Source selection"

[image-3]: ../../img/api/peopledatalabs/peopledatalabs-form-light.png "People Data Labs form"

[image-4]: ../../img/api/peopledatalabs/peopledatalabs-form-dark.png "People Data Labs form"

[image-5]: ../../img/api/peopledatalabs/peopledatalabs-nav-tree-light.png "People Data Labs endpoints in query page nav tree sidebar"

[image-6]: ../../img/api/peopledatalabs/peopledatalabs-nav-tree-dark.png "People Data Labs endpoints in query page nav tree sidebar"

[image-7]: ../../img/api/peopledatalabs/people-data-labs-home-page.png "People Data Labs account home page"

[image-8]: ../../img/api/peopledatalabs/people-data-labs-api-keys.png "People Data Labs API token settings"

[link-1]: https://www.peopledatalabs.com/signup "People Data Labs sign up"

[link-2]: https://www.peopledatalabs.com/talk-to-sales "People Data Labs customer support"

[link-3]: https://www.peopledatalabs.com/pricing "People Data Labs pricing"

[link-4]: https://www.peopledatalabs.com/main "People Data Labs account dashboard"

[link-5]: https://docs.peopledatalabs.com/docs/rate-limiting "Rate Limits info"