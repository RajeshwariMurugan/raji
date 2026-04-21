
## 🔎 Filtering Data in MySQL
---

### ✅ WHERE Clause

Filters rows based on a condition.

```sql
SELECT * FROM Customers WHERE City = 'New York';
```

📌 _Returns all customers from New York._

---

### ⚖️ Comparison Operators

|Operator|Meaning|Example|
|---|---|---|
|=|Equal to|`WHERE Age = 25`|
|<> / !=|Not equal to|`WHERE City != 'Dallas'`|
|>|Greater than|`WHERE Age > 30`|
|<|Less than|`WHERE Age < 18`|
|>=|Greater or equal|`WHERE Age >= 21`|
|<=|Less or equal|`WHERE Age <= 65`|

```sql
SELECT * FROM Customers WHERE Age >= 30;
```

📌 _Returns customers who are 30 years or older._

---

### 🧠 Logical Operators

|Operator|Description|Example|
|---|---|---|
|AND|All conditions true|`WHERE City = 'NY' AND Age > 25`|
|OR|At least one true|`WHERE City = 'NY' OR City = 'LA'`|
|NOT|Reverses condition|`WHERE NOT City = 'Chicago'`|

```sql
SELECT * FROM Customers 
WHERE City = 'New York' AND Age > 25;
```

📌 _Returns customers in New York older than 25._

---

### 🔡 LIKE Operator

Used for pattern matching.

|Pattern|Meaning|
|---|---|
|`%`|Any number of characters|
|`_`|Single character|

```sql
SELECT * FROM Customers WHERE Name LIKE 'A%';
```

📌 _Names starting with 'A'_

```sql
SELECT * FROM Customers WHERE Email LIKE '%@gmail.com';
```

📌 _Emails ending with '@gmail.com'_

---

### 📦 IN Operator

Check if value exists in a list.

```sql
SELECT * FROM Customers 
WHERE City IN ('New York', 'Chicago', 'Dallas');
```

📌 _Returns customers from any of the listed cities._

---

### 🧾 BETWEEN Operator

Check if value is within a range (inclusive).

```sql
SELECT * FROM Orders 
WHERE OrderDate BETWEEN '2023-01-01' AND '2023-12-31';
```

📌 _Orders placed in the year 2023._

---

### 🚫 IS NULL / IS NOT NULL

Checks for NULL values.

```sql
SELECT * FROM Customers 
WHERE Address IS NULL;
```

📌 _Returns customers with no address._

```sql
SELECT * FROM Customers 
WHERE Address IS NOT NULL;
```

📌 _Returns customers who have an address._

---

