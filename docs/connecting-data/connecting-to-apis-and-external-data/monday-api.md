---
description: How to Connect DataDistillr to the Monday API
---

# Connecting to Monday

## First Steps with Monday
Set up an account with [Monday][link-1]{target="_blank"}.

???+ cost

    There are 4 pricing plans:

    - **Student:** $0 seat / month.
    - **Standard:** $10 seat / month. Total $30 per month.
    - **Pro:** $16 seat / month. Total $48 per month.
    - **Enterprise:** [Contact Sales][link-4]{target="_blank"}.

    For more information about Monday.com pricing please visit [https://monday.com/pricing/][link-5]{target="_blank"}

???+ rlimit "Rate Limits"

    The API uses a construct called complexity to define the cost of each query made.

    Monday.com API rate limits are based on the complexity of the queries an app makes in a given time period. There are two limits to keep in mind:

    - A single query is limited to 5,000,000 complexity points
    - All queries made must not exceed 10,000,000 points per minute (1M for trial and free accounts) using your API token generated from the [Admin](#steps-for-getting-the-api-key-as-an-admin) section or the [Access Tokens](#steps-for-getting-the-api-key-as-a-developer) section

## How to Connect DataDistillr to Monday
To set up a data source connect for Monday, you will need to have:

- A [unique name](#name) for your data source connection to be used in queries
- An [API token](#api-key) generated through your Monday.com account

### Data Source Form
To locate the JIRA form, follow the steps in [Connecting Your Data to DataDistillr](../../). When you get to the window to choose the data source type, select API as shown below.


<figure markdown>
  ![Data Source Wizard][image-0]{ width="100%" }
</figure>


On the API screen, select Monday from the list of API forms.


<figure markdown>
  ![List of APIs][image-1]{ width="100%" }
</figure>


The following form will appear. Instructions can be found below on how to find the information required to fill each on the Monday API form.

Once you have filled out all the fields, press the green 'Save' button, and your API will be connected!


<figure markdown>
  ![Monday Form][image-3]{ width="100%" }
</figure>

### Name
Enter any name that will help you recognize this data source within your query window.

!!! info "Acceptable Characters Include"

    - lowercase alphanumeric characters
    - underscores


### API Key
You will need valid authentication through an access token. Each user has their own API token, this grants API access to all the boards to which the user has access (i.e. they're subscribed to).

Currently, monday.com only offers V2 API tokens, which are all personal tokens. To access your API tokens, you can use one of two methods depending on your user level.

!!! note "NOTE"

    **Admin** users are able to utilize both methods to acquire their API tokens. **Member** users can access their API tokens from their Developer tabs.

Admin users are able to utilize both methods to acquire their API tokens.


##### Steps for getting the API key as an admin

Log into your monday.com account.

=== "1. Home Page"

    Click on your avatar (picture icon) in the bottom left corner of your screen

    ![Home Page][image-7]

=== "2. Account Settings"

    Select **Admin** from the resulting menu (this requires you to have admin permissions).

    ![Account Settings][image-8]

=== "3. API Key"

    Go to the **API** section. Your API token will be located here. If you haven't created an API token you will be able to 'Generate a "API v2 Token"'. If you already have an API token you can also create a new one to replace your current token by clicking **Regenerate**.

    ![API Key][image-10]

    !!! note "NOTE"
    
        You can always regenerate a new token, however doing so will cause the previous token to expire.



##### Steps for getting the API key as a developer

=== "1. Home Page"

    Click on your avatar (picture icon) in the bottom left corner of your screen.
    
    ![Home Page][image-7]

=== "2. Account Settings"

    Select **Developers** from the resulting menu.

    ![Account Settings][image-9]

=== "3. My Access Tokens"

    In the top menu, click on the **Developer** dropdown menu. Select the first option on the dropdown menu titled **My Access Tokens**.
    
    ![My Access Tokens][image-11]

=== "4. API Key"

    Click on the blue **Show** button to expose your API token and copy it.
    
    ![API Key][image-12]


## Endpoints
The table below shows a list of endpoints available to connect within the DataDistillr application. If you need to connect to any endpoints not listed in the table below, please use the [Custom API](custom-apis.md) Form.

| Endpoint   | Required | Optional | Description                                   |
|------------|----------|----------|-----------------------------------------------|
| `items`    |          |          | Returns the items where the user has access   |
| `users`    |          |          | Returns the users where the user has access   |
| `boards`   |          |          | Returns the boards where the user has access  |
| `updates`  |          |          | Returns the updates where the user has access |

### How does GraphQL work?
This API is built with GraphQL, a flexible query language that allows you to return as much or as little data as you need.

Unlike REST APIs, the API of monday.com uses a single endpoint: `https://api.monday.com/v2`

GraphQL relies on a type system, where each object is a type and contains fields that define it. These fields can be scalars (such as integers) or can be objects themselves. Some fields also take arguments, which can be used to limit, filter, or sort the data that is returned.

For example, the Board type contains scalar fields like name, id, and description. It also contains an items field, which defines the items on that specific board and contains its own fields (like name, id, state).





### Nav Tree
The endpoints above will display as follows in the nav tree once your API has successfully connected.


<figure markdown>
  ![Monday Endpoints][image-5]{ width="100%" }
</figure>


## Sample Queries
The following queries are intended to help you get started, and make life simpler querying within your API.

For the following examples, suppose that my Monday API data source was called `mymondayapi` and I want to query an endpoint. In the `FROM` clause, the endpoint goes after the Monday data source name.

!!! example "FROM Clause"

    ```sql
    FROM `mymondayapi`.`<ENDPOINT>`
    ```

### Items
monday.com items are a core object in the platform. Items are the objects that hold the actual data within the board, to better illustrate this, you can think of a board as a table and an item as a single row in that table.

```sql
SELECT * 
FROM `mymondayapi`.`items`
LIMIT 1000
```

### Users
Every user in monday.com is a part of an account (i.e. an organization) and could be a member or a guest in that account.

Querying users returns one or multiple users.


```sql
SELECT * 
FROM `mymondayapi`.`users`
LIMIT 1000
```

### Boards
monday.com boards are where users input all of their data. As such it is one of the core components of the platform, and one of the main objects you will need to be familiar with.

A board’s structure is composed of rows (called items), groups of rows (called groups), and columns. The data of the board is stored in the items on the board as well as in the updates sections of each item. Each board has one or more owners and subscribers.

Additionally, there are three different board types (main, shareable, private) and each board can have different sets of permissions. Querying boards can return one board, or a collection of boards.

```sql
SELECT * 
FROM `mymondayapi`.`boards`
LIMIT 1000
```

### Updates
monday.com updates contain additional notes and information added to items outside their columns. The main form of communication within the platform takes place in the updates section.

```sql
SELECT * 
FROM `mymondayapi`.`updates`
LIMIT 1000
```

[image-0]: ../../img/api/data-source-wizard-api-light.png "Data Source Wizard"
[image-1]: ../../img/api/monday/choose-form-monday-light.png "API Data Source selection"
[image-2]: ../../img/api/monday/choose-form-monday-dark.png "API Data Source selection"
[image-3]: ../../img/api/monday/monday-form-light.png "Monday.com form"
[image-4]: ../../img/api/monday/monday-form-dark.png "Monday.com form"
[image-5]: ../../img/api/monday/monday-nav-tree-light.png "Monday.com endpoints in query page nav tree sidebar"
[image-6]: ../../img/api/monday/monday-nav-tree-dark.png "Monday.com endpoints in query page nav tree sidebar"
[image-7]: ../../img/api/monday/monday-home-page.png "Monday.com workspace page"
[image-8]: ../../img/api/monday/monday-account-pop-up-admin.png "Admin page link in account settings pop up"
[image-9]: ../../img/api/monday/monday-account-pop-up-dev.png "Developers page link in account settings pop up"
[image-10]: ../../img/api/monday/monday-admin-api-key.png "Admin API token settings"
[image-11]: ../../img/api/monday/monday-dev-my-access-tokens.png "Monday.com My Apps page"
[image-12]: ../../img/api/monday/monday-dev-api-key.png "Developer API token settings"

[link-1]: https://monday.com/ "Monday.com home page"
[link-2]: https://apps.developer.monday.com/docs "Monday.com apps framework documentation" 
[link-3]: https://graphql.org/learn/ "Introduction to GraphQL"
[link-4]: https://monday.com/sales/contact-us?from=header&source=Website%20-%20Contact%20Sales "Contact Monday.com sales team"
[link-5]: https://monday.com/pricing/ "Monday.com pricing"
[link-6]: https://monday.com/developers/v2/try-it-yourself "Monday.com Developers Try it yourself" 