# 🛠️ `CREATE` Statement in SQL

---
## 📘 What is `CREATE`?

The `CREATE` statement in SQL is used to **create new database objects** such as:
- Tables 🧱
- Databases 🗃️
- Views 👁️
- Indexes 🔍
- Users 👤
- Functions and more...

### 🧾 Syntax: Creating a Table

```roomsql
CREATE TABLE table_name (
    column1 datatype constraints,
    column2 datatype constraints,
    ...
);
```
---
### 🔧 Common Use Cases
#### ✅ Example: Create an employees Table
```roomsql
CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    department VARCHAR(50),
    salary DECIMAL(10, 2)
);
```
#### ✅ Example: Create a Database
```roomsql
CREATE DATABASE company_db;
```
#### ✅ Example: Create a View
```roomsql
CREATE VIEW high_salary_employees AS
SELECT name, salary FROM employees
WHERE salary > 70000;
```
#### ✅ Example: Create an Index
```roomsql
CREATE INDEX idx_dept ON employees(department);
```
#### ✅ Example: Create a function
```roomsql
CREATE FUNCTION add_numbers(@a INT, @b INT)
RETURNS INT
AS
BEGIN
   RETURN @a + @b;
END;

--usage
SELECT dbo.add_numbers(5, 10) AS result;
```
---
### 🧠 Summary
| Object   | Syntax Example                         |
| -------- | -------------------------------------- |
| Table    | `CREATE TABLE employees (...)`         |
| Database | `CREATE DATABASE mydb;`                |
| View     | `CREATE VIEW myview AS SELECT ...`     |
| Index    | `CREATE INDEX idx_name ON table(col);` |
