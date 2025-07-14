# 💬 SQL Statements
---
### 📘 What is an SQL Statement?

An **SQL statement** is a **command** used to perform operations on data in a **relational database** using **Structured Query Language (SQL)**.

You can use SQL to:
- 🔍 Retrieve data
- ➕ Insert data
- 📝 Update or delete data
- 🛠️ Manage tables and users
---
## 🔍 DQL (Data Query Language) statement

### 📘 What is DQL?

**DQL** stands for **Data Query Language**.  
It is a subset of SQL that focuses **only on retrieving data** from a database.

Unlike other SQL categories, DQL **does not change the structure or data** — it just **queries** and fetches the results.

### ✅ Main Purpose of DQL

- To **fetch data** from one or more tables.
- To **filter, sort, and group** queried data.
- To use **conditions** to extract meaningful information.

#### 🧾 Basic Syntax of `SELECT`

```roomsql
SELECT column1, column2 FROM table_name WHERE condition;
```
| Task                    | SQL Example                                                 |
|-------------------------|-------------------------------------------------------------|
| Select all columns      | `SELECT * FROM employees;`                                  |
| Select specific columns | `SELECT name, age FROM employees;`                          |
| Use WHERE condition     | `SELECT * FROM employees WHERE age > 30;`                   |
| Sorting results         | `SELECT * FROM employees ORDER BY age DESC;`                |
| Filtering with LIKE     | `SELECT * FROM employees WHERE name LIKE 'A%';`             |
| Limiting rows (MySQL)   | `SELECT * FROM employees LIMIT 5;`                          |
| Counting rows           | `SELECT COUNT(*) FROM employees WHERE department = 'HR';`   |
---
## 🏗️ DDL (Data Definition Language) Statement

### 📘 What is DDL?

**DDL** stands for **Data Definition Language**.  
It includes SQL statements used to **define, modify, or delete the structure** of database objects like **tables**, **schemas**, **views**, and **indexes**.

### 🧱 Purpose of DDL

- Create and remove **tables**, **databases**, and **schemas**
- Alter table structures (add/remove columns, change data types)
- Delete objects completely

### 📌 Key DDL Statements

| Statement   | Purpose                                              |
|-------------|------------------------------------------------------|
| `CREATE`    | Create a new table, database, or object              |
| `ALTER`     | Modify the structure of an existing object           |
| `DROP`      | Delete an object permanently                         |
| `TRUNCATE`  | Delete all rows from a table (fast and irreversible) |
| `RENAME`    | Rename a table or column                             |

## 🔧 DDL Statement Examples

#### 🏗️ CREATE TABLE
```roomsql
CREATE TABLE students (
  id INT PRIMARY KEY,
  name VARCHAR(100),
  age INT
);
```
#### 🛠️ ALTER TABLE
```roomsql
ALTER TABLE students ADD email VARCHAR(100);
```
#### 🗑️ DROP TABLE
```roomsql
ALTER TABLE students ADD email VARCHAR(100);
```
#### 🔄 RENAME TABLE
```roomsql
RENAME TABLE students TO learners;
```
#### 🧹 TRUNCATE TABLE
```roomsql
TRUNCATE TABLE learners;
```

> ⚠️ **DDL is Auto-Committed**
>
> - DDL operations like `CREATE`, `ALTER`, `DROP`, and `TRUNCATE` are **auto-committed**.
> - That means once executed, **changes are saved immediately** to the database.
> - ❌ You **cannot ROLLBACK** a DDL statement — the changes are permanent.


| DDL Command | Action                              |
|-------------|-------------------------------------|
| `CREATE`    | Defines a new object                |
| `ALTER`     | Modifies existing structure         |
| `DROP`      | Deletes the object permanently      |
| `TRUNCATE`  | Removes all data, retains structure |
| `RENAME`    | Renames tables or columns           |
---

## 📝 DML (Data Manipulation Language) in SQL

### 📘 What is DML?

**DML** stands for **Data Manipulation Language** — a category of SQL statements used to **insert**, **update**, **delete**, and **retrieve** data in existing database tables.

These operations allow users to **manipulate the contents** of a database **without altering its structure**.

### 🧾 Key DML Commands

| Command   | Purpose                               |
|-----------|---------------------------------------|
| `INSERT`  | Add new records (rows) to a table     |
| `UPDATE`  | Modify existing records               |
| `DELETE`  | Remove records from a table           |

### 🔧 DML Command Examples

#### ➕ INSERT
```roomsql
INSERT INTO employees (id, name, department)
VALUES (1, 'Alice', 'HR');
```
#### 🛠️ UPDATE
```roomsql
UPDATE employees
SET department = 'Finance'
WHERE id = 1;
```
#### ❌ DELETE
```roomsql
DELETE FROM employees
WHERE id = 1;
```
> ⚠️ **DML is not Auto-Committed**
>
> DML statements are not auto-committed by default. You must manually.
```roomsql
  COMMIT;   -- Save the changes
  ROLLBACK; -- Undo the changes
```
| DML Command | Description                |
|-------------|----------------------------|
| `UPDATE`    | Changes existing data      |
| `DELETE`    | Removes data from a table  |
| `SELECT`    | (Sometimes DQL) Reads data |
---

## 🔄 DTL Statement(Data Transaction Language) — Also Known as TCL (Transaction Control Language)

### 📘 What is DTL/TCL?

**DTL** (more commonly known as **TCL — Transaction Control Language**) is a subset of SQL used to **manage database transactions** and ensure **data integrity** during multi-step operations.

It allows you to **commit**, **rollback**, and **control savepoints** in transactions.

### 🧾 Key DTL / TCL Commands

| Command             | Description                                              |
|---------------------|----------------------------------------------------------|
| `COMMIT`            | Saves all changes made in the current transaction        |
| `ROLLBACK`          | Undoes all changes made in the current transaction       |
| `SAVEPOINT`         | Sets a checkpoint in a transaction to partially rollback |
| `RELEASE SAVEPOINT` | Deletes a savepoint (optional and DBMS-specific)         |
| `SET TRANSACTION`   | Sets isolation level or properties for a transaction     |

## 🔧 Command Examples

#### ✅ COMMIT
```roomsql
UPDATE employees SET salary = salary + 1000 WHERE department = 'IT';
COMMIT;
```
#### ❌ ROLLBACK
```roomsql
DELETE FROM employees WHERE department = 'HR';
ROLLBACK;
```
#### 🏁 SAVEPOINT and ROLLBACK TO
```roomsql
SAVEPOINT before_delete;
DELETE FROM employees WHERE age > 60;
ROLLBACK TO before_delete;
```
| DTL Command       | Function                                  |
|-------------------|-------------------------------------------|
| `COMMIT`          | Finalizes and saves all changes           |
| `ROLLBACK`        | Reverts all changes since last COMMIT     |
| `SAVEPOINT`       | Creates a rollback point in a transaction |
| `ROLLBACK TO`     | Reverts to a specific savepoint           |
| `SET TRANSACTION` | Sets isolation level (optional use)       |
---

## 🔐 DCL Statement(Data Control Language) in SQL

### 📘 What is DCL?

**DCL (Data Control Language)** is a subset of SQL used to **control access, permissions, and privileges** on database objects like tables, views, procedures, and schemas.

It is used by database administrators to **grant or revoke rights** to users and roles.

### 🧾 Key DCL Commands

| Command   | Description                                         |
|-----------|-----------------------------------------------------|
| `GRANT`   | Gives specific privileges to users or roles         |
| `REVOKE`  | Removes previously granted privileges               |

> ⚠️ Note: DCL statements may also depend on the DBMS and user access level.

### 🔧 DCL Command Syntax & Examples

#### ✅ GRANT

```roomsql
GRANT SELECT, INSERT ON employees TO vedant;
```
#### ❌ REVOKE
```roomsql
REVOKE INSERT ON employees FROM vedant;
```
| Privilege   | Description                        |
|-------------|------------------------------------|
| `SELECT`    | Permission to query data           |
| `INSERT`    | Permission to add new records      |
| `UPDATE`    | Permission to modify data          |
| `DELETE`    | Permission to remove records       |
| `EXECUTE`   | Run stored procedures or functions |
| `ALL`       | All of the above privileges        |

---

## DQL(data query language)
* DQL statements are used to fetch or retrieve the data based on the query we passed in database.
#### SELECT
>Syntax
> 
>SELECT * /DISTINCT COLUMN_NAME OR DISTINCT(COLUMN_NAME)/EXPRESSION(ALIAS_NAME) FROM TABLE_NAME

**DISTINCT KEYWORD**
* It is helpful when there is a need to avoid duplicate values present in any specific columns/table.
```agsl
SELECT DISTINCT * FROM Table_name;
```

## DDL(data definition language)
* Data definition language actually used to define the database schema and structure of the table
* DDL is a set of SQL commands used to create, modify, and delete database structures but not data.
#### CREATE
* This command is used to create the database or its objects (like table, index, function, views, store procedure, and triggers).
>Syntax
> 
>CREATE DATABASE DATABSE_NAME;
```agsl
CREATE VIEW VIEW_NAME;
CREATE TABLE TABLE_NAME(COLUMN1 datatype(size) constraints, COLUMN2 datatype(size) constraints);
```
Q) create the tables Products and Orders Products Productid(pk) ProductName(not null) qty(check) Description Orders Productid(fk from product)OrderID(pk) Qty_sold(check>0) price order_DT
```agsl
CREATE TABLE PRODUCTS(ProductID Number(4) Primary key,ProductName varchar(10) Not Null,QTY Number(3) check(Qty>0),Description varchar(20));
CREATE TABLE Orders(ProductID Number(4) reference products(productID),OrderID number(4) Primary key,QTY_sold Number(5) check(Qty_sold>0),price Number(5),ORDERDT date);
```
Q)create table from another table
```agsl
CREATE TABELE DEMO AS SELECT * FROM EMP
```
#### ALTER
* This is used to alter the structure of the database and there objects.
* This command is used to change the structure of the table I.e adding column, Removing column and renaming colmn
>Syntax : To add column
> 
>ALTER TABLE TABLE_NAME ADD COLUMN_NAME datatype(size);

>Syntax: To rename a column
> 
>ALTER TABLE TABLE_NAME RENAME COLUMN COLUMN_NAME TO NEW_COLUMN_NAME;

>Syntax: to drop a column
> 
>ALTER TABLE TABLE_NAME DROP COLUMN COLUMN_NAME;
>ALTER TABLE TABLE_NAME DROP COLUMN (COLUMN1,COLUMN2);

#### RENAME
* This is used to rename an object existing in the database.
>Syntax
> 
>RENAME TABLE_NAME TO NEW_TABLE_NAME;

#### TRUNCATE
* This is used to remove all records from a table, including all spaces allocated for the records are removed.
* Used to remove all the records permanently but structure of the table is remains same
>Syntax
> 
>TRUNCATE TABLE TABLE_NAME;

#### DROP
* This command is used to delete objects from the database.
* This statement is used to remove both structure and data from the table.
>Syntax
> 
>DROP TABLE TABLE_NAME

>[!Note]
> 
>Oracle using recycle bin even though table is dropped we can restore back using flashback and drop permanently using  purge command
>
>FLASHBACK TABLE TABLE_NAME TO BEFORE_DROP;
> 
>PURGE TABLE TABLE_NAME;

## DML(Data Manipulation language)
* It is the component of the SQL statement that controls access to data and to the database.
* DML commands are not auto committed it means changes made are not permanent to database it can be rolled back

#### Insert
* This command is used to insert the data into a table
>Synatx :
> 
>INSERT INTO TABLE_NAME VALUES(V1,V2…);
>OR
>INSERT INTO TABLE_NAME (COLUMN1,COLUMN2..) VALUES(V1,V2,….);

#### Delete
* Delete statement is used to delete the data from table
* We can also use to delete the particular row based on where clause
* Even after deleting the table the structure of the table is there
* The table can be restored after deletion
>Syntax:
>
> DELETE FROM TABLE_NAME WHERE COLUMN_NAME=VALUE;
>DELETE FROM TABLE_NAME;

#### Update
* Update command is used to update one or more records from the table
>Syntax
>  
>UPDATE TABLE_NAME SET COLUMN_NAME=VALUE WHERE CONDITION

| DELETE COMMAND                                                 | 	TRUNCATE COMMAND                                                 |
|----------------------------------------------------------------|-------------------------------------------------------------------|
| IS DML command                                                 | 	Is a DDL command                                                 |
| We can use where clause in delete                              | 	We can’t use where clause                                        |
| We can use to delete particular row and all the row from table | 	Truncate statement is used to remove all the records permanently |
| Delete statement is slower than Truncate command               | 	Truncate is faster than delete command                           |
| We can restore the data back                                   | 	We can’t restore the data back                                   |

## TCL(Transaction control language) OR DTL(data transaction language)
* These commands are used to control the DML changes
* DML change on the table is not permanent one we need to save in order to make it as permanent
* We can undo(ignore) the same DML changes on a table

#### ROLLBACK
* It will undo the DML changes performed on the table
>Synatax:
> 
>ROLLBACK;
>COMMIT

It will save the DML changes permanently
>Syntax:
> 
>COMMIT;
>SAVEPOINT

From the point of save point we can Undo the changes of DML instead of whole changes
>Syntax:
> 
>SAVEPOINT SAVEPOINT_NAME;
> 
>ROLLBACK TO SAVEPOINT SAVE_POINT_NAME;

## DCL(Data control language)
* Commands or statements are used to control the access and permission of the table

#### GRANT
* The statement is used to provide the access permission to the different user.
>Syntax:
> 
>GRANT SELECT/UPDATE ON TABLE_NAME TO USER_NAME,….;


#### REVOKE
* This command is used to take back the given permission
>Syntax:
> 
>REVOKE SELECT/UPDATE ON TABLE_NAME FROM USER_NAME,…;

#### Merge statement
* The MERGE command in SQL is actually a combination of three SQL statements: INSERT, UPDATE and DELETE.
Syntax:

```roomsql
//.....syntax of MERGE statement....//

//you can use any other name in place of target
MERGE target_table_name AS TARGET

//you can use any other name in place of source
USING source_table_name AS SOURCE   
ON condition (for matching source and target table)
WHEN MATCHED (another condition for updation)

//now use update statement syntax accordingly
THEN UPDATE                       
WHEN NOT MATCHED BY TARGET

//now use insert statement syntax accordingly
THEN INSERT                        
WHEN NOT MATCHED BY SOURCE
THEN DELETE;
```

Example:
```roomsql
/* Selecting the Target and the Source */
MERGE PRODUCT_LIST AS TARGET
USING UPDATE_LIST AS SOURCE

	/* 1. Performing the UPDATE operation */

	/* If the P_ID is same,
	check for change in P_NAME or P_PRICE */
	ON (TARGET.P_ID = SOURCE.P_ID)
	WHEN MATCHED
		AND TARGET.P_NAME <> SOURCE.P_NAME
		OR TARGET.P_PRICE <> SOURCE.P_PRICE

	/* Update the records in TARGET */
	THEN UPDATE
		SET TARGET.P_NAME = SOURCE.P_NAME,
		TARGET.P_PRICE = SOURCE.P_PRICE
	
	/* 2. Performing the INSERT operation */

	/* When no records are matched with TARGET table
	Then insert the records in the target table */
	WHEN NOT MATCHED BY TARGET
	THEN INSERT (P_ID, P_NAME, P_PRICE)		
		VALUES (SOURCE.P_ID, SOURCE.P_NAME, SOURCE.P_PRICE)

	/* 3. Performing the DELETE operation */

	/* When no records are matched with SOURCE table
	Then delete the records from the target table */
	WHEN NOT MATCHED BY SOURCE
	THEN DELETE

/* END OF MERGE */
```
#### Case statement or control statement
* Are uses to query filtering and query optimization by carefully selecting tuples that match our requirements.
Syntax:
```roomsql
CASE case_value
WHEN when_value THEN statement_list
[WHEN when_value THEN statement_list] …
[ELSE statement_list]
END CASE
```
Example:
```roomsql
SELECT CustomerName, Age,
CASE
WHEN Age> 22 THEN 'The Age is greater than 22'
WHEN Age = 21 THEN 'The Age is 21'
ELSE 'The Age is over 30'
END AS QuantityText
FROM Customer;
```
#### View
* Views in SQL are kind of virtual tables.
* We can create a view by selecting fields from one or more tables present in the database. 
Syntax:
```roomsql
CREATE OR REPLACE VIEW view_name AS
SELECT column1,column2,..
FROM table_name
WHERE condition;
```
>[!Note]: 
> 
>we can perform all the operation as comparing to table but for update we need to follow some rules

#### Roles
* A role is created to ease the setup and maintenance of the security model.
* First DBA(data base administrate) create the role

Syntax:
```roomsql
CREATE ROLE  ROLE_NAME;
```
* Provide privileged access to the Created role

Syntax:
```roomsql
GRANT create table, create view TO manager;
```
* Provide manger access to the users

Syntax:
```roomsql
GRANT manager TO SAM, STARK;
```
* Revoke access from role

Syntax:
```roomsql
REVOKE create table FROM manager;
```
* Drop role

Syntax:
```roomsql
DROP ROLE manager;
```

