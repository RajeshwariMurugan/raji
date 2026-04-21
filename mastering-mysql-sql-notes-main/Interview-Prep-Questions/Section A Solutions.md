
---

## 🟢 **Basic SQL Questions & Answers (1–20)**

### 1. What is SQL?

👉 SQL (Structured Query Language) is a standard language used to **store, manipulate, and retrieve data** in relational databases. 🗄️

---

### 2. What are the different types of SQL commands?

⚡ Categories:

- **DDL** (Data Definition Language) → `CREATE, ALTER, DROP`
    
- **DML** (Data Manipulation Language) → `INSERT, UPDATE, DELETE`
    
- **DQL** (Data Query Language) → `SELECT`
    
- **DCL** (Data Control Language) → `GRANT, REVOKE`
    
- **TCL** (Transaction Control Language) → `COMMIT, ROLLBACK, SAVEPOINT`
    

---

### 3. What is a primary key?

🔑 A **primary key** uniquely identifies each record in a table. It:

- Must be **unique**
    
- Cannot be **NULL**
    

---

### 4. What is a foreign key?

🌍 A **foreign key** is a column that creates a **relationship between two tables**, referencing the **primary key** in another table.

---

### 5. Difference between WHERE and HAVING clauses?

- **WHERE** → Filters **rows** before grouping.
    
- **HAVING** → Filters **groups/aggregates** after grouping.
    

---

### 6. Difference between UNION and UNION ALL?

- **UNION** → Combines results, removes duplicates.
    
- **UNION ALL** → Combines results, keeps duplicates.
    

---

### 7. How do you retrieve unique values from a column?

```sql
SELECT DISTINCT column_name FROM table_name;
```

✨ Use `DISTINCT`.

---

### 8. What are aggregate functions in SQL?

📊 Functions that perform a calculation on multiple values:

- `COUNT()`
    
- `SUM()`
    
- `AVG()`
    
- `MIN()`
    
- `MAX()`
    

---

### 9. Difference between CHAR and VARCHAR?

- **CHAR(n)** → Fixed length (pads with spaces).
    
- **VARCHAR(n)** → Variable length (saves space).
    

---

### 10. What is a NULL value in SQL?

❌ `NULL` = missing/unknown value, **not 0 and not empty string**.

---

### 11. How do you filter NULL values?

```sql
SELECT * FROM table_name WHERE column_name IS NULL;
SELECT * FROM table_name WHERE column_name IS NOT NULL;
```

---

### 12. What does the DISTINCT keyword do?

✨ Removes **duplicate values** from the result set.

---

### 13. How do you rename a column or table?

```sql
-- Rename column
SELECT column_name AS new_name FROM table;

-- Rename table
ALTER TABLE old_name RENAME TO new_name;
```

---

### 14. What is the ORDER BY clause used for?

📑 Sorts results in **ascending (`ASC`) or descending (`DESC`) order**.

---

### 15. Difference between DELETE, TRUNCATE, and DROP?

- **DELETE** → Removes rows, can use `WHERE`. 🔍
    
- **TRUNCATE** → Removes all rows (faster, resets identity). ⚡
    
- **DROP** → Deletes entire table structure. 💣
    

---

### 16. How can you change a column datatype?

```sql
ALTER TABLE table_name 
MODIFY column_name NEW_DATATYPE;
```

---

### 17. How do you write a simple SELECT query?

```sql
SELECT column1, column2 FROM table_name;
```

---

### 18. How to retrieve records from two tables using JOIN?

```sql
SELECT a.col, b.col
FROM tableA a
JOIN tableB b ON a.id = b.id;
```

---

### 19. What are constraints in SQL?

⚖️ Rules applied to columns to ensure **data integrity**.  
Types: `PRIMARY KEY, FOREIGN KEY, UNIQUE, NOT NULL, CHECK, DEFAULT`.

---

### 20. Explain the IN and BETWEEN operators.

- **IN** → Match against a list.
    

```sql
SELECT * FROM employees WHERE dept IN ('HR','IT');
```

- **BETWEEN** → Match within a range.
    

```sql
SELECT * FROM employees WHERE salary BETWEEN 3000 AND 6000;
```

---
