# SQL Basics

---
## Data integrity
* It is used to restrict invalid data entering the tables.
#### Data integrity can be achieved in two ways.
1. Data types
2. Constraints
## Data types
* Data types are used to specify what type of data has to be stored in each column of the table

### The different type of datatypes
1. Numeric
2. Non-numeric
3. Dates

### 1. Numeric datatype
**Number datatype**
* Which is used to store numeric values for the selected columns of the table
>Syntax: Number(size/length)

**Number with precision datatype**
* Which is used to store numeric value along with the precision for the selected column of the table
>Syntax: number(size, precision)

### 2. Non-numeric datatype
**Char data type**
* It is fixed in size which is used to store only the characters or alphanumeric values for the specific columns of the table
>Syntax: char(size/length)

**Varchar/Varchar2 datatype**
* It is variable in size which is used to store only the character or alphanumeric values for the selected columns of the table
* Varchar data type can store up to 2000 values
* Varchar2 data type can store up to 4000 values
>Syntax: varchar/varchar2(size/length)

**Date datatype**
* It is a type of datatype which is used to store data type of date into selected columns of the table
* The default format of the date datatype is presented by DD-MM-YYYY

## Constraints
Constraints are used to restrict the invalid data entering into the table
1. Not null
2. Unique
3. Primary key
4. Foreign key
5. Check
6. Default

**Not null**
* It will ensure at least some value has to be present in the selected column of the table

Syntax:
```agsl
CREATE TABLE Student
(
ID int(6) NOT NULL,
NAME varchar(10) NOT NULL,
ADDRESS varchar(20)
);
```
```agsl
ALTER TABLE Emp modify Name Varchar(50) NOT NULL;
```


**Unique constraint**
* It will ensure that duplication of values are not allowed in the selected values of the column

Syntax:
```agsl
CREATE TABLE Student
(
ID int(6) NOT NULL UNIQUE,
NAME varchar(10),
ADDRESS varchar(20)
);
```
```agsl
ALTER TABLE Instructor ADD UNIQUE(ID);
```
**Primary key**
* Primary key is a combination of unique and not null constraints
* Primary key is used to identify records uniquely
* Creating a primary key is not mandatory but it’s highly recommended to create
* only one primary key is allowed in the single table
* The columns which are eligible to become as primary key is called candidate key
* The column which are eligible to become as a primary key columns but not chosen as primary key Is called alternative key
```agsl
CREATE TABLE Student
(
ID int(6) NOT NULL UNIQUE,
NAME varchar(10),
ADDRESS varchar(20),
PRIMARY KEY(ID)
);
```
```agsl
Alter Table Person add Primary Key(Id, Name);
ALTER table Person DROP PRIMARY KEY;
```
**Check**
* Whenever costumer asked for additional validation in the requirement then we make use of check constraints

Syntax:
```agsl
CREATE TABLE Student
(
ID int(6) NOT NULL,
NAME varchar(10) NOT NULL,
AGE int NOT NULL CHECK (AGE >= 18)
);
```
**Create domain**
* A domain is essentially a data type with optional constraints (restrictions on the allowed set of values).

Example:
```agsl
CREATE DOMAIN CPI_DATA AS REAL CHECK
(value >= 0 AND value <= 10);
```
Create table using domain
```agsl
CREATE TABLE student(
sid char(9) PRIMARY KEY,
name varchar(30),
cpi CPI_DATA
);
```

**Foreign key**
* It Is also called as referential integrity constraint
* Used to create relationship between the tables
* To create relationship between the table the common column has to be present in both the tables
* More than one foreign key is allowed in single table
*  Foreign key will accept duplication and null values

Syntax:
```agsl
CREATE TABLE Orders
(
O_ID int NOT NULL,
ORDER_NO int NOT NULL,
C_ID int,
PRIMARY KEY (O_ID),
FOREIGN KEY (C_ID) REFERENCES Customers(C_ID)
)
```
**Default**
* This constraint is used to provide a default value for the fields.
* That is, if at the time of entering new records in the table if the user does not specify any value for these fields then the default value will be assigned to them. 

Syntax:
```agsl
CREATE TABLE Student
(
ID int(6) NOT NULL,
NAME varchar(10) NOT NULL,
AGE int DEFAULT 18
);
```
```agsl
ALTER TABLE tablename ALTER COLUMN columnname DROP DEFAULT;
```
## SQL COMMENTS
**1. Single line comment**
* Comments starting and ending in a single line are considered single-line comments.

Syntax:
```agsl
-- single line comment
```
**2. Multiline comment**
* Comments starting in one line and ending in different lines are considered as multi-line comments. 

Syntax:
```agsl
/* multi line comment
another comment */
```
**3. In-line comments**
* In-line comments are an extension of multi-line comments, comments can be stated in between the statements and are enclosed in between ‘/*’ and ‘*/’. 

Syntax:
```agsl
SELECT * FROM /* Customers; */
```
## Aliases
* Aliases are the temporary names given to tables or columns for the purpose of a particular SQL query.

Syntax:
```agsl
SELECT column as alias_name FROM table_name;
```
Example:
Advantages of SQL Alias
1. It is useful when you use the function in the query.
2. It can also allow us to combine two or more columns.
3. It is also useful when the column names are big or not readable.
4. It is used to combine two or more columns.


**SQL common Commands**
* **SHOW USER** : this command is used to know which user has been logged in to the database
* **CL SCR /Clear Screen** : this command is used to clear the entire scree of the page
* **CONN/ Connect** : this command is used to switch from one user to another without existing from the page
* **SELECT * FROM TAB**; : this command is used to know the list of tables present in the database
* **DESC TABLE_NAME** : used to know the structure of the table