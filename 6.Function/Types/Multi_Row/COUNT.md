# 🔢 SQL Window Function: COUNT()

---
### 📘 What is COUNT() as a Window Function?

The `COUNT()` window function returns the **number of rows** in the current window frame. Unlike `GROUP BY`, it doesn’t reduce the number of rows — it just adds a count value per row based on the window.

### 🧾 Syntax

```roomsql
SELECT column1, column2,
       COUNT(column_name) OVER (
           [PARTITION BY partition_column]
           [ORDER BY order_column]
           [ROWS BETWEEN frame_start AND frame_end]
       ) AS count_output
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

#### ✅ Example: Row Count per Department
```roomsql
SELECT name, dept, salary,
       COUNT(*) OVER (PARTITION BY dept) AS dept_count
FROM employee;
```
### 📤 Output
| name  | dept  | salary | dept\_count |
| ----- | ----- | ------ | ----------- |
| Alice | HR    | 60000  | 2           |
| Bob   | HR    | 50000  | 2           |
| Carol | Sales | 70000  | 3           |
| Dave  | Sales | 72000  | 3           |
| Eve   | Sales | 71000  | 3           |
---
### 💡 Notes
* `PARTITION BY` dept calculates the count within each department.
* `COUNT(*)` counts all rows, even if columns contain NULLs.
* If you use `COUNT(column_name)`, it excludes NULLs from that column.