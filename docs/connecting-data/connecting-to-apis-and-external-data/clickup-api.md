# Connecting to ClickUp

## Creating a ClickUp Account
Set up an account with [ClickUp](https://app.clickup.com/signup){target=_blank}.

???+ cost
    There are several different types of accounts:

    - Free
    - Unlimited - $9 per member per month
    - Business - $19 per member per month
    - Business Plus - $29 per member per month
    - Enterprise

[Details and Comparison](https://clickup.com/pricing){target=_blank}

???+ rlimit "Rate Limits"

    The ClickUp API is limited per OAuth and personal token.

    - Free, Unlimited, and Business Plan - 100 requests per minute per token
    - Business Plus Plan - 1,000 requests per minute per token
    - Enterprise Plan - 10,000 requests per minute per token

    If you exceed this rate, you will receive a 429 status code.

## How to Connect DataDistillr to ClickUp

To set up a data source connection for ClickUp, you will need to have:

- A [unique name] for your data source connection to be used in queries.
- An [API token] generated through your ClickUp account

### Data Source Form

To locate the ClickUp form, follow the steps in [Connecting Your Data to DataDistillr](../../){target=_blank}. When you get to the window to choose the data source type, select API as shown below.

<figure markdown>
![Select API from the available choices][image-1]{width=500}
</figure>

On the API screen, select ClickUp from the list of API types as shown in the image below.



[image-1]: ../../img/api/add-api.png
