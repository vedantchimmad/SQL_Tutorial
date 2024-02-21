# Subquery

---
In SQL a Subquery can be simply defined as a query within another query.
**Key points**
* A subquery is a query within another query. The outer query is called as main query and inner query is called as subquery.
* Subquery must be enclosed in parentheses.
* ORDER BY command cannot be used in a Subquery. GROUPBY command can be used to perform same function as ORDER BY command.

Syntax: 
```roomsql
SELECT column_name
FROM table_name
WHERE column_name expression operator
( SELECT COLUMN_NAME  from TABLE_NAME   WHERE ... );
```
Example 1: 
```roomsql
Select NAME, LOCATION, PHONE_NUMBER from DATABASE
WHERE ROLL_NO IN
(SELECT ROLL_NO from STUDENT where SECTION=’A’);
```
Example 2: 
```roomsql
INSERT INTO Student1  SELECT * FROM Student2
```
Example 3: 
```roomsql
DELETE FROM Student2
WHERE ROLL_NO IN ( SELECT ROLL_NO
FROM Student1
WHERE LOCATION = ’chennai’);
```
Example 4: 
```roomsql
UPDATE Student2
SET NAME=’geeks’
WHERE LOCATION IN ( SELECT LOCATION
FROM Student1
WHERE NAME IN (‘Raju’,’Ravi’));
```
## Co-related subquery
* Each subquery is executed once for every row of the outer query.
* Correlated subqueries are used for row-by-row processing.

Example: 
```roomsql
SELECT last_name, salary, department_id
FROM employees outer
WHERE salary >
(SELECT AVG(salary)
FROM employees
WHERE department_id =
outer.department_id group by department_id);
```
## Grouping data
### Group By
* used to arrange identical data into groups with the help of some functions.
* Group by clause is used in the select statement to collect the records across multiple records group the result by one or more

**Features**
* The column which is present in the select statement should also be present in the group by clause.
* Where clause is used to restrict the non-grouped data and it should be present before the group by clause.
* Having clause is used to restrict the grouped data and it should be present in after the group by clause
* Where clause and having clause are optional and it is used only on a certain condition
* We can’t use group by function in where clause.
* Order by clause should be present always at the end of the query

Syntax:
```roomsql
SELECT column1, function_name(column2)
FROM table_name
WHERE condition
GROUP BY column1, column2
HAVING condition
ORDER BY column1, column2;
```
Example:
```roomsql
SELECT NAME, SUM(sal) FROM Emp
GROUP BY name
HAVING SUM(sal)>3000;
```
### Order by
* used to sort the fetched data in either ascending or descending according to one or more columns.

**Rule**
* By default ORDER BY sorts the data in ascending order.
* We can use the keyword DESC to sort the data in descending order and the keyword ASC to sort in ascending order.

Syntax:
```roomsql
SELECT * FROM table_name ORDER BY column_name ASC | DESC
OR
SELECT * FROM table_name ORDER BY column1 ASC|DESC , column2 ASC|DESC
```
Example:
```roomsql
SELECT * FROM students ORDER BY Age ASC , ROLL_NO DESC;
```
### Having clause
* HAVING clause is used to apply a filter on the result of GROUP BY based on the specified condition.

Syntax:
```roomsql
SELECT col_1, function_name(col_2)
FROM tablename
WHERE condition
GROUP BY column1, column2
HAVING Condition
ORDER BY column1, column2;
```
| Having                                                              | 	Where                                                                   |
|---------------------------------------------------------------------|--------------------------------------------------------------------------|
| In the HAVING clause it will check the condition in group of a row. | 	In the WHERE condition it will check or execute at each row individual. |
| HAVING clause can only be used with aggregate function.             | 	The WHERE Clause cannot be used with aggregate function like Having     |
| Priority Wise HAVING Clause is executed after Group By.             | 	Priority Wise WHERE is executed before Group By.                        |