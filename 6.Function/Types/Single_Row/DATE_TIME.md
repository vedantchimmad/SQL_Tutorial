# 🗓️ Date and Time Functions in SQL

---
SQL provides a variety of **Date and Time** functions to manipulate and retrieve temporal data such as dates, times, and timestamps.

---

### 📆 Common Date & Time Functions
| Function                          | Description                                 | Example                                                        | Output (Example)      |
| --------------------------------- | ------------------------------------------- | -------------------------------------------------------------- | --------------------- |
| `CURRENT_DATE`                    | Returns current date (SQL standard)         | `SELECT CURRENT_DATE;`                                         | `2025-07-15`          |
| `CURRENT_TIME`                    | Returns current time                        | `SELECT CURRENT_TIME;`                                         | `14:20:00`            |
| `CURRENT_TIMESTAMP`               | Returns date + time                         | `SELECT CURRENT_TIMESTAMP;`                                    | `2025-07-15 14:20:00` |
| `NOW()`                           | Returns current datetime (MySQL/PostgreSQL) | `SELECT NOW();`                                                | `2025-07-15 14:20:00` |
| `SYSDATE()`                       | Current date-time at execution (MySQL)      | `SELECT SYSDATE();`                                            | `2025-07-15 14:20:02` |
| `GETDATE()`                       | Current datetime (SQL Server)               | `SELECT GETDATE();`                                            | `2025-07-15 14:20:03` |
| `GETUTCDATE()`                    | UTC date & time (SQL Server)                | `SELECT GETUTCDATE();`                                         | `2025-07-15 08:50:00` |
| `DATE()`                          | Extracts date part from datetime (MySQL)    | `SELECT DATE(NOW());`                                          | `2025-07-15`          |
| `TIME()`                          | Extracts time part from datetime (MySQL)    | `SELECT TIME(NOW());`                                          | `14:20:00`            |
| `DAY(date)`                       | Day of the month                            | `DAY('2025-07-15')`                                            | `15`                  |
| `MONTH(date)`                     | Month (1-12)                                | `MONTH('2025-07-15')`                                          | `7`                   |
| `YEAR(date)`                      | Year                                        | `YEAR('2025-07-15')`                                           | `2025`                |
| `DAYNAME(date)`                   | Returns weekday name (MySQL)                | `DAYNAME('2025-07-15')`                                        | `Tuesday`             |
| `MONTHNAME(date)`                 | Returns month name                          | `MONTHNAME('2025-07-15')`                                      | `July`                |
| `DAYOFWEEK(date)`                 | Weekday number (1=Sunday)                   | `DAYOFWEEK('2025-07-15')`                                      | `3`                   |
| `DAYOFYEAR(date)`                 | Day number in the year (1-366)              | `DAYOFYEAR('2025-07-15')`                                      | `196`                 |
| `QUARTER(date)`                   | Returns quarter (1 to 4)                    | `QUARTER('2025-07-15')`                                        | `3`                   |
| `WEEK(date)`                      | Returns week number of year                 | `WEEK('2025-07-15')`                                           | `29`                  |
| `DATEDIFF(d1, d2)`                | Difference in days between two dates        | `DATEDIFF('2025-07-15', '2025-07-01')`                         | `14`                  |
| `TIMESTAMPDIFF(unit, d1, d2)`     | Difference in years, months, etc. (MySQL)   | `TIMESTAMPDIFF(YEAR, '2000-01-01', '2025-01-01')`              | `25`                  |
| `DATE_ADD(date, INTERVAL x unit)` | Adds time to date                           | `DATE_ADD('2025-07-15', INTERVAL 5 DAY)`                       | `2025-07-20`          |
| `DATE_SUB(date, INTERVAL x unit)` | Subtracts time                              | `DATE_SUB('2025-07-15', INTERVAL 2 MONTH)`                     | `2025-05-15`          |
| `EXTRACT(unit FROM date)`         | Extracts year, month, etc.                  | `EXTRACT(MONTH FROM '2025-07-15')`                             | `7`                   |
| `STR_TO_DATE()`                   | Convert string to date (MySQL)              | `STR_TO_DATE('15-07-2025','%d-%m-%Y')`                         | `2025-07-15`          |
| `DATE_FORMAT(date, format)`       | Format date (MySQL)                         | `DATE_FORMAT(NOW(), '%d-%m-%Y')`                               | `15-07-2025`          |
| `FORMAT(date, format)`            | Format value or date                        | `FORMAT(NOW(), 'dd-MM-yyyy')`                                  | `15-07-2025`          |
| `TO_CHAR(date, format)`           | Convert to string (Oracle/Postgres)         | `TO_CHAR(NOW(), 'YYYY-MM-DD')`                                 | `2025-07-15`          |
| `TO_DATE(string, format)`         | Convert string to date (Oracle/Postgres)    | `TO_DATE('15-07-2025', 'DD-MM-YYYY')`                          | `2025-07-15`          |
| `TO_TIMESTAMP()`                  | Converts to timestamp                       | `TO_TIMESTAMP('2025-07-15 14:20:00', 'YYYY-MM-DD HH24:MI:SS')` | `2025-07-15 14:20:00` |

### 📆 Advanced Date-Time Functions (by SQL dialect)
| Function                 | Description                                          | Example                                 | Output Example            | Dialect       |
| ------------------------ | ---------------------------------------------------- | --------------------------------------- | ------------------------- | ------------- |
| `DATE_TRUNC(part, date)` | Truncates a date to a specified precision            | `DATE_TRUNC('month', '2025-07-15')`     | `2025-07-01 00:00:00`     | PostgreSQL    |
| `TRUNC(date, 'unit')`    | Truncates to date part (like month/year)             | `TRUNC(SYSDATE, 'MM')`                  | `2025-07-01`              | Oracle        |
| `DATENAME(part, date)`   | Returns name of part (e.g., weekday name)            | `DATENAME(WEEKDAY, GETDATE())`          | `Tuesday`                 | SQL Server    |
| `DATEPART(part, date)`   | Extracts part of date as integer                     | `DATEPART(MONTH, GETDATE())`            | `7`                       | SQL Server    |
| `EOMONTH(date)`          | Returns last day of the month                        | `EOMONTH('2025-07-15')`                 | `2025-07-31`              | SQL Server    |
| `LAST_DAY(date)`         | Returns last day of month                            | `LAST_DAY('2025-07-15')`                | `2025-07-31`              | Oracle, MySQL |
| `ADD_MONTHS(date, n)`    | Add/subtract months                                  | `ADD_MONTHS(SYSDATE, 2)`                | `2025-09-15`              | Oracle        |
| `NEXT_DAY(date, 'DAY')`  | Next given weekday from date                         | `NEXT_DAY(SYSDATE, 'FRIDAY')`           | `2025-07-18`              | Oracle        |
| `SYSDATE`                | Current date-time (differs from `CURRENT_TIMESTAMP`) | `SELECT SYSDATE FROM DUAL`              | `2025-07-15 14:20:00`     | Oracle        |
| `SYSUTCDATETIME()`       | Current UTC datetime                                 | `SELECT SYSUTCDATETIME()`               | `2025-07-15 08:50:00.123` | SQL Server    |
| `FROM_UNIXTIME(ts)`      | Converts Unix timestamp to readable format           | `FROM_UNIXTIME(1626345600)`             | `2021-07-15 00:00:00`     | MySQL         |
| `UNIX_TIMESTAMP(date)`   | Converts date to Unix timestamp                      | `UNIX_TIMESTAMP('2025-07-15 00:00:00')` | `1752537600`              | MySQL         |
| `ISDATE(value)`          | Checks if string is valid date                       | `ISDATE('2025-07-15')`                  | `1` (true)                | SQL Server    |

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