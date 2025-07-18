# 🔍 RIGHT ANTI JOIN in SQL

---
## 📘 What is a RIGHT ANTI JOIN?
A **RIGHT ANTI JOIN** returns:
> **Only those records from the right table** that **do NOT have a matching record** in the left table.

> ⚠️ Not all SQL dialects support `RIGHT ANTI JOIN` directly. But you can simulate it using alternatives.
---
### ✅ Simulating RIGHT ANTI JOIN

### 🧩 Example Tables:

#### 🧑 Employees
| emp_id | name    | dept_id |
|--------|---------|---------|
| 1      | Alice   | 101     |
| 2      | Bob     | 102     |
| 3      | Charlie | NULL    |
| 4      | David   | 104     |

#### 🏢 Departments
| dept_id | dept_name |
|---------|-----------|
| 101     | HR        |
| 102     | IT        |
| 103     | Finance   |

---

### 🛠 Method 1: RIGHT JOIN + IS NULL

```roomsql
SELECT d.*
FROM Employees e
RIGHT JOIN Departments d
  ON e.dept_id = d.dept_id
WHERE e.dept_id IS NULL;
```
### 🛠 Method 2: NOT EXISTS
```roomsql
SELECT *
FROM Departments d
WHERE NOT EXISTS (
  SELECT 1
  FROM Employees e
  WHERE e.dept_id = d.dept_id
);
```
### 🛠 Method 3: NOT IN
```roomsql
SELECT *
FROM Departments
WHERE dept_id NOT IN (
  SELECT dept_id FROM Employees WHERE dept_id IS NOT NULL
);
```
#### 📤 Output
| dept_id | dept_name |
|---------| --------- |
| 103     | Finance   |


