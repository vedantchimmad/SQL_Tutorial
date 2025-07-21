# 🔤 String Functions in SQL

---
SQL provides several **string functions** that help manipulate text data. These are **Single Row Functions**, meaning they operate on one row at a time.

---

### ✨ Common String Functions

| Function                     | Description                              | Example                                     | Output             |
|------------------------------|------------------------------------------|---------------------------------------------|--------------------|
| `UPPER(str)`                 | Converts string to uppercase             | `UPPER('sql')`                              | `'SQL'`            |
| `LOWER(str)`                 | Converts string to lowercase             | `LOWER('SQL')`                              | `'sql'`            |
| `LENGTH(str)`                | Returns number of characters             | `LENGTH('Data')`                            | `4`                |
| `SUBSTRING(str, start, len)` | Extracts part of the string              | `SUBSTRING('Database', 1, 4)`               | `'Data'`           |
| `TRIM(str)`                  | Removes spaces from both sides           | `TRIM('  SQL  ')`                           | `'SQL'`            |
| `LTRIM(str)`                 | Removes spaces from left                 | `LTRIM('  Hello')`                          | `'Hello'`          |
| `RTRIM(str)`                 | Removes spaces from right                | `RTRIM('World  ')`                          | `'World'`          |
| `REPLACE(str, old, new)`     | Replaces part of string                  | `REPLACE('Data Science', 'Science', 'Eng')` | `'Data Eng'`       |
| `CONCAT(s1, s2)`             | Concatenates strings                     | `CONCAT('Data', 'Base')`                    | `'DataBase'`       |
| `CONCAT_WS(sep, s1, s2)`     | Concatenates with separator              | `CONCAT_WS('-', '2024','07','15')`          | `'2024-07-15'`     |
| `INSTR(str, substr)`         | Returns position of substring            | `INSTR('Database', 'base')`                 | `5`                |
| `CHARINDEX(substr, str)`     | Position (SQL Server)                    | `CHARINDEX('a', 'Data')`                    | `2`                |
| `REVERSE(str)`               | Reverses the string                      | `REVERSE('SQL')`                            | `'LQS'`            |
| `LEFT(str, n)`               | Gets first `n` characters                | `LEFT('Database', 4)`                       | `'Data'`           |
| `RIGHT(str, n)`              | Gets last `n` characters                 | `RIGHT('Database', 4)`                      | `'base'`           |
| `ASCII(char)`                | ASCII value of character                 | `ASCII('A')`                                | `65`               |
| `CHAR(code)`                 | Character from ASCII code                | `CHAR(66)`                                  | `'B'`              |
| `INITCAP(str)`               | Capitalizes first letter of each word    | `INITCAP('hello world')`                    | `'Hello World'`    |
| `SPACE(n)`                   | Inserts `n` spaces                       | `SPACE(3)`                                  | `'   '`            |
| `REPLICATE(str, n)`          | Repeats string `n` times                 | `REPLICATE('-', 5)`                         | `'-----'`          |
---

### 🧠 Example Usage

```roomsql
SELECT 
  name,
  UPPER(name) AS upper_name,
  LENGTH(name) AS name_length,
  TRIM(name) AS trimmed_name,
  SUBSTRING(name, 1, 3) AS short_name
FROM employees;
```