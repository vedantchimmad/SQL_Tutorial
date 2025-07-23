# 🏅 SQL Window Function: DENSE_RANK()

---
### 📘 What is DENSE_RANK()?

The `DENSE_RANK()` function assigns **rankings** to rows within a partition of a result set.  
Unlike `RANK()`, it does **not skip ranks** when there are ties (duplicate values).

### 🧾 Syntax

```roomsql
SELECT column1, column2,
       DENSE_RANK() OVER (
           [PARTITION BY partition_column]
           ORDER BY sort_column
       ) AS dense_rank
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
#### ✅ Example: Dense Rank Employees by Salary Within Each Department
```roomsql
SELECT name, dept, salary,
       DENSE_RANK() OVER (PARTITION BY dept ORDER BY salary DESC) AS dense_rank
FROM employee;
```
### 📤 Output
| name  | dept  | salary | dense\_rank |
| ----- | ----- | ------ | ----------- |
| Alice | HR    | 60000  | 1           |
| Bob   | HR    | 50000  | 2           |
| Carol | Sales | 72000  | 1           |
| Dave  | Sales | 72000  | 1           |
| Eve   | Sales | 71000  | 2           |
---
### 🔍 Comparison Table
| Function     | Tie Handling    | Skipped Ranks? |
| ------------ | --------------- | -------------- |
| `ROW_NUMBER` | No tie          | No             |
| `RANK`       | Ties share rank | ✅ Yes          |
| `DENSE_RANK` | Ties share rank | ❌ No           |
