# Joins

---
* SQL Join statement is used to combine data or rows from two or more tables based on a common field between them.
### Types of Join
1. INNER JOIN
2. LEFT JOIN
3. RIGHT JOIN
4. FULL JOIN
5. NATURAL JOIN

### 1.Inner join
* The INNER JOIN keyword selects all rows from both the tables as long as the condition is satisfied. 
* It will fetch the common records from both the table

Syntax: 
```roomsql
SELECT table1.column1,table1.column2,table2.column1,....
FROM table1
INNER JOIN table2
ON table1.matching_column = table2.matching_column;
```
Example:
```roomsql
SELECT StudentCourse.COURSE_ID, Student.NAME, Student.AGE FROM Student
INNER JOIN StudentCourse
ON Student.ROLL_NO = StudentCourse.ROLL_NO;
```
### 2.Left join
* his join returns all the rows of the table on the left side of the join and matches rows for the table on the right side of the join.
* LEFT JOIN is also known as LEFT OUTER JOIN.

Syntax: 
```roomsql
SELECT table1.column1,table1.column2,table2.column1,....
FROM table1
LEFT JOIN table2
ON table1.matching_column = table2.matching_column;
```
Example: 
```roomsql
SELECT Student.NAME,StudentCourse.COURSE_ID
FROM Student
LEFT JOIN StudentCourse
ON StudentCourse.ROLL_NO = Student.ROLL_NO;
```
### 3.Right join
* This join returns all the rows of the table on the right side of the join and matching rows for the table on the left side of the join. 
* RIGHT JOIN is also known as RIGHT OUTER JOIN.

Syntax: 
```roomsql
SELECT table1.column1,table1.column2,table2.column1,....
FROM table1
RIGHT JOIN table2
ON table1.matching_column = table2.matching_column;
```
Example: 
```roomsql
SELECT Student.NAME,StudentCourse.COURSE_ID
FROM Student
RIGHT JOIN StudentCourse
ON StudentCourse.ROLL_NO = Student.ROLL_NO;
```
### 4.Full join
* FULL JOIN creates the result-set by combining results of both LEFT JOIN and RIGHT JOIN. 
* The result-set will contain all the rows from both tables.

Syntax: 
```roomsql
SELECT table1.column1,table1.column2,table2.column1,....
FROM table1
FULL JOIN table2
ON table1.matching_column = table2.matching_column;
```
Example:
```roomsql
SELECT Student.NAME,StudentCourse.COURSE_ID
FROM Student
FULL JOIN StudentCourse
ON StudentCourse.ROLL_NO = Student.ROLL_NO;
```
### 5.Self join
* a self join is a regular join that is used to join a table with itself. 

Syntax: 
```roomsql
SELECT columns
FROM table AS alias1
JOIN table AS alias2 ON alias1.column = alias2.column;
```
Example: 
```roomsql
SELECT e.employee_name AS employee,
m.employee_name AS manager FROM
GFGemployees AS e JOIN GFGemployees
AS m ON e.manager_id = m.employee_id;
```
