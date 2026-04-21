
---

## 🛠️ **DBA & DevOps SQL Questions (101–110)**

### 101. How do you take a backup of a database using SQL?

- **SQL Server** →
    

```sql
BACKUP DATABASE MyDB TO DISK = 'C:\backup\MyDB.bak';
```

- **MySQL** → `mysqldump -u user -p dbname > backup.sql`
    
- **Postgres** → `pg_dump dbname > backup.sql`
    

---

### 102. Tools to monitor SQL Server/MySQL/PostgreSQL performance?

🔍 Common tools:

- **SQL Server** → SSMS, SQL Profiler, DMVs
    
- **MySQL** → MySQL Workbench, Percona Monitoring, `EXPLAIN`
    
- **Postgres** → pgAdmin, `EXPLAIN ANALYZE`, pgBadger, Prometheus + Grafana
    

---

### 103. How to automate SQL job scheduling?

- **SQL Server** → SQL Server Agent Jobs
    
- **MySQL/Postgres** → `cron` + scripts or event scheduler (`CREATE EVENT`)
    
- Modern → Orchestrators like **Airflow, dbt, Dagster**
    

---

### 104. Strategies to migrate data between two databases?

📦 Options:

- **Dump & Restore** → `mysqldump`, `pg_dump`, `bcp`
    
- **Replication** → Change Data Capture (CDC), logical replication
    
- **ETL Tools** → Talend, Apache Nifi, Fivetran
    
- **Incremental syncs** → only changed data
    

---

### 105. How do you version control your database schema?

✅ Use tools like:

- **Liquibase / Flyway** (migration scripts)
    
- **Alembic** (for SQLAlchemy)
    
- Keep DDL changes in **Git repos** with CI/CD pipelines
    

---

### 106. What is blue-green deployment for SQL?

🔵🟢 Maintain **two environments** (blue = current, green = new).

- Run migrations on green
    
- Test thoroughly
    
- Switch traffic from blue → green
    
- Rollback by switching back
    

---

### 107. How to do zero-downtime deployments with SQL schema changes?

⚡ Best practices:

- **Backward-compatible migrations** (add new columns before dropping old ones)
    
- Use **views** for compatibility
    
- Deploy in **phases** (expand → migrate data → contract)
    
- Use **online schema change tools** (gh-ost, pt-online-schema-change)
    

---

### 108. What are best practices for database security?

🔒

- Principle of least privilege (no root logins in apps)
    
- Encrypt data **at rest & in transit** (TLS, TDE)
    
- Enable **audit logs**
    
- Regular **patching & updates**
    
- Strong **password policies & MFA**
    
- Use **roles** instead of direct user privileges
    

---

### 109. How do you handle large data imports efficiently?

📂

- Use **bulk insert/load utilities** (`BULK INSERT`, `LOAD DATA INFILE`, `COPY`)
    
- Disable/Drop **indexes & constraints** during load
    
- Batch inserts (avoid single huge transaction)
    
- Use **staging tables**
    

---

### 110. How to audit and log database changes?

📜 Options:

- **Triggers** → log `INSERT/UPDATE/DELETE` into audit tables
    
- **Change Data Capture (CDC)** or **Change Tracking**
    
- **Transaction logs**
    
- External tools → Oracle Audit Vault, SQL Server Audit, pgaudit (Postgres)
    

---
