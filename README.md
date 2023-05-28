
# Oracle DB Notes



## Course Link

[DevGym - Click Here to Take the course](https://devgym.oracle.com/pls/apex/dg/class/databases-for-developers-foundations.html)


## Chapters

- Tables
- Columns and Data Types
- Data Modeling
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

- DATE
The **DATE** data type stores date and time.

> Note : Dates fully support arithmetic operations, so you add to and subtract from dates just as you can with numbers.

4. ### TIMESTAMP Data Type
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

