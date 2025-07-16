# ⚖️ Comparison Operators in SQL

---
## 📘 What Are Comparison Operators?

Comparison operators are used in SQL to **compare two values or expressions**.  
They return a **Boolean result**: `TRUE`, `FALSE`, or `NULL`.

These are commonly used in:
- `WHERE` clause
- `HAVING` clause
- `JOIN` conditions

---

### 🔧 List of SQL Comparison Operators

| Operator     | Description                      | Example                   |
|--------------|----------------------------------|---------------------------|
| `=`          | Equal to                         | `age = 30`                |
| `!=` / `<>`  | Not equal to                     | `salary != 50000`         |
| `>`          | Greater than                     | `marks > 60`              |
| `<`          | Less than                        | `salary < 70000`          |
| `>=`         | Greater than or equal to         | `age >= 18`               |
| `<=`         | Less than or equal to            | `price <= 100`            |
| `BETWEEN`    | Within a range (inclusive)       | `age BETWEEN 18 AND 30`   |
| `LIKE`       | Pattern match                    | `name LIKE 'A%'`          |
| `IN`         | Matches any value in a list      | `dept IN ('HR', 'IT')`    |
| `IS NULL`    | Checks for NULL value            | `email IS NULL`           |
| `IS NOT NULL`| Checks for NOT NULL value        | `email IS NOT NULL`       |

---

### ✅ Example Usage

#### 1. Using `=`, `<>`, `>`, `<`

```roomsql
SELECT name, salary
FROM employees
WHERE salary > 60000;
```
#### 2. Using `BETWEEN`
```roomsql
SELECT name
FROM students
WHERE marks BETWEEN 70 AND 90;
```
#### 3. Using IN
```roomsql
SELECT name
FROM employees
WHERE department IN ('HR', 'IT');
```
#### 4. Using LIKE
```roomsql
SELECT name
FROM customers
WHERE name LIKE 'S%';
```
#### 5. Using IS NULL
```roomsql
SELECT name
FROM users
WHERE phone IS NULL;
```
---
### 🧠 Summary
| Task                | Operator   | Example                   |
| ------------------- | ---------- | ------------------------- |
| Equal check         | `=`        | `age = 25`                |
| Not equal check     | `!=`, `<>` | `dept <> 'HR'`            |
| Greater / Less than | `>`, `<`   | `salary > 50000`          |
| Range check         | `BETWEEN`  | `age BETWEEN 18 AND 30`   |
| List of values      | `IN`       | `status IN ('New','Old')` |
| Pattern match       | `LIKE`     | `name LIKE 'A%'`          |
| NULL check          | `IS NULL`  | `email IS NULL`           |
