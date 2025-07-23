# 🧮 SQL Window Function: ROW_NUMBER()

---
### 📘 What is ROW_NUMBER()?

`ROW_NUMBER()` assigns a **unique sequential integer** to rows **within a partition**, ordered by specified columns. It's often used to:
- Remove duplicates
- Fetch top N rows per group
- Apply custom row rankings

### 🧾 Syntax

```roomsql
SELECT column1, column2,
       ROW_NUMBER() OVER (
           [PARTITION BY partition_column]
           ORDER BY sort_column
       ) AS row_num
FROM table_name;
```
---
### 🧪 Sample Table: employee
| id | name  | dept  | salary |
| -- | ----- | ----- | ------ |
| 1  | Alice | HR    | 60000  |
| 2  | Bob   | HR    | 50000  |
| 3  | Carol | Sales | 70000  |
| 4  | Dave  | Sales | 72000  |
| 5  | Eve   | Sales | 71000  |
#### ✅ Example: Ranking Employees by Salary Within Each Department
```roomsql
SELECT name, dept, salary,
       ROW_NUMBER() OVER (PARTITION BY dept ORDER BY salary DESC) AS row_num
FROM employee;
```
### 📤 Output
| name  | dept  | salary | row\_num |
| ----- | ----- | ------ | -------- |
| Alice | HR    | 60000  | 1        |
| Bob   | HR    | 50000  | 2        |
| Dave  | Sales | 72000  | 1        |
| Eve   | Sales | 71000  | 2        |
| Carol | Sales | 70000  | 3        |
---
### 💡 Notes
* `PARTITION BY` dept: resets row numbering for each department.
* `ORDER BY` salary DESC: ranks higher salary employees first.
* `ROW_NUMBER()` always returns unique values even if there are ties.
* To treat ties equally, use `RANK()` or `DENSE_RANK()` instead.

