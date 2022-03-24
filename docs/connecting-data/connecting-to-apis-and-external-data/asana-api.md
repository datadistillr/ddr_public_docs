# Connecting to the Asana API

## Creating an Asana account
Set up an account with [Asana](https://asana.com/create-account).

### **Costs**
There are a few different types of accounts: free, $10.99/month, and $24.99/month. You can check [HERE](https://asana.com/pricing) for details and comparison.

### **Rate Limits**
Limits are allocated per authorization token. Limits may vary from token to token.

Free account limit: 150 requests per minute.
Premium account limit: 1500 requests per minute.
SearchAPI  are limited to 60 requests per minute.
Duplication endpoints are limited to 5 concurrent jobs.

## How to Connect DataDisillr to Asana
To set up a data source connection for Asana, you will need to have:

- A unique name for your data source connection to be used in queries.
- The API key generated through your Asana account.

### Data Source Form

To locate the Asana form, follow the steps in [Connecting Your Data to DataDistillr](../../). When you get to the window to choose the data source type, select API as shown below.

![Select API from the available choices] [image-3]

On the API screen, select Asana from the list of API types as shown in the image below.

![Select Asana from API types] [image-4]

The following form will appear. Instructions can be found below on how to find the information required to fill each field on the Asana API form.

Once you have filled out all the fields, press the green 'Save' button, and your API will be connected!

![Asana Form] [image-1]

### Name
Enter any name that will help you recognize this data source from within your query window.

Acceptable characters include:

* lowercase alphanumeric characters
* underscores

### API Key
Once you have created a workspace in your Asana account, you can get the API key that you'll need to fill in the form. 
Click on your account icon at the top right of your screen. Then choose `My Settings`.
![Click on Assana Account Icon] [image-5]

## Endpoints
Please see https://developers.asana.com/docs/asana for more on Asana's endpoints.
### Table


### Query Page Sidebar
<figure markdown>
![Asana Query Page Sidebar] [image-2] {width=d}
</figure>

## Sample Queries
### Get tasks

[image-1]: ../../img/api/asana/asana-form-dark.png
[image-2]: ../../img/api/asana/asana-query-page-sidebar.png
[image-3]: ../../img/api/add-data-source-dark.png
[image-4]:../../img/api/new-data-source-api-types.png
[image-5]:../../img/api/asana/asana-account-icon.png