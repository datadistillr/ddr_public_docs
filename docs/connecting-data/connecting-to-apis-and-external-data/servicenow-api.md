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


??? example "Steps for finding your API credentials"

    Head over to your ServiceNow [developer portal](https://developer.servicenow.com/dev.do).
    In the top right corner click the profile icon.
    
    ![ServiceNow Home Page][image-10]
    
    Click the "Manage instance password" tab.
    
    ![Find Instance creds][image-11]
    
    Here you will find your credentials necessary to connect your ServiceNow instance to DataDistillr.
    
    ![Instance creds][image-12]


## Endpoints
The table below shows a list of endpoints available to connect within the DataDistillr application. If you need to connect to an endpoint not listed below, please use the [Custom API](custom-apis.md) Form.

| Endpoint   | Required | URL Params  | Optional | Description                                      |
|------------|----------|-------------|----------|--------------------------------------------------|
| `tables`   |          | `tableName` |          | Returns the table with the matching `tableName`. |
| `case`     |          |             |          | Returns Customer Service Management (CSM) cases. |
| `user`     |          |             |          | Returns set of (CSM) accounts.                   |
| `consumer` |          |             |          | Returns set of (CSM) consumer records.           |
| `contact`  |          |             |          | Returns set of (CSM) consumer contacts.          |



### Nav Tree
The endpoints above will display as follows in the nav tree once your API has successfully connected.

<figure markdown>
  ![ServiceNow Endpoints][image-2]{ width="100%" }
</figure>


## Sample Queries
The following queries are intended to help you get started, and make life simpler querying within your API.

For the following examples, suppose that my ServiceNow API data source was called `myservicenowapi` and I want to query an endpoint. The endpoint goes after the ServiceNow data source name like so: ``#!sql FROM `myServiceNowapi`.`<ENDPOINT>` ``.

### Get Tables

```sql title="Get Tables endpoint"
SELECT *
FROM `myServiceNowapi`.`tables`
WHERE `tableName`='sn_customerservice_case'
LIMIT 100
```

### Get Case

```sql title="Get Case endpoint"
SELECT *
FROM `myServiceNowapi`.`case`
LIMIT 100
```

### Get User

```sql title="Get User endpoint"
SELECT *
FROM `myServiceNowapi`.`user`
LIMIT 100
```

### Get Consumer

```sql title="Get Consumer endpoint"
SELECT *
FROM `myServiceNowapi`.`consumer`
LIMIT 100
```

### Get Contact

```sql title="Get Contact endpoint"
SELECT *
FROM `myServiceNowapi`.`contact`
LIMIT 100
```

[image-1]: ../../img/api/servicenow/servicenow-form.png
[image-2]: ../../img/api/servicenow/servicenow-navtree.png
[image-3]: ../../img/api/ServiceNow/ServiceNow-atlassian-organization.png
[image-4]: ../../img/api/ServiceNow/ServiceNow-find-email.png
[image-5]: ../../img/api/ServiceNow/ServiceNow-manage-api-tokens.png
[image-6]: ../../img/api/ServiceNow/ServiceNow-create-new-api-token.png
[image-7]: ../../img/api/add-api.png
[image-8]: ../../img/api/servicenow/select-servicenow-api.png
[image-9]: ../../img/api/ServiceNow/ServiceNow-create-api-token.png
[image-10]: ../../img/api/servicenow/servicenow-homepage.png
[image-11]: ../../img/api/servicenow/servicenow-get-creds.png
[image-12]: ../../img/api/servicenow/servicenow-creds.png