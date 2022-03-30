---
description: How to Connect DataDistillr to the Veriphone API
---

# Veriphone API

## Creating a Veriphone account
Set up an account with [Veriphone](https://veriphone.io/#page-top).

???+ cost

    There are four pricing plans:
    
    - **STARTER:** $6.99 per month.
    - **PROFESSIONAL:** $29 per month.
    - **BUSINESS:** $79 per month.
    - **ENTERPRISE:** $199 per month.

???+ rlimit "Rate Limits"
    
    API has no information about rate limits.
    
## How to Connect DataDistillr to Veriphone
To set up a data source connect for Veriphone, you will need to have:

- A [unique name](#name) for your data source connection to be used in queries
- An [API token](#api-key) generated through your Veriphone account

### Data Source Form
To locate the Veriphone form, follow the steps in [Connecting Your Data to DataDistillr](../../). When you get to the window to choose the data source type, select API as shown below.

<figure markdown>
  ![Data Source Wizard][image-0]{ width="100%" }
</figure>


On the API screen, select Veriphone from the list of API forms.

<figure markdown>
  ![List of APIs][image-1]{ width="100%" }
</figure>



The following form will appear. Instructions can be found below on how to find the information required to fill each on the Veriphone API form.

Once you have filled out all the fields, press the green 'Save' button, and your API will be connected!

<figure markdown>
  ![Veriphone Form][image-3]{ width="100%" }
</figure>

### Name
Enter any name that will help you recognize this data source within your query window.

!!! info "Acceptable Characters Include"

    - lowercase alphanumeric characters
    - underscores


### API Key
An API key is generated within your account page. The following steps will navigate you to its location. Once created, copy the key and enter it in the Veriphone form under 'API key'.

!!! example "Steps for Getting the API Key"

    === "1. Dashboard"

        In your Veriphone dashboard, go to your account settings by clicking on the **SETTINGS** button or the blue button.
    
        ![Home Page][image-7]

    === "2. API Key"

        Here you can reset your API token.    

        ![API Key][image-8]
        



## Endpoints
The table below shows a list of endpoints available to connect within the DataDistillr application. If you need to connect to any endpoints not listed in the table below, please use the [Custom API](../../) Form.

| Endpoint | Required | Optional                    | Description                                                                     |
|----------|----------|-----------------------------|---------------------------------------------------------------------------------|
| Verify   | phone    | default_country<br>key      | Determines if a number is valid.                                                |
| Example  |          | type<br>country_code<br>key | Returns an example (dummy) phone number for any country/phone-type combination. |


### Nav Tree
The endpoints above will display as follows in the nav tree once your API has successfully connected.

<figure markdown>
  ![Veriphone Endpoints][image-5]{ width="100%" }
</figure>

## Sample Queries
The following queries are intended to help you get started, and make like simpler querying within your API.

For the following examples, suppose that my Veriphone API data source was called `myveriphoneapi` and I want to query an endpoint. In the `FROM` clause, the endpoint goes after the Veriphone data source name.

!!! example "FROM Clause"

    ```sql
    FROM `myapi`.`<ENDPOINT>`
    ```


### Verify
For valid numbers, it will also return the number's type (mobile, land line, toll free, etc...) the carrier and other fields as described in the output section bellow.

If the number does not start with a country prefix, indicated by a leading '+', the number will be checked against the default-country's numbering scheme. If no default-country is provided, a country will be inferred from the IP address originating the request.

```sql
SELECT * 
FROM `myveriphoneapi`.`Verify`
WHERE `phone`='5555555555'
Limit 1000
```

### Example
The country and phone type are optional. If no country is specified , a country will be inferred from the IP address originating the request.

If no phone type is specified, 'mobile' will be used as default type

```sql
SELECT * 
FROM `myveriphoneapi`.`Example`
WHERE `type`='mobile'
LIMIT 1000
```


[image-0]: ../../img/api/data-source-wizard-api-light.png
[image-1]: ../../img/api/veriphone/choose-form-veriphone-light.png
[image-2]: ../../img/api/veriphone/choose-form-veriphone-dark.png
[image-3]: ../../img/api/veriphone/veriphone-form-light.png
[image-4]: ../../img/api/veriphone/veriphone-form-dark.png
[image-5]: ../../img/api/veriphone/veriphone-nav-tree-light.png
[image-6]: ../../img/api/veriphone/veriphone-nav-tree-dark.png
[image-7]: ../../img/api/veriphone/veriphone-dashboard.png
[image-8]: ../../img/api/veriphone/veriphone-settings-censored.png
