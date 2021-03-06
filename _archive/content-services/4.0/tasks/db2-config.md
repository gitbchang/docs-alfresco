---
author: [Alfresco Documentation, Alfresco Documentation]
source: 
audience: 
category: Customization
option: DB2 database
---

# Configuring a DB2 database

This section describes how to configure a DB2 database for use with Alfresco.

1.  Install the DB2 database connector. The database connector allows DB2 database to talk to the Alfresco server.

    1.  Obtain a copy of db2jcc4.jar. This should be available in the /java or /jdbc directory of your DB2 installation.

    2.  Copy the JAR file into the <TOMCAT\_HOME\>/lib directory for Tomcat 6.

2.  Create a database named alfresco.

    Create the database with a larger page size of 32K. Ensure that the database is created with the UTF-8 character set.

    If you do not create the database with these settings, you will see error SQL0286N \(`sqlCode -286, sqlstate 42727`\) because the schema is created for tables that do not fit the page size.

3.  Ensure that the `cur_commit` database configuration parameter is set to `ON`.

    For new databases, this parameter is set to ON, by default. If you have upgraded from a previous DB2 release, you must set this parameter manually.

4.  Create a user named alfresco and set the associated schema.

    This user must have write permissions on all tables and sequences.

    DB2 only integrates with the operating system security. You can not add a database user with a password in the DB2 database as you can with some other databases, for example the Oracle database.

5.  Open the <classpathRoot\>/alfresco-global.properties.sample file.

6.  Locate the following line:

    `dir.root=./alf_data`

7.  Edit the line with an absolute path to point to the directory in which you want to store Alfresco data. For example: `dir.root=C:/Alfresco/alf_data`

8.  Uncomment the following properties:

    ```
    # DB2 connection
    #
    db.driver=com.ibm.db2.jcc.DB2Driver
    db.url=jdbc:db2://${db.host}:${db.port}/${db.name}:retrieveMessagesFromServerOnGetMessage=true; 
    ```

9.  Set the other database connection properties.

    ```
    db.name=alfresco
    db.host=localhost
    db.port=50000
    db.pool.max=40
    ```

    **Note:** Ensure that these database connection properties are not commented out.

10. Save the file without the .sample extension.

11. Restart the Alfresco server.

    If you receive JDBC errors, ensure the location of the DB2 JDBC drivers are on the system path, or add them to the relevant lib directory of the application server.


**Parent topic:**[Configuring databases](../concepts/intro-db-setup.md)

