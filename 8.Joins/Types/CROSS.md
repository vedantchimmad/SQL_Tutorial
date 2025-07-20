# 🔁 CROSS JOIN in SQL

---
## 📘 What is a CROSS JOIN?

A **CROSS JOIN** returns the **Cartesian product** of two tables.  
That means:
> * Each row from the **first table** is paired with **every row** from the **second table**.
> * 🧠 Total rows = rows_in_table1 × rows_in_table2 → 2 × 3 = 6 rows


---

## 🧩 Example Tables

### 🧱 Table A: `colors`

| color_id | color   |
|----------|---------|
| 1        | Red     |
| 2        | Blue    |

### 🧱 Table B: `sizes`

| size_id | size    |
|---------|---------|
| 1       | Small   |
| 2       | Medium  |
| 3       | Large   |

---

## 🔄 CROSS JOIN Query

```roomsql
SELECT c.color, s.size
FROM colors c
CROSS JOIN sizes s;
```
### 📤 Output (Cartesian Product)
| color | size   |
| ----- | ------ |
| Red   | Small  |
| Red   | Medium |
| Red   | Large  |
| Blue  | Small  |
| Blue  | Medium |
| Blue  | Large  |

---
### ✅ Use Cases
* Generating combinations (e.g., product variations, schedule pairings)
* Creating test data
* Building grid-like outputs