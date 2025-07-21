# 🗓️ Date and Time Functions in SQL

---
SQL provides a variety of **Date and Time** functions to manipulate and retrieve temporal data such as dates, times, and timestamps.

---

### 📆 Common Date & Time Functions

| Function             | Description                                           | Example                                | Output (Example)      |
|----------------------|-------------------------------------------------------|----------------------------------------|------------------------|
| `CURRENT_DATE`       | Returns the current date                             | `SELECT CURRENT_DATE;`                 | `2025-07-15`           |
| `CURRENT_TIME`       | Returns the current time                             | `SELECT CURRENT_TIME;`                 | `14:53:23`             |
| `NOW()`              | Returns current date and time (timestamp)            | `SELECT NOW();`                        | `2025-07-15 14:53:23`  |
| `SYSDATE()`          | Returns current date and time (differs slightly from `NOW`) | `SELECT SYSDATE();`               | `2025-07-15 14:53:30`  |
| `GETDATE()`          | Returns current date and time (SQL Server)           | `SELECT GETDATE();`                    | `2025-07-15 14:53:40`  |
| `DATE()`             | Extracts the date part from a datetime                | `SELECT DATE(NOW());`                  | `2025-07-15`           |
| `DAY(date)`          | Returns day of the month                             | `DAY('2025-07-15')`                    | `15`                   |
| `MONTH(date)`        | Returns month number                                 | `MONTH('2025-07-15')`                  | `7`                    |
| `YEAR(date)`         | Returns the year                                     | `YEAR('2025-07-15')`                   | `2025`                 |
| `HOUR(time)`         | Returns hour portion                                 | `HOUR('14:53:23')`                     | `14`                   |
| `MINUTE(time)`       | Returns minute portion                               | `MINUTE('14:53:23')`                   | `53`                   |
| `SECOND(time)`       | Returns second portion                               | `SECOND('14:53:23')`                   | `23`                   |
| `DATEDIFF(d1, d2)`   | Returns difference between two dates (in days)       | `DATEDIFF('2025-07-15', '2025-07-01')` | `14`                   |
| `DATE_ADD(date, INTERVAL x unit)` | Adds a time interval                   | `DATE_ADD('2025-07-15', INTERVAL 5 DAY)` | `2025-07-20`         |
| `DATE_SUB(date, INTERVAL x unit)` | Subtracts a time interval             | `DATE_SUB('2025-07-15', INTERVAL 1 MONTH)` | `2025-06-15`      |
| `EXTRACT(unit FROM date)` | Extracts part of date                          | `EXTRACT(YEAR FROM '2025-07-15')`      | `2025`                 |
| `STR_TO_DATE()`      | Converts string to date                              | `STR_TO_DATE('15-07-2025','%d-%m-%Y')` | `2025-07-15`           |
| `FORMAT(date, format)` | Formats the date to a specific pattern (MySQL)    | `FORMAT(NOW(), 'dd-MM-yyyy')`          | `15-07-2025`           |

---

## 🔄 Example Query

```roomsql
SELECT
  NOW() AS current_datetime,
  DATE(NOW()) AS current_date,
  DAY(NOW()) AS day,
  MONTH(NOW()) AS month,
  YEAR(NOW()) AS year,
  DATEDIFF(NOW(), '2025-01-01') AS days_passed_this_year;
```