# Clause 

---
### 1.Where clause
* WHERE keyword is used for fetching filtered data in a result set.

Syntax:
```roomsql
SELECT column1,column2 FROM table_name WHERE column_name operator value;
```
Q) fetch records of Employee with ages equal to 24.
```roomsql
SELECT * FROM Emp1 WHERE Age=24;
```
### 2.Using clause
* USING Clause is used to match only one column when more than one column matches.
* NATURAL JOIN and USING Clause are mutually exclusive.
* NATURAL JOIN uses all the columns with matching names and datatypes to join the tables. The USING Clause can be used to specify only those columns that should be used for an EQUIJOIN.

Q) Write SQL query to find the working location of the employees. Also give their respective employee_id and last_name?
```roomsql
SELECT e.EMPLOYEE_ID, e.LAST_NAME, d.LOCATION_ID
FROM Employees e JOIN Departments d
USING(DEPARTMENT_ID);
```
### 3.Intersect clause
* As the name suggests, the intersect clause is used to provide the result of the intersection of two select statements.

Syntax:
```roomsql
SELECT column-1, column-2 ……
FROM table 1
WHERE…..

INTERSECT

SELECT column-1, column-2 ……
FROM table 2
WHERE…..
```
Example:
```roomsql
SELECT ID, Name, Bonus
FROM
table1
LEFT JOIN
table2
ON table1.ID = table2.Employee_ID

INTERSECT

SELECT ID, Name, Bonus
FROM
table1
RIGHT JOIN
table2
ON table1.ID = table2.Employee_ID;
```
### 4.Except clause
* contains all the rows that are returned by the first SELECT operation, and not returned by the second SELECT operation. 

Syntax:
```roomsql
SELECT column-1, column-2 ……
FROM table 1
WHERE…..

EXCEPT

SELECT column-1, column-2 ……
FROM table 2
WHERE…..
```
Example:
```roomsql
SELECT ID, Name, Bonus
FROM
table1
LEFT JOIN
table2
ON table1.ID = table2.Employee_ID

EXCEPT

SELECT ID, Name, Bonus
FROM
table1
RIGHT JOIN
table2
ON table1.ID = table2.Employee_ID;
```
### 5.Union clause
* The Union Clause is used to combine two separate select statements and produce the result set as a union of both select statements.
>[!NOTE:]
> 
>The fields to be used in both the select statements must be in the same order, same number, and same data type.
>
>The Union clause produces distinct values in the result set, to fetch the duplicate values too UNION ALL must be used instead of just UNION.

Syntax:
```roomsql
SELECT column_name(s) FROM table1
UNION
SELECT column_name(s) FROM table2;
```
Example:
```roomsql
SELECT ROLL_NO FROM Students UNION
SELECT ROLL_NO FROM Student_Details;
```
Syntax for UNION ALL:
* The resultant set consists of duplicatet values.
```roomsql
SELECT column_name(s) FROM table1
UNION ALL
SELECT column_name(s) FROM table2;
```

Example:
```roomsql
SELECT ROLL_NO FROM Students
UNION ALL 
SELECT ROLL_NO FROM Student_Details; 
```
### 6.Limit clause
* The LIMIT clause is used to set an upper limit on the number of tuples returned by SQL.

Example 1:
```roomsql
SELECT * FROM student LIMIT 3;
```

Example 2:
```roomsql
SELECT *FROM Student ORDER BY ROLLNO LIMIT 5 OFFSET 2;
```
or
```roomsql
SELECT *
FROM Student
ORDER BY ROLLNO LIMIT 2,5; # it skips the
first 2 values and then return the next 5 entries
```

>[!Note]
> 
>offset will skip first 2 rows
> 
>It can’t be used directly means we can use only in order by clause

### 7.With clause
* The clause is used for defining a temporary relation such that the output of this temporary relation is available and is used by the query that is associated with the WITH clause.
* The SQL WITH clause allows you to give a sub-query block a name (a process also called sub-query refactoring), which can be referenced in several places within the main SQL query. 

Syntax:
```roomsql
WITH temporaryTable (averageValue) as
(SELECT avg(Attr1)
FROM Table)
SELECT Attr1
FROM Table, temporaryTable
WHERE Table.Attr1 > temporaryTable.averageValue;
```
Example:
                
Q) Find all the employee whose salary is more than the average salary of all employees. 
```roomsql
WITH temporaryTable(averageValue) as
(SELECT avg(Salary) from Employee) SELECT EmployeeID,Name, Salary FROM Employee, temporaryTable WHERE Employee.Salary > temporaryTable.averageValue;
```
### 8.OFFSET-FETCH Clause
**Offset**
* The OFFSET argument is used to identify the starting point to return rows from a result set. Basically, it exclude the first set of records.
>[!Note:]
>
>OFFSET can only be used with ORDER BY clause. It cannot be used on its own.
>
>OFFSET value must be greater than or equal to zero. It cannot be negative, else return error.

Syntax:
```roomsql
SELECT column_name(s)
FROM table_name
WHERE condition
ORDER BY column_name
OFFSET rows_to_skip ROWS;
```
Example:
```roomsql
SELECT Fname, Lname
FROM Employee
ORDER BY Salary
OFFSET 1 ROWS;
```
**Fetch**
* The FETCH argument is used to return a set of number of rows. 
* FETCH can’t be used itself, it is used in conjunction with OFFSET.
Syntax:
```roomsql
SELECT column_name(s)
FROM table_name
ORDER BY column_name
OFFSET rows_to_skip
FETCH NEXT number_of_rows ROWS ONLY;
```
Example:
```roomsql
SELECT Fname, Lname
FROM Employee
ORDER BY Salary
OFFSET 2 ROWS
FETCH NEXT 4 ROWS ONLY;
```
### 9.With ties clause
* With ties clause will return ties records also

Example:
```roomsql
SELECT * from myTable
order by salary desc
fetch first 3 rows With Ties;
```
### 10.Top clause
* It will help to fetch top no of records

Syntax:
```roomsql
SELECT TOP value column1,column2 FROM table_name;
value: number of rows to return from top
```
Example
```roomsql
SELECT TOP 1 * FROM Customers
WHERE Country=’Spain’;
```