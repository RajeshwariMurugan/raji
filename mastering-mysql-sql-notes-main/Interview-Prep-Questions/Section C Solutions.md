
---

## 🔴 **Advanced SQL Questions & Answers (51–80)**

### 51. Explain ACID properties in a database.

🛡️ **ACID** ensures reliable transactions:

- **A**tomicity → All or nothing
    
- **C**onsistency → Data integrity maintained
    
- **I**solation → Transactions don’t interfere
    
- **D**urability → Changes persist after commit
    

---

### 52. What is a deadlock and how to avoid it?

⚡ **Deadlock** = two transactions waiting on each other → stuck forever.  
✅ Avoid by:

- Accessing resources in same order
    
- Using shorter transactions
    
- Applying `WITH (NOLOCK)` (read uncommitted, with caution)
    

---

### 53. How do you optimize a slow query?

🚀 Tips:

- Use **indexes** wisely
    
- Avoid `SELECT *`
    
- Rewrite with **JOINs** instead of subqueries
    
- Check **execution plan**
    
- Use **proper filtering** (`WHERE` before `HAVING`)
    

---

### 54. What is query execution plan and how to use it?

📊 It shows **how SQL engine executes a query** (order, index usage, joins).

- Use `EXPLAIN` (MySQL/Postgres) or `SET SHOWPLAN_ALL ON` (SQL Server).
    

---

### 55. What are stored procedures and functions?

📦 **Stored Procedure** → Precompiled set of SQL statements.  
📦 **Function** → Returns a single value or table, used in queries.

---

### 56. Difference between a function and a stored procedure?

- **Function** → Must return a value, can be used in `SELECT`.
    
- **Procedure** → Can return multiple results, support transactions, cannot be used directly in `SELECT`.
    

---

### 57. How do you implement error handling in SQL?

💡 Use `TRY...CATCH` (SQL Server) or `EXCEPTION` (Postgres).

```sql
BEGIN TRY
   -- SQL code
END TRY
BEGIN CATCH
   PRINT ERROR_MESSAGE();
END CATCH
```

---

### 58. What are triggers in SQL?

⚡ **Triggers** are special procedures that run **automatically** when an event (INSERT, UPDATE, DELETE) occurs.

---

### 59. How do you audit changes using triggers?

```sql
CREATE TRIGGER audit_trigger
AFTER UPDATE ON employees
FOR EACH ROW
INSERT INTO audit_log(emp_id, old_salary, new_salary, updated_at)
VALUES (OLD.emp_id, OLD.salary, NEW.salary, NOW());
```

---

### 60. What are temp tables and when to use them?

📝 **Temporary tables** store intermediate results during a session/query.  
Use when:

- Breaking down complex queries
    
- Storing intermediate aggregates
    

---

### 61. Difference between temp table and table variable?

- **Temp table** → Stored in tempdb, supports indexes.
    
- **Table variable** → Memory-based, lighter but limited features.
    

---

### 62. What is a materialized view?

👀 A **materialized view** stores the result of a query physically (not just virtual). Used for faster access.

---

### 63. What is sharding in databases?

🌍 Splitting a database into **smaller parts (shards)** across servers for scalability.

---

### 64. What is partitioning in SQL?

📂 Splitting a large table into **smaller logical pieces** for better performance (by range, list, hash).

---

### 65. How do you implement row-level security?

🔒 Restrict rows per user using:

- **Policies** (`CREATE SECURITY POLICY` in SQL Server)
    
- **Views with filtering conditions**
    

---

### 66. What is a sequence?

🔢 An object that generates **sequential numbers** (often used for primary keys).

```sql
CREATE SEQUENCE emp_seq START WITH 1 INCREMENT BY 1;
```

---

### 67. How to paginate records using SQL?

- **MySQL/Postgres** →
    

```sql
SELECT * FROM employees LIMIT 10 OFFSET 20;
```

- **SQL Server** →
    

```sql
SELECT * FROM employees
ORDER BY emp_id
OFFSET 20 ROWS FETCH NEXT 10 ROWS ONLY;
```

---

### 68. Difference between EXISTS and IN?

- **EXISTS** → Checks row existence (faster for correlated queries).
    
- **IN** → Matches against a list/set of values.
    

---

### 69. How do you handle many-to-many relationships in SQL?

🔗 Create a **junction table** with foreign keys referencing both tables.

---

### 70. How do you identify blocking queries?

🔍 Use system views:

- **SQL Server** → `sp_who2`, `sys.dm_exec_requests`
    
- **Postgres** → `pg_locks`
    

---

### 71. What are the performance implications of joins?

- **INNER JOIN** → Usually fastest with indexes
    
- **OUTER JOIN** → More overhead
    
- **CROSS JOIN** → Expensive (Cartesian product)
    

---

### 72. How to analyze and fix slow-running queries?

⚡ Steps:

1. Get **execution plan**
    
2. Check **missing indexes**
    
3. Optimize **joins & subqueries**
    
4. Avoid unnecessary **sorting**
    
5. Reduce **large scans**
    

---

### 73. How does indexing work in JOINs?

✅ Indexes on **join columns** speed up lookups by avoiding full table scans.

---

### 74. How to use indexed views?

📑 Create view + index for faster reads.

```sql
CREATE VIEW sales_summary WITH SCHEMABINDING AS
SELECT cust_id, SUM(amount) AS total
FROM sales
GROUP BY cust_id;

CREATE UNIQUE CLUSTERED INDEX idx_sales_summary ON sales_summary(cust_id);
```

---

### 75. What is lateral join?

🔄 A **lateral join** (Postgres/Oracle: `LATERAL`, SQL Server: `CROSS APPLY`) allows subqueries to reference columns from preceding tables.

```sql
SELECT c.name, o.order_id
FROM customers c
CROSS APPLY (
   SELECT TOP 1 * FROM orders o WHERE o.cust_id = c.id ORDER BY o.date DESC
) o;
```

---

### 76. How do you handle schema changes in production?

⚠️ Best practices:

- Use **version-controlled migrations**
    
- Apply changes in **small batches**
    
- Use **blue-green deployment** or **rolling updates**
    

---

### 77. What is data skew and how to handle it?

⚖️ **Data skew** = uneven data distribution → performance issues.  
Fix:

- Redistribute data
    
- Use **hash partitioning**
    
- Add **salting (extra key values)**
    

---

### 78. Difference between OLAP and OLTP systems?

- **OLAP** (Analytics) → Read-heavy, aggregates, historical data.
    
- **OLTP** (Transactions) → Write-heavy, real-time inserts/updates.
    

---

### 79. How do you write idempotent SQL scripts?

📝 Scripts that can run multiple times without side effects.  
Example:

```sql
IF NOT EXISTS (SELECT * FROM sys.tables WHERE name = 'employees')
   CREATE TABLE employees (...);
```

---

### 80. Difference between a cursor and WHILE loop?

- **Cursor** → Row-by-row iteration (slower, memory heavy).
    
- **WHILE loop** → Iterates based on condition, better than cursors but still slower than set-based queries.
    

---
