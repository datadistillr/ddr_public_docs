---
description: How to Connect DataDistillr to the ClickUp API
---

# Connecting to ClickUp

## First Steps with ClickUp
Set up an account with [ClickUp](https://app.clickup.com/signup){target=_blank}.

???+ cost
    There are both free and [paid](https://clickup.com/pricing){target=_blank} options for this API. 

???+ rlimit "Rate Limits"

    Your account plan tier will limit the number of requests each API key can make per month. Current rate limits are
    available in ClickUp's [documentation](https://clickup.com/api){target=_blank}.

## How to Connect DataDistillr to ClickUp

To set up a data source connection for ClickUp, you will need to have:

- A [unique name](/connecting-data/connecting-to-apis-and-external-data/clickup-api/#name) for your data source
connection to be used in queries.
- An [API key](/connecting-data/connecting-to-apis-and-external-data/clickup-api/#api-key) generated through your
ClickUp account

### Data Source Form

To locate the ClickUp form, follow the steps in [Connecting Your Data to DataDistillr](../../). When you get to the
window to choose the data source type, select API as shown below.

<figure markdown>
![Select API from the available choices][image-1]{width=600}
</figure>

On the API screen, select ClickUp from the list of API types as shown in the image below.

<figure markdown>
![Select ClickUp API from available choices][image-2]{width=500}
</figure>

The following form will appear. Instructions are below on how to find the information required to fill each field on
the ClickUp API form.

Once you have filled out all the fields, press the green 'Save' button, and your API will be connected!

<figure markdown>__
![ClickUp form][image-3]{width=500}
</figure>

### Name
Enter any name that will help you recognize this data source from within your query window.

!!! info "Acceptable Characters Include"

    - lowercase alphanumeric characters
    - underscores

### API Key
An API key is generated within your account page. The following steps will navigate you to its location. Once created,
copy the key and enter it in the ClickUp form under 'API key'.

=== "1. Home page"
    In the ClickUp app, click your profile icon in the bottom left corner of the page.

    ![Click on your ClickUp account profile icon.][image-4]

=== "2. Apps"
    Choose **Apps**.

    ![Choose 'Apps'.][image-5]

=== "3. API Token"
    In the API Token section, click **Copy** (or **Regenerate** to get a new API token and then **Copy**) to save the
    API token to your clipboard.

    ![Click 'Copy' to save API token to clipboard.][image-6]

## Endpoints
Please see [ClickUp's API Reference](https://clickup.com/api){target=_blank} for more on ClickUp's endpoints.

The table below shows a list of endpoints available to connect to within the DataDistillr application. If you need to
connect to any endpoints not listed in the table below, please use the [Custom APIs](https://docs.datadistillr.com/connecting-data/connecting-to-apis-and-external-data/custom-apis/) Form.


| Endpoint | Required | Optional | Description |
|  ----------- | ----------- | ----------- | ----------- |
| `Get Tasks from Lists` | list_id | archived<br>page<br>order_by<br>reverse<br>subtasks<br>statuses<br>include_closed<br>assignees<br>due_date_gt<br>due_date_lt<br>due_created_gt<br>due_created_lt<br>due_updated_gt<br>due_updated_lt<br>custom_fields | Returns all of the tasks associated with the given list. <br><br>Note: custom_fields parameter currently inoperable using this endpoint. |
| `Get Tasks from Lists with Custom Fields` | list_id | archived<br>page<br>order_by<br>reverse<br>subtasks<br>statuses<br>include_closed<br>assignees<br>due_date_gt<br>due_date_lt<br>due_created_gt<br>due_created_lt<br>due_updated_gt<br>due_updated_lt<br>custom_fields | Returns all of the tasks associated with the given list, including custom fields. |
| `Get Task Data from Tasks` | task_id | | Returns data associated with tasks given a specific list_id. <br><br>Note: Endpoint is currently inoperable for tasks that have custom fields. |
| `Get Task Data from Tasks with Custom Fields` | task_id | | Returns data associated with tasks that include custom fields given a specific list_id.|
| `Get Spaces` | team_id | archived | Returns all of the spaces associated with the given team. |
| `Get Folders from Space` | space_id | archived | Returns all of the folders within the given space. |
| `Get Lists from Folder` | folder_id | archived | Returns all of the lists within the given folder. |
| `Get Lists from Space` | space_id | archived | Returns all of the lists within the given space. |
| `Get Tags` | space_id | archived | Returns all of the tags associated with the given space. |

### Nav Tree

The endpoints above will display as follows in the nav tree once your API has successfully connected.

<figure markdown>
  ![ClickUp nav tree][image-7]{width=500}
</figure>

## Sample Queries

The following queries are intended to help you get started, and make life simpler querying within your API.

For the following examples, suppose that my ClickUp API data source was called `clickupapi2000`, and I want to query an
endpoint. The endpoint goes after the ClickUp data source name:

!!! example "FROM Clause"

    ```sql
    FROM `clickupapi2000`.`<ENDPOINT>`
    ```

You must then enter the required parameter in the WHERE clause. Optional parameters can be added after the required parameters by adding 'AND' before each additional parameter.

!!! example "WHERE Clause (required parameter only)"

    ```sql
    WHERE `Required Parameter`='VALUE'
    ```
!!! example "WHERE Clause (required and optional parameters)"

    ```sql
    WHERE `Required Parameter`='VALUE' AND `Optional Parameter`='VALUE'
    ```

### Get Tasks from Lists Endpoint

This query returns 10 tasks within the specified list, including closed tasks. This query uses the optional parameter `include_closed`.

```sql
SELECT *
FROM `clickupapi2000`.`Get Tasks from Lists`
WHERE `list_id`='<Enter List ID Here>'
AND `include_closed`='true'
LIMIT 10
```

This will work for both lists with and without custom fields, just replace the endpoint name accordingly.

### Get Task Data from Tasks Endpoint

This query returns task data for a specific task id.

```sql
SELECT *
FROM `clickupapi2000`.`Get Task Data from Tasks`
WHERE `task_id`='<Enter Task ID Here>'
```

This will work for both tasks with and without custom fields, just replace the endpoint name accordingly.

### Get Spaces Endpoint

This query returns 10 spaces associated with the specified team.

```sql
SELECT *
FROM `clickupapi2000`.`Get Spaces`
WHERE `team_id`='<Enter Team ID Here>'
LIMIT 10
```
### Get Folders from Space Endpoint

This query returns 10 folders within the specified space.

```sql
SELECT *
FROM `clickupapi2000`.`Get Folders from Space`
WHERE `space_id`='<Enter Space ID Here>'
LIMIT 10
```
### Get Lists from Folder Endpoint

This query returns 10 lists within the specified folder.

```sql
SELECT *
FROM `clickupapi2000`.`Get Lists from Folder`
WHERE `folder_id`='<Enter Folder ID Here>'
LIMIT 10

```
### Get Lists from Space Endpoint

This query returns 10 lists within the specified space.

```sql
SELECT *
FROM `clickupapi2000`.`Get Lists from Space`
WHERE `space_id`='<Enter Space ID Here>'
LIMIT 10
```
### Get Tags Endpoint

This query returns 10 tags associated with the specified space.

```sql
SELECT *
FROM `clickupapi2000`.`Get Tags`
WHERE `space_id`='<Enter Space ID Here>'
LIMIT 10
```
### Accessing Nested ClickUp API Data

This query can be used to access nested ClickUp data found in custom fields within ClickUp tasks.

This query is a bit more complex, so let's walk through it step by step:

1. Identify and Specify the task_id for ClickUp task of interest.
```sql
task_id = '<Enter Task ID Here>'
```   

2. Flatten the array with nested objects `('custom_fields')` to retrieve individual objects. Add any other parameters of interest (we've added the 'name' and 'status' columns from ClickUp).
```sql
SELECT `name` as `Name`, flatten(`custom_fields`) as cf, `status`['status'] as `status`
```   

3. For this query, we will use the same data source referenced above and the `Get Task Data from Tasks` Endpoint, so piecing it all together so far we have:
```sql
SELECT `name` as `Name`, flatten(`custom_fields`) as cf, `status`['status'] as `status`
FROM `clickupapi2000`.`Get Task Data from Tasks`
WHERE task_id = '<Enter Task ID Here>'
```

4. We will alias this piece as `t1`.
```sql
(SELECT `name` as `Name`, flatten(`custom_fields`) as cf, `status`['status'] as `status`
FROM `clickupapi2000`.`Get Task Data from Tasks`
WHERE task_id = '<Enter Task ID Here>') as t1
```   

5. In the WHERE clause, we want to access the individual object. In this case, `name` refers to the name given to the custom field.
```sql
cf.`name`  = '<Enter name of Custom Field Here>'
```

6. Identify what column we want to return data from. For ClickUp, we need to use `value`.
7. Use the split function on `value`, delimiting on commas `,` to separate the values in the nested field and create an array. 
```sql
split(t1.`cf`.`value`, ',')
```

8. Lastly flatten the split data to generate individual rows. In our example we have aliased this as `Desired Data`.
```sql
flatten(split(t1.`cf`.`value`, ',')) as `Desired Data`
```

9. Putting everything together this gives us the final query shown below.
```sql
SELECT `Name`, flatten(split(t1.`cf`.`value`, ',')) as `Desired Data`, t1.`status`
FROM
  (SELECT `name` as `Name`, flatten(`custom_fields`) as cf, `status`['status'] as `status`
      FROM `clickupapi2000`.`Get Task Data from Tasks`
      WHERE task_id = 'Enter Task Id Here') as t1
WHERE t1.cf.`name` = '<Enter name of Custom Field Here>'
```

[image-1]: ../../img/api/data-source-wizard-api-light.png
[image-2]: ../../img/api/clickup/clickup-api-types.jpeg
[image-3]: ../../img/api/clickup/clickup-form.png
[image-4]: ../../img/api/clickup/clickup-api-key-user-account.png
[image-5]: ../../img/api/clickup/clickup-api-key-apps.png
[image-6]: ../../img/api/clickup/clickup-api-key-copy.png
[image-7]: ../../img/api/clickup/clickup-nav-tree.png
