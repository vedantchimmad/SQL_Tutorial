# 👁️ SQL View

A **View** is a **virtual table** based on the result set of a `SELECT` query.

It does **not store data** itself — it just shows data stored in underlying tables.


### ✅ Syntax

```sql
CREATE VIEW view_name AS
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```
---
### 📘 Complete Examples
#### 1️⃣ Basic View
 Used for filtering data from a table.
```roomsql
CREATE VIEW high_salary_employees AS
SELECT name, salary
FROM employees
WHERE salary > 80000;
```
#### 2️⃣ View with Selected Columns
Used to restrict access to specific columns.
```roomsql
CREATE VIEW employee_names AS
SELECT id, name
FROM employees;
```
#### 3️⃣ View with JOIN
Combine data from multiple tables.
```roomsql
CREATE VIEW employee_department_view AS
SELECT e.name, d.department_name
FROM employees e
JOIN departments d ON e.dept_id = d.id;
```
#### 4️⃣ View with Aggregate Function
Summarizes data per group.
```roomsql
CREATE VIEW avg_salary_per_dept AS
SELECT dept_id, AVG(salary) AS avg_salary
FROM employees
GROUP BY dept_id;
```
#### 5️⃣ Updatable View
Some views are updatable if based on a single table with no aggregation.
```roomsql
CREATE VIEW editable_view AS
SELECT id, name, salary
FROM employees
WHERE department = 'IT';
```
#### 6️⃣ Non-Updatable View
Not updatable due to aggregation.
```roomsql
CREATE VIEW non_editable_view AS
SELECT dept_id, COUNT(*) AS emp_count
FROM employees
GROUP BY dept_id;
```

