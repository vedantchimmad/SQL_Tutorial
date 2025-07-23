# 🔝 SQL Window Function: MAX()

---
### 🧠 What is MAX() as a Window Function?

The `MAX()` window function returns the **maximum value** of a column over a specified window **without collapsing rows**. Unlike `GROUP BY`, all rows are retained, and the max value is shown per window frame.

### 🧾 Syntax

```roomsql
SELECT column1, column2,
       MAX(numeric_column) OVER (
           [PARTITION BY partition_column]
           [ORDER BY order_column]
           [ROWS frame_specification]
       ) AS max_output
FROM table_name;
```
---
### 🧪 Example Table: employee
| id | name  | dept  | salary |
| -- | ----- | ----- | ------ |
| 1  | Alice | HR    | 60000  |
| 2  | Bob   | HR    | 50000  |
| 3  | Carol | Sales | 70000  |
| 4  | Dave  | Sales | 72000  |
| 5  | Eve   | Sales | 71000  |

#### ✅ Example: Max Salary So Far Within Department
```roomsql
SELECT name, dept, salary,
       MAX(salary) OVER (
           PARTITION BY dept
           ORDER BY salary
           ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW
       ) AS max_so_far
FROM employee;
```
### 📤 Output
| name  | dept  | salary | max\_so\_far |
| ----- | ----- | ------ | ------------ |
| Bob   | HR    | 50000  | 50000        |
| Alice | HR    | 60000  | 60000        |
| Carol | Sales | 70000  | 70000        |
| Eve   | Sales | 71000  | 71000        |
| Dave  | Sales | 72000  | 72000        |
---
### 💡 Notes
* `PARTITION BY` dept isolates calculations by department.
* `ORDER BY` salary controls the row order for comparison.
* `ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW` calculates a running max from the start to the current row.
