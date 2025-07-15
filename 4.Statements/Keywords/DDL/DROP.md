# 🗑️ `DROP` Statement in SQL

---
## 📘 What is `DROP`?

The `DROP` statement is used to **permanently delete** database objects such as:
- Tables
- Databases
- Views
- Functions
- Indexes
- Constraints

> ⚠️ It **removes the structure and all data** — **irreversible**!

### 🧾 Syntax

```roomsql
DROP object_type object_name;
```
---
### 🛠️ Common Use Cases

#### ✅ Example 1: Drop a Table
```roomsql
DROP TABLE employees;
```
#### ✅ Example 2: Drop a Database
```roomsql
DROP DATABASE company_db;
```
#### ✅ Example 3: Drop a View
```roomsql
DROP VIEW high_salary_employees;
```
#### ✅ Example 4: Drop a Column (MySQL / PostgreSQL)
```roomsql
ALTER TABLE employees
DROP COLUMN age;
```
#### ✅ Example 5: Drop a Function
```roomsql
DROP FUNCTION add_numbers;
```
---
### ⚠️ Important Notes
| Rule                         | Description                                                      |
| ---------------------------- | ---------------------------------------------------------------- |
| 💥 Destructive               | Deletes the object AND its data                                  |
| 🛑 Cannot be rolled back     | No undo unless inside a transaction block (not always supported) |
| 🔒 Requires permissions      | You must have proper privileges                                  |
| 📄 Use `IF EXISTS` if unsure | Prevents error if object doesn’t exist                           |


