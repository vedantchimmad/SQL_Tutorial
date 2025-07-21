# 📘 Single Row Functions in SQL

---

### ✅ What Are Single Row Functions?

Single Row Functions operate **on one row at a time** and return **one result per row**.  
They are also called **Scalar Functions**.

---

## 🔹 Types of Single Row Functions

### 1. **String Functions**
| Function     | Description                          | Example                          |
|--------------|--------------------------------------|----------------------------------|
| `UPPER()`    | Converts text to uppercase           | `UPPER('hello') → 'HELLO'`       |
| `LOWER()`    | Converts text to lowercase           | `LOWER('HELLO') → 'hello'`       |
| `LENGTH()`   | Returns length of a string           | `LENGTH('data') → 4`             |
| `SUBSTR()`   | Extracts part of a string            | `SUBSTR('Hello', 2, 3) → 'ell'`  |
| `TRIM()`     | Removes whitespace                   | `TRIM('  name  ') → 'name'`      |

---

### 2. **Number Functions**
| Function     | Description                           | Example                        |
|--------------|---------------------------------------|--------------------------------|
| `ROUND()`    | Rounds a number                       | `ROUND(123.456, 2) → 123.46`   |
| `CEIL()`     | Rounds up to nearest integer          | `CEIL(12.3) → 13`              |
| `FLOOR()`    | Rounds down to nearest integer        | `FLOOR(12.8) → 12`             |
| `ABS()`      | Absolute value                        | `ABS(-15) → 15`                |
| `MOD()`      | Remainder (modulus)                   | `MOD(10, 3) → 1`               |

---

### 3. **Date Functions**
| Function        | Description                        | Example                                  |
|-----------------|------------------------------------|------------------------------------------|
| `SYSDATE()`     | Returns current date/time          | `SYSDATE()`                              |
| `NOW()`         | Returns current timestamp          | `NOW()`                                  |
| `DATE_ADD()`    | Adds interval to date              | `DATE_ADD('2023-01-01', INTERVAL 5 DAY)` |
| `DATEDIFF()`    | Difference between 2 dates         | `DATEDIFF('2023-01-10', '2023-01-01') → 9` |

---

### 4. **Conversion Functions**
| Function     | Description                              | Example                       |
|--------------|------------------------------------------|-------------------------------|
| `CAST()`     | Converts from one data type to another   | `CAST(100 AS CHAR)`           |
| `CONVERT()`  | Converts data to a specified format      | `CONVERT('2023-01-01', DATE)` |

---

## 🔍 Example Query

```roomsql
SELECT 
  name,
  UPPER(name) AS upper_name,
  LENGTH(name) AS name_length,
  ROUND(salary, 2) AS rounded_salary
FROM employees;
```