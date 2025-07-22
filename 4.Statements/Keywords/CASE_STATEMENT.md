# 🧠 CASE Statement in SQL

---
## ✅ What is a CASE Statement?

The `CASE` statement in SQL allows you to add **conditional logic** to your queries — similar to `if-else` logic in programming languages.

---

### 🏗️ Syntax

### ✅ Simple CASE:
```roomsql
CASE column_name
  WHEN value1 THEN result1
  WHEN value2 THEN result2
  ...
  ELSE default_result
END
```
---
## 🧪 Example

### 💡 Example 1: Simple CASE
```roomsql
SELECT name, grade,
  CASE grade
    WHEN 'A' THEN 'Excellent'
    WHEN 'B' THEN 'Good'
    WHEN 'C' THEN 'Average'
    ELSE 'Needs Improvement'
  END AS remarks
FROM students;
```
### 💡 Example 2: Searched CASE
```roomsql
SELECT name, salary,
  CASE 
    WHEN salary >= 100000 THEN 'High'
    WHEN salary >= 50000 THEN 'Medium'
    ELSE 'Low'
  END AS salary_category
FROM employees;
```

### 💡 Example 3: Case with Aggregation
```roomsql
SELECT 
  department,
  COUNT(CASE WHEN gender = 'Male' THEN 1 END) AS male_count,
  COUNT(CASE WHEN gender = 'Female' THEN 1 END) AS female_count
FROM employees
GROUP BY department;
```

