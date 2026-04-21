
## 🔃 Sorting Data in MySQL
---
### 📌 ORDER BY Clause

Used to **sort the result set** by one or more columns.

```sql
SELECT * FROM Customers
ORDER BY Name;
```

📌 _Sorts customers alphabetically by name (ascending by default)._

---

### 🧭 ASC and DESC

|Keyword|Meaning|
|---|---|
|ASC|Ascending (default)|
|DESC|Descending|

```sql
SELECT * FROM Customers
ORDER BY Age DESC;
```

📌 _Returns customers sorted by age from highest to lowest._

---

### 🔢 Sorting by Multiple Columns

```sql
SELECT * FROM Customers
ORDER BY City ASC, Name DESC;
```

📌 _Sorts first by City (A–Z), then by Name (Z–A) within each city._

---

### 🧠 ORDER BY with Aliases or Expressions

You can sort by column **aliases** or **calculated fields**.

```sql
SELECT Name, LENGTH(Name) AS NameLength
FROM Customers
ORDER BY NameLength DESC;
```

📌 _Sorts customers by the length of their names._

---

### ⚠️ ORDER BY Position (Not Recommended)

You can also sort by column position in the SELECT list:

```sql
SELECT Name, City FROM Customers
ORDER BY 2;  -- Sorts by City
```

📌 _Works, but not readable or safe if the query changes._

---

### 🧪 ORDER BY + LIMIT (Top-N Query)

```sql
SELECT * FROM Customers
ORDER BY Age DESC
LIMIT 5;
```

📌 _Returns top 5 oldest customers._

---
