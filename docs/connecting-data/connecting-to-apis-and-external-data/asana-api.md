# Connecting to the Asana API

## First steps with Asana
Set up an account with [Asana](https://asana.com/create-account){target=_blank}.

???+ cost
    There are both free and [paid](https://asana.com/pricing){target=_blank} options for this API. 

???+ rlimit "Rate Limits"
    Your account plan tier will limit the number of requests each API key can make per month. Current rate limits are available in Asana's [documentation](https://developers.asana.com/docs/rate-limits){target=_blank}.

## How to Connect DataDisillr to Asana
To set up a data source connection for Asana, you will need to have:

- A [unique name](/connecting-data/connecting-to-apis-and-external-data/asana-api/#name) for your data source connection to be used in queries.
- The [API key](/connecting-data/connecting-to-apis-and-external-data/asana-api/#api-key) generated through your Asana account.

### Data Source Form

To locate the Asana form, follow the steps in [Connecting Your Data to DataDistillr](../../). When you get to the window to choose the data source type, select API as shown below.

<figure markdown>
![Select API from the available choices] [image-3]
</figure>

On the API screen, select Asana from the list of API types as shown in the image below.

<figure markdown>
![Select Asana from API types] [image-4]{width=600}
</figure>

The following form will appear. Instructions can be found below on how to find the information required to fill each field on the Asana API form.

Once you have filled out all the fields, press the green 'Save' button, and your API will be connected!

<figure markdown>
![Asana Form] [image-1]{width=600}
</figure>

### Name
Enter any name that will help you recognize this data source from within your query window.

!!! info "Acceptable Characters Include"

    - lowercase alphanumeric characters
    - underscores

### API Key
An API key is generated within your account page. The following steps will navigate you to its location. Once created, copy the key and enter it in the Asana form under 'API key'.

=== "1. Home page"
    In the Asana app, click your profile icon in the top right corner of the page. Choose **My Settings**.

    ![Click on Asana Account Icon. Choose 'My Settings'.] [image-5]

=== "2. Account Settings"  
    In the **My Settings** window, click on the **Apps** tab.

    ![Click on the Apps Tab in the 'My Settings' window.] [image-6]

=== "3. Apps"
    Click on **Manage Developer Apps** which opens a new tab in your browser.

    ![Click on 'Manage Developer Apps'.] [image-7]

=== "4. Personal Access Tokens"
    In the **Personal access tokens** section, choose **Create new token**.

    ![Click on 'Create new token'.] [image-8]

=== "5. New Token"
    Enter a descriptive name for your token and check the checkbox to agree to the API terms and conditions. Click **Create token**.

    ![Enter name and check the checkbox. Click 'Create token'.] [image-9]

=== "6. Copy Token"
    Click **Copy** to copy the token to your clipboard.

    ![Click 'Copy' to copy the token.] [image-10]

## Endpoints
Please see [Asana's API Reference](https://developers.asana.com/docs/asana){target=_blank} for more on Asana's endpoints.

The table below shows a list of endpoints available to connect to within the DataDistillr application. If you need to connect to any endpoints not listed in the table below, please use the [Custom APIs](https://docs.datadistillr.com/connecting-data/connecting-to-apis-and-external-data/custom-apis/) Form.

| Endpoint | Required | Optional | Description |
|  ----------- | ----------- | ----------- | ----------- |
| `/tasks` | assignee<br>project<br>section<br>workspace<br> |  completed_since<br>modified_since<br>limit<br>offset<br>opt_pretty<br>opt_fields | Returns the tasks which match the parameters provided. |
| `/users` | | workspace<br>team<br>limit<br>offset<br>opt_pretty<br>opt_fields | Returns the users that the current user has access to. |
| `/workspaces` | | limit<br>offset<br>opt_pretty<br>opt_fields | Returns the workspaces associated with the current user. |
| `/projects` | | workspace<br>team<br>archived<br>limit<br>offset<br>opt_pretty<br>opt_fields | Returns the projects associated with the current user. (Asana recommends filtering by team to avoid timeouts for large domains). |
| `/tags` | workspace | limit<br>offset<br>opt_pretty<br>opt_fields | Returns the tags for the given workspace. |
| `/organizations/{workspace_gid}/teams` | | limit<br>offset<br>opt_pretty<br>opt_fields | Returns all of the teams in the organization connected to the current user. |


### Nav Tree

The endpoints above will display as follows in the nav tree once your API has successfully connected.

<figure markdown>
  ![Asana Query Page Sidebar][image-2]{width=500}
</figure>

## Sample Queries

The following queries are intended to help you get started, and make life simpler querying within your API.

For the following examples, suppose that my Asana API data source was called `asanaapi2000`, and I want to query an endpoint. The endpoint goes after the Asana data source name:

!!! example "FROM Clause"

    ```sql
    FROM `asanaapi2000`.`<ENDPOINT>`
    ```

### Get Tasks Endpoint

This query returns all tasks associated with the specified project.

```sql
SELECT *
FROM asanaapi2000.`/tasks`
WHERE `project`='1201829319351080'
LIMIT 100
```

### Get Users Endpoint

This query returns all users associated with the specified workspace, displaying 50 users per page.

```sql
SELECT *
FROM asanaapi2000.`/users`
WHERE `workspace`='944661173197038'
AND `limit`='50'
LIMIT 100
```

### Get Workspaces Endpoint

This query returns all workspaces accessible to the current user.

```sql
SELECT *
FROM asanaapi2000.`/workspaces`
LIMIT 100
```

### Get Projects Endpoint

This query returns all projects associated with the specified workspace, displaying 10 projects per page.

```sql
SELECT *
FROM asanaapi20000.`/projects`
WHERE `workspace`='944661173197038'
AND `limit`='10'
LIMIT 100
```

### Get Tags Endpoint

This query returns all tags associated with the specified workspace.

```sql
SELECT *
FROM asanaapi2000.`/tags`
WHERE `workspace`='944661173197038'
LIMIT 100
```

### Get Teams Endpoint

This query returns all teams associated with the specified workspace_gid, displaying 10 teams per page.

```sql
SELECT *
FROM asanaapi2000.`/organizations/:workspace_gid/teams`
WHERE `workspace_gid`='944661173197038'
AND `limit`='10'
LIMIT 100
```


[image-1]: ../../img/api/asana/asana-form-light.png
[image-2]: ../../img/api/asana/asana-nav-tree.png
[image-3]: ../../img/api/add-api.png
[image-4]:../../img/api/asana/api-types-asana.jpeg
[image-5]:../../img/api/asana/asana-account-icon-settings.png
[image-6]:../../img/api/asana/asana-settings-apps.png
[image-7]:../../img/api/asana/asana-manage-dev-apps.png
[image-8]:../../img/api/asana/asana-create-new-token.png
[image-9]:../../img/api/asana/asana-create-new-token-form.png
[image-10]:../../img/api/asana/asana-copy-token.png
