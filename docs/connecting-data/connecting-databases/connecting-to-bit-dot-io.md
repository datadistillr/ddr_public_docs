---
description: Configuring a data source connection to Bit.io
---

# Connecting to Bit.io
Bit.io is a serverless Postgres database which is available at [bit.io](https://bit.io). 

From a usage perspective, querying bit.io is exactly like querying a Postgres database from DataDistillr. 

## Configuring DataDistllr to Connect to Bit.io
After creating a database on Bit.io, click on the connect icon at the top of the screen:

![Bit.io Connect](<../../img/connecting-data/bit.io/connect.png>)

Next, you'll need to get a few artifacts from the Bit.io configuration. Specifically, you will need:

* Your username
* Your database name:  Note that the database name is `<user_name>/<db_name>`
* The password for your database.

![Bit.io Connection Screen](<../../img/connecting-data/bit.io/BitIo%20Connection.png>)

Next, open DataDistillr, navigate to add datasources, then select Databases and then select bit.io.

In this form, give your connection a name.  In the `Database Name` field, fill out your database name.

!!! warning "Be Sure to Supply Your Complete Database Name"

    The database name must be in the format of <username>/<database>

Next, add your username and password for your database.

!!! warning "Make Sure You Use Your Database Password"
    
    Bit.io generates a password for each database.  Be sure to use the database password and not your account password.
    

![DataDistillr Connection Screen](<../../img/connecting-data/bit.io/bit_io_connection_form.png>)

Once you are done, save your settings and you should be ready to query data from Bit.io!