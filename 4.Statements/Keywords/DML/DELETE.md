# 🗑️ `DELETE` Statement in SQL

---
## 📘 What is `DELETE`?

The `DELETE` statement in SQL is used to **remove one or more rows** from a table based on a condition.

> ⚠️ Note :
> * Unlike `TRUNCATE`, `DELETE` can remove **specific records**.
> * Deletes all rows from the table but keeps the table structure.
### 🧾 Syntax

```roomsql
DELETE FROM table_name
WHERE condition;
```
---
### 📊 Example Table: employees
| id | name  | department | salary |
| -- | ----- | ---------- | ------ |
| 1  | Alice | HR         | 60000  |
| 2  | Bob   | IT         | 75000  |
| 3  | Carol | Sales      | 65000  |

### 🛠️ Common Use Cases
#### ✅ Example 1: Delete a Single Row
```roomsql
DELETE FROM employees
WHERE name = 'Bob';
```
#### ✅ Example 2: Delete Multiple Rows
```roomsql
DELETE FROM employees
WHERE salary < 65000;
```
#### ✅ Example 3: Delete All Rows
```roomsql
DELETE FROM employees;
```
#### ✅ Example 4: Use with Subquery
```roomsql
DELETE FROM employees
WHERE id IN (
  SELECT id FROM employees WHERE department = 'Sales'
);
```
---
### ⚠️ Key Differences: DELETE vs TRUNCATE
| Feature            | `DELETE`               | `TRUNCATE`             |
| ------------------ | ---------------------- | ---------------------- |
| Condition allowed  | ✅ Yes (with `WHERE`)   | ❌ No                   |
| Row-by-row logging | ✅ Yes                  | ❌ Minimal              |
| Rollback support   | ✅ Yes (in transaction) | ❌ Not always supported |
| Triggers fire      | ✅ Yes                  | ❌ No                   |
| Speed              | 🐢 Slower              | 🚀 Faster              |

