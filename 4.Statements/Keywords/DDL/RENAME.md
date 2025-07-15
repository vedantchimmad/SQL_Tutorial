# ✏️ `RENAME` in SQL

---
## 📘 What is `RENAME`?

The `RENAME` operation in SQL is used to **change the name** of a database object like:
- A table
- A column
- A database
- A view
- An index (in some DBMS)

> ⚠️ RENAME only changes the **name** — the structure and data remain unchanged.


### ✅ Syntax: Rename a Table

#### 🔹 Standard SQL / PostgreSQL / Oracle:

```roomsql
ALTER TABLE old_table_name
RENAME TO new_table_name;
```
---
### 🛠️ Common Use Cases
#### ✅ Example 1: Rename Table
```roomsql
ALTER TABLE employees
RENAME TO staff;
```
#### ✅ Example 2: Rename Column
```roomsql
ALTER TABLE staff
RENAME COLUMN name TO full_name;
```
#### ✅ Example 3: Rename View
```roomsql
ALTER VIEW old_view_name
RENAME TO new_view_name;
```
---
### 🧠 Summary
| Action                    | Syntax (Generic)                            |
| ------------------------- | ------------------------------------------- |
| Rename table              | `ALTER TABLE old_name RENAME TO new_name;`  |
| Rename column             | `ALTER TABLE tbl RENAME COLUMN old TO new;` |
| Rename table (SQL Server) | `EXEC sp_rename 'old', 'new';`              |
