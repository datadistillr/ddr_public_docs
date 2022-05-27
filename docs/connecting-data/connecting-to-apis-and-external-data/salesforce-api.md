---
description: How to Connect DataDistillr to the Salesforce API
---

# Connecting to Salesforce

## First Steps with Salesforce

Set up an account
with [Salesforce](https://www.salesforce.com/form/signup/freetrial-elf-v2/?d=70130000000EqoP){target=_blank}.

???+ cost
[Prices](https://www.salesforce.com/editions-pricing/overview/){target=_blank} vary depending on which Salesforce
Product you are working with.

???+ rlimit "Rate Limits"
Your account plan tier will limit the number of API requests per 24-hour period. Current rate limits for each account
tier are available in
Salesforce's [documentation](https://developer.salesforce.com/docs/atlas.en-us.salesforce_app_limits_cheatsheet.meta/salesforce_app_limits_cheatsheet/salesforce_app_limits_platform_api.htm){target=_blank}
.

## How to Connect DataDistillr to Salesforce

To set up a data source connection for Salesforce, you will need to have:

- A [callback URL](#salesforce-set-up) generated in your DataDistillr account.
- A [unique name](#name) for your data source connection to be used in queries.
- A [consumer key](#consumer-key-consumer-secret) generated in your Salesforce account.
- A [consumer secret](#consumer-key-consumer-secret) generated in your Salesforce account.
- A [subdomain](#subdomain) generated in your Salesforce account.

### Data Source Form

To locate the Salesforce form, follow the steps in [Connecting Your Data to DataDistillr](../../). When you get to the
window to choose the data source type, select API as shown below.

![Select API from the available choices][image-0]

On the API screen, select Salesforce from the list of API types as shown in the image below.

![Select Salesforce API from available choices][image-1]

The following form will appear. Instructions are below on how to find the information required to fill each field on the
Salesforce API form.

Once you have filled out all the fields, press the green 'Save' button, and your API will be connected!

![Salesforce form][image-2]{#salesforce-form}

### Salesforce set-up

Before you can connect your Salesforce data to DataDistillr, you need to do some set-up in your Salesforce profile.

=== "1. Find Account info"

    When you set up your Salesforce account, you should have received an email that looks like the one below. This
    gives you the URL to access your Salesforce account, as well as your Username.

    ![Salesforce Account Info][image-3]

=== "2. Log in"

    Navigate to the URL found in the email, and type in your Username and Password.

    ![Salesforce Login Screen][image-4]

=== "3. Settings"

    In the top right corner, click on the gear icon. From the dropdown menu, select **Setup**.    

    ![Salesforce Settings][image-5]

=== "4. Setup Home"

    In the left-hand navigation panel, scroll down to the **PLATFORM TOOLS** section. Under **Apps**, select
    **App Manager**.

    ![Setup Home find App Manager][image-6]

=== "5. App Manager"

    In the top right corner of the App Manager screen, select **New Connected App**.

    ![Select New Connected App][image-7]

=== "6. Configure: Basic Information"

    In the Form that appears, fill out the following sections under Basic Information: Connected App Name, API Name,
    and Contact Email.

    ![Basic Information Section][image-8]

=== "7. Configure: API"

    Scroll down to the section titled "API (Enable OAuth Settings)".

    - Check the box next to **Enable OAuth Settings**
    - For **Callback URL**, copy and paste the Callback URL found in the [DataDistillr API Form](#salesforce-form)
    - For **Selected OAuth Scopes**, select "Full Access (full)" and "Perform requests at any time (refresh_token,
    offline_access)" and Add them to the list of Selected OAuth Scopes

    ![Configure API info][image-9]

=== "8. Save and Wait"

    Scroll down to the bottom of the form and press **Save**, then wait approximately 10 minutes for the changes to take effect.

    ![Save Salesforce config][image-10]

### Name

Enter any name that will help you recognize this data source from within your query window.

!!! info "Acceptable Characters Include"

    - lowercase alphanumeric characters
    - underscores

### Consumer Key, Consumer Secret

Follow steps 1-4 in [Salesforce set-up](#salesforce-set-up) to Navigate to the App Manager, then follow the directions
below to find your Consumer Key.

=== "1. App Manager"

    Once you are in the App Manager, find the Connected App you created. Ours is named `ddr_webapp`. Click on the
    downward facing arrow at the Right to expand a selection panel. Select **View**.
    
    ![View Connected App][image-11]

=== "2. Find Consumer Key and Secret"

    You can find the consumer key and consumer secret in the section labeled "API (Enable OAuth Settings)". Copy and
    paste these values into the Salesforce Data Source Form.          

    ![Consumer and Secret][image-12]

### Subdomain

The subdomain can be found in the original email, referenced above, or in the URL. The subdomain is the part found at
the beginning of the URL between https:// and .my.salesforce.com. In the example below, the subdomain is `datadistillr3`
.

![Salesforce subdomain][image-13]

## Endpoints

Please see the [Salesforce API Reference](https://developer.salesforce.com/docs#browse){target=_blank} that corresponds
to your Salesforce product of interest for more on Salesforce's endpoints.

The table below shows a list of endpoints available to connect to within the DataDistillr application. If you need to
connect to any endpoints not listed in the table below, please use the [Custom APIs](custom-apis.md) Form.

| Endpoint | Required | Optional | Description |
|  ----------- | ----------- | ----------- | ----------- |
| `/chatter/users` | |  | Returns information about all users in an organization. |
| `/chatter/users/:user_id` |user_id |  | Returns information about a specific user. |

### Nav Tree

The endpoints above will display as follows in the nav tree once your API has successfully connected.

![Salesforce Nav Tree][image-14]

## Sample Queries

The following queries are intended to help you get started, and make life simpler querying within your API.

For the following examples, suppose that my Salesforce API data source was called `salesforceapi`, and I want to query
an endpoint. The endpoint goes after the Salesforce data source name:

!!! example "FROM Clause"

    ```sql
    FROM `salesforceapi`.`<ENDPOINT>`
    ```

### Get Users Endpoint

This query returns chatter user info for a specific user ID.

```sql
SELECT *
FROM `salesforceapi`.`/chatter/users/:user_id`
WHERE `user_id` = '1234a12345A1BCDEF2' LIMIT 1000
```

[image-0]: ../../img/api/add-api.png

[image-1]: ../../img/api/salesforce/salesforce-select-api.jpeg

[image-2]: ../../img/api/salesforce/salesforce-form.png

[image-3]: ../../img/api/salesforce/salesforce-account-info.png

[image-4]: ../../img/api/salesforce/salesforce-login-screen.png

[image-5]: ../../img/api/salesforce/salesforce-settings-setup.png

[image-6]: ../../img/api/salesforce/salesforce-setup-home.png

[image-7]: ../../img/api/salesforce/salesforce-select-connectedapp.png

[image-8]: ../../img/api/salesforce/salesforce-basic-info.png

[image-9]: ../../img/api/salesforce/salesforce-api-config.png

[image-10]: ../../img/api/salesforce/salesforce-save-config.png

[image-11]: ../../img/api/salesforce/salesforce-view-app-manager.png

[image-12]: ../../img/api/salesforce/salesforce-consumerkey-secret.png

[image-13]: ../../img/api/salesforce/salesforce-subdomain.png

[image-14]: ../../img/api/salesforce/salesforce-nav-tree.png