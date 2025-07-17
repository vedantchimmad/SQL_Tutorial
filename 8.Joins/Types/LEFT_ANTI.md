# ⛔ LEFT ANTI JOIN in SQL

---
## 📘 What is LEFT ANTI JOIN?
A **LEFT ANTI JOIN** returns **only the rows from the left table** that **do not have any matching rows** in the right table.

🧠 Think of it as:
> "Give me everything in the LEFT table that has **NO MATCH** in the RIGHT table."

### ✅ Syntax (SQL-like pseudocode)

Most SQL dialects like SQL Server, PostgreSQL, or Oracle do **not have an explicit `LEFT ANTI JOIN`**, but you can achieve it using:

```roomsql
SELECT *
FROM table1
WHERE NOT EXISTS (
  SELECT 1
  FROM table2
  WHERE table1.common_column = table2.common_column
);
```
---
## 🧩 Example
### 🧑 Employees :
| emp_id | name    | dept_id |
| ------ | ------- | ------- |
| 1      | Alice   | 101     |
| 2      | Bob     | 102     |
| 3      | Charlie | NULL    |
| 4      | David   | 104     |
### 🏢 Departments
| dept_id | dept_name |
| ------- | --------- |
| 101     | HR        |
| 102     | IT        |
| 103     | Finance   |

### 🛠 Query
```roomsql
SELECT *
FROM Employees e
WHERE NOT EXISTS (
  SELECT 1
  FROM Departments d
  WHERE e.dept_id = d.dept_id
);
```
### 📤 Output
| emp_id | name    | dept_id |
| ------ | ------- | ------- |
| 3      | Charlie | NULL    |
| 4      | David   | 104     |
* These employees do not belong to any existing department in the Departments table.
---
### ✅ When to Use LEFT ANTI JOIN
* To find unrelated or orphaned records.
* To identify mismatches or missing associations between tables.



