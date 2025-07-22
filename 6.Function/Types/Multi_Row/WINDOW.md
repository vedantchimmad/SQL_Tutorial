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
---
## 🪟 SQL Window Frame

---

## 🧠 What is a Window Frame?

A **window frame** defines the **subset of rows** over which a **window function** operates within its partition. It’s especially useful for **running totals**, **moving averages**, etc.

---

### ✳️ Syntax Overview

```roomsql
<window_function> OVER (
  PARTITION BY column
  ORDER BY column
  ROWS|RANGE BETWEEN <start> AND <end>
)
```
### 🆚 ROWS vs RANGE
| Frame Type | Description                        |
| ---------- | ---------------------------------- |
| `ROWS`     | Operates on **physical row count** |
| `RANGE`    | Operates on **value-based range**  |

### 🎯 Frame Boundaries
| Boundary              | Meaning                                 |
| --------------------- | --------------------------------------- |
| `UNBOUNDED PRECEDING` | From the **first row** in the partition |
| `n PRECEDING`         | From **n rows before** the current row  |
| `CURRENT ROW`         | The **current row**                     |
| `n FOLLOWING`         | **n rows after** the current row        |
| `UNBOUNDED FOLLOWING` | Till the **last row** in the partition  |

### .📌 Example

#### Example 1: Running Total
```roomsql
SELECT
  employee_id,
  salary,
  SUM(salary) OVER (
    ORDER BY employee_id
    ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW
  ) AS running_total
FROM employees;
```
#### 📌 Example 2: Moving Average (Last 2 + Current)
```roomsql
SELECT
  employee_id,
  salary,
  AVG(salary) OVER (
    ORDER BY employee_id
    ROWS BETWEEN 2 PRECEDING AND CURRENT ROW
  ) AS moving_avg
FROM employees;
```
---
### ✅ Summary Table
| Keyword               | Meaning                        |
| --------------------- | ------------------------------ |
| `ROWS`                | Uses row count for window size |
| `RANGE`               | Uses column value range        |
| `BETWEEN ... AND ...` | Defines sliding frame          |
| `UNBOUNDED`           | Start or end of partition      |
| `CURRENT ROW`         | Refers to row being evaluated  |
