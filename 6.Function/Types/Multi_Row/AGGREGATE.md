# 📊 SQL Aggregate Functions

---
## ✅ What Are Aggregate Functions?

---
Aggregate functions **perform a calculation on a set of values** and return a single summarizing result. They are commonly used with `GROUP BY` clauses.

---

### 📦 Common Aggregate Functions

| Function   | Description                                | Example                            |
|------------|--------------------------------------------|------------------------------------|
| `COUNT()`  | Returns the number of rows                 | `COUNT(*)`, `COUNT(column_name)`   |
| `SUM()`    | Returns the total sum of a numeric column  | `SUM(salary)`                      |
| `AVG()`    | Returns the average value                  | `AVG(salary)`                      |
| `MIN()`    | Returns the minimum value                  | `MIN(salary)`                      |
| `MAX()`    | Returns the maximum value                  | `MAX(salary)`                      |

---

### 💡 Example Query

```roomsql
SELECT department,
       COUNT(*) AS total_employees,
       SUM(salary) AS total_salary,
       AVG(salary) AS average_salary,
       MIN(salary) AS lowest_salary,
       MAX(salary) AS highest_salary
FROM employees
GROUP BY department;
```