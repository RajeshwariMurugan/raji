
## 📊 Aggregating & Grouping Data in MySQL

---

## 🔢 What is Aggregation?

**Aggregation** means summarizing data — like counting rows, finding averages, totals, min/max values, etc.

MySQL provides **aggregate functions** for this purpose.

---

### 📦 Common Aggregate Functions

|Function|Description|Example|
|---|---|---|
|`COUNT()`|Counts the number of rows|`COUNT(*)` or `COUNT(column)`|
|`SUM()`|Adds values in a column|`SUM(Salary)`|
|`AVG()`|Calculates average|`AVG(Price)`|
|`MIN()`|Finds minimum value|`MIN(Age)`|
|`MAX()`|Finds maximum value|`MAX(Score)`|

---

### ✅ Examples

```sql
SELECT COUNT(*) FROM Customers;
```

📌 _Total number of customers_

```sql
SELECT AVG(Salary) FROM Employees;
```

📌 _Average salary of all employees_

```sql
SELECT MIN(OrderDate), MAX(OrderDate) FROM Orders;
```

📌 _Earliest and latest order dates_

---

## 📚 GROUP BY Clause

**GROUP BY** is used to **group rows** that have the same values in one or more columns and then perform aggregation **on each group**.

---

### 🧾 Syntax

```sql
SELECT column, AGG_FUNC(column)
FROM table
GROUP BY column;
```

---

### ✅ Basic Example

```sql
SELECT City, COUNT(*) AS TotalCustomers
FROM Customers
GROUP BY City;
```

📌 _Counts how many customers are in each city_

---

### 🔄 Multiple Aggregates

```sql
SELECT Department, COUNT(*) AS TotalEmployees, AVG(Salary) AS AvgSalary
FROM Employees
GROUP BY Department;
```

📌 _Shows employee count and average salary per department_

---

### 🧠 GROUP BY Multiple Columns

```sql
SELECT City, Gender, COUNT(*) AS Total
FROM Customers
GROUP BY City, Gender;
```

📌 _Groups by both City and Gender_

---

### 🔎 Filtering Groups: HAVING Clause

**HAVING** is used to filter groups (like `WHERE`, but for grouped results).

```sql
SELECT City, COUNT(*) AS TotalCustomers
FROM Customers
GROUP BY City
HAVING COUNT(*) > 5;
```

📌 _Returns only cities with more than 5 customers_

---

### 🔄 Difference Between WHERE and HAVING

|Clause|Used For|Applies To|
|---|---|---|
|`WHERE`|Filter **rows**|Before grouping|
|`HAVING`|Filter **groups**|After grouping|

Example using both:

```sql
SELECT City, AVG(Age) AS AvgAge
FROM Customers
WHERE Age > 18
GROUP BY City
HAVING AVG(Age) > 30;
```

📌 _Groups only adults and shows cities where average age is above 30_

---

## 🧪 Real-World Example

Table: `Orders`

|OrderID|CustomerID|TotalAmount|Status|
|---|---|---|---|
|1|101|150.00|Shipped|
|2|102|250.00|Pending|
|3|101|120.00|Shipped|

```sql
SELECT CustomerID, SUM(TotalAmount) AS TotalSpent
FROM Orders
GROUP BY CustomerID;
```

📌 _Shows how much each customer has spent_

---

## 🧠 Tips

- Always include **non-aggregated columns** in the `GROUP BY` clause.
    
- Use **aliases** (`AS`) for cleaner output.
    
- Use **HAVING** instead of **WHERE** to filter after grouping.
    

---
