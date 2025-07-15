# ✂️ `TRUNCATE` in SQL

---
## 📘 What is `TRUNCATE`?

The `TRUNCATE` statement in SQL is used to **quickly delete all rows** from a table **without logging individual row deletions**.  
It is faster and uses fewer system/log resources than `DELETE`.

### 🔁 Syntax

```roomsql
TRUNCATE TABLE table_name;
```
---
### 🛠️ Common Use Case
#### 1. Truncate table
```roomsql
TRUNCATE TABLE employees;
```
> ⚠️ Important Notes
> * Removes all data from the employees table, but keeps the table structure.

---
### 🧱 TRUNCATE vs DELETE vs DROP
| Feature         | `TRUNCATE`                   | `DELETE`               | `DROP`                 |
| --------------- | ---------------------------- | ---------------------- | ---------------------- |
| Deletes rows    | ✅ All rows                   | ✅ All or specific rows | ❌ Deletes entire table |
| Where clause    | ❌ Not allowed                | ✅ Allowed              | ❌ Not applicable       |
| Rollback        | ⚠️ Sometimes (depends on DB) | ✅ Yes                  | ❌ No                   |
| Logs each row   | ❌ No                         | ✅ Yes                  | ❌ N/A                  |
| Resets Identity | ✅ Yes (in most DBMS)         | ❌ No                   | ❌ Not relevant         |
| Keeps schema    | ✅ Yes                        | ✅ Yes                  | ❌ No                   |
| Speed           | 🚀 Fast                      | 🐢 Slower              | 🚀 Fast                |
