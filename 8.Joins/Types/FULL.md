# 🔄 FULL JOIN in SQL

---
## 📘 What is FULL JOIN?
A `FULL JOIN` (or `FULL OUTER JOIN`) returns:
- **All records from both left and right tables**
- If there is no match, the result will contain `NULL` for unmatched columns.

### ✅ Syntax

```roomsql
SELECT table1.column1, table2.column2, ...
FROM table1
FULL JOIN table2
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
FULL JOIN Departments d
ON e.dept_id = d.dept_id;
```
### 📤 Output
| name    | dept\_name |
| ------- | ---------- |
| Alice   | HR         |
| Bob     | IT         |
| NULL    | Finance    |
| Charlie | NULL       |
| David   | NULL       |
* Combines results of both LEFT JOIN and RIGHT JOIN
* Shows unmatched records from both tables
---
### ✅ When to Use FULL JOIN
* When you want a complete view of both tables.
* To find unmatched records in both directions.
