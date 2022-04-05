---
description: How to Connect DataDistillr to the UPC Database API
---

# Connecting to UPC Database

## First Steps with UPC Database
Set up an account with [UPC Database][link-1]{target="_blank"}.

???+ cost

    There are four pricing plans:
    
    - **Free:** $0 per month.
    - **Hobbyist:** $2.50 per month.
    - **Standard:** $10 per month.
    - **Professional:** $50 per month.

    For more information about UPC Database pricing, please visit [https://upcdatabase.org/api-pricing][link-2]{target="_blank"}

???+ rlimit "Rate Limits"

    API does not have information about rate limits.

## How to Connect DataDistillr to UPC Database
To set up a data source connect for UPC Database, you will need to have:

- A [unique name](#name) for your data source connection to be used in queries
- An [API token](#api-key) generated through your UPC Database account

### Data Source Form
To locate the UPC Database form, follow the steps in [Connecting Your Data to DataDistillr](../../). When you get to the window to choose the data source type, select API as shown below.

<figure markdown>
  ![Data Source Wizard][image-0]{ width="100%" }
</figure>

On the API screen, select UPC Database from the list of API forms.


<figure markdown>
  ![List of APIs][image-1]{ width="100%" }
</figure>


The following form will appear. Instructions can be found below on how to find the information required to fill each on the UPC Database API form.

Once you have filled out all the fields, press the green 'Save' button, and your API will be connected!

<figure markdown>
  ![UPC Database Form][image-3]{ width="100%" }
</figure>

### Name
Enter any name that will help you recognize this data source within your query window.

!!! info "Acceptable Characters Include"

    - lowercase alphanumeric characters
    - underscores


### API Key
An API key is generated within your account page. The following steps will navigate you to its location. Once created, copy the key and enter it in the UPC Database form under 'API key'.

##### Steps for getting the API key

=== "1. Home Page"

    While in the UPC Database home page, click the **Your Account** drop down menu and then click on **Dashboard**.

    ![Home Page][image-7]

=== "2. Dashboard"

    This page displays your account information. Click on **API Keys** in the sidebar.

    ![Dashboard][image-8]

=== "3. API Key"

    In this page you can create and remove tokens from your account.

    ![API Key][image-9]


## Endpoints
The table below shows a list of endpoints available to connect within the DataDistillr application. If you need to connect to any endpoints not listed in the table below, please use the [Custom API](custom-apis.md) Form.

| Endpoint            | Required     | Optional | Description                                                              |
|---------------------|--------------|----------|--------------------------------------------------------------------------|
| `/product/{id}`     | id           |          | Get product information for a particular item                            |
| `/search/`          |              | query    | Search for a product based on item parameters                            |
| `/currency/latest`  | base         |          | Retrieve a list of currently supported currencies by the currency API    |
| `/currency/history` | base<br>date |          | Retrieve a list of historically supported currencies by the currency API |
| `/currency/symbols` |              |          | Retrieve a list of  currencies symbols of the currency API               |


### Nav Tree
The endpoints above will display as follows in the nav tree once your API has successfully connected.

<figure markdown>
  ![UPC Database Endpoints][image-5]{ width="100%" }
</figure>

## Sample Queries
The following queries are intended to help you get started, and make life simpler querying within your API.

For the following examples, suppose that my UPC Database API data source was called `myupcdbapi` and I want to query an endpoint. In the `FROM` clause, the endpoint goes after the UPC Database data source name.

!!! example "FROM Clause"

    ```sql
    FROM `myupcdbapi`.`<ENDPOINT>`
    ```


### Get Product
With this endpoint you can search information about a SKU with the ID of the product.

```sql
SELECT * 
FROM `myupcdbapi`.`/product/:id`
WHERE `id`='0786162004864'
LIMIT 1000
```

### Search for Product
With this endpoint you can search products with keywords.

```sql
SELECT * 
FROM `myupcdbapi`.`/search`
WHERE `query`='Gum'
LIMIT 1000
```

### Retrieve List of The Latest Currency
With this endpoint you can get the currencies that are supported.

```sql
SELECT * 
FROM `myupcdbapi`.`/currency/latest`
WHERE `base`='USD'
LIMIT 1000
```

### Retrieve List of Historic Currency
With this endpoint you can get the currencies that were supported throughout history
.
```sql
SELECT * 
FROM `myupcdbapi`.`/currency/history`
WHERE `base`='USD'
AND `date`='2010-12-15'
LIMIT 1000
```

### Retrieve List of Currency Symbols
With this endpoint you can get the symbols of the currencies.

```sql
SELECT * 
FROM `myupcdbapi`.`/currency/symbols`
LIMIT 1000
```

[image-0]: ../../img/api/data-source-wizard-api-light.png "Data Source Wizard"
[image-1]: ../../img/api/upcdb/choose-form-upc-light.png "API Data Source selection"
[image-2]: ../../img/api/upcdb/choose-form-upc-dark.png "API Data Source selection"
[image-3]: ../../img/api/upcdb/upc-form-light.png "UPC Database form"
[image-4]: ../../img/api/upcdb/upc-form-dark.png "UPC Database form"
[image-5]: ../../img/api/upcdb/upc-nav-tree-light.png "UPC Database endpoints in query page nav tree sidebar"
[image-6]: ../../img/api/upcdb/upc-nav-tree-dark.png "UPC Database endpoints in query page nav tree sidebar"
[image-7]: ../../img/api/upcdb/upc-home.png "UPC Database home page"
[image-8]: ../../img/api/upcdb/upc-dashboard.png "UPC Database account dashboard"
[image-9]: ../../img/api/upcdb/upc-api-keys.png "API token settings"
[image-10]: ../../img/api/upcdb/upc-api-history.png "API history settings"

[link-1]: https://upcdatabase.org/signup "UPC Database sign up" 
[link-2]: https://upcdatabase.org/api-pricing "UPC Database pricing" 