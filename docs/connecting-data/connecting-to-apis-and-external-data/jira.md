# Connecting to JIRA

## Creating a JIRA account
Set up an account with [JIRA](https://www.atlassian.com/software/opsgenie/try).

### Costs
There are several types of accounts in JIRA. The free version and the one that cost $50 per month.

### Rate Limits
The JIRA API is limited to 10 requests per second. If you exceed this rate, you will receive a 429 status code 

## How to Connect DataDistillr to JIRA
To set up a data source connection for JIRA, you will need to have:

- A unique name for your data source connection to be used in queries
- The domain of your Atlassian account
- The email associated with your Atlassian account
- The API token generated through your Atlassian account

### Data Source Form
To locate the JIRA form, follow the steps in [Connecting Your Data to DataDistillr](../../). When you get to the window to choose the data source type, select API as shown below.

On the API screen, select JIRA from the list of API forms.

The following form will appear. Instructions can be found below on how to find the information requried to fill each field on the JIRA API form.

Once you have filled out all the fields, press the green 'Save' button, and your API will be connected!

![JIRA Form][image-1]

#### Name
Enter any name that will help you recognize this data source from within your query window.

Acceptable characters include:
- lowercase alphanumeric characters
- underscores

#### Domain
You can access your Organization at [https://admin.atlassian.com/](https://admin.atlassian.com/) to find your domain.

![Finding your domain][image-3]


#### User

![Finding your email][image-4]

#### API Key
To generate your API key, navigate to our Account where you will have the option to generate an API key as highlighted below. Copy this API key and enter it in the JIRA form under 'API key'.

![Go to your api manager][image-5]
![Create a new api key][image-6]


## Endpoints
The table below shows a list of endpoints available to connect within the DataDistillr application. If you need to connect to an endpoint not listed below, please use the [Custom API](custom-apis.md) Form.

### Table

| Endpoint                   | Required | Optional                                                                                                                                                                      | Description                                               |
|----------------------------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------|
| `/board/{boardId}`         |          |                                                                                                                                                                               | Returns the board with the matching board ID.             |
| `/board`                   |          | startAt<br>maxResults<br>type<br>name<br>projectKeyOrId<br>accountIdLocation<br>projectLocation<br>includePrivate<br>negateLocationFiltering<br>orderBy<br>expand<br>filterId | Returns all boards.                                       |
| `/board/{boardId}/epic`    |          | startAt<br>maxResults<br>done                                                                                                                                                 | Returns all epics from the board, for the given board ID. |
| `/board/{boardId}/issue`   |          | startAt<br>maxResults<br>jql<br>validateQuery<br>fields<br>expand                                                                                                             | Returns all issues from a board, for a given board ID.    |
| `/board/{boardId}/project` |          | startAt<br>maxResults                                                                                                                                                         | Returns all projects that are associated with the board.  |



### Nav Tree
The endpoints above will display as follows in the nav tree once your API has successfully connected.

![JIRA Endpoints][image-2]

## Sample Queries
The following queries are intended to help you get started, and make life simpler querying within your API.


Suppose that my JIRA API data source was called `myjiraapi`

### Get Board Endpoint
Suppose that I get a board with the ID of `1`. This will be the result.

```sql
SELECT *
FROM `myjiraapi`.`/board/:boardId`
WHERE `boardId`='1'
LIMIT 100
```

### Get All Boards Endpoint
Suppose that I get a board with the ID of `1`. This will be the result.

```sql
SELECT *
FROM `myjiraapi`.`/board`
LIMIT 100
```

### Get Epics Endpoint
Suppose that I get a board with the ID of `1`. This will be the result.

```sql
SELECT *
FROM `myjiraapi`.`/board/:boardId/epic`
WHERE `boardId`='1'
LIMIT 100
```

### Get Issues Endpoint
Suppose that I get a board with the ID of `1`. This will be the result.

```sql
SELECT *
FROM `myjiraapi`.`/board/:boardId/issue`
WHERE `boardId`='1'
LIMIT 100
```

### Get Projects Endpoint
Suppose that I get a board with the ID of `1`. This will be the result.

```sql
SELECT *
FROM `myjiraapi`.`/board/:boardId/project`
WHERE `boardId`='1'
LIMIT 100
```


[image-6]: ../../img/api/jira/jira-create-new-api-token.png
[image-5]: ../../img/api/jira/jira-manage-api-tokens.png
[image-4]: ../../img/api/jira/jira-find-email.png
[image-3]: ../../img/api/jira/jira-atlassian-organization.png
[image-1]: ../../img/api/jira/jira-form-dark.png
[image-2]: ../../img/api/jira/jira-query-page-sidebar-dark.png
