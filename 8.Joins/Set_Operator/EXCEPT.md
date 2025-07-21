# 🚫 SQL `EXCEPT` Operator

## ✅ What is `EXCEPT`?

The `EXCEPT` operator returns **only the rows from the first SELECT query** that are **not present in the second SELECT query**.

It performs a **set difference** operation.

---

### 🧠 Key Points

- Removes duplicates by default.
- Returns results from **first query minus second query**.
- Both `SELECT` statements must have:
    - The **same number of columns**.
    - **Compatible data types**.
    - Same **order of columns**.

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

## 💡 Query Using `EXCEPT`

```roomsql
SELECT name FROM employees_2023
EXCEPT
SELECT name FROM employees_2024;
```
### 📤 Output
| name |
| ---- |
| Bob  |
