---
description: How to Connect DataDistillr to External Data Sources
---

# Connecting to APIs and External Data

One of DataDistillr's most powerful features is the ability to connect to external data sources. 
Many organizations make data accessible via API, however querying APIs with SQL can be complicated.
The good news is you can configure DataDistillr to query nearly all APIs, but it does require some understanding of
both the API you are querying and how DataDistillr works. These documents will walk you through all the possibilities
for configuring DataDistillr to query your API.

!!! warning "Considerations with Remote Data"
    
    __3rd party terms of service__

    When querying remote data, be sure to comply with the data source owner's terms of service. 
    Users who violate 3rd party terms of service will have their remote connections removed.

    __Latency Concerns__

    If you have a remote data source that you are repeatedly querying and the data is not changing, we encourage
    you to save this data to your DataDistillr account. Your queries will return faster, and you will not be subject
    to any 3rd party's bandwidth restrictions.

### __What You Need__

In order to connect to any API, you will need the following information, which should be in your API documentation:

#### __Minimum Information__

* The connection URL.
* The request type (either `GET` or `POST`).
* The type of data the API returns.  We currently support `JSON`, `CSV` and `XML`.

#### __Optional Information__

* **Authentication information:** If your API uses token based authentication (OAuth2), there are several additional
fields which you will need to configure so that we can obtain the tokens.
* **Access credentials:**  Alternatively, if your API uses basic authentication, you will need to supply your username
and password.
* **[API Parameters](passing-parameters.md):** Often APIs will have parameters which can be included as part of the
API request. DataDistillr can translate your SQL queries so that these variables are included in the request.
Including parameters is optional, but it will result in faster execution.

### __APIs we Support__

We currently support the following APIs with forms to make the connection process as easy as possible.
If your API is not on the list below, you may use the [Custom API](custom-apis.md) form to connect to your
API or [contact us](../../../getting-help) for assistance.

DataDistillr currently supports:

* [Affinity](affinity-api.md)
* [AirTable](airtable-api.md)
* [Asana](asana-api.md)
* [ClickUp](clickup-api.md)
* [Crunchbase](crunchbase-api.md)
* [Datadog](datadog-api.md)
* [DonorSearch](donorsearch-api.md)
* [Fiscal Data](fiscaldata-api.md)
* [GitHub](github-api.md)
* [Harmonic](harmonic-api.md)
* [JIRA](jira.md)
* [Monday](monday-api.md)
* [People Data Labs](peopledatalabs-api.md)
* [Placer.ai](placer-api.md)
* [Quickbooks](quickbooks-api.md)
* [Salesforce](salesforce-api.md)
* [ServiceNow](servicenow-api.md)
* [Stripe](stripe-api.md)
* [Twilio](twilio-api.md)
* [UPC Database](upc-database-api.md)
* [Veriphone](veriphone-api.md)
* [VirusTotal](virustotal-api.md)

Happy Distilling!
