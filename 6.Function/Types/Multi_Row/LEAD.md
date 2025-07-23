# 🔄 SQL Window Function: LEAD()

---
### 📘 What is LEAD()?

The `LEAD()` function gives access to a **subsequent row's value** from the current row within the result set, based on the specified `ORDER BY`. It is commonly used to compare **current and next row values**.

### 🧾 Syntax

```roomsql
SELECT column1, column2,
       LEAD(target_column, offset, default_value)
       OVER (PARTITION BY partition_column ORDER BY sort_column) AS next_value
FROM table_name;
```
* `target_column`: The column to pull the future value from.
* `offset`: (Optional) How many rows forward to look. Default is 1.
* `default_value`: (Optional) What to return if there is no next row. Default is NULL.
---
### 🧪 Sample Table: sales
| id | employee | month | sales |
| -- | -------- | ----- | ----- |
| 1  | Alice    | Jan   | 2000  |
| 2  | Alice    | Feb   | 2500  |
| 3  | Alice    | Mar   | 1800  |
| 4  | Bob      | Jan   | 3000  |
| 5  | Bob      | Feb   | 2800  |
#### ✅ Example: Show current and next month's sales
```roomsql
SELECT employee, month, sales,
       LEAD(sales) OVER (PARTITION BY employee ORDER BY month) AS next_month_sales
FROM sales;
```
### 📤 Output
| employee | month | sales | next\_month\_sales |
| -------- | ----- | ----- | ------------------ |
| Alice    | Jan   | 2000  | 2500               |
| Alice    | Feb   | 2500  | 1800               |
| Alice    | Mar   | 1800  | NULL               |
| Bob      | Jan   | 3000  | 2800               |
| Bob      | Feb   | 2800  | NULL               |
---
### 🔁 Related Functions
* `LAG()` – fetches the previous row’s value.
* `LEAD()` – fetches the next row’s value.

