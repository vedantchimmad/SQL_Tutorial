# 🔗 SQL `INTERSECT` Operator

---
## ✅ What is `INTERSECT`?

The `INTERSECT` operator returns **only the rows that are common** to the result sets of two or more `SELECT` statements.


### 🧠 Key Points

- Returns **distinct rows** that appear in **both** queries.
- Similar to a logical `AND`.
- Each `SELECT` must return **same number of columns** with **compatible data types**.

---

## 🧪 Example Tables

### 🧾 Table: `employees_2023`

| name    |
|---------|
| Alice   |
| Bob     |
| Charlie |

### 🧾 Table: `employees_2024`

| name    |
|---------|
| Alice   |
| David   |
| Charlie |

---

## 💡 Query Using `INTERSECT`

```roomsql
SELECT name FROM employees_2023
INTERSECT
SELECT name FROM employees_2024;
```
### 📤 Output
| name    |
| ------- |
| Alice   |
| Charlie |
