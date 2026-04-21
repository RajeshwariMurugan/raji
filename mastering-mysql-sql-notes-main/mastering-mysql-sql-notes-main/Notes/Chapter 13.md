
# 🧩 Relationships and Joins in MySQL

---

### 🔗 1. Relationships in MySQL

> **What are Relationships?**  
> Define how tables relate to each other to organize data efficiently and avoid duplication.

#### Types of Relationships

| Relationship Type    | Description                             | Example                         |
|---------------------|-------------------------------------|---------------------------------|
| **One-to-One (1:1)**  | One row in Table A relates to one row in Table B | Person ↔ Passport               |
| **One-to-Many (1:N)** | One row in Table A relates to many rows in Table B | Customer ↔ Orders               |
| **Many-to-Many (M:N)**| Many rows in Table A relate to many in Table B (via junction table) | Students ↔ Courses              |

---

### 🔑 2. Keys in Relationships

| Key Type         | Description                               | Example               |
|------------------|-------------------------------------------|-----------------------|
| **Primary Key (PK)**   | Unique identifier for each row           | `customer_id` in Customers table  |
| **Foreign Key (FK)**   | References PK of another table          | `customer_id` in Orders table      |

---

### 🔄 3. Joins in MySQL

> **What is a Join?**  
> Combines rows from multiple tables based on related columns.

#### Why use Joins?
- To fetch related data spread across tables.
- Enables complex queries to answer business questions.

---

### 🧮 4. Types of Joins

| Join Type           | Description                                      | Result                                 |
|---------------------|-------------------------------------------------|----------------------------------------|
| **INNER JOIN**      | Returns rows where there's a match in both tables | Only matching rows                      |
| **LEFT JOIN**       | Returns all rows from left table + matches from right | All left rows + matching right rows (NULL if no match) |
| **RIGHT JOIN**      | Returns all rows from right table + matches from left | All right rows + matching left rows (NULL if no match) |
| **FULL JOIN** (Not directly in MySQL) | Returns all rows when matched in either table | All rows from both tables (simulate with UNION)            |

---

### 💻 5. Join Syntax

```sql
SELECT columns
FROM table1
JOIN_TYPE table2
ON table1.column = table2.column;
````

---

### 🔍 6. Join Examples

#### Sample Tables

**Customers**

|customer_id (PK)|name|
|---|---|
|1|Alice|
|2|Bob|
|3|Charlie|

**Orders**

|order_id (PK)|customer_id (FK)|product|
|---|---|---|
|101|1|Laptop|
|102|2|Phone|
|103|1|Keyboard|

---

#### 🟢 INNER JOIN

```sql
SELECT Customers.name, Orders.product
FROM Customers
INNER JOIN Orders ON Customers.customer_id = Orders.customer_id;
```

|name|product|
|---|---|
|Alice|Laptop|
|Bob|Phone|
|Alice|Keyboard|

_Only customers with orders._

---

#### 🟡 LEFT JOIN

```sql
SELECT Customers.name, Orders.product
FROM Customers
LEFT JOIN Orders ON Customers.customer_id = Orders.customer_id;
```

|name|product|
|---|---|
|Alice|Laptop|
|Bob|Phone|
|Alice|Keyboard|
|Charlie|NULL|

_All customers, including those without orders._

---

#### 🔵 RIGHT JOIN

```sql
SELECT Customers.name, Orders.product
FROM Customers
RIGHT JOIN Orders ON Customers.customer_id = Orders.customer_id;
```

|name|product|
|---|---|
|Alice|Laptop|
|Bob|Phone|
|Alice|Keyboard|

_All orders with their customers._

---

#### 🟣 FULL JOIN (Simulated)

```sql
SELECT Customers.name, Orders.product
FROM Customers
LEFT JOIN Orders ON Customers.customer_id = Orders.customer_id

UNION

SELECT Customers.name, Orders.product
FROM Customers
RIGHT JOIN Orders ON Customers.customer_id = Orders.customer_id;
```

_All customers and all orders, matched or unmatched._

---

### 🔄 7. Bonus: Self Join

- Join a table to itself to compare rows.
    

```sql
SELECT A.employee_name AS Employee, B.employee_name AS Manager
FROM Employees A
LEFT JOIN Employees B ON A.manager_id = B.employee_id;
```

---

### 📝 Summary

- **Relationships** connect tables logically (1:1, 1:N, M:N).
    
- **Keys** enforce these connections (Primary and Foreign Keys).
    
- **Joins** combine related data across tables.
    
- Use **INNER JOIN** for matching data only.
    
- Use **LEFT/RIGHT JOIN** to include unmatched rows from one side.
    
- Simulate **FULL JOIN** with UNION in MySQL.
    
- **Self Join** is useful for hierarchical data.
    

---

