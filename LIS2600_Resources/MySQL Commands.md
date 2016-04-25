A MySQL database server contains many databases (or schemas). Each database consists of one or more tables. A table is made up of columns (or fields) and rows (records).

The SQL keywords and commands are _NOT_ case-sensitive. For clarity, they are shown in uppercase. The *names* or *identifiers* (database names, table names, column names, etc.) are case-sensitive in some systems, but not in other systems. Hence, it is best to treat *identifiers* as case-sensitive.

##### SHOW DATABASES

You can use `SHOW DATABASES` to list all the existing databases in the server.

    mysql> **SHOW DATABASES;**
  
  |  Database |
|---|
|  information_schema |
| mysql  |
|  performance_schema |
| test |
    
The databases "`mysql`", "`information_schema`" and "`performance_schema`" are system databases used internally by MySQL. A "`test`" database is provided during installation for your testing.

You can create a new database using SQL command "`CREATE DATABASE *databaseName*`"; and delete a database using "`DROP DATABASE *databaseName*`". You could optionally apply condition "`IF EXISTS`" or "`IF NOT EXISTS`" to these commands. For example,

    mysql> **CREATE DATABASE southwind;**
    Query OK, 1 row affected (0.03 sec)

    mysql> **DROP DATABASE southwind;**
    Query OK, 0 rows affected (0.11 sec)

    mysql> **CREATE DATABASE IF NOT EXISTS southwind;**
    Query OK, 1 row affected (0.01 sec)

    mysql> **DROP DATABASE IF EXISTS southwind;**
    Query OK, 0 rows affected (0.00 sec)

**IMPORTANT**: Use SQL `DROP` (and `DELETE`) commands with extreme care, as the deleted entities are irrecoverable. **THERE IS NO UNDO!!!**

##### SHOW CREATE DATABASE

The `CREATE DATABASE` commands uses some defaults. You can issue a "`SHOW CREATE DATABASE *databaseName*`" to display the full command and check these default values. We use `\G` (instead of `';'`) to display the results vertically. (Try comparing the outputs produced by `';'` and `\G`.)

    mysql> **CREATE DATABASE IF NOT EXISTS southwind;**

    mysql> **SHOW CREATE DATABASE southwind \\G**
    *************************** 1. row ***************************
           Database: southwind
    Create Database: CREATE DATABASE `southwind` /\*!40100 DEFAULT CHARACTER SET latin1 \*/

##### Back-Quoted Identifiers (`name`)

Unquoted names or identifiers (such as database name, table name and column name) cannot contain blank and special characters, or crash with MySQL keywords (such as `ORDER` and `DESC`). You can include blanks and special characters or use MySQL keyword as identifier by enclosing it with a pair of back-quote, in the form of ``*name*``.

For robustness, the `SHOW `command back-quotes all the identifiers, as illustrated in the above example.

##### Comments and Version Comments

MySQL *multi-line comments* are enclosed within `/*` and `*/`; *end-of-line comments* begins with `--` (followed by a space) or `#`.

The `/*!40100 ...... */` is known as *version comment*, which will only be run if the server is at or above this version number `4.01.00`. To check the version of your MySQL server, issue query "`SELECT version()`".

ID | Product Code | Name | Quantity | Unit Price
  ---|---
  1001 | 46557 | flange | 10 | $47.99
  1002 | 37774 | oil filter | 35 | $6.99
  1003 | 86643 | gasket | 5 | $34.99

### Creating and Deleting a Database - CREATE DATABASE and DROP DATABASE

You can create a new database using SQL command "`CREATE DATABASE *databaseName*`"; and delete a database using "`DROP DATABASE *databaseName*`". You could optionally apply condition "`IF EXISTS`" or "`IF NOT EXISTS`" to these commands. For example: