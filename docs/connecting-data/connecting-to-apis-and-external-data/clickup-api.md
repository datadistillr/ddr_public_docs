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

- A [unique name](/connecting-data/connecting-to-apis-and-external-data/clickup-api/#name) for your data source connection to be used in queries.
- An [API key](/connecting-data/connecting-to-apis-and-external-data/clickup-api/#api-key) generated through your ClickUp account

### Data Source Form

To locate the ClickUp form, follow the steps in [Connecting Your Data to DataDistillr](../../){target=_blank}. When you get to the window to choose the data source type, select API as shown below.

<figure markdown>
![Select API from the available choices][image-1]{width=600}
</figure>

On the API screen, select ClickUp from the list of API types as shown in the image below.

<figure markdown>
![Select ClickUp API from available choices][image-2]{width=500}
</figure>

The following form will appear. Instructions can be found below on how to find the information required to fill each field on the ClickUp API form.

Once you have filled out all the fields, press the green 'Save' button, and your API will be connected!

<figure markdown>
![ClickUp form][image-3]{width=500}
</figure>

### Name
Enter any name that will help you recognize this data source from within your query window.

!!! info "Acceptable Characters Include"

    - lowercase alphanumeric characters
    - underscores

### API Key
An API key is generated within your account page. The following steps will navigate you to its location. Once created, copy the key and enter it in the Asana form under 'API key'.

=== "1. Home page"
    In the ClickUp app, click your profile icon in the bottom left corner of the page.

    ![Click on your ClickUp account profile icon.][image-4]

=== "2. Apps"
    Choose **Apps**.

    ![Choose 'Apps'.][image-5]

=== "3. API Token"
    In the API Token section, click **Copy** (or **Regenerate** to get a new API token and then **Copy**) to save the API token to your clipboard.

    ![Click 'Copy' to save API token to clipboard.][image-6]

## Endpoints
Please see [ClickUp's API Reference](https://clickup.com/api){target=_blank} for more on ClickUp's endpoints.

The table below shows a list of endpoints available to connect to within the DataDistillr application. If you need to connect to any endpoints not listed in the table below, please use the [Custom APIs](https://docs.datadistillr.com/connecting-data/connecting-to-apis-and-external-data/custom-apis/){target=_blank} Form.

| Endpoint | Required | Optional | Description |
|  ----------- | ----------- | ----------- | ----------- |
| `/list/{list_id}/task` | | archived<br>page<br>order_by<br>reverse<br>subtasks<br>statuses<br>include_closed<br>assignees<br>due_date_gt<br>due_date_lt<br>due_created_gt<br>due_created_lt<br>due_updated_gt<br>due_updated_lt<br>custom_fields | Returns all of the tasks associated with the given list. |
| `/team/{team_id}/space` | | archived | Returns all of the spaces associated with the given team. |
| `/space/{space_id}/folder` | | archived | Returns all of the folders within the given space. |
| `/folder/{folder_id}/list` | | archived | Returns all of the lists within the given folder. |
| `/space/{space_id}/list` | | archived | Returns all of the lists within the given space. |
| `/space/{space_id}/tag` | | archived | Returns all of the tags associated with the given space. |

### Nav Tree

The endpoints above will display as follows in the nav tree once your API has successfully connected.

<figure markdown>
  ![ClickUp nav tree][image-7]{width=500}
</figure>

## Sample Queries

The following queries are intended to help you get started, and make life simpler querying within your API.

Suppose that my ClickUp API data source was called `clickupapi2000`

### Get Tasks Endpoint

```sql
SELECT *
FROM clickupapi2000.`/list/:list_id/task`
WHERE `list_id`='175636929'
AND `include_closed`='true'
LIMIT 10
```

### Get Spaces Endpoint

```sql
SELECT *
FROM clickupapi2000.`/team/:team_id/space`
WHERE `team_id`='3054541'
LIMIT 10
```
### Get Folders Endpoint

```sql
SELECT *
FROM clickupapi2000.`/space/:space_id/folder`
WHERE `space_id`='3110392'
LIMIT 10
```
### Get Lists Endpoint

```sql
SELECT *
FROM clickupapi2000.`/folder/:folder_id/list`
WHERE `folder_id`='96278401'
LIMIT 10

```
### Get Folder-less Lists Endpoint

```sql
SELECT *
FROM clickupapi2000.`/space/:space_id/list`
WHERE `space_id`='3110392'
LIMIT 10
```
### Get Space Tags Endpoint

```sql
SELECT *
FROM clickupapi2000.`/space/:space_id/tag`
WHERE `space_id`='3110392'
LIMIT 10
```

[image-1]: ../../img/api/data-source-wizard-api-light.png
[image-2]: ../../img/api/clickup/clickup-api-types.png
[image-3]: ../../img/api/clickup/clickup-form.png
[image-4]: ../../img/api/clickup/clickup-api-key-user-account.png
[image-5]: ../../img/api/clickup/clickup-api-key-apps.png
[image-6]: ../../img/api/clickup/clickup-api-key-copy.png
[image-7]: ../../img/api/clickup/clickup-nav-tree.png
