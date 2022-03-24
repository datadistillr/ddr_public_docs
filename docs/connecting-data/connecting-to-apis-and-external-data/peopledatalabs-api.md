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
The table below shows a list of endpoints available to connect within the DataDistillr application. If you need to connect to any endpoints not listed in the table below, please use the [Custom API](../../) Form.

!!! info "person/enrich"

    Enrich a person record on a variety of fields

    ??? danger "Required"
    
        none

    ??? note "Optional"
				
        - name
        - first_name
        - last_name
        - middle_name
        - location
        - street_address
        - locality
        - region
        - country
        - postal_code
        - company
        - school
        - phone
        - email
        - email_hash
        - profile
        - lid
        - birth_date
        - min_likelihood
        - required
        - data_include
        - include_if_matched
        - titlecase
        - pretty
        - api_key



!!! info "person/retrieve/{person_id}"

    Retrieves a person based on a PDL ID.

    ??? danger "Required"
    
        - person_id

    ??? note "Optional"

        - titlecase
        - pretty
        - api_key


!!! info "person/identify"

    Recover all related profiles for an identity

    ??? danger "Required"
    
        none

    ??? note "Optional"
				
        - name
        - first_name
        - last_name
        - middle_name
        - location
        - street_address
        - locality
        - region
        - country
        - postal_code
        - company
        - school
        - phone
        - email
        - email_hash
        - profile
        - lid
        - birth_date
        - min_likelihood
        - required
        - data_include
        - include_if_matched
        - titlecase
        - pretty
        - api_key


!!! info "person/search"

    Search in the People Data Labs Dataset

    ??? danger "Required"
    
        none

    ??? note "Optional"
				
        - query
        - sql
        - size
        - scroll_token
        - dataset
        - data_include
        - titlecase
        - pretty
        - api_key


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

[image-1]: ../../img/api/peopledatalabs/people-data-labs-home-page.png
[image-2]: ../../img/api/peopledatalabs/people-data-labs-api-keys.png