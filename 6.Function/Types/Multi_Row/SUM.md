# 📊 SQL Window Function: SUM()

---
### 🧠 What is SUM() as a Window Function?

The `SUM()` window function returns a **running total** or **cumulative sum** of a column over a defined window.

It doesn't collapse rows like `GROUP BY`. Instead, it preserves all rows and adds a new column with the sum.

#### 🧾 Syntax

```roomsql
SELECT column1, column2, 
       SUM(numeric_column) OVER (
           [PARTITION BY partition_column]
           [ORDER BY order_column]
           [ROWS frame_specification]
       ) AS sum_output
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

#### ✅ Example: Running Total of Salary per Department
```roomsql
SELECT name, dept, salary,
       SUM(salary) OVER (
           PARTITION BY dept
           ORDER BY salary
           ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW
       ) AS running_total
FROM employee;
```
### 📤 Output
| name  | dept  | salary | running\_total |
| ----- | ----- | ------ | -------------- |
| Bob   | HR    | 50000  | 50000          |
| Alice | HR    | 60000  | 110000         |
| Carol | Sales | 70000  | 70000          |
| Eve   | Sales | 71000  | 141000         |
| Dave  | Sales | 72000  | 213000         |
