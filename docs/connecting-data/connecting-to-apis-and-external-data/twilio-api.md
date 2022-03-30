---
description: How to Connect DataDistillr to the Twilio API
---

# Connecting to Twilio

## Creating a Twilio account
Set up an account with [Twilio](https://www.twilio.com/try-twilio){target=_blank}.

### Costs
The [pricing](https://www.twilio.com/pricing){target=_blank} for your twilio account is Pay-As-You-Go. [Check out Twilio's pricing for details](https://www.twilio.com/pricing){target=_blank}

### Rate Limits
No rate limit as cost is connected to the product usage 

## How to Connect DataDistillr to Twilio
To set up a data source connection for Twilio, you will need to have:

- A [unique name](#name) for your data source connection to be used in queries
- The [Account SID](#api-key) generated through your Twilio account
- The [Auth Token](#api-key) generated through your Twilio account

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
An Organization is a management layer that gives admins the ability to view and apply controls to all Atlassian accounts using an email address belonging to their company.

!!! example "Steps for getting your domain"

    === "1. Home page"

        On the Twilio homepage click the console tab in the top right corner.

        ![Twilio Home Page][image-10]

    === "2. Account SID, Auth Token"

        In the console find your Account SID and Auth Token in the circled section. Click the copy icon at their righthand side.

        ![Account Pop Up][image-11]


## Endpoints
The table below shows a list of endpoints available to connect within the DataDistillr application. If you need to connect to an endpoint not listed below, please use the [Custom API](custom-apis.md) Form.

| Endpoint | Required                | Optional | Description                                             |
|----------|-------------------------|----------|---------------------------------------------------------|
| `calls`  |                         |          | Returns info on the calls associated with your account. |
| `/board` | to<br>from<br>dataSent  |          | Returns info on messages associated with your account   |



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



### Get Board
This board will only be returned if the user has permission to view it.

```sql
SELECT *
FROM `myTwilioapi`.`/board/:boardId`
WHERE `boardId`='1'
LIMIT 100
```

### Get All Boards
This only includes boards that the user has permission to view.

```sql
SELECT *
FROM `myTwilioapi`.`/board`
LIMIT 100
```

### Get Epics
This only includes epics that the user has permission to view. Note, if the user does not have permission to view the board, no epics will be returned at all.

```sql
SELECT *
FROM `myTwilioapi`.`/board/:boardId/epic`
WHERE `boardId`='1'
LIMIT 100
```

### Get Issues
This only includes issues that the user has permission to view. An issue belongs to the board if its status is mapped to the board's column. Epic issues do not belong to the scrum boards. Note, if the user does not have permission to view the board, no issues will be returned at all. Issues returned from this resource include Agile fields, like sprint, closedSprints, flagged, and epic. By default, the returned issues are ordered by rank.

```sql
SELECT *
FROM `myTwilioapi`.`/board/:boardId/issue`
WHERE `boardId`='1'
LIMIT 100
```

### Get Projects
If the user does not have permission to view the board, no projects will be returned at all. Returned projects are ordered by the name.

```sql
SELECT *
FROM `myTwilioapi`.`/board/:boardId/project`
WHERE `boardId`='1'
LIMIT 100
```


[image-1]: ../../img/api/twilio/twilio-form.png
[image-2]: ../../img/api/twilio/twilio-navtree.png
[image-7]: ../../img/api/data-source-wizard-api-light.png
[image-8]: ../../img/api/twilio/twilio-api-select.png
[image-10]: ../../img/api/twilio/twilio-console.png
[image-11]: ../../img/api/twilio/twilio-creds.png