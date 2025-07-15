# 🔝 `TOP` in SQL

---
## 📘 What is `TOP`?

The `TOP` keyword in SQL is used to **limit the number of rows returned** in a query result.  
It's most commonly used when you want to retrieve the **first N records**, often ordered by a column (like highest salary, most recent date, etc.).

### 🧾 Syntax (SQL Server)

```roomsql
SELECT TOP N column1, column2, ...
FROM table_name
ORDER BY column_name [ASC|DESC];
```
### 📝 TOP is supported in:

* SQL Server
* MS Access
* Use LIMIT in MySQL/PostgreSQL
* Use FETCH FIRST in Oracle

---
## 📊 Example Table: employees

### 🔧 Common Use Cases

#### 1. Top 3 Highest Salaries
```roomsql
SELECT TOP 3 * FROM employees
ORDER BY salary DESC;
```
#### 2. Top 2 in Alphabetical Order by Name
```roomsql
SELECT TOP 2 name FROM employees
ORDER BY name ASC;
```
---
## 🧠 Alternatives in Other SQL Dialects
| Database    | Equivalent Syntax              |
| ----------- | ------------------------------ |
| MySQL       | `SELECT ... FROM ... LIMIT N;` |
| PostgreSQL  | `SELECT ... FROM ... LIMIT N;` |
| Oracle 12c+ | `FETCH FIRST N ROWS ONLY`      |
| SQL Server  | `SELECT TOP N`                 |
