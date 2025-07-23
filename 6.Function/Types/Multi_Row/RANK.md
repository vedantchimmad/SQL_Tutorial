# 🏆 SQL Window Function: RANK()

---
### 📘 What is RANK()?

The `RANK()` function assigns a **rank** to each row within a partition of a result set. If there are **ties** (same values in `ORDER BY`), it assigns **the same rank** to those rows, and **skips the next ranks** accordingly.

### 🧾 Syntax

```roomsql
SELECT column1, column2,
       RANK() OVER (
           [PARTITION BY partition_column]
           ORDER BY sort_column
       ) AS rank
FROM table_name;
```
---
### 🧪 Sample Table: employee
| id | name  | dept  | salary |
| -- | ----- | ----- | ------ |
| 1  | Alice | HR    | 60000  |
| 2  | Bob   | HR    | 50000  |
| 3  | Carol | Sales | 72000  |
| 4  | Dave  | Sales | 72000  |
| 5  | Eve   | Sales | 71000  |
#### ✅ Example: Rank Employees by Salary Within Each Department
```roomsql
SELECT name, dept, salary,
       RANK() OVER (PARTITION BY dept ORDER BY salary DESC) AS rank
FROM employee;
```
### 📤 Output
| name  | dept  | salary | rank |
| ----- | ----- | ------ | ---- |
| Alice | HR    | 60000  | 1    |
| Bob   | HR    | 50000  | 2    |
| Carol | Sales | 72000  | 1    |
| Dave  | Sales | 72000  | 1    |
| Eve   | Sales | 71000  | 3    |
---
### 🔍 Key Differences
* `RANK()` skips ranks after ties (e.g., 1, 1, 3).
* `DENSE_RANK()` does not skip ranks (e.g., 1, 1, 2).
* `ROW_NUMBER()` always gives a unique number, even for ties.

### 💡 Use Cases
* Find top N per group with possible ties
* Assign rankings in leaderboards
* Handle duplicate scoring scenarios