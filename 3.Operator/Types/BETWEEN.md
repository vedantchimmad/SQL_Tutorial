# 🔍 SQL `BETWEEN` Operator

---
## 📘 What Is `BETWEEN`?

The `BETWEEN` operator in SQL is used to **filter the result set** within a **range of values**.  
It returns values **inclusive of the boundaries**.

### ✅ Syntax

```roomsql
SELECT column_name
FROM table_name
WHERE column_name BETWEEN value1 AND value2;
```
---
### 🛠️ Use Cases
#### 🧪 Example 1: Numeric Range
```roomsql
SELECT name, age
FROM students
WHERE age BETWEEN 18 AND 25;
```
#### 🧪 Example 2: Date Range
```roomsql
SELECT order_id, order_date
FROM orders
WHERE order_date BETWEEN '2024-01-01' AND '2024-12-31';
```
#### 🧪 Example 3: Text/Alphabetical Range
```roomsql
SELECT name
FROM employees
WHERE name BETWEEN 'A' AND 'M';
```