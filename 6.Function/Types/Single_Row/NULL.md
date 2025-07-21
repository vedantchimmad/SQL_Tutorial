# ⚠️ NULL in SQL

---
## ✅ What is NULL?

- `NULL` in SQL represents a **missing, unknown, or undefined value**.
- It is **not** the same as `0`, an empty string (`''`), or `FALSE`.

---

## 🔍 Behavior of NULL

| Operation              | Result       |
|------------------------|--------------|
| `NULL + 5`             | `NULL`       |
| `'abc' || NULL`        | `NULL`       |
| `NULL = NULL`          | `FALSE`      |
| `NULL IS NULL`         | `TRUE`       |
| `NULL IS NOT NULL`     | `FALSE`      |
| `COALESCE(NULL, 10)`   | `10`         |
| `NVL(NULL, 'N/A')`     | `'N/A'`      |

---

## 🚫 Important Rules

1. **Any operation with NULL returns NULL**, except for special functions like `COALESCE` or `IS NULL`.
2. `NULL = NULL` returns `FALSE`. Use `IS NULL` or `IS NOT NULL` instead.
3. **Aggregate functions** ignore `NULL` values (except `COUNT(*)`).

---

## 💡 Useful NULL Handling Functions

| Function     | Description                                  | Example                     | Output  |
|--------------|----------------------------------------------|-----------------------------|---------|
| `IS NULL`    | Checks if a column has NULL                  | `email IS NULL`             | TRUE/FALSE |
| `IS NOT NULL`| Checks if a column is NOT NULL               | `salary IS NOT NULL`        | TRUE/FALSE |
| `COALESCE()` | Returns the first non-NULL value             | `COALESCE(NULL, 'Guest')`   | Guest   |
| `IFNULL()`   | MySQL-specific for NULL replacement          | `IFNULL(NULL, 0)`           | 0       |
| `NVL()`      | Oracle-specific NULL replacement             | `NVL(NULL, 'N/A')`          | N/A     |

---

## 🧪 Example

```roomsql
SELECT
  name,
  COALESCE(phone, 'No Phone') AS phone_status
FROM customers
WHERE email IS NOT NULL;
```