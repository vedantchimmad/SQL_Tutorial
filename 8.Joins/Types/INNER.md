# 🔍 INNER JOIN in SQL

---
## 📘 What is INNER JOIN?
`INNER JOIN` returns **only the rows that have matching values** in both tables.


### ✅ Syntax

```roomsql
SELECT table1.column1, table2.column2, ...
FROM table1
INNER JOIN table2
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
INNER JOIN Departments d
ON e.dept_id = d.dept_id;
```
### 📤 Output
| name  | dept\_name |
| ----- | ---------- |
| Alice | HR         |
| Bob   | IT         |

* Only employees with matching dept_id in both tables are returned.
* Rows with NULL or no match (like Charlie and David) are excluded.
---
### ✅ When to Use INNER JOIN
* You only want matching data from both tables.
* Commonly used in normalized databases to bring related info together.
