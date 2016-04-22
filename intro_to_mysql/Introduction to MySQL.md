MySQL is an open source relational database that has become of the mainstays of the World Wide Web.

MySQL is written in C and C++. Its SQL parser is written in yacc, but it uses a home-brewed lexical analyzer. MySQL works on many system platforms, including AIX, BSDi, FreeBSD, HP-UX, Linux, OS X, Microsoft Windows, NetBSD, OpenBSD, OpenSolaris,QNX, Oracle Solaris, and Symbian, among other operating systems. 

MySQL can also be run on cloud computing platforms such as Amazon EC2. Some of the common cloud deployment models for MySQL are:

* Virtual machine image --  In this implementation, cloud users can upload a machine image of their own with MySQL installed, or use a ready-made machine image with an optimized installation of MySQL on it, such as the one provided by Amazon EC2.
* MySQL as a service -- Some cloud platforms offer MySQL "as a service". In this configuration, application owners do not have to install and maintain the MySQL database on their own. Instead, the database service provider takes responsibility for installing and maintaining the database, and application owners pay according to their usage. Notable cloud-based MySQL services are the Amazon Relational Database Service; Rackspace; HP Converged Cloud; Heroku and Jelastic.
* Managed MySQL cloud hosting -- In this implementation, the database is not offered as a service, but the cloud provider hosts the database and manages it on the application owner's behalf. 

The MySQL server software itself and the client libraries use dual-licensing distribution. They are offered under GPL version 2, beginning from 28 June 2000 (which in 2009 has been extended with a FLOSS License Exception) or to use a proprietary license. (Support can be obtained from the official manual. Free support additionally is available in different IRC channels and forums. Oracle offers paid support via its MySQL Enterprise products. They differ in the scope of services and in price. Additionally, a number of third party organisations exist to provide support and services, including MariaDB and Percona.)

MySQL is offered under two different editions: the open source MySQL Community Server and the proprietary Enterprise Server. MySQL Enterprise Server is differentiated by a series of proprietary extensions which install as server plugins, but otherwise shares the version numbering system and is built from the same code base.

Major features as available in MySQL 5.6:

* A broad subset of ANSI SQL 99, as well as extensions
* Cross-platform support
* Stored procedures, using a procedural language that closely adheres to SQL/PSM
* Triggers
* Cursors
* Updatable views
* Online DDL when using the InnoDB Storage Engine.
* Information schema
* Performance Schema that collects and aggregates statistics about server execution and query performance for monitoring purposes.
* A set of SQL Mode options to control runtime behavior, including a strict mode to better adhere to SQL standards.
* X/Open XA](https://en.wikipedia.org/wiki/X/Open_XA "X/Open XA" (DTP) support; two phase commit as part of this, using the default InnoDB storage engine
* Transactions with savepoints when using the default InnoDB Storage Engine. The NDB Cluster Storage Engine also supports transactions.
* ACID compliance when using InnoDB and NDB Cluster Storage Engines
* SSL support
* Query caching
* Sub-SELECTs (i.e. nested SELECTs)
* Built-in Replication support (i.e. Master-Master Replication & Master-Slave Replication) with one master per slave, many slaves per master. Multi-master replication is provided in MySQL Cluster, and multi-master support can be added to unclustered configurations using Galera Cluster.
* Full-text indexing and searching
* Embedded database library
* Unicode support
* Partitioned tables with pruning of partitions in optimizer
* Shared-nothing clustering through MySQL Cluster
* Multiple storage engines, allowing one to choose the one that is most effective for each table in the application.
* Native storage engines InnoDB, MyISAM, Merge, Memory (heap), Federated, Archive, CSV, Blackhole, NDB Cluster.
* Commit grouping, gathering multiple transactions from multiple connections together to increase the number of commits per second.

The developers release minor updates of the MySQL Server approximately every two months. The sources can be obtained from MySQL's website or from MySQL's GitHub repository, both under the GPL license.

### Deployment

![LAMP\_software\_bundle.svg.png](resources/CBAB91152D125F5AE3AC3D57E031CFCB.png)

MySQL can be built and installed manually from source code, but it is more commonly installed from a binary package unless special customizations are required. On most Linux distributions, the package management system can download and install MySQL with minimal effort, though further configuration is often required to adjust security and optimization settings.

Though MySQL began as a low-end alternative to more powerful proprietary databases, it has gradually evolved to support higher-scale needs as well. It is still most commonly used in small to medium scale single-server deployments, either as a component in a LAMP-based Web application or as a standalone database server. (LAMP is Linux-Apache-MySQL-PHP.) Much of MySQL's appeal originates in its relative simplicity and ease of use, which is enabled by an ecosystem of open source tools such as [phpMyAdmin](https://www.phpmyadmin.net/). In the medium range, MySQL can be scaled by deploying it on more powerful hardware, such as a multi-processor server with gigabytes of memory.

There are however limits to how far performance can scale on a single server ('scaling up'), so on larger scales, multi-server MySQL ('scaling out') deployments are required to provide improved performance and reliability. A typical high-end configuration can include a powerful master database which handles data write operations and is replicated to multiple slaves that handle all read operations. The master server continually pushes binlog events to connected slaves so in the event of failure a slave can be promoted to become the new master, minimizing downtime. Further improvements in performance can be achieved by caching the results from database queries in memory using memcached, or breaking down a database into smaller chunks called shards which can be spread across a number of distributed server clusters.

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

```c
    mysql> **CREATE DATABASE southwind;**
    Query OK, 1 row affected (0.03 sec)

    mysql> **DROP DATABASE southwind;**
    Query OK, 0 rows affected (0.11 sec)

    mysql> **CREATE DATABASE IF NOT EXISTS southwind;**
    Query OK, 1 row affected (0.01 sec)

    mysql> **DROP DATABASE IF EXISTS southwind;**
    Query OK, 0 rows affected (0.00 sec)
```

Use the SQL `DROP` (and `DELETE`) commands with extreme care, as the deleted entities are irrecoverable. **THERE IS NO UNDO!!!**

SHOW CREATE DATABASE

The CREATE DATABASE commands uses some defaults. You can issue a "SHOW CREATE DATABASE databaseName" to display the full command and check these default values. We use `\G` (instead of ';') to display the results vertically. (Try comparing the outputs produced by ';' and `\G`.)
mysql> CREATE DATABASE IF NOT EXISTS southwind;

```c
mysql> SHOW CREATE DATABASE southwind \G
*************************** 1. row ***************************
       Database: southwind
Create Database: CREATE DATABASE `southwind` /*!40100 DEFAULT CHARACTER SET latin1 */
```

### Back-Quoted Identifiers (`name`)

Unquoted names or identifiers (such as database name, table name and column name) cannot contain blank and special characters, or clash with MySQL keywords (such as ORDER and DESC). You can include blanks and special characters or use MySQL keyword as identifier by enclosing it with a pair of back-quote, in the form of `name`. For robustness, the SHOW command back-quotes all the identifiers, as illustrated in the above example.

### Comments and Version Comments

MySQL multi-line comments are enclosed within /* and */; end-of-line comments begins with `--` (followed by a space) or `#`. The /*!40100 ...... */ is known as version comment, which will only be run if the server is at or above this version number 4.01.00. To check the version of your MySQL server, issue query "SELECT version()".

### Setting the Default Database - USE

The command "`USE *databaseName*`" sets a particular database as the default (or current) database. You can reference a table in the default database using `*tableName*` directly. But you need to use the fully-qualified *`databaseName.tableName`* to reference a table NOT in the default database.

In our example, we have a database named "`southwind`" with a table named "`products`". If we issue "`USE southwind`" to set `southwind` as the default database, we can simply call the table as "`products`". Otherwise, we need to reference the table as "`southwind.products`".

To display the current default database, issue command "`SELECT DATABASE()`".

### Creating and Deleting a Table - CREATE TABLE and DROP TABLE

You can create a new table *in the default database* using command "`CREATE TABLE *tableName*`" and "`DROP TABLE *tableName*`". You can also apply condition "`IF EXISTS`" or "`IF NOT EXISTS`". To create a table, you need to define all its columns, by providing the columns' *name*, *type*, and *attributes*.

Create a table "`products`" in the database "`southwind`".

-- Remove the database "southwind", if it exists. -- Beware that DROP (and DELETE) actions are irreversible and not recoverable!
    mysql> **DROP DATABASE IF EXISTS southwind;**
    Query OK, 1 rows affected (0.31 sec)

    -- Create the database "southwind"
    mysql> **CREATE DATABASE southwind;**
    Query OK, 1 row affected (0.01 sec)

    -- Show all the databases in the server -- to confirm that "southwind" database has been created.
    mysql> **SHOW DATABASES;**
    +--------------------+
    | Database           |
    +--------------------+
    | southwind          |
    | ......             |

    -- Set "southwind" as the default database so as to reference its table directly.
    mysql> **USE southwind;**
    Database changed

    -- Show the current (default) database
    mysql> **SELECT DATABASE();**
    +------------+
    | DATABASE() |
    +------------+
    | southwind  |
    +------------+

    -- Show all the tables in the current database. -- "southwind" has no table (empty set).
    mysql> **SHOW TABLES;**
    Empty set (0.00 sec)

    -- Create the table "products". Read "explanations" below for the column defintions
    mysql> **CREATE TABLE IF NOT EXISTS products ( productID INT UNSIGNED NOT NULL AUTO\_INCREMENT, productCode CHAR(3) NOT NULL DEFAULT '', name VARCHAR(30) NOT NULL DEFAULT '', quantity INT UNSIGNED NOT NULL DEFAULT 0, price DECIMAL(7,2) NOT NULL DEFAULT 99999.99, PRIMARY KEY (productID) );**
    Query OK, 0 rows affected (0.08 sec)

    -- Show all the tables to confirm that the "products" table has been created
    mysql> **SHOW TABLES;**
    +---------------------+
    | Tables_in_southwind |
    +---------------------+
    | products            |
    +---------------------+

    -- Describe the fields (columns) of the "products" table
    mysql> **DESCRIBE products;**
    +-------------+------------------+------+-----+------------+----------------+
    | Field       | Type             | Null | Key | Default    | Extra          |
    +-------------+------------------+------+-----+------------+----------------+
    | productID   | int(10) unsigned | NO   | PRI | NULL       | auto_increment |
    | productCode | char(3)          | NO   |     |            |                |
    | name        | varchar(30)      | NO   |     |            |                |
    | quantity    | int(10) unsigned | NO   |     | 0          |                |
    | price       | decimal(7,2)     | NO   |     | 99999.99   |                |
    +-------------+------------------+------+-----+------------+----------------+

    -- Show the complete CREATE TABLE statement used by MySQL to create this table
    mysql> **SHOW CREATE TABLE products \\G**
    *************************** 1. row ***************************
           Table: products
    Create Table: 
    CREATE TABLE `products` ( `productID` int(10) unsigned NOT NULL AUTO\_INCREMENT, `productCode` char(3) NOT NULL DEFAULT '', `name` varchar(30) NOT NULL DEFAULT '', `quantity` int(10) unsigned NOT NULL DEFAULT '0', `price` decimal(7,2) NOT NULL DEFAULT '99999.99', PRIMARY KEY (`productID`) ) ENGINE=InnoDB DEFAULT CHARSET=latin1

We define 5 columns in the table `products`:

`productID`, `productCode`, `name`, `quantity` and `price`. The types are:

* `productID` is` INT UNSIGNED `- non-negative integers.
* `productCode` is `CHAR(3)` - a fixed-length alphanumeric string of 3 characters.
* `name` is `VARCHAR(30)` - a variable-length string of up to 30 characters.
We use fixed-length string for `productCode`, as we assume that the `productCode` contains *exactly* 3 characters. On the other hand, we use variable-length string for `name`, as its length varies -`VARCHAR` is more efficient than `CHAR`.
* `quantity` is also `INT UNSIGNED` (non-negative integers).
* `price` is` DECIMAL(10,2) `- a decimal number with 2 decimal places.
`DECIMAL` is *precise* (represented as integer with a fix decimal point). On the other hand, `FLOAT` and `DOUBLE` (real numbers) are not precise and are approximated. `DECIMAL` type is recommended for currency.

The attribute "`NOT NULL`" specifies that the column cannot contain the `NULL` value. `NULL` is a special value indicating "no value", "unknown value" or "missing value". In our case, these columns shall have a proper value. We also set the default value of the columns. The column will take on its default value, if no value is specified during the record creation.

We set the column `productID` as the so-called *primary key*. Values of the primary-key column must be unique. Every table shall contain a primary key. This ensures that every row can be distinguished from other rows. You can specify a single column or a set of columns (e.g., `firstName` and `lastName`) as the primary key. An *index* is build automatically on the primary-key column to facilitate fast search. Primary key is also used as reference by other tables.

We set the column `productID` to `AUTO_INCREMENT`. with default starting value of 1\. When you insert a row with `NULL` (recommended) (or 0, or a missing value) for the `AUTO_INCREMENT` column, the maximum value of that column plus 1 would be inserted. You can also insert a valid value to an `AUTO_INCREMENT` column, bypassing the auto-increment.

### Inserting Rows - INSERT INTO

Let's fill up our "`products`" table with rows. We set the `productID` of the first record to 1001, and use `AUTO_INCREMENT` for the rest of records by inserting a `NULL`, or with a missing column value. Take note that strings must be enclosed with a pair of single quotes (or double quotes).

-- Insert a row with all the column values
    mysql> **INSERT INTO products VALUES (1001, 'PEN', 'Pen Red', 5000, 1.23);**
    Query OK, 1 row affected (0.04 sec)

    -- Insert multiple rows in one command -- Inserting NULL to the auto\_increment column results in max\_value + 1
    mysql> **INSERT INTO products VALUES (NULL, 'PEN', 'Pen Blue', 8000, 1.25), (NULL, 'PEN', 'Pen Black', 2000, 1.25);**
    Query OK, 2 rows affected (0.03 sec)
    Records: 2  Duplicates: 0  Warnings: 0

    -- Insert value to selected columns -- Missing value for the auto\_increment column also results in max\_value + 1
    mysql> **INSERT INTO products (productCode, name, quantity, price) VALUES ('PEC', 'Pencil 2B', 10000, 0.48), ('PEC', 'Pencil 2H', 8000, 0.49);**
    Query OK, 2 row affected (0.03 sec)

    -- Missing columns get their default values
    mysql> **INSERT INTO products (productCode, name) VALUES ('PEC', 'Pencil HB');**
    Query OK, 1 row affected (0.04 sec)

    -- 2nd column (productCode) is defined to be NOT NULL
    mysql> **INSERT INTO products values (NULL, NULL, NULL, NULL, NULL);**
    ERROR 1048 (23000): Column 'productCode' cannot be null

    -- Query the table
    mysql> **SELECT \* FROM products;**
    +-----------+-------------+-----------+----------+------------+
    | productID | productCode | name      | quantity | price      |
    +-----------+-------------+-----------+----------+------------+
    |      1001 | PEN         | Pen Red   |     5000 |       1.23 |
    |      1002 | PEN         | Pen Blue  |     8000 |       1.25 |
    |      1003 | PEN         | Pen Black |     2000 |       1.25 |
    |      1004 | PEC         | Pencil 2B |    10000 |       0.48 |
    |      1005 | PEC         | Pencil 2H |     8000 |       0.49 |
    |      1006 | PEC         | Pencil HB |        0 | 9999999.99 |
    +-----------+-------------+-----------+----------+------------+
    6 rows in set (0.02 sec)

    -- Remove the last row
    mysql> **DELETE FROM products WHERE productID = 1006;**

##### INSERT INTO Syntax

We can use the `INSERT INTO` statement to insert a new row with all the column values, using the following syntax:

INSERT INTO *tableName* VALUES (*firstColumnValue*, ..., *lastColumnValue*)  -- All columns

You need to list the values in the same order in which the columns are defined in the `CREATE TABLE`, separated by commas. For columns of string data type (`CHAR`, `VARCHAR`), enclosed the value with a pair of single quotes (or double quotes). For columns of numeric data type (`INT`, `DECIMAL`, `FLOAT`, `DOUBLE`), simply place the number.

You can also insert multiple rows in one `INSERT INTO` statement:

INSERT INTO *tableName* VALUES 
       (*row1FirstColumnValue*, ..., *row1lastColumnValue*),
       (*row2FirstColumnValue*, ..., *row2lastColumnValue*), 
       ...

To insert a row with values on selected columns only, use:

-- Insert single record with selected columns
    INSERT INTO *tableName* (*column1Name*, ..., *columnNName*) VALUES (*column1Value*, ..., *columnNValue*)
    -- Alternately, use SET to set the values
    INSERT INTO *tableName* SET *column1*=*value1*, *column2*=*value2*, ...

    -- Insert multiple records
    INSERT INTO *tableName* 
       (*column1Name*, ..., *columnNName*)
    VALUES 
       (*row1column1Value*, ..., *row2ColumnNValue*),
       (*row2column1Value*, ..., *row2ColumnNValue*),
       ...

The remaining columns will receive their default value, such as `AUTO_INCREMENT`, default, or `NULL`.

#### Querying the Database - SELECT

The most common, important and complex task is to query a database for a subset of data that meets your needs - with the `SELECT` command. The `SELECT` command has the following syntax:

-- List all the rows of the specified columns
    SELECT *column1Name*, *column2Name*, ... FROM *tableName*
     -- List all the rows of ALL columns, \* is a wildcard denoting all columns
    SELECT *\** FROM *tableName*
     -- List rows that meet the specified *criteria* in WHERE clause
    SELECT *column1Name*, *column2Name*,... FROM *tableName* WHERE *criteria*
    SELECT *\** FROM *tableName* WHERE *criteria*

Here are examples:

-- List all rows for the specified columns
    mysql> **SELECT name, price FROM products;**
    +-----------+-------+
    | name      | price |
    +-----------+-------+
    | Pen Red   |  1.23 |
    | Pen Blue  |  1.25 |
    | Pen Black |  1.25 |
    | Pencil 2B |  0.48 |
    | Pencil 2H |  0.49 |
    +-----------+-------+
    5 rows in set (0.00 sec)

    -- List all rows of ALL the columns. The wildcard \* denotes ALL columns
    mysql> **SELECT \* FROM products;**
    +-----------+-------------+-----------+----------+-------+
    | productID | productCode | name      | quantity | price |
    +-----------+-------------+-----------+----------+-------+
    |      1001 | PEN         | Pen Red   |     5000 |  1.23 |
    |      1002 | PEN         | Pen Blue  |     8000 |  1.25 |
    |      1003 | PEN         | Pen Black |     2000 |  1.25 |
    |      1004 | PEC         | Pencil 2B |    10000 |  0.48 |
    |      1005 | PEC         | Pencil 2H |     8000 |  0.49 |
    +-----------+-------------+-----------+----------+-------+
    5 rows in set (0.00 sec)

### SELECT without Table

You can also issue `SELECT` without a table. For example, you can `SELECT` an expression or evaluate a built-in function.

mysql> **SELECT 1+1;**
    +-----+
    | 1+1 |
    +-----+
    |   2 |
    +-----+
    1 row in set (0.00 sec)

    mysql> **SELECT NOW();**
    +---------------------+
    | NOW()               |
    +---------------------+
    | 2012-10-24 22:13:29 |
    +---------------------+
    1 row in set (0.00 sec)

    // Multiple columns
    mysql> **SELECT 1+1, NOW();**
    +-----+---------------------+
    | 1+1 | NOW()               |
    +-----+---------------------+
    |   2 | 2012-10-24 22:16:34 |
    +-----+---------------------+
    1 row in set (0.00 sec)

### Comparison Operators

For numbers (`INT`, `DECIMAL`, `FLOAT`), you could use comparison operators: `'='` (equal to), `'<>'` or `'!='` (not equal to), `'>'` (greater than), `'<'` (less than), `'>='` (greater than or equal to), `'<='` (less than or equal to), to compare two numbers. For example, `price > 1.0`, `quantity <= 500`.

mysql> SELECT name, price FROM products **WHERE price \< 1.0**;
    +-----------+-------+
    | name      | price |
    +-----------+-------+
    | Pencil 2B |  0.48 |
    | Pencil 2H |  0.49 |
    +-----------+-------+
    2 rows in set (0.00 sec)

    mysql> SELECT name, quantity FROM products **WHERE quantity \<= 2000**;
    +-----------+----------+
    | name      | quantity |
    +-----------+----------+
    | Pen Black |     2000 |
    +-----------+----------+
    1 row in set (0.00 sec)

CAUTION: Do not compare `FLOAT`s (real numbers) for equality (`'='` or `'<>'`), as they are not precise. On the other hand, `DECIMAL` are precise.

For strings, you could also use `'='`, `'<>'`, `'>'`, `'<'`, `'>='`, `'<='` to compare two strings (e.g., `productCode = 'PEC').` The ordering of string depends on the so-called *collation* chosen. For example,

mysql> SELECT name, price FROM products **WHERE productCode = 'PEN'**;
                                          -- String values are quoted
    +-----------+-------+
    | name      | price |
    +-----------+-------+
    | Pen Red   |  1.23 |
    | Pen Blue  |  1.25 |
    | Pen Black |  1.25 |
    +-----------+-------+
    3 rows in set (0.00 sec)

### String Pattern Matching - LIKE and NOT LIKE

For strings, in addition to full matching using operators like `'='` and `'<>'`, we can perform *pattern matching* using operator `LIKE` (or `NOT LIKE`) with wildcard characters. The wildcard `'_'` matches any single character; `'%'` matches any number of characters (including zero). For example,

* `'abc%'` matches strings beginning with `'abc'`;
* `'%xyz'` matches strings ending with `'xyz'`;
* `'%aaa%'` matches strings containing `'aaa'`;
* `'___'` matches strings containing exactly three characters; and
* `'a_b%'` matches strings beginning with `'a'`, followed by any single character, followed by `'b'`, followed by zero or more characters.

-- "name" begins with 'PENCIL'
    mysql> SELECT name, price FROM products **WHERE name LIKE 'PENCIL%'**;
    +-----------+-------+
    | name      | price |
    +-----------+-------+
    | Pencil 2B |  0.48 |
    | Pencil 2H |  0.49 |
    +-----------+-------+

    -- "name" begins with 'P', followed by any two characters, -- followed by space, followed by zero or more characters
    mysql> SELECT name, price FROM products **WHERE name LIKE 'P\_\_ %'**;
    +-----------+-------+
    | name      | price |
    +-----------+-------+
    | Pen Red   |  1.23 |
    | Pen Blue  |  1.25 |
    | Pen Black |  1.25 |
    +-----------+-------+

MySQL also support regular expression matching via the `REGEXE` operator.

### Arithmetic Operators

You can perform arithmetic operations on numeric fields using arithmetic operators, as tabulated below:

OperatorDescription+Addition-Subtraction\*Multiplication/DivisionDIVInteger Division%Modulus (Remainder)

### Logical Operators - AND, OR, NOT, XOR

You can combine multiple conditions with boolean operators `AND`, `OR`, `XOR`. You can also invert a condition using operator `NOT`. For examples,

mysql> SELECT * FROM products **WHERE quantity \>= 5000 AND name LIKE 'Pen %'**;
    +-----------+-------------+----------+----------+-------+
    | productID | productCode | name     | quantity | price |
    +-----------+-------------+----------+----------+-------+
    |      1001 | PEN         | Pen Red  |     5000 |  1.23 |
    |      1002 | PEN         | Pen Blue |     8000 |  1.25 |
    +-----------+-------------+----------+----------+-------+

    mysql> SELECT * FROM products **WHERE quantity \>= 5000 AND price \< 1.24 AND name LIKE 'Pen %'**;
    +-----------+-------------+---------+----------+-------+
    | productID | productCode | name    | quantity | price |
    +-----------+-------------+---------+----------+-------+
    |      1001 | PEN         | Pen Red |     5000 |  1.23 |
    +-----------+-------------+---------+----------+-------+

    mysql> SELECT * FROM products **WHERE NOT (quantity \>= 5000 AND name LIKE 'Pen %')**;
    +-----------+-------------+-----------+----------+-------+
    | productID | productCode | name      | quantity | price |
    +-----------+-------------+-----------+----------+-------+
    |      1003 | PEN         | Pen Black |     2000 |  1.25 |
    |      1004 | PEC         | Pencil 2B |    10000 |  0.48 |
    |      1005 | PEC         | Pencil 2H |     8000 |  0.49 |
    +-----------+-------------+-----------+----------+-------+

#### IN, NOT IN

You can select from members of a set with `IN` (or `NOT IN`) operator. This is easier and clearer than the equivalent `AND-OR` expression.

mysql> SELECT * FROM products **WHERE name IN ('Pen Red', 'Pen Black')**;
    +-----------+-------------+-----------+----------+-------+
    | productID | productCode | name      | quantity | price |
    +-----------+-------------+-----------+----------+-------+
    |      1001 | PEN         | Pen Red   |     5000 |  1.23 |
    |      1003 | PEN         | Pen Black |     2000 |  1.25 |
    +-----------+-------------+-----------+----------+-------+

#### BETWEEN, NOT BETWEEN

To check if the value is within a range, you could use `BETWEEN ... AND ...` operator. Again, this is easier and clearer than the equivalent `AND-OR` expression.

mysql> SELECT * FROM products 
           **WHERE (price BETWEEN 1.0 AND 2.0) AND (quantity BETWEEN 1000 AND 2000)**;
    +-----------+-------------+-----------+----------+-------+
    | productID | productCode | name      | quantity | price |
    +-----------+-------------+-----------+----------+-------+
    |      1003 | PEN         | Pen Black |     2000 |  1.25 |
    +-----------+-------------+-----------+----------+-------+

#### IS NULL, IS NOT NULL

`NULL` is a special value, which represent "no value", "missing value" or "unknown value". You can checking if a column contains `NULL` by `IS NULL` or `IS NOT NULL`. For example,

mysql> **SELECT \* FROM products WHERE productCode IS NULL**;
    Empty set (0.00 sec)

Using comparison operator (such as `=` or `<>`) to check for `NULL` is a *mistake* - a very *common mistake*. For example:

SELECT * FROM products WHERE productCode = NULL;
    -- This is a common mistake. NULL cannot be compared.