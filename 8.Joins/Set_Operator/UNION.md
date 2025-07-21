# 🔀 SQL `UNION` Operator

---
## ✅ What is `UNION`?

The `UNION` operator is used to **combine the results of two or more `SELECT` statements**, removing **duplicate rows** in the result.

## 🧠 Key Points

- Each `SELECT` must have the **same number of columns**.
- Columns must have **similar data types**.
- It automatically removes **duplicate rows** unless you use `UNION ALL`.

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
| Eva     |

---

### 💡 Query Using `UNION`

```roomsql
SELECT name FROM employees_2023
UNION
SELECT name FROM employees_2024;
```
### 📤 Output
| name    |
| ------- |
| Alice   |
| Bob     |
| Charlie |
| David   |
| Eva     |
