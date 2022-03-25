# ServiceNow API

## Creating a ServiceNow account
Set up an account with [ServiceNow](https://www.servicenow.com/).


### Rate Limits
To prevent excessive inbound REST API requests, set rules that limit the number of inbound REST API requests processed per hour. 
You can create rules to limit requests for specific users, users with specific roles, or all users.

## How to Connect DataDistillr to ServiceNow
To set up a data source connection for ServiceNow, you will need to have:

- A unique name for your data source connection to be used in queries
- The Instance Name associated ServiceNow Instance
- The Username associated with your ServiceNow Instance
- The Password associated with your ServiceNow Instance

### Data Source Form
To locate the ServiceNow form, follow the steps in [Connecting Your Data to DataDistillr](../../). When you get to the window to choose the data source type, select API as shown below.

<figure markdown>
  ![Data Source Wizard][image-7]{ width="100%" }
</figure>



On the API screen, select ServiceNow from the list of API forms.

<figure markdown>
  ![List of APIs][image-8]{ width="100%" }
</figure>



The following form will appear. Instructions can be found below on how to find the information required to fill each field on the ServiceNow API form.

Once you have filled out all the fields, press the green 'Save' button, and your API will be connected!

<figure markdown>
  ![ServiceNow Form][image-1]{ width="100%" }
</figure>


### Name
Enter any name that will help you recognize this data source from within your query window.

Acceptable characters include:

- lowercase alphanumeric characters
- underscores

### Instance ID


!!! example "Steps for getting your domain"

    === "1. Home page"

        In the ServiceNow app, click your profile icon in the top right corner of the page.

        ![ServiceNow Home Page][image-10]

    === "2. Accout settings"

        In the section with your name, click the **Account settings** link, this will take you to another page that contains information about your Atlassian account.

        ![Account Pop Up][image-11]

    === "3. Find Domain"

        In the left-hand sidebar, click the **Products** link and your domain will be located in the "ServiceNow settings" section.

        ![Find Domain][image-12]

### User
This is the email that is tied to your Atlassian account.

!!! example "Steps for getting your email"

    === "1. Home page"

        In the ServiceNow app, click your profile icon in the top right corner of the page.

        ![ServiceNow Home Page][image-10]

    === "2. Accout settings"

        In the section with your name, click the **Account settings** link, this will take you to another page that contains information about your Atlassian account.

        ![Account Pop Up][image-11]

    === "3. Find email"

        In the left-hand sidebar, click the **Email** link and your email will located in the "Current email" section.

        ![Find Domain][image-4]


### API Key
An API key is generated within your account page. The following steps will navigate you to its location. Once created, copy the key and enter it in the ServiceNow form under 'API key'.

!!! example "Steps for getting the API key"

    === "1. Home page"

        In the ServiceNow app, click your profile icon in the top right corner of the page.

        ![ServiceNow Home Page][image-10]

    === "2. Accout settings"

        In the section with your name, click the **Account settings** link, this will take you to another page that contains information about your Atlassian account.

        ![Account Pop Up][image-11]    

    === "3. Go to security page"

        In the left-hand sidebar, click **Security**. Then click **Create and manage API tokens** under the "API token" section.

        ![Go to your API manager][image-5]

    === "4. Create new API key"

        Click **API tokens** in the left-hand sidebar and this will display all the API tokens you've generated. To generate a new API key, click the blue **Create API token** button.

        ![Create a new API key][image-6]

    === "5. Label token"

        Give the your new token a label. Be careful, as this is the only time you will be able to see the API token so make sure you copy it.

        ![Label token][image-9]


## Endpoints
The table below shows a list of endpoints available to connect within the DataDistillr application. If you need to connect to an endpoint not listed below, please use the [Custom API](custom-apis.md) Form.

| Endpoint                   | Required | Optional                                                                                                                                                                      | Description                                               |
|----------------------------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------|
| `/board/{boardId}`         |          |                                                                                                                                                                               | Returns the board with the matching board ID.             |
| `/board`                   |          | startAt<br>maxResults<br>type<br>name<br>projectKeyOrId<br>accountIdLocation<br>projectLocation<br>includePrivate<br>negateLocationFiltering<br>orderBy<br>expand<br>filterId | Returns all boards.                                       |
| `/board/{boardId}/epic`    |          | startAt<br>maxResults<br>done                                                                                                                                                 | Returns all epics from the board, for the given board ID. |
| `/board/{boardId}/issue`   |          | startAt<br>maxResults<br>jql<br>validateQuery<br>fields<br>expand                                                                                                             | Returns all issues from a board, for a given board ID.    |
| `/board/{boardId}/project` |          | startAt<br>maxResults                                                                                                                                                         | Returns all projects that are associated with the board.  |



### Nav Tree
The endpoints above will display as follows in the nav tree once your API has successfully connected.

<figure markdown>
  ![ServiceNow Endpoints][image-2]{ width="100%" }
</figure>


## Sample Queries
The following queries are intended to help you get started, and make life simpler querying within your API.

For the following examples, suppose that my ServiceNow API data source was called `myServiceNowapi` and I want to query an endpoint. The endpoint goes after the ServiceNow data source name like so: ``#!sql FROM `myServiceNowapi`.`<ENDPOINT>` ``.

### Get Board
This board will only be returned if the user has permission to view it.

```sql title="Get Board endpoint"
SELECT *
FROM `myServiceNowapi`.`/board/:boardId`
WHERE `boardId`='1'
LIMIT 100
```

### Get All Boards
This only includes boards that the user has permission to view.

```sql title="Get All Boards endpoint"
SELECT *
FROM `myServiceNowapi`.`/board`
LIMIT 100
```

### Get Epics
This only includes epics that the user has permission to view. Note, if the user does not have permission to view the board, no epics will be returned at all.

```sql title="Get Epics endpoint"
SELECT *
FROM `myServiceNowapi`.`/board/:boardId/epic`
WHERE `boardId`='1'
LIMIT 100
```

### Get Issues
This only includes issues that the user has permission to view. An issue belongs to the board if its status is mapped to the board's column. Epic issues do not belong to the scrum boards. Note, if the user does not have permission to view the board, no issues will be returned at all. Issues returned from this resource include Agile fields, like sprint, closedSprints, flagged, and epic. By default, the returned issues are ordered by rank.

```sql title="Get Issues endpoint"
SELECT *
FROM `myServiceNowapi`.`/board/:boardId/issue`
WHERE `boardId`='1'
LIMIT 100
```

### Get Projects
If the user does not have permission to view the board, no projects will be returned at all. Returned projects are ordered by the name.

```sql title="Get Projects endpoint"
SELECT *
FROM `myServiceNowapi`.`/board/:boardId/project`
WHERE `boardId`='1'
LIMIT 100
```


[image-1]: ../../img/api/servicenow/servicenow-form.png
[image-2]: ../../img/api/ServiceNow/ServiceNow-query-page-sidebar-light.png
[image-3]: ../../img/api/ServiceNow/ServiceNow-atlassian-organization.png
[image-4]: ../../img/api/ServiceNow/ServiceNow-find-email.png
[image-5]: ../../img/api/ServiceNow/ServiceNow-manage-api-tokens.png
[image-6]: ../../img/api/ServiceNow/ServiceNow-create-new-api-token.png
[image-7]: ../../img/api/add-api.png
[image-8]: ../../img/api/servicenow/select-servicenow-api.png
[image-9]: ../../img/api/ServiceNow/ServiceNow-create-api-token.png
[image-10]: ../../img/api/ServiceNow/ServiceNow-home-page.png
[image-11]: ../../img/api/ServiceNow/ServiceNow-account-pop-up.png
[image-12]: ../../img/api/ServiceNow/ServiceNow-domain.png