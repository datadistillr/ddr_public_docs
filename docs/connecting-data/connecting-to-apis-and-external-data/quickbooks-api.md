---
description: How to Connect DataDistillr to the Quickbooks API
---

# Connecting to Quickbooks

## First Steps with Quickbooks

Set up an account with [Intuit Developer](https://accounts.intuit.com/signup.html?offering_id=Intuit.devx.devx&redirect_url=https%3A%2F%2Fdeveloper.intuit.com%2Fapp%2Fdeveloper%2Fhomepage%3FdevXlogin%3Dtrue){target=_blank}

???+ cost
    This API is free.

???+ rlimit "Rate Limits"
    [API Limits Information](https://developer.intuit.com/app/developer/qbo/docs/learn/rest-api-features#:~:text=07%3A00%20hours.-,API%20call%20limits%20and%20throttles,-Server){target=_blank}

## How to Connect DataDistillr to Quickbooks

To set up a data source connection for Quickbooks, you will need to have:

- A [unique name](/connecting-data/connecting-to-apis-and-external-data/quickbooks-api/#name) for your data source connection to be used in queries.
- A [client ID](/connecting-data/connecting-to-apis-and-external-data/quickbooks-api/#client-id) generated through your Intuit Developer account.
- A [client secret](/connecting-data/connecting-to-apis-and-external-data/quickbooks-api/#client-secret) generated through your Intuit Developer account.
- A [realm ID](/connecting-data/connecting-to-apis-and-external-data/quickbooks-api/#realm-id) generated through your Intuit Developer account.

### Data Source Form

To locate the Quickbooks form, follow the steps in [Connecting Your Data to DataDistillr](../../). When you get to the window to choose the data source type, select API as shown below.

<figure markdown>
![Select API from the available choices][image-1]{width=600}
</figure>

On the API screen, select Quickbooks from the list of API types as shown in the image below.

<figure markdown>
![Select Quickbooks API from available choices][image-2]{width=500}
</figure>

The following form will appear. Instructions can be found below on how to find the information required to fill each field on the Quickbooks API form.

### Name

### Client ID

### Client secret

### Realm ID

[image-1]: ../../img/api/data-source-wizard-api-light.png
[image-2]: ../../img/api/quickbooks/quickbooks-api-types.jpeg
