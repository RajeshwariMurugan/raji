
## Introduction to Databases & MySQL
---
### Database

A **database** is an organized collection of data that is stored and accessed electronically. It allows for efficient data management, retrieval, and manipulation using systems like SQL-based relational databases or NoSQL alternatives.

>***A Structured collection of Data***

### Types of Databases

1. **Relational DB** 
   Data stored in structured format of rows and column (table) and language used to interact with is Structured Query Language.

   Examples : `MySQL` , `PostgreSQL` , `Oracle`

2. **NoSQL DB**
   Data stored in unstructured format like .json , graph , key:value pair etc.
   Examples : `MongoDB` , `Firebase` , `Cassandra`

---

### SQL Commands & Queries

**SQL Commands** are instructions used to perform specific tasks in a database, such as creating tables, inserting data, or modifying structures. They are grouped into categories like DDL, DML, DCL, and TCL.

**SQL Queries** are specific types of SQL commands used to retrieve data from a database, typically using the `SELECT` statement with conditions and filters.

SQL Commands basic types and functions:

|           Task            |            Command            |
| :-----------------------: | :---------------------------: |
| **Permission Management** |      GRANT , USE db_name      |
|    **Creating Tables**    |         CREATE TABLE          |
|   **Modifying Tables**    |          ALTER TABLE          |
|   **Data Manipulation**   | INSERT INTO , UPDATE , DELETE |

Some basic syntaxes:

| Syntax                   | Description                           |
| ------------------------ | ------------------------------------- |
| CREATE DATABASE db_name; | creates a new DB                      |
| DROP DATABASE db_name;   | deletes the created DB                |
| USE db_name;             | to select the desired DB to work with |
