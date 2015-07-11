# SQLite
## Objective
Students will learn what databases are and get an intro on using SQLite in Android applications.
## Overview
### What's a database? (do slides)
Data stored in computers is basically in the form of files.  If just using "files", you need to define the data organization structure yourself.  Formats like XML and JSON define some structure for you, but you still need to manage storing and retrieving data.  Databases generally provide services that let you store and retrieve data, in a safe manner.  They also generally provide a way to search data, and in the case of standard relational databases, structured schemas.
### Relational Database (aka SQL)
When we say "database", we often mean a relational database, which is also often referred to as a SQL database.  Just remember "database" and "SQL" are probably referring to the same thing.  Relational db is a set of structured tables that may relate to each other.
### Tables
Each table represents an "entity" type, and the columns are attributes related to that entity.  Think Product, Customer, and Order.
### Relating tables
Each table generally has a unique id associated with each row.  If one table relates to another, it can hold a reference to that other table row.
(Slies.  Example with one table split into two)
### Data access
Pretty much all databases have specialized data access functions or languages.  For relational DBs, this is almost always SQL.  Structured Query Language.  Its specific to databases, and defines searching and modifying data in a DB.
We're not doing much SQL, but you should learn some on your own.  You'll run into it a lot.

### Create/Modify Statements

You create/modify/reove tables with a special part of SQL called DDL: Data Definition Language.  There's a lot in this topic, but you should know about:

1. CREATE
2. ALTER
3. DROP

#### CREATE

Use create to make tables (and other things like indexes, views).

```SQL
CREATE TABLE [table name] ( [column definitions] ) [table parameters]
```

```SQL
CREATE TABLE employees (
    id            INTEGER      PRIMARY KEY,
    first_name    VARCHAR(50) not null,
    last_name     VARCHAR(75) not null,
    fname         VARCHAR(50) not null,
    dateofbirth   DATE         null
);
```

#### ALTER

Add, mod, drop table columns.  Some other stuff.  A little beyond today's discussion.

#### DROP

Remove stuff.

### Insert/Update

SQL provides a few operations to actually manage your data.

#### INSERT

There are a few variations of INSERT, but the most common inserts a row into a table.

```SQL
INSERT INTO table (column1 [, column2, column3 ... ]) VALUES (value1 [, value2, value3 ... ])
```

You have INSERT INTO, the table, the colums that you're inserting into, then the values.  This adds a row (assuming it doesn't have an error).

#### UPDATE

Update modifies existing data.  General UPDATE statement

```SQL
UPDATE table_name SET column_name = value [, column_name = value ...] [WHERE condition]
```

Specify UPDATE, table name, the list of columns and the value to set them to, then the WHERE clause.  The WHERE clause is used in both UPDATE and SELECT to figure out which rows to set the values on.  If no WHERE clause, the update modifies all rows.

#### DELETE

Remove rows from the table that match the WHERE clause

```SQL
DELETE FROM table_name [WHERE condition];
```

#### Query

SQL databases are highly tuned to allow you to select data quickly.  Use the SELECT keyword to select data.

Basic selects are simple, but the full power of select is really complicated:

```SQL
SELECT [ALL | DISTINCT] column1[,column2] FROM table1[,table2] [WHERE "conditions"] [GROUP BY "column-list"] [HAVING "conditions] [ORDER BY "column-list" [ASC | DESC] ]
```

For our purposes, you'll need to know about specifying columns, use the WHERE clause, and using the ORDER BY clause.

You can specify either specific columns, or the wildcard '*', which will select all columns.  WHERE is the same as UPDATE and DELETE.  ORDER BY lets you specify how the output data is sorted.  You can load all of your data into memory and then sort, but sorting in the database is going to be a lot faster in every imaginable scenario.

#### WHERE

Where is important to understand.  It lets you specify what rows are involved in your query or UPDATE/DELETE statements.  

* =	Equal
* <> Not equal.  Sometimes written as !=
* > Greater than
* < Less than
* >= Greater than or equal
* <= Less than or equal
* BETWEEN Between an inclusive range
* LIKE Search for a pattern
* IN

Clauses can be combined with AND and OR, and can be nested in parenthesis.  They can get super complicated.

Your data will often represent specific entities, so you'll be sticking mostly with looking for singular values by id, or displaying a full list.  However, as you build more complex apps, you'll be using write more complex select, update, and delete statements.

Some basics

[http://www.w3schools.com/sql/trysql.asp?filename=trysql_select_all](http://www.w3schools.com/sql/trysql.asp?filename=trysql_select_all)

[http://www.w3schools.com/sql/](http://www.w3schools.com/sql/)

[http://www.sqlcourse.com/](http://www.sqlcourse.com/)

## Do Now (Morning-ish)
Run these basic operations in the Sql [test window](http://www.w3schools.com/sql/trysql.asp?filename=trysql_select_all):

1. Select all Customers
2. Select all Orders
3. Select all OrderDetails
4. Select OrderDetails where quantity is greater or equal to 10
5. Add a customer
6. Change that customer's name
7. Delete your new customer

## Foreign tables and joins

This is relatively complex for today, but related tables can be joined together on queries.  When working with data for an app, you often query these individually, but sql lets you do some pretty heavy query optimization.

Join Customers, Orders, OrderDetails, and Products for a report.

## SQLite on Android

SQLite is a small SQL database that provides the basic features of the bigger server counterparts, but in a smaller package.  Used in many environments.  Comes built into Android.

Android provides custom objects that facilitate interacting with and maintaining your database.

### Selecting by ID

### Querying by comparison

### Cursors

## Exercises

Clone example app: [https://github.com/kpgalligan/BasicSQLite](https://github.com/kpgalligan/BasicSQLite)
Take the Step 2 branch, and add an address field to the database.  Insert that data, then show it in the list.  Some hints.  The values that show up in the list are in the Person class' 'toString' method.  If you get that done, remove the delete/insert calls from the BasicDbTask and create a form that will let you add fields to the db by typing them in.

## Development Strategies
### Raw SQL

Our examples so far are raw SQL.  Lots of projects do this, and Google generally recommends it, but there's a lot of boilerplate code involved.  Not a fan.

### ORM Framework

Object Relational Manager.  Maps tables to classes, basically.  These are used pretty heavily, as they reduce boilerplate and make development faster and less error prone.  However, lots of the industry disagrees with the benefits, and consider the performance overhead to be too much.  Lots of opinions here.

1. OrmLite - One of the early ones.  I did the port work for Android's portion.  Lots of functionality.  Performance could improve, but is generally fine (working on that).
2. GreenDAO - Code is generated.  Faster.  Not a natural map for OOP.  Not a fan.
3. ActiveAndroid
4. SquiDB
5. Other DB's - Realm, others?
 
#### Quick ORMLite Example

Move to branch "Step3...".  Changes:

1. Base class for DB helper is OrmLiteSqliteOpenHelper
2. Person class modified a bit and added OrmLite annotations
3. Table created with utility.  Removed all the native SQL.

### Exercises

#### Modify ORM Data

1. Add a description field to the Person class.  Make sure it also has the DatabaseField annotation, and increment the version number in MySQLiteOpenHelper.
2. Add an Address class and table.  Connect it to the Person table by adding an int personId field.  Modify the insertData method to also take address data, and create the address records.
3. Show addresses in a list.

With class, walk through chagnes, and demo foreign mapping.

### Final Exercise

Clone the calculator app, and keep a history of results.  Start with one you worked on, or clone this:

https://github.com/jaellysbales/scientific-calculator/tree/master/ScientificCalculator

In my demo, the stored answer list is shown by long-pressing equals.  Clicking on a stored value inserts it as the current euquation.

## Exit Ticket  
Please complete the exit ticket [here](https://docs.google.com/forms/d/12jvJtywjkGzFxLZJBlSXu2L4Wwhe4hzTS1fuoimpYAI/viewform?usp=send_form).
