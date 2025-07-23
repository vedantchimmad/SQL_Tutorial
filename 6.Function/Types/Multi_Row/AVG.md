# 📊 SQL Window Function: AVG()

---
### 📘 What is AVG() as a Window Function?

The `AVG()` window function calculates the **average value** of a numeric column over a specified window of rows — but **does not collapse** rows like the regular `GROUP BY` + `AVG()` does.

### 🧾 Syntax

```roomsql
SELECT column1, column2,
       AVG(numeric_column) OVER (
           [PARTITION BY partition_column]
           [ORDER BY order_column]
           [ROWS BETWEEN frame_start AND frame_end]
       ) AS avg_output
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
#### ✅ Example: Running Average Salary per Department
```roomsql
SELECT name, dept, salary,
       AVG(salary) OVER (
           PARTITION BY dept
           ORDER BY salary
           ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW
       ) AS running_avg
FROM employee;
```
### 📤 Output
| name  | dept  | salary | running\_avg |
| ----- | ----- | ------ | ------------ |
| Bob   | HR    | 50000  | 50000.00     |
| Alice | HR    | 60000  | 55000.00     |
| Carol | Sales | 70000  | 70000.00     |
| Eve   | Sales | 71000  | 70500.00     |
| Dave  | Sales | 72000  | 71000.00     |
---
### 💡 Notes
* `PARTITION BY` dept keeps the average isolated within each department.
* `ORDER BY` salary allows the use of a running average.
* `ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW` defines the frame for the rolling calculation.

