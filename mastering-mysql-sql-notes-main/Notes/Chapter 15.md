
# 📘 Subqueries & Views

---

### 🔍 **1. What is a Subquery?**

A **Subquery** is a query nested **inside another query**.

- It returns data that will be used by the main (outer) query.
    
- Also called: **Inner Query** or **Nested Query**.
    

> 🔹 A subquery must be enclosed in **parentheses `()`**.

#### ✅ **Types of Subqueries:**

|Type|Description|
|---|---|
|📍 **Single Row Subquery**|Returns **only one row**|
|📍 **Multiple Row Subquery**|Returns **multiple rows**|
|📍 **Multiple Column Subquery**|Returns **multiple columns**|
|📍 **Correlated Subquery**|Depends on the outer query|
|📍 **Nested Subquery**|Subquery inside another subquery|

---

### 🧪 **2. Subquery Example (Basic)**

```sql
-- Get employees who earn more than the average salary
SELECT name, salary
FROM employees
WHERE salary > (
    SELECT AVG(salary)
    FROM employees
);
```

🔸 Here, the **inner query** gets the average salary.  
🔸 The **outer query** finds employees who earn more than that.

---

### 🧠 **3. Subquery in SELECT Clause**

```sql
SELECT name,
       (SELECT department_name
        FROM departments
        WHERE departments.id = employees.department_id) AS dept
FROM employees;
```

📝 Subquery returns department name **per row**.

---

### 📌 **4. Subquery in FROM Clause**

```sql
SELECT avg_salary
FROM (
    SELECT AVG(salary) AS avg_salary
    FROM employees
) AS temp;
```

📂 This lets you treat a subquery like a **temporary table**.

---

### 🔗 **5. Correlated Subquery**

A subquery that **uses data from the outer query**.

```sql
SELECT name
FROM employees e
WHERE salary > (
    SELECT AVG(salary)
    FROM employees
    WHERE department_id = e.department_id
);
```

🔁 This query compares each employee’s salary to the **average salary in their department**.

---

### ✅ **6. Subquery Operators in MySQL** 🔧

|🔣 Operator|💬 Use Case|📌 Description|
|---|---|---|
|`=`|Single Row Subquery|Compare with a **single** value|
|`IN`|Multiple Row Subquery|Match **any** value in a list|
|`ANY` / `SOME`|One of the values|True if **at least one** comparison is true|
|`ALL`|All values must match|True only if the condition is true for **all**|
|`EXISTS`|Check existence|Returns true if subquery **returns any rows**|

---

#### 🟢 `=` Operator (Single Row Subquery)

📌 **Use Case**: Compare with one value only.

```sql
SELECT name
FROM employees
WHERE department_id = (
    SELECT id
    FROM departments
    WHERE name = 'Sales'
);
```

📝 The subquery must return **exactly one row**, or it will throw an error.

---

#### 🟡 `IN` Operator (Multiple Row Subquery)

📌 **Use Case**: Compare with **any value** in a list.

```sql
SELECT name
FROM employees
WHERE department_id IN (
    SELECT id
    FROM departments
    WHERE location = 'New York'
);
```

📝 Returns employees in **any** of the departments located in New York.

---

#### 🔵 `ANY` / `SOME` Operator

📌 **Use Case**: Compare with **any value** returned by the subquery.

```sql
SELECT name, salary
FROM employees
WHERE salary > ANY (
    SELECT salary
    FROM employees
    WHERE department_id = 3
);
```

📝 This returns employees whose salary is **greater than at least one** person in department 3.

✅ `SOME` is a synonym of `ANY` — they work the same.

---

#### 🔴 `ALL` Operator

📌 **Use Case**: Compare with **all** values returned by the subquery.

```sql
SELECT name, salary
FROM employees
WHERE salary > ALL (
    SELECT salary
    FROM employees
    WHERE department_id = 3
);
```

📝 Returns employees whose salary is **greater than everyone** in department 3.

---

#### 🟣 `EXISTS` Operator

📌 **Use Case**: Check if subquery **returns any rows**.

```sql
SELECT name
FROM employees e
WHERE EXISTS (
    SELECT 1
    FROM departments d
    WHERE d.id = e.department_id
    AND d.location = 'London'
);
```

📝 Returns employees who **belong to departments in London**.

- `SELECT 1` is a dummy value – it doesn’t matter what you select in `EXISTS`.
    
- Only checks **if any row exists**, not what it contains.
    

---

### 🔍 **Quick Recap Table**

|🔣 Operator|✅ Use When...|🔎 Returns True If...|
|---|---|---|
|`=`|You expect **one value**|The value matches|
|`IN`|You expect **many values**|Value is **in the list**|
|`ANY` / `SOME`|You want **any match**|One comparison is true|
|`ALL`|You want **all to match**|All comparisons are true|
|`EXISTS`|You want to check **existence**|Subquery returns rows|

---

### 🧩 **7. What is a View?**

A **View** is a **virtual table** based on a SELECT query.

- It **doesn't store data** physically.
    
- You can query it like a real table.
    
- Used to simplify complex queries.
    

#### 📌 Syntax:

```sql
CREATE VIEW view_name AS
SELECT column1, column2
FROM table
WHERE condition;
```

---

### 🔍 **8. View Example**

```sql
CREATE VIEW high_salary_employees AS
SELECT name, salary
FROM employees
WHERE salary > 50000;
```

```sql
-- Now you can query the view:
SELECT * FROM high_salary_employees;
```

🎉 Easier to read and use!

---

### 🔄 **9. Updating Views**

If a view is **updatable**, you can do:

```sql
UPDATE view_name
SET column = value
WHERE condition;
```

⚠️ **Limitations**:

- Views with `GROUP BY`, `DISTINCT`, or joins may not be updatable.
    

---

### 🧽 **10. Dropping a View**

```sql
DROP VIEW view_name;
```

📌 Deletes the view (not the data from original tables).

---

### 🎯 **11. Advantages of Views**

✅ Simplifies complex queries  
✅ Increases security (hide sensitive columns)  
✅ Logical data independence  
✅ Reusability

---

### 🚫 **12. Limitations of Views**

⚠️ Can’t always be updated  
⚠️ No indexes (views don’t store data)  
⚠️ Dependent on base tables — if table is dropped, view breaks

---

### 🧠 **13. Common Subquery vs View Usage**

|Task|Use Subquery or View?|
|---|---|
|One-time filtering|🟩 **Subquery**|
|Reusable reporting|🟦 **View**|
|Complex logic simplification|🟦 **View**|
|Performance tuning|🟩 **Subquery** (sometimes faster)|

---

### 💡 **Tips & Best Practices**

- 🧠 Use aliases in subqueries for readability.
    
- 🧼 Clean up views not in use (`DROP VIEW`).
    
- ✅ Use views for consistent business logic.
    
- 🚀 Avoid using views with heavy joins in performance-critical apps.
    

---

### 📚 Summary Table

|Concept|Description|Example|
|---|---|---|
|🧩 Subquery|Query inside another query|`SELECT * FROM ... WHERE col IN (SELECT ...)`|
|📊 View|Virtual table from a SELECT|`CREATE VIEW myview AS SELECT ...`|
|🔁 Correlated Subquery|Uses outer query values|`WHERE col = (SELECT ... WHERE outer.col = inner.col)`|

---
