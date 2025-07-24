# 🗃️ Database Objects in SQL

---
Database objects are **logical structures** used to store or manage data in a **relational database**.

---

### 📋 List of Common Database Objects

| Object         | Description                                                                 |
|----------------|-----------------------------------------------------------------------------|
| **Table**       | Stores data in rows and columns.                                             |
| **View**        | A virtual table based on the result of a SQL query.                          |
| **Index**       | Improves the speed of data retrieval.                                        |
| **Sequence**    | Generates numeric values (often for primary keys).                           |
| **Synonym**     | Alias for another database object.                                           |
| **Stored Procedure** | A saved block of SQL code that can be executed.                       |
| **Function**    | Similar to procedures, but returns a single value.                          |
| **Trigger**     | Executes automatically in response to table events (INSERT, UPDATE, DELETE).|
| **Schema**      | Logical container that holds database objects.                              |
| **Constraint**  | Enforces rules on table data (e.g., PRIMARY KEY, FOREIGN KEY).              |

---

### 🧾 Object Examples

### 1. **Table**
```roomsql
CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    salary DECIMAL(10,2)
);
```
### 2. **View**
```roomsql
CREATE VIEW high_salary_employees AS
SELECT name, salary FROM employees WHERE salary > 70000;
```
### 3. **Index**
```roomsql
CREATE INDEX idx_emp_name ON employees(name);
```
### 4. Sequence
```roomsql
CREATE SEQUENCE emp_seq START WITH 1 INCREMENT BY 1;
```
### 5. Synonym
```roomsql
CREATE SYNONYM emp FOR employees;
```
### 6. Stored Procedure
```roomsql
CREATE PROCEDURE raise_salary(emp_id INT, increment DECIMAL)
BEGIN
   UPDATE employees SET salary = salary + increment WHERE id = emp_id;
END;
```
### 7. Function
```roomsql
CREATE FUNCTION get_tax(salary DECIMAL)
RETURNS DECIMAL
RETURN salary * 0.2;
```
### 8. Trigger
```roomsql
CREATE TRIGGER trg_salary_check
BEFORE UPDATE ON employees
FOR EACH ROW
WHEN (NEW.salary < 0)
BEGIN
  RAISE EXCEPTION 'Salary cannot be negative';
END;
```
