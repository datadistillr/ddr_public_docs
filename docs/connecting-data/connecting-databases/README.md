---
description: How to connect relational and NoSQL databases to DataDistillr
---

# Connecting Databases

## __Relational Databases__

DataDistillr can connect to a wide variety of commonly used relational databases. DataDistillr uses JDBC as the
connection mechanism, so if there is a particular database or other source that has a JDBC driver, and it is not
listed as a source that we support, please [email our support team](mailto:support@datadistllr.com) and we can add it.

DataDistillr currently supports:

* [Bit.io](connecting-to-bit-dot-io.md) - Serverless Postgres
* BitQuery
* Elasticsearch
* MySQL / MariaDB
* MSSQL Server
* Oracle
* Postgres
* Snowflake
* [Splunk](connecting-to-splunk.md)

... and more coming soon! You can request a database by [emailing our support team](mailto:support@datadistllr.com)

The connection procedure for relational databases is essentially the same for most relational databases.
You will need:

* A **unique name** for your database connection to be used in queries
* The **hostname** and **port** for your database
* Your access **credentials**
* Any other configuration variables needed to connect

### __Adding Your Relational Database__

Starting from the Data Sources page as shown below, click _Add a new database datasource_.
![Data Sources main page](<../../img/connecting-data/add-data-sources-page.PNG>)


You will see a selection of databases as shown below. Select the database you are connecting to DataDistillr.

![Add a new data source to DataDistillr](<../../img/connecting-data/data-source-options.PNG>)

After selecting a database type, you will see a form similar to the one below. Fill out the fields and click _Save_ to
connect the relational database to DataDistillr. The example below is for a MySQL database.

![MySQL Connection Form](<../../img/connecting-data/MySQL-connection-form.png>)

Next, you'll need to [link your data source to your project](../linking-data-to-your-project.md).
