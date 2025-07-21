# 🔀 SQL `UNION ALL` Operator

---
## ✅ What is `UNION ALL`?

The `UNION ALL` operator is used to **combine the result sets** of two or more `SELECT` statements, **including duplicates**.

---

### 🧠 Key Differences Between `UNION` and `UNION ALL`

| Feature         | `UNION`              | `UNION ALL`          |
|----------------|----------------------|----------------------|
| Duplicates     | Removed              | Included             |
| Performance    | Slower (due to dedup)| Faster               |
| Use Case       | Unique results needed| All results needed   |

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

## 💡 Query Using `UNION ALL`

```roomsql
SELECT name FROM employees_2023
UNION ALL
SELECT name FROM employees_2024;
```
### 📤 Output (With Duplicates)
| name    |
| ------- |
| Alice   |
| Bob     |
| Charlie |
| Alice   |
| David   |
| Eva     |
