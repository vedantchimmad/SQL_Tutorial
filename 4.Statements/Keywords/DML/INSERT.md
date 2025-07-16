# ➕ `INSERT` Statement in SQL

---
## 📘 What is `INSERT`?

The `INSERT` statement is used to **add new records** (rows) into a table.

### 🧾 Syntax

### ✅ Insert into All Columns

```roomsql
INSERT INTO table_name
VALUES (value1, value2, ...);
```
>⚠️ Note:
> * Values must match the column order and data types.
---
### 🛠️ Common Use Cases
#### ✅ Example 1: Insert Full Row
```roomsql
INSERT INTO employees
VALUES (2, 'Bob', 'IT', 75000);
```
#### ✅ Example 2: Insert into Specific Columns
```roomsql
INSERT INTO employees (id, name, department)
VALUES (3, 'Carol', 'Sales');
```
#### ✅ Example 3: Insert Multiple Rows
```roomsql
INSERT INTO employees (id, name, department, salary)
VALUES 
(4, 'Dave', 'HR', 62000),
(5, 'Erin', 'IT', 71000);
```
#### ✅ Example 4: Insert from Another Table
```roomsql
INSERT INTO new_table (col1, col2)
SELECT col1, col2 FROM old_table
WHERE condition;
```
---
### 🧠 Summary
| Task                      | Example                                   |
| ------------------------- | ----------------------------------------- |
| Insert full row           | `INSERT INTO t VALUES (...);`             |
| Insert specific columns   | `INSERT INTO t(col1, col2) VALUES (...);` |
| Insert multiple rows      | `VALUES (...), (...);`                    |
| Insert from another table | `INSERT INTO t SELECT ... FROM t2;`       |
