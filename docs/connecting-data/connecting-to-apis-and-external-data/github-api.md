---
description: How to Connect DataDistillr to the Github API
---

# Connecting to GitHub

## First Steps with GitHub
An account is not necessary for the GitHub API. If you'd like you can set up an account with [GitHub](https://github.com/signup){target=_blank}.

???+ cost "Costs"

    This is the free version of the GitHub API. 


???+ rlimit "Rate Limits"

    The GitHub API has [rate limits](https://docs.github.com/en/rest/overview/resources-in-the-rest-api#rate-limiting){target=_blank}. 
    Once you exceed a certain number of requests in a specific period, GitHub returns an error.

## How to Connect DataDistillr to Github
To set up a data source connection for Github, you will need to have:

- A unique [name](#name) for your data source connection to be used in queries.



### Data Source Form

To locate the Github form, follow the steps in [Connecting Your Data to DataDistillr](../../). When you get to the window to choose the data source type, select API as shown below.&#x20;

![Select API from the available choices][image-5]

On the API screen, select Github from list of API forms as shown in the image below.

![Select Github API from available choices][image-6]

The following form will appear. Instructions can be found below on how to find the information required to fill each field on the Github API form.

Once you have filled out all the fields, press the green 'Save' button, and your API will be connected!

![Github Form][image-1]

### Name

Enter any name that will help you recognize this data source from within your query window. &#x20;

!!! info "Acceptable characters include"

    * lowercase alphanumeric characters
    * underscores


## Endpoints

The table below shows a list of endpoints available to connect to within the DataDistillr application. If you need to connect to any endpoints not listed in the table below, please use the [Custom API](custom-apis.md) Form.

| Endpoint | URL Params  | Required Params | Description                                                                |
|----------|-------------|-----------------|----------------------------------------------------------------------------|
| `users`  |             |                 | Lists all users, in the order that they signed up on GitHub                |
| `search` | searchGroup | 'q'             | The GitHub Search API lets you to search for the specific item efficiently |
| `repos`  |             |                 | Lists all public repositories in the order that they were created.         |
| `org`    | org         |                 | Get info on an organization.                                               |


### Nav Tree

The endpoint above will display as follows in the nav tree once your API has successfully connected.

![Github Endpoints][image-3]

## Sample Queries

The following queries are intended to help you get started, and make life simpler querying within your API.

For the following examples, suppose that my Github data source was called `mygithubapi` and I want to query an endpoint. The endpoint goes after the Github data source name:

!!! example "FROM Clause"

    ```sql
    FROM `mygithubapi`.`<ENDPOINT>`
    ```

### Get Users Endpoint

Lists all users, in the order that they signed up on GitHub. This list includes personal user accounts and organization accounts.

```sql
SELECT * FROM `mygithubapi`.`users`
LIMIT 1000
```

### Search Endpoint

The Search API helps you search for the specific item you want to find. For example, you can find a user or a specific file in a repository.

!!! info 
    
    This endpoint is different than the other endpoints. The `q` param is used to create a search query. 
    Check out GitHub's [Search API Docs](https://docs.github.com/en/rest/reference/search){target=_blank} for more info.  
    <span style="color:red">Warning, this endpoint has pagination and can use up your rate limits very quickly</span>

For example, if you're looking for a list of popular users, you might try the following query. This query searches for users with the name tom. The results are restricted to users with more than 42 repositories and over 1,000 followers.

```sql
SELECT * FROM `mygithubapi`.`search`
WHERE searchGroup = 'users' 
AND q = 'tom+repos:%3E42+followers:%3E1000'
LIMIT 1000
```

### Get Repos Endpoint

Lists all public repositories in the order that they were created.

```sql
SELECT * FROM `mygithubapi`.`repos`
LIMIT 1000
```


### Get Org Endpoint

The event stream can be queried and filtered by time, priority, sources and tags.

```sql
SELECT * FROM `mygithubapi`.`org`
WHERE org = '<ORGANIZATION NAME>'
LIMIT 1000
```


[image-1]: ../../img/api/github/github-form.png
[image-3]: ../../img/api/github/github-endpoints.png
[image-5]: ../../img/api/add-api.png
[image-6]: ../../img/api/github/github-select-api.png
