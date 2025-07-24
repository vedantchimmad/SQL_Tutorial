# 📘 SQL Functions

---
## ✅ What is a Function in SQL?

A **Function** in SQL is a named program unit that:
- Performs a specific task
- Can accept input parameters
- Must return **a single value**
- Can be reused in SELECT, WHERE, ORDER BY, etc.

### 🔧 Types of SQL Functions

#### 🔹 1. **System Functions** – Built-in (e.g. `GETDATE()`, `LEN()`)
#### 🔹 2. **User-Defined Functions (UDF)** – Created by users

### 🧠 Syntax – User-Defined Function

```roomsql
CREATE FUNCTION function_name (@param1 datatype, ...)
RETURNS return_datatype
AS
BEGIN
    -- Logic
    RETURN return_value
END;
```
---
### 🧪 Examples
#### 🔸 Example 1: Return Square of a Number
```roomsql
CREATE FUNCTION GetSquare(@Number INT)
RETURNS INT
AS
BEGIN
    RETURN @Number * @Number
END;
```
➡️ Usage:
```roomsql
SELECT dbo.GetSquare(5) AS SquareResult;
```
#### 🔸 Example 2: Return Full Name
```roomsql
CREATE FUNCTION GetFullName(@FirstName NVARCHAR(50), @LastName NVARCHAR(50))
RETURNS NVARCHAR(101)
AS
BEGIN
    RETURN @FirstName + ' ' + @LastName
END;
```
➡️ Usage:
```roomsql
SELECT dbo.GetFullName('John', 'Doe') AS FullName;
```
#### 🔸 Example 3: Function Used in a SELECT Statement
```roomsql
SELECT EmployeeID, dbo.GetFullName(FirstName, LastName) AS FullName
FROM Employees;
```
---
#### 🧹 Drop a Function
```roomsql
DROP FUNCTION function_name;
```
#### 🔄 Inline Table-Valued Function
```roomsql
CREATE FUNCTION GetHighSalaryEmployees(@MinSalary INT)
RETURNS TABLE
AS
RETURN (
    SELECT * FROM Employees WHERE Salary > @MinSalary
);
```
➡️ Usage:
```roomsql
SELECT * FROM dbo.GetHighSalaryEmployees(50000);
```



