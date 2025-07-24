# 📘 Stored Procedure in SQL

---
## ✅ What is a Stored Procedure?
A **Stored Procedure** is a precompiled collection of one or more SQL statements that can:
- Accept input parameters
- Return output parameters
- Be reused across applications
- Improve performance and security

### 🧠 Syntax

#### ➤ Without Parameters
```roomsql
CREATE PROCEDURE procedure_name
AS
BEGIN
    -- SQL logic here
END;
```
#### ➤ With Input Parameters
```roomsql
CREATE PROCEDURE GetEmployeeByID
    @EmpID INT
AS
BEGIN
    SELECT * FROM Employees WHERE EmployeeID = @EmpID;
END;
```
#### ➤ With Output Parameter
```roomsql
CREATE PROCEDURE GetEmployeeCount
    @DeptID INT,
    @EmpCount INT OUTPUT
AS
BEGIN
    SELECT @EmpCount = COUNT(*) FROM Employees WHERE DepartmentID = @DeptID;
END;
```
---
### 🧪 Examples
#### 🔹 Example 1: Insert Employee
```roomsql
CREATE PROCEDURE AddEmployee
    @Name NVARCHAR(100),
    @Salary DECIMAL(10, 2)
AS
BEGIN
    INSERT INTO Employees (Name, Salary)
    VALUES (@Name, @Salary);
END;
```
➡️ Execute:
```roomsql
EXEC AddEmployee 'Alice', 70000.00;
```
#### 🔹 Example 2: Update Salary
```roomsql
CREATE PROCEDURE UpdateSalary
    @EmpID INT,
    @NewSalary DECIMAL(10, 2)
AS
BEGIN
    UPDATE Employees
    SET Salary = @NewSalary
    WHERE EmployeeID = @EmpID;
END;
```
#### 🔹 Example 3: Return All Employees
```roomsql
CREATE PROCEDURE GetAllEmployees
AS
BEGIN
    SELECT * FROM Employees;
END;
```
➡️ Execute:
```roomsql
EXEC GetAllEmployees;
```
---
#### 🧹 Drop a Stored Procedure
```roomsql
DROP PROCEDURE procedure_name;
```
#### 🛠️ Run Procedure From Python (Optional)
```python
import pyodbc

conn = pyodbc.connect('your_connection_string')
cursor = conn.cursor()

# Example: Call GetAllEmployees
cursor.execute("{CALL GetAllEmployees}")
for row in cursor:
    print(row)
```

