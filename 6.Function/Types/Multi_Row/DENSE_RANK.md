# 🏅 SQL Window Function: DENSE_RANK()

---
### 📘 What is DENSE_RANK()?

The `DENSE_RANK()` function assigns **rankings** to rows within a partition of a result set.  
Unlike `RANK()`, it does **not skip ranks** when there are ties (duplicate values).

### 🧾 Syntax

```roomsql
SELECT column1, column2,
       DENSE_RANK() OVER (
           [PARTITION BY partition_column]
           ORDER BY sort_column
       ) AS dense_rank
FROM table_name;
``` 