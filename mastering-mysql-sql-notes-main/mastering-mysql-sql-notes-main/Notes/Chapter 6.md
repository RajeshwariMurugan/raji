
## Basic SQL Queries (CRUD Operations)
---
### 🗂️ CRUD Operations – SQL Basics

#### 📌 What is CRUD?

CRUD stands for **Create, Read, Update, Delete** — the four basic operations for managing data in a database.

#### ✅ 1. Create

**Definition**: Add new data to the database.  
**SQL Command**: `INSERT`

```sql
INSERT INTO students (id, name, age)
VALUES (1, 'Alice', 20);
```

---

#### 🔍 2. Read

**Definition**: View or retrieve data.  
**SQL Command**: `SELECT`

```sql
SELECT * FROM students;
```

---
#### ✏️ 3. Update

**Definition**: Change existing data.  
**SQL Command**: `UPDATE`

```sql
UPDATE students
SET age = 21
WHERE id = 1;
```

---

#### ❌ 4. Delete

**Definition**: Remove data.  
**SQL Command**: `DELETE`

```sql
DELETE FROM students
WHERE id = 1;
```

---

#### 🧠 Summary

|Operation|Action|SQL Keyword|
|---|---|---|
|Create|Add data|`INSERT`|
|Read|View data|`SELECT`|
|Update|Change data|`UPDATE`|
|Delete|Remove data|`DELETE`|

---
### 🛠️ SQL Data Manipulation Sequence

This note covers the basic steps to manipulate data in SQL, in order:  
`Insert → Retrieve → Filter → Sort → Update → Delete`

#### 1️⃣ Inserting Data

**Definition**: Add new records to a table.  
**Command**: `INSERT INTO`

```sql
INSERT INTO students (id, name, age)
VALUES (1, 'Alice', 20);
```

---

#### 2️⃣ Retrieving Data

**Definition**: View or fetch data from a table.  
**Command**: `SELECT`

```sql
SELECT * FROM students;
```

---

#### 3️⃣ Filtering Data

**Definition**: Get specific data using conditions.  
**Command**: `WHERE`

```sql
SELECT * FROM students
WHERE age > 18;
```

---

#### 4️⃣ Sorting Data

**Definition**: Order the data (ascending or descending).  
**Command**: `ORDER BY`

```sql
SELECT * FROM students
ORDER BY age DESC;
```

---

#### 5️⃣ Updating Data

**Definition**: Modify existing records.  
**Command**: `UPDATE + SET`

```sql
UPDATE students
SET age = 21
WHERE id = 1;
```

---

#### 6️⃣ Deleting Data

**Definition**: Remove records from a table.  
**Command**: `DELETE FROM`

```sql
DELETE FROM students
WHERE id = 1;
```

---

#### ✅ Quick Summary Table

|Step|Action|SQL Keyword|
|---|---|---|
|1. Insert|Add data|`INSERT INTO`|
|2. Retrieve|View data|`SELECT`|
|3. Filter|Condition-based|`WHERE`|
|4. Sort|Arrange data|`ORDER BY`|
|5. Update|Modify data|`UPDATE ... SET`|
|6. Delete|Remove data|`DELETE FROM`|

---

