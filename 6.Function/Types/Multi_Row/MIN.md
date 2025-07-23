# 🧮 SQL Window Function: MIN()

---
### 📘 What is MIN() as a Window Function?

The `MIN()` window function returns the **minimum value** of a column over a specified window (a set of rows defined by `PARTITION BY` and `ORDER BY`), **without reducing** the number of rows in the output.

### 🧾 Syntax

```roomsql
SELECT column1, column2,
       MIN(numeric_column) OVER (
           [PARTITION BY partition_column]
           [ORDER BY order_column]
           [ROWS BETWEEN frame_start AND frame_end]
       ) AS min_output
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
#### ✅ Example: Minimum Salary So Far Within Department
```roomsql
SELECT name, dept, salary,
       MIN(salary) OVER (
           PARTITION BY dept
           ORDER BY salary
           ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW
       ) AS min_so_far
FROM employee;
```
### 📤 Output
| name  | dept  | salary | min\_so\_far |
| ----- | ----- | ------ | ------------ |
| Bob   | HR    | 50000  | 50000        |
| Alice | HR    | 60000  | 50000        |
| Carol | Sales | 70000  | 70000        |
| Eve   | Sales | 71000  | 70000        |
| Dave  | Sales | 72000  | 70000        |

---
### 💡 Notes
* `PARTITION BY` dept: Resets the minimum calculation for each department.
* `ORDER BY` salary: Ensures min is calculated in increasing salary order.
* `ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW`: Calculates a running min from the beginning of the partition to the current row.