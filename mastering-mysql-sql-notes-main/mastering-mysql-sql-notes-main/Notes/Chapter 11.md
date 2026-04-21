
## 🗑️ Deleting Data in MySQL
---
### ❌ DELETE Statement

Used to **remove one or more records** from a table.

```sql
DELETE FROM table_name
WHERE condition;
```

---

### ✅ Basic Example

```sql
DELETE FROM Customers
WHERE CustomerID = 4;
```

📌 _Deletes the customer with ID 4._

---

### ⚠️ Always Use WHERE!

If you **omit the `WHERE` clause**, **all rows** in the table will be deleted.

```sql
DELETE FROM Customers;
```

📌 _Deletes **all** customer records. Dangerous!_

---

### 🔍 Deleting with Multiple Conditions

```sql
DELETE FROM Customers
WHERE City = 'Chicago' AND Age < 18;
```

📌 _Deletes customers from Chicago who are under 18._

---

### 🧼 Delete Based on NULL

```sql
DELETE FROM Customers
WHERE Email IS NULL;
```

📌 _Deletes customers without an email address._

---

### 🧪 Safe Delete: Check First with SELECT

```sql
SELECT * FROM Customers
WHERE City = 'Boston';
```

Then:

```sql
DELETE FROM Customers
WHERE City = 'Boston';
```

📌 _Always verify before running a DELETE._

---

### 🚫 Cannot Delete from Multiple Tables

Unlike `SELECT`, `DELETE` in MySQL cannot target multiple tables unless using **JOIN with alias** (advanced use case).

---

### ♻️ AUTO_INCREMENT After DELETE

Deleting rows **does not reset** the `AUTO_INCREMENT` value.

```sql
DELETE FROM Customers WHERE CustomerID = 10;
```

📌 _The next inserted ID will still continue from the last highest value._


---

## 🧹 TRUNCATE vs DELETE in MySQL

|Feature|DELETE|TRUNCATE|
|---|---|---|
|Purpose|Deletes rows based on condition|Deletes **all** rows in the table|
|Syntax|`DELETE FROM table WHERE condition;`|`TRUNCATE TABLE table;`|
|Condition support|Yes, can delete specific rows|No, deletes entire table|
|Logging|Fully logged (row by row)|Minimal logging, faster|
|Speed|Slower on large tables|Faster for deleting all rows|
|AUTO_INCREMENT reset|**No** — counter is not reset|**Yes** — counter is reset to 1|
|Triggers|Activates DELETE triggers|Does **not** activate DELETE triggers|
|Transaction support|Can be rolled back if inside transaction|Often can’t be rolled back (depends on storage engine)|
|Locks|Row-level locking|Table-level locking|

---

### 📝 Examples

**DELETE all rows:**

```sql
DELETE FROM Customers;
```

- Deletes all rows but keeps the table structure and AUTO_INCREMENT value.
    

---

**TRUNCATE all rows:**

```sql
TRUNCATE TABLE Customers;
```

- Quickly removes all rows and resets AUTO_INCREMENT to 1.
    

---

### ⚠️ When to Use Which?

- Use **DELETE** when:
    
    - You want to delete specific rows using conditions.
        
    - You need to activate triggers.
        
    - You want the option to rollback the delete inside transactions.
        
- Use **TRUNCATE** when:
    
    - You want to delete **all rows** quickly.
        
    - You want to reset AUTO_INCREMENT.
        
    - You don’t need to activate triggers or worry about rollback.
        

---
