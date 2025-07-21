# 🔢 Numeric Functions in SQL

SQL provides built-in **numeric functions** to perform calculations or transformations on numeric data types like `INT`, `DECIMAL`, or `FLOAT`.

---

## 📘 Common Numeric Functions

| Function       | Description                                 | Example                     | Output   |
|----------------|---------------------------------------------|-----------------------------|----------|
| `ABS(x)`       | Returns the absolute value of a number      | `ABS(-15)`                  | `15`     |
| `CEIL(x)`      | Rounds **up** to the nearest integer        | `CEIL(4.3)`                 | `5`      |
| `FLOOR(x)`     | Rounds **down** to the nearest integer      | `FLOOR(4.7)`                | `4`      |
| `ROUND(x, d)`  | Rounds to `d` decimal places                | `ROUND(123.456, 2)`         | `123.46` |
| `TRUNC(x, d)`  | Truncates without rounding                 | `TRUNC(123.456, 2)`         | `123.45` |
| `MOD(x, y)`    | Returns the remainder of `x ÷ y`            | `MOD(10, 3)`                | `1`      |
| `POWER(x, y)`  | Raises `x` to the power of `y`              | `POWER(2, 3)`               | `8`      |
| `SQRT(x)`      | Returns the square root                     | `SQRT(25)`                  | `5`      |
| `EXP(x)`       | Returns `e^x` (exponential)                 | `EXP(1)`                    | `2.718`  |
| `LOG(x)`       | Returns the natural logarithm (base `e`)    | `LOG(1)`                    | `0`      |
| `LOG10(x)`     | Returns logarithm base 10                   | `LOG10(1000)`               | `3`      |
| `SIGN(x)`      | Returns `-1`, `0`, or `1` for sign of `x`   | `SIGN(-20)`                 | `-1`     |
| `RAND()`       | Returns a random float between 0 and 1      | `RAND()`                    | `0.724`  |

---

## 💡 Example Use Case

```roomsql
SELECT
  salary,
  ROUND(salary * 1.1, 2) AS raised_salary,
  FLOOR(salary / 1000) AS salary_bracket
FROM employees;
```