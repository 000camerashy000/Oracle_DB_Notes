
# Oracle DB Notes



## Course Link

[DevGym - Click Here to Take the course](https://devgym.oracle.com/pls/apex/dg/class/databases-for-developers-foundations.html)


## Chapters

- Tables
- Columns and Data Types
- Select and Where
- Joins
- Aggregates and Group By
- Insert and Commit
- Update and Transactions
- Delete and Truncate

## Notes

- ## Types of Tables in Oracle

1. A **heap-organized** table does not store rows in any particular order. The CREATE TABLE statement creates a heap-organized table by default.

2. An **index-organized** table orders rows according to the primary key values. For some applications, index-organized tables enhance performance and use disk space more efficiently.

3. An **external table** is a read-only table whose metadata is stored in the database but whose data is stored outside the database.

- ## Columns
A table definition is a table name and set of columns.

1. A column identifies an attribute of the entity described by the table. For example, the column ***employee_id*** in the ***employees table*** refers to the * *employee ID attribute of an employee entity.* *
2. In general, you give each column a **column name**, a **data type**, and a **width** when you create a table.

```
Example : CREATE TABLE employees( 
    employee_id    NUMBER(6), 
    first_name     VARCHAR2(20), 
    last_name      VARCHAR2(25)
    )
```
- ## Data Types
1. ### Character Data Type
Character data types store alphanumeric data in strings. The most common character data type is **VARCHAR2**
The **NCHAR** and **NVARCHAR2** data types store Unicode character data.

2. ### Numeric Data Type
The Oracle Database numeric data types store fixed and floating-point numbers, zero, and infinity. Some numeric types also store values that are the undefined result of an operation, which is known as "not a number" or NaN.

- NUMBER Data Type
The **NUMBER** data type stores fixed and floating-point numbers.
The **NUMBER** data type is recommended for most cases in which you must store numeric data.

You specify a fixed-point number in the form **NUMBER** *(p,s)* where *p* and *s* refer to the following 
**Precision** & **Scale**

3. ### Datetime Data Type
The datetime data types are **DATE** and **TIMESTAMP**

- **DATE**
The **DATE** data type stores date and time.

> Note : Dates fully support arithmetic operations, so you add to and subtract from dates just as you can with numbers.

> Oracle Database stores time in 24-hour format — HH:MI:SS

- **TIMESTAMP**
The **TIMESTAMP** data type is an extension of the DATE data type.
**TIMESTAMP** stores fractional seconds in addition to the information stored in the DATE data type. The **TIMESTAMP** data type is useful for storing precise time values, such as in applications that must track event order.

> The main advantage of data types **TIMESTAMP** it can store time-zone information in it.the value is adjusted to the time zone of the user session

- ## SELECT STATEMENT

**SELECT** statement or subquery to retrieve data from one or more tables
```
select * from table -- display everything from the specified table
```
```
select col1, col2 from table -- display the info stored in col1 & col2 columns only, from specified table
```
- ## WHERE STATEMENT

The **WHERE** condition lets you restrict the rows selected to those that satisfy one or more conditions.
> If you keep this clause empty, then the database returns all rows from the tables, in the FROM clause.

- ### List of some where conditions to use for filtering records
1. ***=*** - equal to
```
where a.col1 = 10
-- this clause would only show records which have '10' values inside it.
```
2. ***<>*** - not equal to
```
where a.col1 <> 10 
-- this clause would show every records but except the one's with '10' in it.
```
3. **and** - to combine many where function and give records after matching all conditions
```
where a.col1 = 10 and a.col2 = 20 
-- this clause would only show records which satisfy both the conditions.
```
4. **or** - to combine many where function but to give records if any one of the conditions is met
```
where a.col1 = 10 or a.col2 = 20 
-- this clause would show records which satisfy both the conditions or any one of them.
```
5. **in** (to use when filtering a certain list of values instead of repeatedly using or condition)
```
where a.col1 in (10,20,30,40)
-- this clause would show records which have 10 or 20 or 30 or 40 values in it.
```
6. **not in**
```
where a.col1 not in (10,20,30,40)
-- this clause would show records which does not contain 10 or 20 or 30 or 40 values in it.
```
7. **between** (in order to get records in specific range)
```
where a.col1 between 10 and 40
-- this clause would show records which have 10 or 20 or 30 or 40 values in it.
```
8. **like** ( _ [match any one character]  %[matches any number of character] wildcards to use to maximize like function)
```
where a.col1 like '_atch'
-- this clause would show records which matches with any one character followed by 'atch',
it can be Match or it can be Catch 
or it can be any numeric value to like 1atch, 2actch as long as there is a character present before the word 'atch' it would be displayed.
```
```
where a.col1 like '%atch'
-- this clause would show records which matches with any number of character(string or numeric) followed by 'atch'
```
9. **null** - for records with no value
```
where a.col1 is null
-- this clause would show records which have no values in it.
```
10. **not null** - to obtain records having any values of any datatype
```
where a.col1 is not null
-- this clause would show records which have some values in it.
```

- ## Joins
    - **Types of Joins**
    1. **Inner Join**
    - display only the records which have a match in both the table
    ```
    SQL Query

    select * from table1
    inner join table2 on table1.ID = table2.ID
    ```
    2. **Outer Join** -  display records from a table even if the match is not found in another table
    - *Left Join* - A left join includes all the rows from the left table and matching rows from the right table.
        ```
        SQL Query
        
        select * from table1
        left join table2 on table1.ID = table2.ID
        ```
    - *Right Join* -  A right join includes all the rows from the right table and matching rows from the left table.
        ```
        SQL Query
        
        select * from table1
        right join table2 on table1.ID = table2.ID
        ```
    3. **Full Outer Join**
    - A full outer join combines all the rows from both Table A and Table B.
    - It includes matching rows based on common values in the specified columns.
    - If there are no matches, NULL values are used to fill in the missing data from the non-matching side.
    ```
    SQL Query

    select * from table1
    full outer join table2 on table1.ID = table2.ID
    ```
- ## Aggregates and Group By
**GROUP BY** clause if you want the database to group the selected rows based on the value of expression for each row and return a single row of summary information (this information can be ***sum*** or ***average*** of all the grouped values or we can get ***minimum*** or ***maximum*** value from the group) for each group

> This clause contains **CUBE** or **ROLLUP** extensions

- **ROLLUP**
    - The **ROLLUP** function in SQL is used to generate a result set that represents the grand totals of a given query, as well as intermediate subtotals. It allows you to specify multiple levels of aggregation, creating a hierarchical structure in the result set. ROLLUP computes the subtotals and the grand total for each specified level of grouping.
- **CUBE**
    - The **CUBE** function in SQL is similar to ROLLUP but provides even more flexibility. It generates a result set that includes all possible combinations of the specified columns for aggregation


- ## Insert & Commit
Example Command to Enter Values inside your Table

**Single Row INSERT statement - Query to run when adding couple of information**
```
-- Suppose you have a Table Toys in which you want to enter information
INSERT INTO Toys (
    toy_name,
    colour,
    purchase_date,
    cost
) values (
    'Iron Man', 'Red', 10-08-2016, 800
)

## Please Make sure to enter the correct Values for respective column
```
**Multi-Row INSERT statement - Query to copy all the records from one table to another**
```
-- Suppose you have a Table new_toys
INSERT INTO new_toys ( select * from toys)

## if the user wants to enter the same information into multiple tables then we can select multiple tables into INSERT statement to enter the same values in multiple specified tables
```

**COMMIT**

Use the **COMMIT** statement to end your current transaction and make permanent all changes performed in the transaction.

Until you **COMMIT** a transaction:
- You can see any changes you have made during the transaction by querying the modified tables, but other users cannot see the changes. After you **COMMIT** the transaction, the changes are visible to other users' statements that execute after the commit.
- You can roll back (undo) any changes made during the transaction with the **ROLLBACK** statement
- Most of the SQL Clients have **Auto-Commit** functionality built-in which as the name suggest automatically **COMMIT** to the changes the user made, Please refer to the ***Preferences/Settings*** of your SQL Client to check which instances trigger auto-commit function

- ## Update & Transactions
**UPDATE**
- The **UPDATE** function in SQL is used to modify existing records in a database table.
- It allows you to change the values of one or more columns in one or multiple rows based on specified conditions. 
- UPDATE statements typically include a SET clause to specify the new values and a WHERE clause to determine which rows should be updated.

**Transactions**
- A transaction is a sequence of SQL statements that Oracle Database treats as a single unit. This statement also erases all savepoints in the transaction and releases transaction locks.

## Example of a Transaction in SQL using an Employee Table example

```
SET TRANSACTION NAME 'sal_update'; 

## This statement begins a transaction and names it sal_update
```
```
UPDATE employees 
    SET salary = 7000 
    WHERE last_name = 'Banda';

## This statement updates the salary for Banda to 7000.
```
```
SAVEPOINT after_banda_sal; 

## This statement creates a savepoint named after_banda_sal, enabling changes in this transaction to be rolled back to this point.
```
```
UPDATE employees
    SET salary = 12000 
    WHERE last_name = 'Greene';

## This statement updates the salary for Greene to 12000.
```
```
SAVEPOINT after_greene_sal; 

## This statement creates a savepoint named after_greene_sal, enabling changes in this transaction to be rolled back to this point.
```
```
ROLLBACK TO SAVEPOINT
    after_banda_sal;

## This statement rolls back the transaction to t3, undoing the update to Greene's salary at t4. The sal_update transaction has not ended.
```
```
UPDATE employees
    SET salary = 11000 
    WHERE last_name = 'Greene';

## This statement updates the salary for Greene to 11000 in transaction sal_update.
```
```
ROLLBACK;

## This statement rolls back all changes in transaction sal_update, ending the transaction.
```
```
SET TRANSACTION NAME 'sal_update2';

## This statement begins a new transaction in the session and names it sal_update2.
```
```
UPDATE employees
    SET salary = 7050 
    WHERE last_name = 'Banda';

UPDATE employees
    SET salary = 10950 
    WHERE last_name = 'Greene';

## This statements updates the salary for Banda to 7050 and Greene to 10950
```
```
COMMIT;

##This statement commits all changes made in transaction sal_update2, ending the transaction. The commit guarantees that the changes are saved in the online redo log files.
```
- ## Delete and Truncate
**DELETE**
- The DELETE function in SQL is used to remove one or more rows from a table based on specified conditions. 
- It allows you to selectively delete specific records that meet certain criteria using the WHERE clause. 
- The DELETE statement permanently removes data from the table, and the action can be rolled back if executed within a transaction.

**Truncate**
- The TRUNCATE function in SQL is used to remove all rows from a table, basically deleting all the data within it. Unlike the DELETE statement, which removes individual rows. 
- TRUNCATE provides a more effective way to remove all data from a table by deleting the space occupied by the table's data pages.
- TRUNCATE is a non-transactional operation, that is it cannot be rolled back. It quickly removes all data from a table without generating extensive transaction logs.
## Resources for Practising

 - [Live SQL - Practise Oracle SQL Online](https://livesql.oracle.com/apex/f?p=590:1000)
 - [Oracle Database - Run Oracle DB Locally](https://www.oracle.com/database/technologies/appdev/xe.html)
## FAQ

#### How much does this cost?

Nothing. Nada. Nil. Zilch. That's right, it's 100% FREE!

#### When does the course end?

The modules have no fixed end date. Once you're registered you can take open classes whenever you want

#### What will I learn on this course?

This course will teach you the basics of SQL and working with Oracle Database


## Authors

- [@000camerahy000](https://www.github.com/000camerahy000)

