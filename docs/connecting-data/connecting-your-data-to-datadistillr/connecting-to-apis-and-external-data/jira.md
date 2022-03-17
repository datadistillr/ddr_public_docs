# Connecting to JIRA

## JIRA Data Source Form
To set up a data sourcr connection for JIRA, you will need to have:

- A unique name for your data source connection to be used in queries
- The domain of your Atlassian account
- The email associated with your Atlassian account
- The API token generated through your Atlassian account

### Form

![JIRA Form][image-1]


### Domain
You can access your Organization at [https://admin.atlassian.com/](https://admin.atlassian.com/) to find your domain.

![Finding your domain][image-3]


### User

![Finding your email][image-4]

### API Key

![Go to your api manager][image-5]
![Create a new api key][image-6]


## Endpoints


### Table

| Endpoint                   | Required | Optional                                                                                                                                                                      | Description                                               |
|----------------------------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------|
| `/board/{boardId}`         |          |                                                                                                                                                                               | Returns the board with the matching board ID.             |
| `/board`                   |          | startAt<br>maxResults<br>type<br>name<br>projectKeyOrId<br>accountIdLocation<br>projectLocation<br>includePrivate<br>negateLocationFiltering<br>orderBy<br>expand<br>filterId | Returns all boards.                                       |
| `/board/{boardId}/epic`    |          | startAt<br>maxResults<br>done                                                                                                                                                 | Returns all epics from the board, for the given board ID. |
| `/board/{boardId}/issue`   |          | startAt<br>maxResults<br>jql<br>validateQuery<br>fields<br>expand                                                                                                             | Returns all issues from a board, for a given board ID.    |
| `/board/{boardId}/project` |          | startAt<br>maxResults                                                                                                                                                         | Returns all projects that are associated with the board.  |



### Query Page Sidebar

![JIRA Endpoints][image-2]

## Sample Queries

Suppose that my JIRA API data source was called `myjiraapi`

### Get Board Endpoint

```sql
SELECT *
FROM `myjiraapi`.`/board/:boardId`
WHERE `boardId`='1'
LIMIT 100
```

### Get All Boards Endpoint

```sql
SELECT *
FROM `myjiraapi`.`/board`
LIMIT 100
```

### Get Epics Endpoint

```sql
SELECT *
FROM `myjiraapi`.`/board/:boardId/epic`
WHERE `boardId`='1'
LIMIT 100
```

### Get Issues Endpoint

```sql
SELECT *
FROM `myjiraapi`.`/board/:boardId/issue`
WHERE `boardId`='1'
LIMIT 100
```

### Get Projects Endpoint

```sql
SELECT *
FROM `myjiraapi`.`/board/:boardId/project`
WHERE `boardId`='1'
LIMIT 100
```


[image-6]: ../../../img/api/jira-create-new-api-token.png
[image-5]: ../../../img/api/jira-manage-api-tokens.png
[image-4]: ../../../img/api/jira-find-email.png
[image-3]: ../../../img/api/jira-atlassian-organization.png
[image-1]: ../../../img/api/jira-form-dark.png
[image-2]: ../../../img/api/jira-query-page-sidebar-dark.png
