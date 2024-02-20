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