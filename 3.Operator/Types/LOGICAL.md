# 🔗 Logical Operators in SQL

---
## 📘 What Are Logical Operators?

Logical operators are used in SQL to **combine multiple conditions** in a `WHERE`, `HAVING`, or `JOIN` clause.  
They return a result based on the **truth values** (`TRUE`, `FALSE`, or `NULL`) of the conditions involved.

## 🔧 List of Logical Operators

| Operator | Description                              | Example                                |
|----------|------------------------------------------|----------------------------------------|
| `AND`    | All conditions must be true              | `age > 18 AND salary > 50000`          |
| `OR`     | At least one condition must be true      | `city = 'Delhi' OR city = 'Mumbai'`    |
| `NOT`    | Reverses the result of the condition     | `NOT department = 'HR'`                |

---
### 🛠️ Use Cases

#### ✅ Example 1: Using `AND`

```roomsql
SELECT name, salary
FROM employees
WHERE department = 'IT' AND salary > 60000;
```
#### ✅ Example 2: Using `OR`
```roomsql
SELECT name, city
FROM customers
WHERE city = 'Bangalore' OR city = 'Mumbai';
```
#### ✅ Example 3: Using `NOT`
```roomsql
SELECT name
FROM employees
WHERE NOT department = 'HR';
```
#### ✅ Example 4: Combined Use
```roomsql
SELECT name
FROM students
WHERE (marks > 60 AND attendance > 75)
   OR (sports = 'Yes' AND grade = 'A');
```
---
## 🧠 Truth Table Summary
### 🔹 `AND`
| Condition 1 | Condition 2 | Result |
| ----------- | ----------- | ------ |
| TRUE        | TRUE        | TRUE   |
| TRUE        | FALSE       | FALSE  |
| FALSE       | FALSE       | FALSE  |
### 🔹 `OR`
| Condition 1 | Condition 2 | Result |
| ----------- | ----------- | ------ |
| TRUE        | FALSE       | TRUE   |
| FALSE       | FALSE       | FALSE  |
| TRUE        | TRUE        | TRUE   |
### 🔹 `NOT`
| Condition | Result |
| --------- | ------ |
| TRUE      | FALSE  |
| FALSE     | TRUE   |
