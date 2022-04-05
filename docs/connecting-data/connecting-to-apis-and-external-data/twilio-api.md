---
description: How to Connect DataDistillr to the Twilio API
---

# Connecting to Twilio

## First steps with Twilio
Set up an account with [Twilio](https://www.twilio.com/try-twilio){target=_blank}.

???+ cost "Costs"
    
    The [pricing](https://www.twilio.com/pricing){target=_blank} for your twilio account is Pay-As-You-Go. 

???+ rlimit "Rate Limits"

    Almost all Twilio products have rate limits to ensure that all customers experience a high level of performance when using Twilio's platform. Please review the specific product [API documentation](https://www.twilio.com/docs/api){target=_blank} to find the rate limits.

## How to Connect DataDistillr to Twilio
To set up a data source connection for Twilio, you will need to have:

- A [unique name](#name) for your data source connection to be used in queries
- The [Account SID](#account-sid-and-auth-token) generated through your Twilio account
- The [Auth Token](#account-sid-and-auth-token) generated through your Twilio account

### Data Source Form
To locate the Twilio form, follow the steps in [Connecting Your Data to DataDistillr](../../). When you get to the window to choose the data source type, select API as shown below.

<figure markdown>
  ![Data Source Wizard][image-7]{ width="100%" }
</figure>



On the API screen, select Twilio from the list of API forms.

<figure markdown>
  ![List of APIs][image-8]{ width="100%" }
</figure>



The following form will appear. Instructions can be found below on how to find the information required to fill each field on the Twilio API form.

Once you have filled out all the fields, press the green 'Save' button, and your API will be connected!

<figure markdown>
  ![Twilio Form][image-1]{ width="100%" }
</figure>


### Name
Enter any name that will help you recognize this data source from within your query window.

!!! info "Acceptable Characters Include"

    - lowercase alphanumeric characters
    - underscores


### Account SID and Auth Token

=== "1. Home page"

    On the Twilio homepage click the console tab in the top right corner.

    ![Twilio Home Page][image-10]

=== "2. Account SID, Auth Token"

    In the console find your Account SID and Auth Token in the Account Info section. Click the copy icon at their righthand side.

    ![Account Pop Up][image-11]


## Endpoints
The table below shows a list of endpoints available to connect within the DataDistillr application. If you need to connect to an endpoint not listed below, please use the [Custom API](custom-apis.md) Form.

| Endpoint   | Required               | Optional | Description                                             |
|------------|------------------------|----------|---------------------------------------------------------|
| `calls`    |                        |          | Returns info on the calls associated with your account. |
| `messages` | to<br>from<br>dateSent |          | Returns info on messages associated with your account   |



### Nav Tree
The endpoints above will display as follows in the nav tree once your API has successfully connected.

<figure markdown>
  ![Twilio Endpoints][image-2]{ width="100%" }
</figure>


## Sample Queries
The following queries are intended to help you get started, and make life simpler querying within your API.

For the following examples, suppose that my Twilio API data source was called `myTwilioapi` and I want to query an endpoint. The endpoint goes after the Twilio data source name:

!!! example "FROM Clause"

    ```sql
    FROM `myTwilioapi`.`<ENDPOINT>`
    ```



### Get Calls
This endpoint will retrieve calls associated with your account.

```sql
SELECT *
FROM `myTwilioapi`.`calls`
WHERE `boardId`='1'
LIMIT 100
```

### Get Messages
This endpoint will retrieve calls associated with your account.

```sql
SELECT *
FROM `myTwilioapi`.`messages`
WHERE `to`='<RECIPIENT>'
AND `from`='<SENDER>'
AND `dateSent`='<DATE SENT>'
LIMIT 100
```



[image-1]: ../../img/api/twilio/twilio-form.png
[image-2]: ../../img/api/twilio/twilio-endpoints.png
[image-7]: ../../img/api/data-source-wizard-api-light.png
[image-8]: ../../img/api/twilio/twilio-api-select.jpeg
[image-10]: ../../img/api/twilio/twilio-console.png
[image-11]: ../../img/api/twilio/twilio-creds.png