# ⬅️ LEFT JOIN in SQL

---
## 📘 What is LEFT JOIN?
A `LEFT JOIN` returns **all records from the left table**, and the **matched records from the right table**.  
If there is **no match**, NULLs are returned for columns from the right table.

### ✅ Syntax

```roomsql
SELECT table1.column1, table2.column2, ...
FROM table1
LEFT JOIN table2
ON table1.common_column = table2.common_column;
```
---
## 🧩 Example
### 🧑 Employees :
| emp\_id | name    | dept\_id |
| ------- | ------- | -------- |
| 1       | Alice   | 101      |
| 2       | Bob     | 102      |
| 3       | Charlie | NULL     |
| 4       | David   | 104      |
### 🏢 Departments
| dept\_id | dept\_name |
| -------- | ---------- |
| 101      | HR         |
| 102      | IT         |
| 103      | Finance    |

### 🛠 Query
```roomsql
SELECT e.name, d.dept_name
FROM Employees e
LEFT JOIN Departments d
ON e.dept_id = d.dept_id;
```
### 📤 Output
| name    | dept\_name |
| ------- | ---------- |
| Alice   | HR         |
| Bob     | IT         |
| Charlie | NULL       |
| David   | NULL       |
* All employees are shown.
* If a department does not exist for an employee, dept_name is NULL.
---
### ✅ When to Use LEFT JOIN
* When you want all rows from the left table.
* Helpful to find unmatched records or missing data in the right table.