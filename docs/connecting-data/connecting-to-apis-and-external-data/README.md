---
description: How to Connect DataDistillr to External Data Sources
---

# Connecting to APIs and External Data

One of DataDistillr's most powerful features is the ability to connect to external data sources.  Many organizations make data accessible via API, however querying APIs with SQL can be complicated.  The good news is that you can configure DataDistillr can query nearly all APIs, but it does require some understanding of both the API you are querying and how DataDistillr works.  These documents will walk you through all the possibilities for configuring DataDistillr to query your API, from the simplist to most complex. &#x20;

!!! warning "Considerations with Remote Data"
    When querying remote data, be sure to comply with the data source owner's terms of service.  Users found to be violating 3rd party terms of service will have their remote connections removed.

    __Dealing with Latency Concerns__

    If you have a remote data source that you are repeatedly querying, and the data is not changing, we encourage you to save this data to your DataDistillr account. Your queries will return faster, and you will not be subject to any 3rd party's bandwidth restrictions.


### __What You Need__

In order to connect to any API, you will need the following information, which should be in your API documentation:

#### __Minimum Information__

* The connection URL
* The request type.  This will be either `GET` or `POST`. &#x20;
* What kind of data the API returns.  We currently support `JSON`, `CSV` and `XML`.

#### __Optional Information__

* Authentication information:  If your API uses token based authentication (OAuth2), there are several additional fields which you will need to configure so that we can obtain the tokens.
* Access credentials:  Alternatively, if your API uses basic authentication, you will need to supply your username and password.
* [API Parameters](passing-parameters.md):  Often APIs will have parameters which can be included as part of the API request. DataDistillr can translate your SQL queries so that these variables are included in the request.  It is not always necessary to do so, but it will result in faster execution.

Happy Distilling!
