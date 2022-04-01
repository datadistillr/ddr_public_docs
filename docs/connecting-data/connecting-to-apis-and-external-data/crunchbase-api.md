---
description: How to Connect DataDistillr to the Crunchbase API
---

# Crunchbase API

## First Steps with Crunchbase

Set up an account with [Crunchbase](https://www.crunchbase.com/register){target=_blank}.

???+ cost
    This is a paid API. [Crunchbase Pricing](https://www.crunchbase.com/buy/select-product){target=_blank}

???+ rlimit "Rate Limits"
    Your account plan tier will limit the number of requests each API key can make per month.

## How to Connect DataDistillr to Crunchbase

To set up a data source connection for Crunchbase, you will need to have:

- A [unique name](/connecting-data/connecting-to-apis-and-external-data/crunchbase-api/#name) for your data source connection to be used in queries.
- An [API key](/connecting-data/connecting-to-apis-and-external-data/crunchbase-api/#api-key)
In order to access the Crunchbase API, one must pay for an [Enterprise](https://about.crunchbase.com/products/crunchbase-enterprise/?utm_source=cb&utm_medium=banner_ad&utm_campaign=data_crunchbase_ad&utm_content=enterprise&utm_term=click_here#enterprise-form){target=_blank} or [Applications](https://about.crunchbase.com/products/data-licensing/?utm_source=cb&utm_medium=banner_ad&utm_campaign=data_crunchbase_ad&utm_content=applications&utm_term=click_here#applications-form){target=_blank} license. A user key is emailed to the user following registration. [Contact](https://about.crunchbase.com/about-us/contact-us/){target=_blank} Crunchbase for more details.

### Data Source Form

To locate the Crunchbase form, follow the steps in [Connecting Your Data to DataDistillr](../../). When you get to the window to choose the data source type, select API as shown below.

<figure markdown>
![Select API from the available choices][image-1]{width=600}
</figure>

On the API screen, select Crunchbase from the list of API types as shown in the image below.

<figure markdown>
![Select Crunchbase API from available choices][image-2]{width=500}
</figure>

The following form will appear. Instructions can be found below on how to find the information required to fill each field on the Crunchbase API form.

Once you have filled out all the fields, press the green 'Save' button, and your API will be connected!

<figure markdown>
![Crunchbase form][image-3]{width=500}
</figure>

### Name
Enter any name that will help you recognize this data source from within your query window.

!!! info "Acceptable Characters Include"

    - lowercase alphanumeric characters
    - underscores

### API Key
This is the user key which is emailed to you following registration. See [Crunchbase API Authentication](https://data.crunchbase.com/docs/using-the-api#authentication){target=_blank} for more information.

If you lose your key, contact [api@crunchbase.com](mailto:api@crunchbase.com)

## Endpoints
Please see [Crunchbase's API Reference](https://data.crunchbase.com/docs/using-the-api){target=_blank} for more on Crunchbase's endpoints.

The table below shows a list of endpoints available to connect to within the DataDistillr application. If you need to connect to any endpoints not listed in the table below, please use the [Custom APIs](https://docs.datadistillr.com/connecting-data/connecting-to-apis-and-external-data/custom-apis/) Form.

| Endpoint | Required | Optional | Description |
|  ----------- | ----------- | ----------- | ----------- |
| `/entities/organizations/{entity_id}` | | field_ids<br>card_ids | Returns the records for the organizations associated with the specified entity. |
| `entities/organizations/{entity_id}/cards/{card_id}` | | card_field_ids<br>after_id<br>before_id<br>order<br>limit | Returns the records for the specified card associated with the specified entity. |

### Nav Tree

The endpoints above will display as follows in the nav tree once your API has successfully connected.

<figure markdown>
  ![Crunchbase nav tree][image-4]{width=500}
</figure>

## Sample Queries

The following queries are intended to help you get started, and make life simpler querying within your API.

For the following examples, suppose that my Crunchbase API data source was called `crunchbase_1`, and I want to query an endpoint. The endpoint goes after the Crunchbase data source name:

!!! example "FROM Clause"

    ```sql
    FROM `crunchbase_1`.`<ENDPOINT>`
    ```

### Get Organizations Endpoint

This query returns all organizations associated with the specified entity.

```sql
SELECT *
FROM `crunchbase_1`.`/entities/organizations/:entity_id`
WHERE `entity_id`='tesla-motors'
LIMIT 1000
```

### Get Organizations Card Endpoint

This query returns the records for the specified card associated with the specified entity.

```sql
SELECT * FROM `crunchbase_1`.`/entities/organizations/:entity_id/cards/:card_id`
WHERE `entity_id`='crunchbase' AND `card_id`='press_references'
LIMIT 1000
```

[image-1]: ../../img/api/data-source-wizard-api-light.png
[image-2]: ../../img/api/crunchbase/crunchbase-api-types.jpeg
[image-3]: ../../img/api/crunchbase/crunchbase-form.png
[image-4]: ../../img/api/crunchbase/crunchbase-nav-tree.png
