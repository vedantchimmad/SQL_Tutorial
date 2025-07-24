# 🧱 SQL Table – Definition and Example

---
## 📌 What is a Table?

A **table** is a core database object used to **store structured data** in **rows and columns**.

Each row is a **record**, and each column is a **field** (attribute) of that record.

### 🧾 Syntax to Create a Table

```roomsql
CREATE TABLE table_name (
    column1 datatype constraint,
    column2 datatype constraint,
    ...
);
```
---
###  🧱 All possible examples
#### ✅ Basic Table
```roomsql
CREATE TABLE employees (
    emp_id INT PRIMARY KEY,
    name VARCHAR(100),
    department VARCHAR(50),
    salary DECIMAL(10, 2)
);
```
#### 🔐 With Constraints
```roomsql
CREATE TABLE departments (
    dept_id INT PRIMARY KEY,
    dept_name VARCHAR(100) UNIQUE,
    location VARCHAR(50) NOT NULL
);
```
#### 🔗 With Foreign Key
```roomsql
CREATE TABLE projects (
    project_id INT PRIMARY KEY,
    project_name VARCHAR(100),
    emp_id INT,
    FOREIGN KEY (emp_id) REFERENCES employees(emp_id)
);
```
#### ⏱️ With Default & Check
```roomsql
CREATE TABLE attendance (
    record_id INT PRIMARY KEY,
    emp_id INT,
    date DATE DEFAULT GETDATE(),
    hours_worked INT CHECK (hours_worked <= 24)
);
```
#### 📦 Temporary Table
```roomsql
CREATE TEMPORARY TABLE temp_data (
    id INT,
    value VARCHAR(50)
);
```
#### 📁 Table from Existing Table
```roomsql
CREATE TABLE employee_copy AS
SELECT * FROM employees;
```
---
### 🔒 Common Constraints in Tables
| Constraint    | Purpose                                   |
| ------------- | ----------------------------------------- |
| `PRIMARY KEY` | Uniquely identifies each row.             |
| `FOREIGN KEY` | References a column in another table.     |
| `NOT NULL`    | Column must have a value.                 |
| `UNIQUE`      | Column must have unique values.           |
| `CHECK`       | Validates values based on a condition.    |
| `DEFAULT`     | Sets a default value if none is provided. |
