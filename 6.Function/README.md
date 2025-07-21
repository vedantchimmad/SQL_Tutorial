# 🧬 SQL Functions

---
## 📌 What Are Row-Level Functions?

Row-level functions (also called **scalar functions**) operate **on individual rows** and return a **single value** per row.

They do **not** operate on groups of rows (unlike aggregate functions).

---

### 🧩 Types of Row-Level Functions

#### 🔠 1. String Functions

| Function      | Description                                 | Example                         |
|---------------|---------------------------------------------|---------------------------------|
| `UPPER()`     | Converts to uppercase                       | `UPPER('sql') → 'SQL'`         |
| `LOWER()`     | Converts to lowercase                       | `LOWER('SQL') → 'sql'`         |
| `LENGTH()`    | Returns number of characters                | `LENGTH('Data') → 4`           |
| `SUBSTRING()` | Extracts part of string                     | `SUBSTRING('Hello', 2, 3)`     |
| `TRIM()`      | Removes whitespace                          | `TRIM('  sql ') → 'sql'`       |
| `CONCAT()`    | Joins two or more strings                   | `CONCAT('Data', 'Base')`       |

---

#### 🔢 2. Numeric Functions

| Function      | Description                        | Example                    |
|---------------|------------------------------------|----------------------------|
| `ABS()`       | Absolute value                     | `ABS(-7) → 7`              |
| `CEIL()`      | Rounds up to next integer          | `CEIL(4.2) → 5`            |
| `FLOOR()`     | Rounds down to previous integer    | `FLOOR(4.8) → 4`           |
| `ROUND()`     | Rounds to given decimal places     | `ROUND(3.456, 2) → 3.46`   |
| `POWER()`     | Exponentiation                     | `POWER(2, 3) → 8`          |
| `MOD()`       | Returns remainder                  | `MOD(10, 3) → 1`           |

---

#### 📅 3. Date & Time Functions

| Function         | Description                         | Example                          |
|------------------|-------------------------------------|----------------------------------|
| `CURRENT_DATE`   | Returns today's date                | `2025-07-15`                     |
| `CURRENT_TIME`   | Returns current time                | `14:35:22`                       |
| `NOW()`          | Returns current date and time       | `2025-07-15 14:35:22`            |
| `DATEADD()`      | Adds interval to date               | `DATEADD(day, 5, '2025-07-10')`  |
| `DATEDIFF()`     | Difference between dates            | `DATEDIFF(day, '2025-07-10', '2025-07-15') → 5` |
| `EXTRACT()`      | Extracts part of a date             | `EXTRACT(YEAR FROM '2025-07-15') → 2025` |

---

### 🔍 Example Query

```sql
SELECT 
  name,
  UPPER(name) AS upper_name,
  ROUND(salary * 1.1, 2) AS updated_salary,
  LENGTH(name) AS name_length
FROM employees;
```
---
### 📘 Single Row Functions vs Multi Row Functions
| Feature                | 🔹 **Single Row Functions**         | 🔸 **Multi Row Functions**                    |
| ---------------------- | ----------------------------------- | --------------------------------------------- |
| **Definition**         | Operate on each **individual row**  | Operate on **group of rows (entire column)**  |
| **Returns**            | One result per row                  | One result for **multiple rows**              |
| **Used In**            | `SELECT`, `WHERE`, `ORDER BY`       | `SELECT` (with `GROUP BY` or standalone)      |
| **Also Called**        | **Scalar functions**                | **Aggregate functions**                       |
| **Examples**           | `UPPER()`, `ROUND()`, `SUBSTRING()` | `SUM()`, `AVG()`, `MAX()`, `MIN()`, `COUNT()` |
| **Grouping Required?** | ❌ No                                | ✅ Often used with `GROUP BY`                  |

---


# Functions

---
SQL functions are used to perform calculations on data and to modify the individual data items

### SQL functions are divided into 2 types

1. Single Row functions
2. Multi row functions

## Single row functions
* The no of input rows are equal to the no of outputs

### Numeric functions
* which can be used to perform mathematical calculations.

#### 1. SQRT()

* It takes any numeric values and returns the square root value of that number.
Syntax:
```roomsql
SELECT SQRT(..value..)
```
Example:
```roomsql
SELECT SQRT(100)
```
#### 2.PI()
* Using pi() function, value of PI can be used anywhere in the query.

Syntax:
```roomsql
SELECT PI()
```
Example:
```roomsql
SELECT PI()
```
#### 3.SQUARE()
* SQUARE() function is used to find the square of any number.

Syntax:
```roomsql
SELECT SQUARE(..value..)
```
Example:
```roomsql
SELECT SQUARE(12)
```
#### 4.ROUND()
* ROUND() function is used to round a value to the nearest specified decimal place.

Syntax:
```roomsql
SELECT ROUND(..value.., number_of_decimal_places)
```
Example:
```roomsql
SELECT ROUND(125.315,2)
```
#### 5.CEILING()
* CEILING() function is used to find the next highest value (integer).

Syntax:
```roomsql
SELECT CEILING(..value..)
```
Example:
```roomsql
SELECT CEILING(45.56)
```
#### 6.FLOOR()
* FLOOR() function returns the next lowest value (integer).

Syntax:
```roomsql
SELECT FLOOR(..value..)
```
Example:
```roomsql
SELECT FLOOR(45.56)
```
### Character function

### 1.Case Manipulation
#### 1.UPPER
* Function is used to convert all the character in a string into Uppercase

Syntax:
```roomsql
UPPER(literal/Column_name)
```
Example:
```roomsql
SELECT  UPPER(“sql”) from dual;
```
#### 2.LOWER
* Function is used to convert all the character in a string into lowecase

Syntax: 
```roomsql
LOWER(literal/Column_name)
```
Example:
```roomsql
SELECT  LOwer(“SQL”) from dual;
```
#### 3.INITCAP
* This function converts alpha character values to uppercase for the first letter of each word and all others in lowercase.

Syntax: 
```roomsql
INITCAP(literal/Column_name)
```
Example: 
```roomsql
SELECT INITCAP('geeksforgeeks is a computer science portal for geeks') FROM DUAL;
```
### 2.Character Manipulation
#### 1.REPLACE
* This function is used to replace substring from a given string

Syntax: 
```roomsql
REPLACE(string, Substring to be replaced, New string)
```
Example: 
```roomsql
SELECT REPLACE(“JAVA”, “J”, ”L”) from dual;
```
#### 2.SUBSTR
* This function is used to extract the substring from a given string
* The extraction of a substring happens from LHS to RHS

Syntax: 
```roomsql
SUBSTR(string, starting position, length(optional))
```
Example: 
```roomsql
SELECT SUBSTR(“SPIDER” ,2,3) FROM DUAL;
```
#### 3.CONCAT
* This function is used to merge the 2 literals or columns
* Concat function always accepts 2 parameter

Syntax:
```roomsql
CONCAT(STRING1,STRING2)
```
Example: 
```roomsql
SELECT CONCAT(CONCAT(FNAME,SAL)JOB) FROM EMP
```
#### 4.LENGTH
* This function is used to find the length of a given string

Syntax: 
```roomsql
LENGTH(literals/Column_name)
```
Example: 
```roomsql
select length(ename) from emp
```
#### 5.TRIM
* This function is used to remove the specified character from given string
* The deferent types of trim functions are
1. LTRIM
2. RTRIM
3. TRIM

#### 1. LTRIM
* This function is used is used to remove all specified characters from the LHS of a given string

Syntax: 
```roomsql
LTRIM(string, trim-string)
```
Example: 
```roomsql
select LTRIM(“vedant”, “ev”) from dual;
```
#### 2. RTRIM
* This function is used to remove the specified characters from the RHS of a given string

Syntax: 
```roomsql
RTRIM(string, trim-string)
```
Example: 
```roomsql
select RTRIM(“QSPIDER”, “QSP”) FROM DUAL;
```
#### 6.INSTR function
* This function is used to find the position of a substring from a given string based on no of occurrence

Syntax: 
```roomsql
INSTR(String, substring, starting position, no of occurrence)
```
Example: 
```roomsql
SELECT( “QSPIDERS”, ”S”, 1,1) from dual
```
### Date function
* The format of the data in the table must be matched with the input data to insert.
* DATE	format YYYY-MM-DD
* DATETIME	format: YYYY-MM-DD HH:MI: SS
* TIMESTAMP	format: YYYY-MM-DD HH:MI: SS
* YEAR	format YYYY or YY
#### 1.NOW()
* Returns the current date and time

Syntax:
```roomsql
SELECT NOW()
```
#### 2.CURDATE() or CUR_DATE()
* Returns the current date

Syntax: 
```roomsql
SELECT CURDATE()
```
#### 3.CURTIME() or CUR_TIME()
* Returns the current time

Syntax: 
```roomsql
SELECT CURTIME()
```
#### 4.DATE()
* Extracts the date part of a date or date/time expression. Example: For the below table named ‘Test’

Syntax: 
```roomsql
SELECT Name, DATE(BirthTime)
AS BirthDate FROM Test;
```
#### 5.EXTRACT()
* Returns a single part of a date/time.
* Several units can be considered but only some are used such as MICROSECOND, SECOND, MINUTE, HOUR, DAY, WEEK, MONTH, QUARTER, YEAR, etc. And ‘date’ is a valid date expression.

Syntax: 
```roomsql
EXTRACT(unit FROM date);
```
Example:
```roomsql
SELECT Name, Extract(DAY FROM
BirthTime) AS BirthDay FROM Test;
```
#### 6.DATE_ADD()
* Adds a specified time interval to date

Syntax: 
```roomsql
DATE_ADD(date, INTERVAL expr type);
```
Example:
```roomsql
SELECT Name, DATE_ADD(BirthTime, INTERVAL
1 YEAR) AS BirthTimeModified FROM Test;
```
#### 7.DATE_SUB()
* Subtracts a specified time interval from a date.

Syntax: 
```roomsql
DATE_SUB(date, INTERVAL expr type);
```
Example:
```roomsql
SELECT Name, DATE_SUB(BirthTime, INTERVAL
1 YEAR) AS BirthTimeModified FROM Test;
```
#### 8.DATEDIFF()
* Returns the number of days between two dates

Syntax: 
```roomsql
DATEDIFF(date1, date2);
```
Example: 
```roomsql
SELECT DATEDIFF('2017-01-13','2017-01-03') AS DateDiff;
```
#### 9.DAY()
* It returns the day portion of a date value.

Syntax: 
```roomsql
SELECT DAY("2018-07-16");
```
#### 10.DAYNAME()
* It returns the weekday name for a date.

Syntax: 
```roomsql
SELECT DAYNAME('2008-05-15');
```
#### 11.MONTHNAME()
* It returns the full month name for a date.

Syntax: 
```roomsql
SELECT MONTHNAME("2018/07/18");
```
#### 12.TO_DAYS()
* It converts a date into numeric days.

Syntax: 
```roomsql
SELECT TO_DAYS("2018-07-18");
```
### Null function
* This functions are basically used to perform on null values
* IS NULL and IS NOT NULL Keywords are used to check null values
#### 1.ISNULL()
* In SQL Server, ISNULL() function is used to replace NULL values. 

Syntax: 
```roomsql
SELECT column(s), ISNULL(column_name, value_to_replace) FROM table_name;
```
#### 2.IFNULL()
* If the first argument is not NULL, the function returns the first argument. Otherwise, the second argument is returned.

Syntax: 
```roomsql
SELECT column(s), IFNULL(column_name, value_to_replace)
FROM table_name;
```
#### 3.COALESCE()
* COALESCE function in SQL returns the first non-NULL expression among its arguments.

Syntax: 
```roomsql
SELECT column(s), CAOLESCE(expression_1,….,expression_n)
FROM table_name;
```
Example:
```roomsql
SELECT Name, COALESCE(Phone1, Phone2) AS Contact
FROM Contact_info;
```
#### 4.NULLIF()
* The NULLIF function takes two arguments. If the two arguments are equal, then NULL is returned. Otherwise, the first argument is returned. 

Syntax: 
```roomsql
SELECT column(s), NULLIF(expression1, expression2)
FROM table_name;
```
### Conversion function
### I.Implicit data type conversion
* In this type of conversion, the data is converted from one type to another implicitly (by itself/automatically).

Example: 
```roomsql
SELECT employee_id,first_name,salary
FROM employees
WHERE salary > '15000';
```
### II.Explicit data type conversion
* In this type of conversion, the data is converted from one type to another explicitly (by the user).
#### 1.TO_CHAR()
* TO_CHAR function is used to typecast a numeric or date input to a character type with a format model (optional).

Example: 
```roomsql
TO_CHAR(number1, [format], [nls_parameter])
```
#### 2.TO_CHAR() with Dates
* Can include any valid date format element in the query

Syntax: 
```roomsql
TO_CHAR(date, ’format_model’)
```
Example: 
```roomsql
SELECT employee_id, TO_CHAR(hire_date, ’MM/YY’) Month_Hired
FROM employees
WHERE last_name = ’Higgins’;
```
#### 3.TO_NUMBER()
* Convert a character string to a number format

Syntax:
```roomsql
TO_NUMBER(char[, ’format_model’])
```
#### 4.TO_DATE()
* Convert a character string to a date format

Syntax: 
```roomsql
TO_DATE(char[, ’format_model’])
```
### Aggregate functions
* In database management an aggregate function is a function where the values of multiple rows are grouped together as input on certain criteria to form a single value of more significant meaning.
#### Various Aggregate Functions
#### 1.Count()
* It will return non null values

Syntax: 
```roomsql
count(salary)
```
#### 2.Sum()
* Returns sum of non null values

Syntax: 
```roomsql
SUM(salary)
```
#### 3.Avg()
* Return avg of non null values

Syntax: 
```roomsql
Avg(salary)=Sum(salary) / count(salary)
```
#### 4.Min()
* Minimum value in the salary column except NULL

Syntax: 
```roomsql
Min(salary)
```
#### 5) Max()
* Maximum value in the salary

Syntax: 
Max(salary)
#### 6)First()
* The FIRST() function returns the first value of the selected column. 

Syntax:
```roomsql
SELECT FIRST(column_name) FROM table_name;
```
#### 7)Last()
* The LAST() function returns the last value of the selected column. 

Syntax: 
```roomsql
SELECT LAST(column_name) FROM table_name;
```
## Window function 
Window functions apply to aggregate and ranking functions over a particular window
* OVER clause is used with window functions to define that window.
* Partitions rows to form a set of rows.(PARTITION BY clause is used)
* Orders rows within those partitions into a particular order. (ORDER BY clause is used) 
1) ### Aggregate window function
aggregate functions such as SUM(), COUNT(), AVERAGE(), MAX(), and MIN() applied over a particular window (set of rows) are called aggregate window functions.
```roomsql
SELECT Name, Age, Department, Salary, 
 AVG(Salary) OVER( PARTITION BY Department) AS Avg_Salary
 FROM employee
```
2) ### RANK
As the name suggests, the rank function assigns rank to all the rows within every partition. Rank is assigned such that rank 1 given to the first row and rows having same value are assigned same rank. For the next rank after two same rank values, one rank value will be skipped.
```roomsql
SELECT Name, Age, Department, Salary, 
 RANK() OVER( PARTITION BY Department) AS rank_sallery 
 FROM employee
```
3) ### DENSE_RANK
It assigns rank to each row within partition. Just like rank function first row is assigned rank 1 and rows having same value have same rank.
```roomsql
SELECT Name, Age, Department, Salary, 
 DENSE_RANK() OVER( PARTITION BY Department) AS rank_sallery 
 FROM employee
```
4) ### ROW_NUMBER
ROW_NUMBER() gives each row a unique number. It numbers rows from one­ to the total rows. The rows are put into groups base­d on their values.
```roomsql
SELECT Name, Age, Department, Salary, 
 ROW_NUMBER() OVER( PARTITION BY Department) AS rn 
 FROM employee
```