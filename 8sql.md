# SQL Cheat Sheet – Interview Quick Reference

## ✅ Basic SQL Syntax

```sql
SELECT column1, column2 FROM table;
INSERT INTO table (col1, col2) VALUES (val1, val2);
UPDATE table SET col1 = val1 WHERE condition;
DELETE FROM table WHERE condition;
```

---

## ✅ Clauses & Keywords

```sql
WHERE       -- filter rows
GROUP BY    -- group rows for aggregate functions
ORDER BY    -- sort results
HAVING      -- filter after GROUP BY
LIMIT       -- restrict number of rows (MySQL/Postgres)
```

---

## ✅ Joins

```sql
-- INNER JOIN
SELECT * FROM A INNER JOIN B ON A.id = B.a_id;

-- LEFT JOIN
SELECT * FROM A LEFT JOIN B ON A.id = B.a_id;

-- RIGHT JOIN
SELECT * FROM A RIGHT JOIN B ON A.id = B.a_id;

-- FULL OUTER JOIN (Not in MySQL directly)
SELECT * FROM A FULL OUTER JOIN B ON A.id = B.a_id;
```

---

## ✅ Aggregate Functions

```sql
COUNT(*)     -- number of rows
SUM(column)  -- total value
AVG(column)  -- average value
MAX(column)  -- highest value
MIN(column)  -- lowest value
```

---

## ✅ Common Interview Queries

### 1. Get top 5 highest paid employees

```sql
SELECT name, salary FROM employees ORDER BY salary DESC LIMIT 5;
```

### 2. Find duplicate rows

```sql
SELECT col, COUNT(*) FROM table GROUP BY col HAVING COUNT(*) > 1;
```

### 3. Get department-wise employee count

```sql
SELECT department, COUNT(*) FROM employees GROUP BY department;
```

### 4. Fetch 2nd highest salary

```sql
SELECT MAX(salary) FROM employees WHERE salary < (SELECT MAX(salary) FROM employees);
```

### 5. Get employees who don't belong to any department

```sql
SELECT * FROM employees WHERE department_id IS NULL;
```

---

## ✅ Constraints

```sql
PRIMARY KEY   -- unique + not null
FOREIGN KEY   -- reference another table
UNIQUE        -- column must have unique values
NOT NULL      -- disallow nulls
CHECK         -- enforce condition
DEFAULT       -- assign default value
```

---

## 💡 Pro Tips for Interviews

* Always pair `GROUP BY` with aggregate functions.
* Use `HAVING` to filter grouped data.
* Know difference between `WHERE` (rows) and `HAVING` (groups).
* Explain NULL-safe comparisons: `IS NULL`, `IS NOT NULL`.
* Understand when to use subqueries vs joins.
