# 🔄 `UPDATE` Statement in SQL

---
## 📘 What is `UPDATE`?

The `UPDATE` statement is used to **modify existing records** in a table.

### 🧾 Syntax

```roomsql
UPDATE table_name
SET column1 = value1,
    column2 = value2,
    ...
WHERE condition;
```

> ⚠️ Note :
> * Without a WHERE clause, all rows will be updated.
---
### 📊 Example Table: employees
| id | name  | department | salary |
| -- | ----- | ---------- | ------ |
| 1  | Alice | HR         | 60000  |
| 2  | Bob   | IT         | 75000  |
| 3  | Carol | Sales      | 65000  |

### 🛠️ Common Use Cases
#### ✅ Example 1: Update a Single Row
```roomsql
UPDATE employees
SET salary = 70000
WHERE name = 'Carol';
```
#### ✅ Example 2: Update Multiple Columns
```roomsql
UPDATE employees
SET department = 'HR',
    salary = 62000
WHERE id = 2;
```
#### ✅ Example 3: Update All Rows 
```roomsql
UPDATE employees
SET salary = salary + 2000;
```
#### ✅ Example 4: Conditional Update
```roomsql
UPDATE employees
SET department = 'Admin'
WHERE department = 'HR' AND salary < 65000;
```
