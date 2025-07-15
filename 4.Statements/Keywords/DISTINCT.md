# 🔹 `DISTINCT` in SQL

---
## 📘 What is `DISTINCT`?

The `DISTINCT` keyword in SQL is used to **remove duplicate values** from the result set.  
It ensures that only **unique values** are returned for the specified column(s).

### 🧾 Syntax

```roomsql
SELECT DISTINCT column1, column2, ...
FROM table_name;
```
---
## 📊 Example Table: employees
| id  | name  | department | salary |
|-----| ----- | ---------- | ------ |
| 1   | Alice | HR         | 60000  |
| 2   | Bob   | IT         | 75000  |
| 3   | Carol | IT         | 65000  |
| 4   | Dave  | HR         | 62000  |
| 5   | Erin  | Sales      | 58000  |
| 6   | Frank | Sales      | 58000  |

### 🔧 Common Use Cases

#### 1. Unique Departments
```roomsql
SELECT DISTINCT department FROM employees;
```
#### 2. Unique Department & Salary Combinations
```roomsql
SELECT DISTINCT department, salary FROM employees;
```