In the late 1960s, Edgar Codd developed the relational database model, which featured minimal redundancy and an easily understood structure and superseded hierarchical and network databases. The SQL language was developed to operate on relational databases.  

SQL stands for Structured Query Language. SQL lets you access and manipulate databases. It is an ANSI (American National Standards Institute) standard. Although SQL is an ANSI (American National Standards Institute) standard, there are different versions of the SQL language. However, to be compliant with the ANSI standard, they all support at least the major commands (such as SELECT, UPDATE, DELETE, INSERT, WHERE) in a similar manner.

(What exactly is a database? A database is a self-describing collection of integrated records, where a record is a representation of some physical or conceptual object. Each record has multiple attributes, such as name, address, and telephone number. Individual names, addresses, etc., are the data. A database consists of both data and metadata. Metadata is the data that describes the data’s structure within a database. If you know how your
data is arranged, then you can retrieve it. Because the database contains a description of its own structure, it’s self-describing. The database is integrated because it includes not only data items but also the relationships among data items. The database stores metadata in an area called the data dictionary, which describes the tables, columns, indexes, constraints, and other items that make up the database.) (What is a database management system? A database management system, or DBMS, is a set of programs used to define, administer, and process databases and their associated applications. Database management systems that run on platforms of multiple classes, large and small, are called "scalable" systems.)

### What Can SQL do?

* SQL can execute queries against a database
* SQL can retrieve data from a database
* SQL can insert records in a database
* SQL can update records in a database
* SQL can delete records from a database
* SQL can create new databases
* SQL can create new tables in a database
* SQL can create stored procedures in a database
* SQL can create views in a database
* SQL can set permissions on tables, procedures, and views

To build a Web site that shows data from a database, you will need:

* An RDBMS database program (i.e. MS Access, SQL Server, MySQL)
* To use a server-side scripting language, like PHP or ASP
* To use SQL to get the data you want
* To use HTML/CSS

RDBMS stands for Relational Database Management System. RDBMS is the basis for SQL, and for all modern database systems such as MS SQL Server, IBM DB2, Oracle, MySQL, and Microsoft Access.

The data in RDBMS is stored in database objects called tables, a table being a collection of related data entries and it consists of columns and rows.

### Database Tables

A database most often contains one or more tables. Each table is identified by a name, and tables contain records (rows) with data.

### Key SQL Commands

* **SELECT** - extracts data from a database
* **UPDATE** - updates data in a database
* **DELETE** - deletes data from a database
* **INSERT INTO** - inserts new data into a database
* **CREATE DATABASE** - creates a new database
* **ALTER DATABASE** - modifies a database
* **CREATE TABLE** - creates a new table
* **ALTER TABLE** - modifies a table
* **DROP TABLE** - deletes a table
* **CREATE INDEX** - creates an index (search key)
* **DROP INDEX** - deletes an index

_A note on SQL syntax_: SQL is NOT case sensitive: select is the same as SELECT. The semicolon is the standard way to separate each SQL statement in database systems that allow more than one SQL statement to be executed in the same call to the server; some database systems require a semicolon at the end of each SQL statement.

### The SQL SELECT Statement

The SELECT statement is used to select data from a database. The result is stored in a result table, called the result-set.

```c
SELECT column_name,column_name
FROM table_name;
```

and

```c
SELECT * FROM table_name;
```

The following SQL statement selects the “Author" and “Title" columns from a table called “Books”:

```c
SELECT Author,Title FROM Books;
```

The following SQL statement selects all the columns from the “Books" table:

```c
SELECT * FROM Books;
```

(Most database software systems allow navigation in the result-set with programming functions, like: Move-To-First-Record, Get-Record-Content, Move-To-Next-Record, etc.)

#### An Exemplar Database, aka "Books"

| Item | Author | Title | Publisher | Date | Place
|--------|-------|-----------|------|-------
|1|Hemingway, Ernest |The Sun Also Rises |Scribner |1926 |New York |
|2|Thoreau, Henry David |Walden; Or, Life in the Woods |Ticknor and Fields |1854 |Boston |
|3|Tunis, John |The Kid from Tomkinsville |Harcourt Brace |1940 |New York |
|4|Watata, Arnold | Aberrant Behavior among Archivists|Anonymous | 1999|

### ….. And Variants

#### The SQL SELECT DISTINCT Statement

In a table, a column may contain many duplicate values; and sometimes you only want to list the different (distinct) values.

The DISTINCT keyword can be used to return only distinct (different) values.

```c
SELECT DISTINCT column_name,column_name
FROM table_name;
```

```c
SELECT DISTINCT Place FROM Books;
```

### SQL WHERE Clause

The WHERE clause is used to extract only those records that fulfill a specified criterion.

```c
SELECT *column\_name*,*column\_name*
FROM *table\_name*
WHERE *column\_name operator value*;
```

```c
SELECT * FROM Books
WHERE Place='Boston';
```

#### Text Fields vs. Numeric Fields

SQL requires single quotes around text values (most database systems will also allow double quotes). However, numeric fields should not be enclosed in quotes:

```c
SELECT * FROM Books
WHERE Item=2;
```