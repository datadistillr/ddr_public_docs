# JIRA API

## Creating a JIRA account
Set up an account with [JIRA](https://www.atlassian.com/software/opsgenie/try).

Your Atlassian account is your online Atlassian identity that exists independently of the Atlassian products you use. The account includes attributes like your email address and display name.

### Costs
There are four plan tiers:

**Free**
: $0 Always free for 10 users

**Standard**
:	$7.50 per user (average) $75 a month

**Premium**
:	$14.50 per user (average) $145 a month

**Enterprise**
:	Billed annually

### Rate Limits
The JIRA API is limited to 500 API requests per 5 minutes. Once you exceed this limit, calls will return HTTP status 429 and a message telling you that you've been limited.

Also as a means of preventing room "spam", API methods that involve sending messages to rooms or individual people are limited to 30 requests per minute.


## How to Connect DataDistillr to JIRA
To set up a data source connection for JIRA, you will need to have:

- A unique name for your data source connection to be used in queries
- The domain of your Atlassian account
- The email associated with your Atlassian account
- The API token generated through your Atlassian account

### Data Source Form
To locate the JIRA form, follow the steps in [Connecting Your Data to DataDistillr](../../). When you get to the window to choose the data source type, select API as shown below.

<figure markdown>
  ![Data Source Wizard][image-7]{ width="100%" }
  <figcaption>Data Source Wizard</figcaption>
</figure>



On the API screen, select JIRA from the list of API forms.

<figure markdown>
  ![List of APIs][image-8]{ width="100%" }
  <figcaption>List of APIs</figcaption>
</figure>



The following form will appear. Instructions can be found below on how to find the information requried to fill each field on the JIRA API form.

Once you have filled out all the fields, press the green 'Save' button, and your API will be connected!

<figure markdown>
  ![JIRA Form][image-1]{ width="100%" }
  <figcaption>JIRA Form</figcaption>
</figure>


### Name
Enter any name that will help you recognize this data source from within your query window.

Acceptable characters include:

- lowercase alphanumeric characters
- underscores

### Domain
An Organization is a management layer that gives admins the ability to view and apply controls to all Atlassian accounts using an email address belonging to their company. 

You can access your Organization at [https://admin.atlassian.com/](https://admin.atlassian.com/) to find your domain.

<figure markdown>
  ![Finding your domain][image-3]{ width="100%" }
  <figcaption>Domain</figcaption>
</figure>

!!! example "Steps to get your domain"

    === "1. Home page"

        In the JIRA app, click your profile icon in the top right corner of the page.

        ![JIRA Home Page][image-10]

    === "2. Accout settings"

        In the section with your name, click the **Account settings** link, this will take you to another page that contains information about your Atlassian account.

        ![Account Pop Up][image-11]

    === "3. Find Domain"

        In the left-hand sidebar, click **Products** and there will be your domain under the "Jira settings" section.

        ![Find Domain][image-12]

### User
This is the email that is tied to your Atlassian account.

!!! example "Steps to get your user"

    === "1. Home page"

        In the JIRA app, click your profile icon in the top right corner of the page.

        ![JIRA Home Page][image-10]

    === "2. Accout settings"

        In the section with your name, click the **Account settings** link, this will take you to another page that contains information about your Atlassian account.

        ![Account Pop Up][image-11]

    === "3. Find email"

        In the left-hand sidebar, click **Products** and there will be your domain under the "Jira settings" section.

        ![Find Domain][image-4]


### API Key
To generate your API key, navigate to our Account where you will have the option to generate an API key as highlighted below. Copy this API key and enter it in the JIRA form under 'API key'.

!!! example "Steps to get API key"

    === "1. Home page"

        In the JIRA app, click your profile icon in the top right corner of the page.

        ![JIRA Home Page][image-10]

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

<figure markdown>
  ![JIRA Endpoints][image-2]{ width="100%" }
  <figcaption>Query Page Sidebar</figcaption>
</figure>


## Sample Queries
The following queries are intended to help you get started, and make life simpler querying within your API.


Suppose that my JIRA API data source was called `myjiraapi`

### Get Board Endpoint
Suppose that I get a board with the ID of `1`. This will be the result.

```sql title="Get Board endpoint"
SELECT *
FROM `myjiraapi`.`/board/:boardId`
WHERE `boardId`='1'
LIMIT 100
```

### Get All Boards Endpoint
Suppose that I get a board with the ID of `1`. This will be the result. `SELECT` `#!sql SELECT`

```sql title="Get All Boards endpoint"
SELECT *
FROM `myjiraapi`.`/board`
LIMIT 100
```

### Get Epics Endpoint
Suppose that I get a board with the ID of `1`. This will be the result. `#!sql SELECT * FROM table`

```sql title="Get Epics endpoint" linenums="1" hl_lines="2"
SELECT *
FROM `myjiraapi`.`/board/:boardId/epic`
WHERE `boardId`='1'
LIMIT 100
```

### Get Issues Endpoint
Suppose that I get a board with the ID of `1`. This will be the result.

```sql title="Get Issues endpoint"
SELECT *
FROM `myjiraapi`.`/board/:boardId/issue`
WHERE `boardId`='1'
LIMIT 100
```

Please see the [Project license](#costs) for further details

### Get Projects Endpoint
Suppose that I get a board with the ID of `1`. This will be the result.

```sql title="Get Projects endpoint
SELECT *
FROM `myjiraapi`.`/board/:boardId/project`
WHERE `boardId`='1'
LIMIT 100
```

```py title="bubble_sort.py"
def bubble_sort(items):
    for i in range(len(items)):
        for j in range(len(items) - 1 - i):
            if items[j] > items[j + 1]:
                items[j], items[j + 1] = items[j + 1], items[j]
```
!!! note "Admon title"
This is the body of the admonition

??? question "Help me please"
This is the body of my question


=== "C"

    ``` c
    #include <stdio.h>

    int main(void) {
      printf("Hello world!\n");
      return 0;
    }
    ```

=== "C++"

    ``` c++
    #include <iostream>

    int main(void) {
      std::cout << "Hello world!" << std::endl;
      return 0;
    }
    ```





!!! example

    === "Unordered List"

        ``` markdown title="List, unordered"
        * Sed sagittis eleifend rutrum
        * Donec vitae suscipit est
        * Nulla tempor lobortis orci
        ```

    === "Ordered List"

        ``` markdown title="List, ordered"
        1. Sed sagittis eleifend rutrum
        2. Donec vitae suscipit est
        3. Nulla tempor lobortis orci
        ```


=== "C"

    ``` c
    #include <stdio.h>

    int main(void) {
      printf("Hello world!\n");
      return 0;
    }
    ```

=== "C++"

    ``` c++
    #include <iostream>

    int main(void) {
      std::cout << "Hello world!" << std::endl;
      return 0;
    }
    ```

- A unique name for your data source connection to be used in queries.
- The Base ID (Called 'Project Path' on the form).
- The API Key generated through your Airtable account.

**Name**
:	A unique name for your data source connection to be used in queries

**Domain**
:	The domain of you Atlassian account.

**User**
:	The email associated with your Atlassian account.

**API key**
:	The API token generated through your Atlassian account.

!!! Name

    The email associated with your Atlassian account.

!!! Domain

    The API token generated through your Atlassian account

!!! User

    The email associated with your Atlassian account.

!!! API key

    The API token generated through your Atlassian account

[image-1]: ../../img/api/jira/jira-form-dark.png
[image-2]: ../../img/api/jira/jira-query-page-sidebar-dark.png
[image-3]: ../../img/api/jira/jira-atlassian-organization.png
[image-4]: ../../img/api/jira/jira-find-email.png
[image-5]: ../../img/api/jira/jira-manage-api-tokens.png
[image-6]: ../../img/api/jira/jira-create-new-api-token.png
[image-7]: ../../img/api/data-source-wizard-api.png
[image-8]: ../../img/api/jira/jira-choose-jira-form.png
[image-9]: ../../img/api/jira/jira-create-api-token.png
[image-10]: ../../img/api/jira/jira-home-page.png
[image-11]: ../../img/api/jira/jira-account-pop-up.png
[image-12]: ../../img/api/jira/jira-domain.png