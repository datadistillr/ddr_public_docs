# Connecting to ServiceNow

## Creating a ServiceNow account
Set up an account with [ServiceNow](https://www.servicenow.com/){target="_blank"}.

### Costs

Get a custom quote from [ServiceNow](https://www.servicenow.com/lpgp/pricing-itsm.html?campid=29573&cid=p:all:dg:b:prsp:core_brand_prsp:ams:all&s_kwcid=AL!11692!3!529674030705!e!!g!!servicenow%20cost&ds_c=GOOG_AMS_All_EN_DEMANDGEN_ALBU_PRSP_Brand_EXA_&cmcid=71700000065217230&ds_ag=ServiceNow+Cost_EXA&cmpid=58700005783664262&ds_kids=p52805252935&gclid=Cj0KCQjw3IqSBhCoARIsAMBkTb36TvnRRoLA7mVtpVIDN9ZNZurDHz-EHtidmtp7af3b-A7PSShNmoUaAmDdEALw_wcB&gclsrc=aw.ds){target="_blank"}.

### Rate Limits
To prevent excessive inbound REST API requests, set rules that limit the number of inbound REST API requests processed per hour. 
You can create rules to limit requests for specific users, users with specific roles, or all users. You can learn more about that in the [ServiceNow](https://docs.servicenow.com/bundle/sandiego-application-development/page/integrate/inbound-rest/concept/inbound-REST-API-rate-limiting.html){target=_blank} docs.

## How to Connect DataDistillr to ServiceNow
To set up a data source connection for ServiceNow, you will need to have:

- A [unique name](#name) for your data source connection to be used in queries
- The [Instance Name](#instance-id-username-and-password) associated ServiceNow Instance
- The [Username](#instance-id-username-and-password) associated with your ServiceNow Instance
- The [Password](#instance-id-username-and-password) associated with your ServiceNow Instance

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

!!! info "Acceptable Characters Include"

    - lowercase alphanumeric characters
    - underscores

### Instance ID, Username and Password

=== "1. Home Page"

    Head over to your ServiceNow [developer portal](https://developer.servicenow.com/dev.do).
    In the top right corner click the profile avatar.
    
    ![ServiceNow Home Page][image-10]

=== "2. My Instance"

    Click the "Manage instance password" tab.
    
    ![Find Instance creds][image-11]

=== "3. Instance Credentials" 

    Here you will find your credentials necessary (Instance name, Username and Password) to connect your ServiceNow instance to DataDistillr.

    ![Instance creds][image-12]


## Endpoints
The table below shows a list of endpoints available to connect within the DataDistillr application. If you need to connect to an endpoint not listed below, please use the [Custom API](custom-apis.md) Form.

| Endpoint   | Required | URL Params  | Description                                      |
|------------|----------|-------------|--------------------------------------------------|
| `tables`   |          | `tableName` | Returns the table with the matching `tableName`. |
| `case`     |          |             | Returns Customer Service Management (CSM) cases. |
| `user`     |          |             | Returns set of (CSM) accounts.                   |
| `consumer` |          |             | Returns set of (CSM) consumer records.           |
| `contact`  |          |             | Returns set of (CSM) consumer contacts.          |



### Nav Tree
The endpoints above will display as follows in the nav tree once your API has successfully connected.

<figure markdown>
  ![ServiceNow Endpoints][image-2]{ width="100%" }
</figure>


## Sample Queries
The following queries are intended to help you get started, and make life simpler querying within your API.

For the following examples, suppose that my ServiceNow API data source was called `myservicenowapi` and I want to query an endpoint. The endpoint goes after the JIRA data source name:

!!! example "FROM Clause"

    ```sql
    FROM `myservicenowapi`.`<ENDPOINT>`
    ```

### Get Tables

Retrieves multiple records for the specified table.

```sql title="Get Tables endpoint"
SELECT *
FROM `myServiceNowapi`.`tables`
WHERE `tableName`='sn_customerservice_case'
LIMIT 100
```

### Get Case

Retrieves a specified set of Customer Service Management (CSM) cases.
```sql title="Get Case endpoint"
SELECT *
FROM `myServiceNowapi`.`case`
LIMIT 100
```

### Get User

Retrieves a specified set of Customer Service Management (CSM) accounts
```sql title="Get User endpoint"
SELECT *
FROM `myServiceNowapi`.`user`
LIMIT 100
```

### Get Consumer

Retrieves a specified set of Customer Service Management (CSM) accounts
```sql title="Get Consumer endpoint"
SELECT *
FROM `myServiceNowapi`.`consumer`
LIMIT 100
```

### Get Contact

Retrieves a specified set of Customer Service Management (CSM) contacts.

```sql title="Get Contact endpoint"
SELECT *
FROM `myServiceNowapi`.`contact`
LIMIT 100
```

[image-1]: ../../img/api/servicenow/servicenow-form.png
[image-2]: ../../img/api/servicenow/servicenow-navtree.png
[image-7]: ../../img/api/data-source-wizard-api-light.png
[image-8]: ../../img/api/servicenow/select-servicenow-api.png
[image-10]: ../../img/api/servicenow/servicenow-homepage.png
[image-11]: ../../img/api/servicenow/servicenow-get-creds.png
[image-12]: ../../img/api/servicenow/servicenow-creds.png