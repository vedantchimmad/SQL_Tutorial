# 🧠 SQL Query Execution Order (Logical Processing Order)

---
### 📘 What is Execution Order in SQL?

SQL queries don’t execute in the **same order** as written!  
Instead, SQL follows a **logical processing order** — the way the SQL engine processes each part of the query.


### 🔢 Actual SQL Execution Order

| Step | Clause       | Description                                 |
|------|--------------|---------------------------------------------|
| 1    | `FROM`       | Choose and join tables                      |
| 2    | `WHERE`      | Filter rows (before grouping)               |
| 3    | `GROUP BY`   | Group filtered rows                         |
| 4    | `HAVING`     | Filter groups                               |
| 5    | `SELECT`     | Select columns and expressions              |
| 6    | `DISTINCT`   | Remove duplicate rows (if specified)        |
| 7    | `ORDER BY`   | Sort the result                             |
| 8    | `LIMIT` / `TOP` | Limit number of rows (if specified)     |

---

### 🧾 Example Query

```roomsql
SELECT department, AVG(salary) AS avg_sal
FROM employees
WHERE salary > 50000
GROUP BY department
HAVING AVG(salary) > 60000
ORDER BY avg_sal DESC
LIMIT 3;
```
### 🔍 Breakdown of Execution
| Step | What Happens                                     |
| ---- | ------------------------------------------------ |
| 1    | `FROM employees` → Load the table                |
| 2    | `WHERE salary > 50000` → Filter rows             |
| 3    | `GROUP BY department` → Group rows by department |
| 4    | `HAVING AVG(salary) > 60000` → Filter groups     |
| 5    | `SELECT department, AVG(salary) AS avg_sal`      |
| 6    | `DISTINCT` (if used) → Remove duplicates         |
| 7    | `ORDER BY avg_sal DESC` → Sort the result        |
| 8    | `LIMIT 3` → Show only top 3 rows                 |

### 🔁 Written vs Executed Order
| Written Order | Executed Order      |
| ------------- | ------------------- |
| `SELECT`      | `FROM`              |
| `FROM`        | `WHERE`             |
| `WHERE`       | `GROUP BY`          |
| `GROUP BY`    | `HAVING`            |
| `HAVING`      | `SELECT`            |
| `ORDER BY`    | `DISTINCT` (if any) |
| `LIMIT / TOP` | `ORDER BY`          |
