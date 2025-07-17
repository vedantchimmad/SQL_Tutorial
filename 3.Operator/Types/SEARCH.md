# 🔍 SQL `SEARCH` Equivalent Operators

---
SQL does **not have a direct `SEARCH` keyword**, but you can perform search-like operations using the following:

---
### ✅ 1. `LIKE` — Pattern Matching

#### 📘 Syntax:
```roomsql
SELECT column_name
FROM table_name
WHERE column_name LIKE 'pattern';
```
---
## 🛠️ Use Cases
#### 🧪 Example 1: with like
```roomsql
-- Names starting with 'A'
SELECT * FROM students WHERE name LIKE 'A%';

-- Names ending with 'n'
SELECT * FROM students WHERE name LIKE '%n';

-- Names containing 'sh'
SELECT * FROM students WHERE name LIKE '%sh%';
```