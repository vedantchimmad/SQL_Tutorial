# ⏪ SQL Window Function: LAG()

---
### 📘 What is LAG()?

The `LAG()` function allows you to access **a value from a previous row** in the same result set, based on the `ORDER BY` clause. It’s useful for comparing the current row to a **previous row** (e.g., trends, changes).

### 🧾 Syntax

```roomsql
SELECT column1, column2,
       LAG(target_column, offset, default_value)
       OVER (PARTITION BY partition_column ORDER BY sort_column) AS previous_value
FROM table_name;
```
* `target_column`: Column from which to fetch the previous value.
* `offset`: (Optional) Number of rows behind to look. Default is 1.
* `default_value`: (Optional) Value returned if no previous row exists. Default is NULL.
---
### 🧪 Sample Table: sales
| id | employee | month | sales |
| -- | -------- | ----- | ----- |
| 1  | Alice    | Jan   | 2000  |
| 2  | Alice    | Feb   | 2500  |
| 3  | Alice    | Mar   | 1800  |
| 4  | Bob      | Jan   | 3000  |
| 5  | Bob      | Feb   | 2800  |
#### ✅ Example: Show current and previous month's sales
```roomsql
SELECT employee, month, sales,
       LAG(sales) OVER (PARTITION BY employee ORDER BY month) AS previous_month_sales
FROM sales;
```
### 📤 Output
| employee | month | sales | previous\_month\_sales |
| -------- | ----- | ----- | ---------------------- |
| Alice    | Jan   | 2000  | NULL                   |
| Alice    | Feb   | 2500  | 2000                   |
| Alice    | Mar   | 1800  | 2500                   |
| Bob      | Jan   | 3000  | NULL                   |
| Bob      | Feb   | 2800  | 3000                   |
---
### 🔁 Related Functions
* `LEAD()` – accesses the next row
* `LAG()` – accesses the previous row
* `ROW_NUMBER()` – ranks rows in order
