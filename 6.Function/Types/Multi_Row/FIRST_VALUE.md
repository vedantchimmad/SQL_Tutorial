# 🥇 SQL Window Function: FIRST_VALUE()

---
### 📘 What is FIRST_VALUE()?

The `FIRST_VALUE()` function returns the **first value** in an ordered window (partition) of rows. It's often used to **compare each row** to the first row in a group.

### 🧾 Syntax

```roomsql
SELECT column1, column2,
       FIRST_VALUE(target_column)
       OVER (PARTITION BY partition_column ORDER BY sort_column) AS first_val
FROM table_name;
```
* `target_column`: The column from which to retrieve the first value.
* `PARTITION BY`: Divides data into groups (optional).
* `ORDER BY`: Determines the order within each partition.
---
### 🧪 Sample Table: sales
| id | employee | month | sales |
| -- | -------- | ----- | ----- |
| 1  | Alice    | Jan   | 2000  |
| 2  | Alice    | Feb   | 2500  |
| 3  | Alice    | Mar   | 1800  |
| 4  | Bob      | Jan   | 3000  |
| 5  | Bob      | Feb   | 2800  |
#### ✅ Example: Show each month's sales and first month’s sales for each employee
```roomsql
SELECT employee, month, sales,
       FIRST_VALUE(sales) OVER (PARTITION BY employee ORDER BY month) AS first_month_sales
FROM sales;
```
### 📤 Output
| employee | month | sales | first\_month\_sales |
| -------- | ----- | ----- | ------------------- |
| Alice    | Jan   | 2000  | 2000                |
| Alice    | Feb   | 2500  | 2000                |
| Alice    | Mar   | 1800  | 2000                |
| Bob      | Jan   | 3000  | 3000                |
| Bob      | Feb   | 2800  | 3000                |
---
### 🔁 Related Functions
* `LAST_VALUE()` – gets the last value in the window
* `LAG()` / `LEAD()` – get previous/next values
* `ROW_NUMBER()` – assign a row number by order


