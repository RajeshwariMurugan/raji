
## 📘 Retrieval of Data in MySQL
---
### 🔍 SELECT Statement

Used to retrieve data from one or more tables.

```sql
SELECT column1, column2 FROM table_name;
```

- `*` selects all columns:
    

```sql
SELECT * FROM Customers;
```

---

### 🎯 WHERE Clause

Filters rows based on a condition.

```sql
SELECT * FROM Customers WHERE City = 'New York';
```

---

### 🎚️ Comparison Operators

|Operator|Meaning|
|---|---|
|=|Equal to|
|!= / <>|Not equal to|
|>, <|Greater/Less|
|>=, <=|Greater/Less or equal|
|BETWEEN|Between a range|
|IN (...)|Match any in list|

---

### ⚙️ Logical Operators

- `AND`, `OR`, `NOT`
    

```sql
SELECT * FROM Customers WHERE City = 'New York' AND Age > 25;
```

---

### 📑 ORDER BY

Sorts result set.

```sql
SELECT * FROM Customers ORDER BY Name ASC;
```

- `ASC` = ascending (default)
    
- `DESC` = descending
    

---

### 🎛️ LIMIT

Restricts number of rows returned.

```sql
SELECT * FROM Customers LIMIT 5;
```

---

### 🔄 DISTINCT

Removes duplicate values.

```sql
SELECT DISTINCT City FROM Customers;
```

---

### 🧮 Aggregate Functions

|Function|Use|
|---|---|
|COUNT()|Number of rows|
|SUM()|Total of values|
|AVG()|Average value|
|MAX()|Highest value|
|MIN()|Lowest value|

Example:

```sql
SELECT COUNT(*) FROM Customers;
```

---
