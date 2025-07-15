# 🔧 `ALTER` Statement in SQL

---
## 📘 What is `ALTER`?

The `ALTER` statement is used to **modify the structure** of an existing database object such as a **table**, **column**, **index**, etc.

---
### 🛠️ Common Use Cases of `ALTER TABLE`

#### ✅ 1. Add a Column

```roomsql
ALTER TABLE employees
ADD age INT;
```
#### ✅ 2. Modify Column Data Type
```roomsql
ALTER TABLE employees
ALTER COLUMN salary DECIMAL(12, 2);
```
#### ✅ 3. Rename a Column (SQL Server)
```roomsql
ALTER TABLE employees
RENAME COLUMN name TO full_name;
```
#### ✅ 4. Drop a Column
```roomsql
ALTER TABLE employees
DROP COLUMN age;
```
#### ✅ 5. Rename a Table
```roomsql
ALTER TABLE employees
RENAME TO staff;
```
#### ✅ 6. Add a Constraint (Example: NOT NULL)
```roomsql
ALTER TABLE employees
ALTER COLUMN salary SET NOT NULL;
```
---
### 🧠 Summary of Common Alterations
| Operation      | SQL Syntax Example                                    |
| -------------- | ----------------------------------------------------- |
| Add Column     | `ALTER TABLE emp ADD age INT;`                        |
| Modify Column  | `ALTER TABLE emp ALTER COLUMN name TYPE VARCHAR(50);` |
| Drop Column    | `ALTER TABLE emp DROP COLUMN age;`                    |
| Rename Column  | `ALTER TABLE emp RENAME COLUMN old TO new;`           |
| Rename Table   | `ALTER TABLE old_name RENAME TO new_name;`            |
| Add Constraint | `ALTER TABLE emp ADD CONSTRAINT ...;`                 |

>⚠️ Notes
> * ALTER does not affect data — only the schema.
> * Some changes may require exclusive table locks.
> * Different databases may use slightly different syntax.

