# 🔍 FULL ANTI JOIN in SQL

---
## 📘 What is a FULL ANTI JOIN?

A **FULL ANTI JOIN** returns:
> All rows **from both tables** that **do not have a matching record** in the other table.

This is the **opposite** of a `FULL OUTER JOIN` — instead of keeping all matches, we keep **only the unmatched** rows.

> ❌ Most SQL dialects (like MySQL, SQL Server, PostgreSQL) **do not directly support** FULL ANTI JOIN — but we can simulate it.

---
## 🧩 Example Tables

### 🧱 Table A: `students`
| student_id | name     |
|------------|----------|
| 1          | Alice    |
| 2          | Bob      |
| 3          | Charlie  |

### 🧱 Table B: `results`
| student_id | grade    |
|------------|----------|
| 2          | B        |
| 4          | A        |

---


## 🛠 Simulating FULL ANTI JOIN using UNION

```roomsql
-- Unmatched from students
SELECT s.student_id, s.name, NULL AS grade
FROM students s
LEFT JOIN results r ON s.student_id = r.student_id
WHERE r.student_id IS NULL

UNION

-- Unmatched from results
SELECT r.student_id, NULL AS name, r.grade
FROM results r
LEFT JOIN students s ON r.student_id = s.student_id
WHERE s.student_id IS NULL;
```
### 📤 Output
| student\_id | name    | grade |
| ----------- | ------- | ----- |
| 1           | Alice   | NULL  |
| 3           | Charlie | NULL  |
| 4           | NULL    | A     |
---
### ✅ Summary
| Join Type         | Description                             |
| ----------------- | --------------------------------------- |
| `FULL OUTER JOIN` | All matched + unmatched from both sides |
| `FULL ANTI JOIN`  | Only unmatched records from both tables |
