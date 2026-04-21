
---

## 🟡 **Intermediate SQL Questions & Answers (21–50)**

### 21. What is a JOIN? List different types of JOINs.

🔗 **JOIN** combines rows from two or more tables based on related columns.  
Types:

- **INNER JOIN** → matching rows only
    
- **LEFT JOIN** → all rows from left + matches
    
- **RIGHT JOIN** → all rows from right + matches
    
- **FULL OUTER JOIN** → all rows from both tables
    
- **CROSS JOIN** → Cartesian product
    

---

### 22. What is a self JOIN?

A **self join** is a table joined with itself 🔁, often using aliases.

```sql
SELECT a.emp_id, b.emp_id
FROM employees a
JOIN employees b ON a.manager_id = b.emp_id;
```

---

### 23. Difference between INNER JOIN and OUTER JOIN?

- **INNER JOIN** → Returns only **matching rows**.
    
- **OUTER JOIN** → Returns matching + **non-matching rows** (LEFT, RIGHT, FULL).
    

---

### 24. What is a subquery?

📦 A **subquery** is a query nested inside another SQL statement.

---

### 25. What is a correlated subquery?

🔄 A **correlated subquery** runs once **for each row** of the outer query (depends on outer query values).

---

### 26. How do you update multiple columns in SQL?

```sql
UPDATE employees
SET salary = salary * 1.1,
    department = 'IT'
WHERE emp_id = 5;
```

---

### 27. What is the GROUP BY clause used for?

📊 Groups rows with the same values into summary rows (used with **aggregates**).

---

### 28. How does SQL handle NULLs in GROUP BY and ORDER BY?

- **GROUP BY** → All `NULL`s form **one group**.
    
- **ORDER BY** → `NULL`s are sorted **first or last** (depends on DB).
    

---

### 29. What is a CASE statement? Provide an example.

📝 Conditional logic in SQL.

```sql
SELECT emp_id,
       CASE 
         WHEN salary > 5000 THEN 'High'
         ELSE 'Low'
       END AS salary_level
FROM employees;
```

---

### 30. How can you fetch the first N rows from a table?

- **MySQL / PostgreSQL** →
    

```sql
SELECT * FROM employees LIMIT 5;
```

- **SQL Server** →
    

```sql
SELECT TOP 5 * FROM employees;
```

---

### 31. How do you find duplicate records in a table?

```sql
SELECT name, COUNT(*)
FROM employees
GROUP BY name
HAVING COUNT(*) > 1;
```

---

### 32. How to delete duplicate rows from a table?

```sql
DELETE FROM employees
WHERE emp_id NOT IN (
   SELECT MIN(emp_id)
   FROM employees
   GROUP BY name
);
```

---

### 33. What is normalization?

📐 Process of organizing data to **reduce redundancy** and **improve integrity**.

---

### 34. What are the normal forms in database design?

- **1NF** → Atomic values
    
- **2NF** → No partial dependency
    
- **3NF** → No transitive dependency
    
- **BCNF** → Stronger form of 3NF
    

---

### 35. What is denormalization?

📉 Adding redundancy to improve **read performance**, often at the cost of storage.

---

### 36. What is a view in SQL?

👁️ A **view** is a **virtual table** based on a query result.

---

### 37. How to update a view in SQL?

```sql
CREATE OR REPLACE VIEW emp_view AS
SELECT emp_id, name, salary FROM employees;
```

---

### 38. Difference between a view and a table?

- **Table** → stores physical data.
    
- **View** → virtual, doesn’t store data (except materialized views).
    

---

### 39. What are indexes in SQL?

📚 **Indexes** speed up data retrieval but use extra space.

---

### 40. How do indexes affect performance?

✅ Faster **SELECT**  
⚠️ Slower **INSERT, UPDATE, DELETE** (due to index maintenance)

---

### 41. What is a clustered index?

📍 Sorts & stores rows physically in table order. One per table.

---

### 42. What is a non-clustered index?

📌 Separate structure → stores pointers to actual data. Many allowed per table.

---

### 43. Difference between a unique constraint and a primary key?

- **Primary key** → unique + not null (only one per table).
    
- **Unique constraint** → ensures uniqueness but allows one `NULL`.
    

---

### 44. What is the use of the COALESCE function?

🧩 Returns the **first non-NULL** value in a list.

```sql
SELECT COALESCE(middle_name, 'N/A') FROM employees;
```

---

### 45. Difference between RANK, DENSE_RANK, and ROW_NUMBER?

- **RANK()** → Gaps in ranking
    
- **DENSE_RANK()** → No gaps
    
- **ROW_NUMBER()** → Unique sequence always
    

---

### 46. What is a CTE (Common Table Expression)?

🧾 A temporary result set defined using `WITH`.

```sql
WITH top_salaries AS (
   SELECT * FROM employees WHERE salary > 5000
)
SELECT * FROM top_salaries;
```

---

### 47. How do you use recursive CTEs?

Used for hierarchical queries (e.g., org chart).

```sql
WITH RECURSIVE emp_hierarchy AS (
   SELECT emp_id, manager_id FROM employees WHERE manager_id IS NULL
   UNION ALL
   SELECT e.emp_id, e.manager_id
   FROM employees e
   JOIN emp_hierarchy h ON e.manager_id = h.emp_id
)
SELECT * FROM emp_hierarchy;
```

---

### 48. What is a window function?

🔍 Performs calculations across a **set of rows** related to current row without collapsing results.

---

### 49. How does the OVER clause work in SQL?

📏 Defines the **window (partition + order)** for window functions.

```sql
SELECT emp_id, salary,
       RANK() OVER(PARTITION BY dept ORDER BY salary DESC) AS rnk
FROM employees;
```

---

### 50. What are transactions in SQL?

🛡️ A **transaction** is a sequence of operations treated as a **single unit of work**.  
Properties = **ACID**: Atomicity, Consistency, Isolation, Durability.

---
