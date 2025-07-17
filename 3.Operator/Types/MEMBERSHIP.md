# ✅ SQL Membership Operator: `IN`

---
## 📘 What is `IN` in SQL?

The `IN` operator is used to **check if a value exists** in a **given list of values**.  
It’s a **shorter and cleaner** alternative to writing multiple `OR` conditions.

### ✅ Syntax

```roomsql
SELECT column_name
FROM table_name
WHERE column_name IN (value1, value2, ..., valueN);
```
---
### 🛠️ Use Cases
#### 🧪 Example 1: Numeric List
```roomsql
SELECT name, department
FROM employees
WHERE department_id IN (101, 102, 103);
```
#### 🧪 Example 2: Text List
```roomsql
SELECT *
FROM customers
WHERE city IN ('Mumbai', 'Delhi', 'Chennai');
```
#### 🧪 Example 3: With Subquery
```roomsql
SELECT name
FROM students
WHERE roll_no IN (SELECT roll_no FROM toppers);
```
####  🧪 Example 4: Using NOT IN
```roomsql
SELECT name
FROM employees
WHERE department NOT IN ('HR', 'Finance');
```
