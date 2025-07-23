
# 📊 `NTILE()` Window Function in SQL

---
### 📘 What is NTILE()?
The `NTILE()` function is used to divide a result set into a specified number of roughly equal **buckets** or **groups**. It is commonly used for **quantile analysis**, such as quartiles or deciles.

### 🔧 Syntax

```roomsql
SELECT column1, column2, 
       NTILE(n) OVER (ORDER BY sort_column) AS bucket_column
FROM table_name;
```

- `n`: Number of groups to divide the result set into.
- `sort_column`: Determines the order in which rows are distributed.

---

### 📘 Example Table: `employees`

| employee_id | name    | salary |
|-------------|---------|--------|
| 1           | John    | 10000  |
| 2           | Alice   | 12000  |
| 3           | Bob     | 9000   |
| 4           | Charlie | 11000  |
| 5           | Dave    | 13000  |
| 6           | Eva     | 9500   |

#### 📥 Query

```roomsql
SELECT name, salary,
       NTILE(3) OVER (ORDER BY salary DESC) AS salary_group
FROM employees;
```
### 📤 Output

| name    | salary | salary_group |
|---------|--------|--------------|
| Dave    | 13000  | 1            |
| Alice   | 12000  | 1            |
| Charlie | 11000  | 2            |
| John    | 10000  | 2            |
| Eva     | 9500   | 3            |
| Bob     | 9000   | 3            |

---

### 🧠 Notes

- `NTILE(n)` distributes rows into `n` groups based on the order of a specified column.
- Groups are **as evenly sized as possible**. If the number of rows doesn't divide evenly, the first groups will have one more row than the later ones.
- Often used for **ranking**, **tiering**, or **bucket analysis**.
