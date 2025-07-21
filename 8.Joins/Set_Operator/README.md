# 🔀 SQL Set Operators

---
## 📘 What are Set Operators?

Set operators allow you to **combine results from two or more SELECT queries**.  
Each query must return the **same number of columns**, with **compatible data types**.

### 🔧 Common SQL Set Operators

| Operator     | Description                                       |
|--------------|---------------------------------------------------|
| `UNION`      | Combines results and removes duplicates           |
| `UNION ALL`  | Combines all results including duplicates         |
| `INTERSECT`  | Returns common rows from both queries (not in MySQL) |
| `EXCEPT`     | Returns rows from first query not in second (aka `MINUS` in Oracle) |

---

## 🧪 Example Data

### 🔹 Table A: `Students_2023`

| name   |
|--------|
| Alice  |
| Bob    |
| Charlie|

### 🔹 Table B: `Students_2024`

| name   |
|--------|
| Bob    |
| David  |
| Alice  |

---

### ✅ 1. `UNION`

```roomsql
SELECT name FROM Students_2023
UNION
SELECT name FROM Students_2024;
```
#### 📤 Output:
| name    |
| ------- |
| Alice   |
| Bob     |
| Charlie |
| David   |
### ✅ 2. `UNION ALL`
```roomsql
SELECT name FROM Students_2023
UNION ALL
SELECT name FROM Students_2024;
```
#### 📤 Output:
| name    |
| ------- |
| Alice   |
| Bob     |
| Charlie |
| Bob     |
| David   |
| Alice   |

### ✅ 3. INTERSECT (not in MySQL)

```roomsql
SELECT name FROM Students_2023
INTERSECT
SELECT name FROM Students_2024;
```
#### 📤 Output:
| name  |
| ----- |
| Alice |
| Bob   |

### ✅ 4. EXCEPT / MINUS
```roomsql
SELECT name FROM Students_2023
EXCEPT
SELECT name FROM Students_2024;
```
#### 📤 Output:
| name    |
| ------- |
| Charlie |

---
> ⚠️ Important Rules
> * Column count & types must match in all SELECTs.
> * ORDER BY can only be applied to the final full query.
> * Some operators like INTERSECT/EXCEPT may not be supported in all databases (e.g., MySQL).

