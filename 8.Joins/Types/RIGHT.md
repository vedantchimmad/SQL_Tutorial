# ➡️ RIGHT JOIN in SQL

---
## 📘 What is RIGHT JOIN?
A `RIGHT JOIN` returns **all records from the right table**, and the **matched records from the left table**.  
If there is **no match**, NULLs are returned for columns from the left table.

### ✅ Syntax

```roomsql
SELECT table1.column1, table2.column2, ...
FROM table1
RIGHT JOIN table2
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
RIGHT JOIN Departments d
ON e.dept_id = d.dept_id;
```
### 📤 Output
| name  | dept\_name |
| ----- | ---------- |
| Alice | HR         |
| Bob   | IT         |
| NULL  | Finance    |
* All departments are shown.
* If no employee is assigned to a department, name is NULL.
---
### ✅ When to Use RIGHT JOIN
* When you want all rows from the right table.
* Useful when the right table is primary and you want to check for missing matches on the left.

