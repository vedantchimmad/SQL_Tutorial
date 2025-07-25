# 🚦 SQL Trigger

---
## ✅ What is a Trigger?

A **Trigger** is a special kind of stored procedure that automatically **executes (fires)** in response to certain events on a table or view such as:
- `INSERT`
- `UPDATE`
- `DELETE`

### 🔧 Syntax

```roomsql
CREATE TRIGGER trigger_name
ON table_name
AFTER | INSTEAD OF [INSERT, UPDATE, DELETE]
AS
BEGIN
    -- Trigger logic here
END;
```
---
### 📌 Types of Triggers
| Type              | Description                                                  |
| ----------------- | ------------------------------------------------------------ |
| **AFTER Trigger** | Executes **after** the triggering action                     |
| **INSTEAD OF**    | Executes **instead of** the triggering action                |
| **DDL Trigger**   | Executes in response to DDL statements like `CREATE`, `DROP` |
### 🔧 Example
#### 🧪 Example 1: AFTER INSERT Trigger
```roomsql
CREATE TRIGGER trg_AfterInsert_Employee
ON Employees
AFTER INSERT
AS
BEGIN
    PRINT 'A new employee was added.'
END;
```
#### 🧪 Example 2: AFTER UPDATE Trigger – Audit Log
```roomsql
CREATE TRIGGER trg_AuditSalaryChange
ON Employees
AFTER UPDATE
AS
BEGIN
    INSERT INTO SalaryAudit(EmpID, OldSalary, NewSalary, ChangedOn)
    SELECT i.EmpID, d.Salary, i.Salary, GETDATE()
    FROM inserted i
    JOIN deleted d ON i.EmpID = d.EmpID
    WHERE i.Salary <> d.Salary;
END;
```
#### 🧪 Example 3: INSTEAD OF DELETE Trigger – Prevent Delete
```roomsql
CREATE TRIGGER trg_PreventDelete
ON Employees
INSTEAD OF DELETE
AS
BEGIN
    PRINT 'Delete is not allowed on this table.';
END;
```
---
### 📋 View Existing Triggers
```roomsql
SELECT name, object_id, parent_class_desc, create_date
FROM sys.triggers
WHERE parent_id = OBJECT_ID('Employees');
```