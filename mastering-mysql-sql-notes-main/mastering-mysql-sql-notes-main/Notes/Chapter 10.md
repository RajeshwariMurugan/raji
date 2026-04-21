
## ✏️ Updating Data in MySQL
---
### 🔧 UPDATE Statement

Used to **modify existing records** in a table.

```sql
UPDATE table_name
SET column1 = value1, column2 = value2
WHERE condition;
```

---

### ✅ Basic Example

```sql
UPDATE Customers
SET City = 'Los Angeles'
WHERE CustomerID = 3;
```

📌 _Updates the city of the customer with ID 3 to "Los Angeles"._

---

### ⚠️ Always Use WHERE!

If you **omit the `WHERE` clause**, **all rows** will be updated.

```sql
UPDATE Customers
SET City = 'Unknown';
```

📌 _This will set the city to 'Unknown' for **every customer**._

---

### 🧠 Updating Multiple Columns

```sql
UPDATE Customers
SET Name = 'John Doe', City = 'Chicago'
WHERE CustomerID = 5;
```

📌 _Updates both name and city for customer with ID 5._

---

### 🔍 Use with SELECT for Safe Updates

Always check affected rows before updating:

```sql
SELECT * FROM Customers
WHERE City = 'Dallas';
```

Then:

```sql
UPDATE Customers
SET City = 'Houston'
WHERE City = 'Dallas';
```

---

### 🧪 Using Expressions in Updates

```sql
UPDATE Customers
SET Age = Age + 1
WHERE City = 'New York';
```

📌 _Increments age by 1 for all customers in New York._

---

### 🚫 Update Based on NULL

```sql
UPDATE Customers
SET Address = 'Pending'
WHERE Address IS NULL;
```

📌 _Fills in missing addresses with 'Pending'._

---
