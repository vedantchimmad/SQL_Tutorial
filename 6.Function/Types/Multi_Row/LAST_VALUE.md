# 🔚 SQL Window Function: LAST_VALUE()

---
### 📘 What is LAST_VALUE()?

The `LAST_VALUE()` function returns the **last value** in an ordered window (partition) of rows. It's useful to compare every row in a group to the **last value** of that group.

### 🧾 Syntax

```roomsql
SELECT column1, column2,
       LAST_VALUE(target_column)
       OVER (
         PARTITION BY partition_column 
         ORDER BY sort_column 
         ROWS BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING
       ) AS last_val
FROM table_name;
```
> 🔁 ROWS BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING is often required to ensure the window includes the full partition.
---
### 🧪 Sample Table: sales
| id | employee | month | sales |
| -- | -------- | ----- | ----- |
| 1  | Alice    | Jan   | 2000  |
| 2  | Alice    | Feb   | 2500  |
| 3  | Alice    | Mar   | 1800  |
| 4  | Bob      | Jan   | 3000  |
| 5  | Bob      | Feb   | 2800  |
#### ✅ Example: Show each row’s sales and last month's sales for the employee
```roomsql
SELECT employee, month, sales,
       LAST_VALUE(sales) OVER (
         PARTITION BY employee 
         ORDER BY month 
         ROWS BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING
       ) AS last_month_sales
FROM sales;
```
### 📤 Output
| employee | month | sales | last\_month\_sales |
| -------- | ----- | ----- | ------------------ |
| Alice    | Jan   | 2000  | 1800               |
| Alice    | Feb   | 2500  | 1800               |
| Alice    | Mar   | 1800  | 1800               |
| Bob      | Jan   | 3000  | 2800               |
| Bob      | Feb   | 2800  | 2800               |
---
### 🔁 Related Functions
* `FIRST_VALUE()` – returns the first value in the partition
* `LAG()` / `LEAD()` – access previous/next values
* `ROW_NUMBER()` – row numbering in window