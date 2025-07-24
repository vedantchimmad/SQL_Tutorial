# 📘 SQL INDEX – Complete Guide with Examples

---

## 🔹 What is an Index?

An **index** in SQL is used to speed up the retrieval of rows by creating a *pointer* to the data in a table — similar to a book index.

* ✅ Improves SELECT performance  
* ❌ May slow down INSERT/UPDATE/DELETE (due to index maintenance)

---
### 📘 Complete Examples
#### 1️⃣ Create Index on Single Column
* ✔️ Speeds up queries using WHERE name = 'John'
```roomsql
CREATE INDEX idx_employee_name
ON employees(name);
```
#### 2️⃣ Create Unique Index
* ✔️ Ensures email is unique
* ✔️ Similar to unique constraint
```roomsql
CREATE UNIQUE INDEX idx_unique_email
ON employees(email);
```
#### 3️⃣ Create Index on Multiple Columns (Composite Index)
```roomsql
CREATE INDEX idx_dept_salary
ON employees(dept_id, salary);
```
#### 4️⃣ Create Index with DESC Order (Some RDBMS like PostgreSQL)
* ✔️ Optimizes queries with ORDER BY salary DESC
```roomsql
CREATE INDEX idx_salary_desc
ON employees(salary DESC);
```