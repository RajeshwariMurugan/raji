
## MySQL Data Types
---
##### Schema

A **schema** is a structured framework or blueprint that defines how data is organized and how relationships between data are handled. In databases, it specifies tables, fields, data types, and constraints.

**Example:**

```sql
CREATE TABLE Students (
  StudentID INT,
  Name VARCHAR(50),
  Age INT
);
```

_This schema defines the structure of the `Students` table with columns and data types._

---
##### Primary Key

A **Primary Key** is a unique identifier for each record in a database table; it ensures that no two rows have the same value in that column.  

**Example:**

```sql
CREATE TABLE Students (
  StudentID INT PRIMARY KEY,
  Name VARCHAR(50)
);
```

_`StudentID` uniquely identifies each student._

---
##### Foreign Key

A **Foreign Key** is a field in one table that links to the Primary Key in another table, establishing a relationship between the two tables.

**Example:**

```sql
CREATE TABLE Enrollments (
  EnrollmentID INT,
  StudentID INT,
  FOREIGN KEY (StudentID) REFERENCES Students(StudentID)
);
```

_`StudentID` in `Enrollments` refers to `StudentID` in `Students`, linking the two tables._

---

##### Normalization

**Normalization** is the process of organizing data in a database to reduce redundancy and improve data integrity. It involves dividing large tables into smaller, related tables and defining relationships between them.

> *No Duplicate* 
> *Accurate & Consistent*
> *Efficient & Logical*

---
##### Data Types

**Data Types** in MySQL define the kind of data that can be stored in a column. They specify whether a column holds numbers, text, dates, etc., helping the database manage and validate the data correctly.

**Example**

```sql
CREATE TABLE Employees (
  ID INT,
  Name VARCHAR(50),
  HireDate DATE,
  Salary DECIMAL(10,2)
);
```

- `INT` → for whole numbers
    
- `VARCHAR(50)` → for text up to 50 characters
    
- `DATE` → for date values
    
- `DECIMAL(10,2)` → for numbers with decimals (e.g., salary)

---

##### 🧮 **String Data Types in MySQL**

| **Data Type in SQL** | **Range / Size Limit**    | **Definition**         | **When to Use**                     | **Example**                   |
| -------------------- | ------------------------- | ---------------------- | ----------------------------------- | ----------------------------- |
| `CHAR(n)`            | 0 to 255 characters       | Fixed-length string    | Use when all values are same length | `CHAR(10)` for fixed ID codes |
| `VARCHAR(n)`         | 0 to 65,535 bytes*        | Variable-length string | Use when string length varies       | `VARCHAR(50)` for names       |
| `TINYTEXT`           | Up to 255 bytes           | Small text string      | For short notes or messages         | Short comment field           |
| `TEXT`               | Up to 65,535 bytes        | Medium-length text     | For paragraphs or article content   | Product descriptions          |
| `MEDIUMTEXT`         | Up to 16,777,215 bytes    | Longer text string     | For large text data                 | Blog posts or documentation   |
| `LONGTEXT`           | Up to 4,294,967,295 bytes | Very large text        | For large documents or logs         | Books, logs                   |
| `TINYBLOB`           | Up to 255 bytes           | Small binary data      | Store small files or images         | Small icons                   |
| `BLOB`               | Up to 65,535 bytes        | Binary Large Object    | Store medium-sized binary files     | Uploaded images               |
| `MEDIUMBLOB`         | Up to 16MB                | Larger binary data     | Audio/video files                   | Audio clips                   |
| `LONGBLOB`           | Up to 4GB                 | Very large binary      | Store large multimedia files        | Movies, backups               |


*Note: `VARCHAR` size limit depends on the row size and character set (e.g., UTF-8).

---
##### 🧮 **Integer Data Types in MySQL**

|**Data Type in SQL**|**Range (Signed)**|**Definition**|**When to Use**|**Example**|
|---|---|---|---|---|
|`TINYINT`|-128 to 127|Very small integer (1 byte)|When storing small numbers (e.g., flags, age, status)|`TINYINT` for `isActive` (0/1)|
|`SMALLINT`|-32,768 to 32,767|Small integer (2 bytes)|For small ranges like quantity or short IDs|`SMALLINT` for number of items|
|`MEDIUMINT`|-8,388,608 to 8,388,607|Medium integer (3 bytes)|When `SMALLINT` is too small but `INT` is too big|`MEDIUMINT` for user IDs|
|`INT` or `INTEGER`|-2,147,483,648 to 2,147,483,647|Standard integer (4 bytes)|Commonly used for general-purpose counting or IDs|`INT` for employee ID|
|`BIGINT`|-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807|Large integer (8 bytes)|For very large numbers like large user counts or money in cents|`BIGINT` for bank balance in cents|

---

##### ✅ Notes:

- Use **`UNSIGNED`** to double the positive range (e.g., `TINYINT UNSIGNED`: 0 to 255).
    
- Choose the smallest type that fits your data to save space and improve performance.

---

##### 📊 Decimal / Float Data Types in MySQL

|**Data Type in SQL**|**Range / Precision**|**Definition**|**When to Use**|**Example**|
|---|---|---|---|---|
|`DECIMAL(p, s)` or `NUMERIC(p, s)`|Exact values, up to 65 digits|Fixed-point number with precision (`p`) and scale (`s`)|For exact values like money or rates|`DECIMAL(10,2)` for currency (e.g., 99999999.99)|
|`FLOAT(p)`|~7 digits precision|Approximate, single-precision floating point|When storage is more important than exact precision|`FLOAT` for temperature or scientific data|
|`DOUBLE` or `DOUBLE PRECISION`|~15 digits precision|Approximate, double-precision floating point|For more accurate scientific or large-range data|`DOUBLE` for coordinates or measurements|
|`REAL`|Synonym for `DOUBLE` (in MySQL)|Same as `DOUBLE`|Same as above|`REAL` for latitude/longitude|

---

##### 🕒 Date / Time Data Types in MySQL

|**Data Type in SQL**|**Range**|**Definition**|**When to Use**|**Example**|
|---|---|---|---|---|
|`DATE`|'1000-01-01' to '9999-12-31'|Stores only date (YYYY-MM-DD)|For birthdays, due dates, etc.|`DATE` for `birth_date`|
|`DATETIME`|'1000-01-01 00:00:00' to '9999-12-31 23:59:59'|Date and time (no timezone)|For events with both date and time|`DATETIME` for order time|
|`TIMESTAMP`|'1970-01-01 00:00:01' UTC to '2038-01-19 03:14:07' UTC|Date and time in UTC, auto-updatable|For last updated/created timestamps|`TIMESTAMP` for `last_login`|
|`TIME`|'-838:59:59' to '838:59:59'|Stores only time (HH:MM:SS)|For durations or specific times|`TIME` for meeting duration|
|`YEAR`|1901 to 2155|Stores a 4-digit year|For year-only values|`YEAR` for graduation year|

---
