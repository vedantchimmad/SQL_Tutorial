# 🔁 SQL Subquery (Sub-select)

---
### 📘 What is a Subquery?

A **subquery** is a query nested inside another SQL query. It is also known as a **nested query** or **inner query**, and it returns data to the **outer query**.

### ✅ Use Cases

- Filter rows using a result from another query
- Replace temporary tables
- Compute values for use in conditions or columns

### 🧾 Syntax

```roomsql
SELECT column1
FROM table1
WHERE column2 = (SELECT column2 FROM table2 WHERE condition);
```
---
### 🧪 Example Tables
#### Employees
| id | name  | dept_id | salary |
| -- | ----- | ------- | ------ |
| 1  | Alice | 10      | 70000  |
| 2  | Bob   | 20      | 50000  |
| 3  | Carol | 10      | 80000  |

#### Departments
| dept_id | dept_name  |
| ------- | ---------- |
| 10      | Engineering |
| 20      | Marketing  |

#### 🎯 Example 1: Subquery in WHERE
Get employees in the 'Engineering' department:
```roomsql
SELECT name
FROM employees
WHERE dept_id = (
  SELECT dept_id 
  FROM departments 
  WHERE dept_name = 'Engineering'
);
```
#### 🎯 Example 2: Subquery in SELECT
Get employee names and their department name (using subquery in SELECT):
```roomsql
SELECT name,
  (SELECT dept_name 
   FROM departments 
   WHERE departments.dept_id = employees.dept_id) AS department
FROM employees;
```
#### 🎯 Example 3: Subquery in FROM
Use subquery as a temporary table:
```roomsql
SELECT avg_salary
FROM (
  SELECT AVG(salary) AS avg_salary 
  FROM employees
) AS avg_result;
```
#### 🎯 Example 4: Subquery with IN
Get employees from departments with IDs 10 or 20 (using subquery):
```roomsql
SELECT name 
FROM employees 
WHERE dept_id IN (
  SELECT dept_id 
  FROM departments 
  WHERE dept_name IN ('Engineering', 'Marketing')
);
```
#### 🎯 Example 5: Correlated Subquery
Example: Employees with salary > department average
```roomsql
SELECT name, salary
FROM employees e1
WHERE salary > (
  SELECT AVG(salary)
  FROM employees e2
  WHERE e1.dept_id = e2.dept_id
);
```

---
### 🧠 Types of Subqueries
| Type       | Description                                      |
| ---------- | ------------------------------------------------ |
| Single-row | Returns one row (e.g., using `=`)                |
| Multi-row  | Returns multiple rows (e.g., `IN`, `ANY`, `ALL`) |
| Correlated | Refers to outer query row by row                 |
| Scalar     | Returns a single value                           |
---
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