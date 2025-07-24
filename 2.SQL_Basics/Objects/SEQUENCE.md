# 📘 SQL SEQUENCE – Auto Increment Generator

---

## 🔹 What is a SEQUENCE?

A **SEQUENCE** is a database object that generates a sequence of unique numeric values — often used to generate primary keys automatically.

- ✅ Independent of tables (unlike AUTO_INCREMENT)
- ✅ Useful for multi-table insertions
- ✅ Available in Oracle, PostgreSQL, SQL Server (as `SEQUENCE`)
- ❌ MySQL uses AUTO_INCREMENT instead (no native SEQUENCE support before version 8.0)

### 🔸 Syntax (PostgreSQL / Oracle / SQL Server)
```roomsql
CREATE SEQUENCE sequence_name
START WITH start_value
INCREMENT BY step
MINVALUE min
MAXVALUE max
CYCLE|NOCYCLE
CACHE n;
```
---
### 📋 Examples in Table Format
| **Example**            | **SQL Code**                                                            | **Explanation**                               |
| ---------------------- | ----------------------------------------------------------------------- | --------------------------------------------- |
| Create simple sequence | `CREATE SEQUENCE emp_seq START WITH 1 INCREMENT BY 1;`                  | Starts from 1, increments by 1                |
| Get next value         | `SELECT NEXTVAL('emp_seq');`                                            | Returns the next value (e.g., 1, then 2, ...) |
| Get current value      | `SELECT CURRVAL('emp_seq');`                                            | Returns last value used in session            |
| Create with MIN/MAX    | `CREATE SEQUENCE emp_seq START WITH 100 MINVALUE 100 MAXVALUE 200;`     | Sequence will run from 100 to 200             |
| Create with CYCLE      | `CREATE SEQUENCE cyc_seq START 1 MAXVALUE 5 CYCLE;`                     | After 5, it starts again at 1                 |
| Drop sequence          | `DROP SEQUENCE emp_seq;`                                                | Deletes the sequence object                   |
| Insert using sequence  | `INSERT INTO employees(id, name) VALUES (NEXTVAL('emp_seq'), 'Alice');` | Inserts with auto-generated ID                |

### 🔹 Example:
#### 🔹 PostgreSQL
```roomsql
CREATE TABLE employees (
  id INT PRIMARY KEY,
  name TEXT
);

CREATE SEQUENCE emp_id_seq
  START WITH 1
  INCREMENT BY 1;

INSERT INTO employees (id, name)
VALUES (NEXTVAL('emp_id_seq'), 'Vedant');

SELECT * FROM employees;
```
#### 🔹 In Oracle
```roomsql
CREATE SEQUENCE emp_seq START WITH 100 INCREMENT BY 10;

INSERT INTO employees (id, name)
VALUES (emp_seq.NEXTVAL, 'John');
```
#### 🔹 SQL Server Example
```roomsql
CREATE SEQUENCE OrderSeq
START WITH 1000
INCREMENT BY 1;

SELECT NEXT VALUE FOR OrderSeq;  -- Returns 1000
```

