# Operator

---
* Operators are used to perform specific kind of operations on the operands based on the certain-conditions
### Types of operations
#### 1.Arithmetic operations
* Operators are used to perform arithmetic operations on operands
```agsl
SELECT SAL*12 ANUL_SALARY FROM EMP;
```
>Ex : +,-,*,%

#### 2.Logical operators
* Logical operators are used to perform logical operations on operands
```agsl
SELECT * FROM EMP WHERE EMPNAME =”VEDANT” AND EMPNAME=”VIVEK”;
```
>Ex : and, or, not,SOME/ANY,ALL,EXISTS

#### 3.ALL Operator
* ALL operator is used to select all tuples of SELECT STATEMENT. It is also used to compare a value to every value in another value set or result from a subquery.
* The ALL operator returns TRUE if all of the subqueries values meet the condition. The ALL must be preceded by comparison operators and evaluates true if all of the subqueries values meet the condition.
* ALL is used with SELECT, WHERE, HAVING statement.

Syntax:
```agsl
SELECT column_name(s)
FROM table_name
WHERE column_name comparison_operator ALL
(SELECT column_name
FROM table_name
WHERE condition(s));
```

Q) Find the name of the product if all the records in the OrderDetails has Quantity either equal to 6 or 2.

Ans)
```agsl
SELECT ProductName
FROM Products
WHERE ProductID = ALL (SELECT ProductId
FROM OrderDetails
WHERE Quantity = 6 OR Quantity = 2);
```
#### 4. SOME Operator
* SOME operator evaluates the condition between the outer and inner tables and evaluates to true if the final result returns any one row. If not, then it evaluates to false.
* The SOME and ANY comparison conditions are similar to each other and are completely interchangeable.

Ans) 
```agsl
SELECT NAME
FROM INSTRUCTOR
WHERE SALARY > SOME(SELECT SALARY
FROM INSTRUCTOR
WHERE DEPT='COMPUTER SCIENCE');
```
#### 5.EXISTS Operator
* The EXISTS condition in SQL is used to check whether the result of a correlated nested query is empty (contains no tuples) or not.
* The result of EXISTS is a boolean value True or False.
* It can be used in a SELECT, UPDATE, INSERT or DELETE statement.

Q) Using EXISTS condition with SELECT statement To fetch the first and last name of the customers who placed atleast one order.

Ans) 
```agsl
SELECT fname, lname
FROM Customers
WHERE EXISTS (SELECT *
FROM Orders
WHERE Customers.customer_id = Orders.c_id);
```
#### 6.Relational operators
* Are used to perform relation between operands
```agsl
SELECT * FROM EMP WHERE SAL = 2000;
```
>Ex :<,>, <=,>=,=,!=

#### 7.Special operators/ Keywords operators
Ex: IS, LIKE, IN, BETWEEN

**IS Operator or keyword**
* Is operator is used to compare with null or not null values
 
Q) Display all the employees who don’t have reporting manager
```agsl
SELECT * FROM EMP WHERE MGR IS NULL
```
**Like operator**
* It is used to perform pattern matching
* We can achieve pattern matching in two ways with help of wildcards is % or _
1. % It matches with single to N characters

Q)Display all the employee whose name starts with later S
```agsl
SELECT * FROM EMP WHERE ENAME LIKE S%;
```
2. _It matches with single character or values

Q)Display all the employee whose name is having letter L as second character
```agsl
SELECT * FROM EMP WHERE ENAME LIKE _L%;
```
>[!Note]
>
>LIKE is case sensitive and ILIKE is case-insensitive

**IN Operator**
* Whenever we want to make use of the OR operator more than one time instead of that we can make use of the IN operator

Q)Display all the employees whose job is clear or the salesman
```agsl
SELECT * FROM EMP WHERE JOB IN (“CLEAR”,”SALESMAN”)
```
**BETWEEN Operator**
* It is used to display the output for the range of values
* Whenever we use of the between operator it should be followed by and operator

Q)Display the employees who is earning salary between the range of 1000 and 4000
```agsl
SELECT * FROM EMP WHERE SAL BETWEEN 1000 AND 4000
```
#### 8.Concatenation Operator
* || or concatenation operator is use to link columns or character strings.
```agsl
SELECT id, first_name, last_name, first_name || last_name,
salary, first_name || salary FROM myTable
```
#### 9.Alternative Quote Operator
* we want to use apostrophe in our literal value but we can’t use it directly.
* overcome the problem Oracle introduce an operator known as Alternative Quote Operator(q).
```agsl
Query that uses Alternative Quote Operator(q)
SELECT id, first_name, last_name, salary,
first_name||q'{ has salary's }'||salary
AS "new" FROM myTable
```