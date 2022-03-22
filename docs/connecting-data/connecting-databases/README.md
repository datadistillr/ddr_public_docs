---
description: How to connect relational and NoSQL databases to DataDistillr
---

# Connecting Databases

## __Relational Databases__

DataDistillr can connect to a wide variety of commonly used relational databases.  DataDistillr uses JDBC as the connection mechanism, so if there is a particular database or other source that has a JDBC driver, and it is not listed as a source that we support, please [email our support team](mailto:support@datadistllr.com) and we can add it. &#x20;

DataDistillr currently supports:

* MySQL / MariaDB
* MSSQL Server
* Oracle
* Postgres
* [Splunk](connecting-to-splunk.md)
* More coming soon!  You can request a database by emailing our support team.&#x20;

The connection procedure for relational databases is essentially the same for most relational databases.  You will need to have:

* A unique name for your database connection to be used in queries
* The hostname and port for your database
* Your access credentials
* Any other configuration variables needed to connect.

### __Adding Your Relational Database__

After clicking on the `Add Data Source` button and selecting `Database`  you will see a selection of databases as shown below.  Simply select the database you are connecting to DataDistillr.&#x20;

![Add a new data source to DataDistillr](<../../img/Screen Shot 2021-11-14 at 7.50.19 PM.png>)

After selecting a database type, you will see the form below.  For most relational databases, the form looks basically the same.  The example below is for a MySQL database.

![MySQL Connection Form](<../../img/Screen Shot 2021-11-14 at 7.59.39 PM.png>)

Once you submit the form, your relational database is now connected to DataDistillr, but there is still one final step: [linking your data source to your project](../../linking-data-to-your-project.md).