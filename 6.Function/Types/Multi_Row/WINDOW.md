# 🪟 SQL Window Functions

---
### ✅ What Are Window Functions?

**Window functions** perform **calculations across a set of rows** related to the current row **without collapsing the result set**.  
They use the `OVER()` clause to define the **window of rows**.

---

### 📋 Key Points

- Do **not group rows** like aggregate functions.
- Use **`OVER()`** clause to specify the "window".
- Useful for **ranking, running totals, averages, gaps, etc.**

---

### 🔍 Common Window Functions

| Function         | Description                                       | Example                               |
|------------------|---------------------------------------------------|---------------------------------------|
| `ROW_NUMBER()`   | Assigns unique row number to each row             | `ROW_NUMBER() OVER (ORDER BY salary)` |
| `RANK()`         | Gives rank, with gaps for duplicates              | `RANK() OVER (ORDER BY score DESC)`   |
| `DENSE_RANK()`   | Ranks without gaps                                | `DENSE_RANK() OVER (ORDER BY age)`    |
| `NTILE(n)`       | Divides rows into `n` buckets                     | `NTILE(4) OVER (ORDER BY salary)`     |
| `LAG()`          | Returns previous row's value                      | `LAG(salary) OVER (ORDER BY id)`      |
| `LEAD()`         | Returns next row's value                          | `LEAD(salary) OVER (ORDER BY id)`     |
| `FIRST_VALUE()`  | First value in window                             | `FIRST_VALUE(salary) OVER (...)`      |
| `LAST_VALUE()`   | Last value in window                              | `LAST_VALUE(salary) OVER (...)`       |
| `CUME_DIST()`    | Cumulative distribution                           | `CUME_DIST() OVER (ORDER BY marks)`   |
| `PERCENT_RANK()` | Percent rank of a row within a window             | `PERCENT_RANK() OVER (ORDER BY age)`  |

---

### 🏗️ Syntax

```roomsql
SELECT 
   employee_id,
   salary,
   RANK() OVER (PARTITION BY department ORDER BY salary DESC) AS rank_within_dept
FROM employees;
```
### 🧩 When To Use
* Ranking employees or students
* Detecting duplicates or gaps
* Comparing row with previous/next
* Calculating running totals, percentiles

