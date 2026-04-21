
---

## 🟣 **Scenario-Based & Real-World SQL (81–100)**

### 81. Write a query to get the second highest salary.

```sql
SELECT MAX(salary) AS second_highest
FROM employees
WHERE salary < (SELECT MAX(salary) FROM employees);
```

---

### 82. Get top 3 products by revenue in each category.

```sql
SELECT category, product_id, revenue
FROM (
   SELECT category, product_id, revenue,
          RANK() OVER(PARTITION BY category ORDER BY revenue DESC) AS rnk
   FROM products
) t
WHERE rnk <= 3;
```

---

### 83. Find all employees who joined in the last 3 months.

```sql
SELECT * FROM employees
WHERE join_date >= DATEADD(MONTH, -3, GETDATE());
```

---

### 84. Write a query to calculate the running total.

```sql
SELECT emp_id, salary,
       SUM(salary) OVER(ORDER BY emp_id) AS running_total
FROM employees;
```

---

### 85. Pivot rows to columns.

```sql
SELECT emp_id,
       MAX(CASE WHEN month = 'Jan' THEN salary END) AS Jan,
       MAX(CASE WHEN month = 'Feb' THEN salary END) AS Feb
FROM salaries
GROUP BY emp_id;
```

---

### 86. Unpivot columns into rows.

```sql
SELECT emp_id, month, salary
FROM salaries
UNPIVOT (salary FOR month IN (Jan, Feb, Mar)) u;
```

---

### 87. Find all orders without matching customers.

```sql
SELECT o.*
FROM orders o
LEFT JOIN customers c ON o.cust_id = c.id
WHERE c.id IS NULL;
```

---

### 88. Query to get monthly revenue growth.

```sql
SELECT month,
       revenue,
       revenue - LAG(revenue) OVER(ORDER BY month) AS growth
FROM monthly_sales;
```

---

### 89. Find gaps in a sequence of numbers.

```sql
SELECT t1.num + 1 AS gap_start
FROM numbers t1
LEFT JOIN numbers t2 ON t1.num + 1 = t2.num
WHERE t2.num IS NULL;
```

---

### 90. Group data into 5-minute time buckets.

```sql
SELECT DATEADD(MINUTE, DATEDIFF(MINUTE, 0, event_time)/5*5, 0) AS bucket,
       COUNT(*) AS event_count
FROM events
GROUP BY DATEADD(MINUTE, DATEDIFF(MINUTE, 0, event_time)/5*5, 0);
```

---

### 91. Get customer churn rate from subscription data.

```sql
SELECT month,
       COUNT(CASE WHEN status = 'churned' THEN 1 END)*1.0 / COUNT(*) AS churn_rate
FROM subscriptions
GROUP BY month;
```

---

### 92. Find the longest streak of active days for a user.

```sql
SELECT user_id, MAX(streak) AS longest_streak
FROM (
   SELECT user_id,
          ROW_NUMBER() OVER(PARTITION BY user_id ORDER BY activity_date) -
          ROW_NUMBER() OVER(PARTITION BY user_id, grp ORDER BY activity_date) AS streak
   FROM (
       SELECT user_id, activity_date,
              DATEADD(DAY, -ROW_NUMBER() OVER(PARTITION BY user_id ORDER BY activity_date), activity_date) AS grp
       FROM activities
   ) t
) x
GROUP BY user_id;
```

---

### 93. Perform fuzzy matching in SQL.

👉 Use functions like `SOUNDEX()` or `LEVENSHTEIN()` (if supported).

```sql
SELECT *
FROM customers
WHERE SOUNDEX(name) = SOUNDEX('Jon');
```

---

### 94. Write a query to calculate conversion rates.

```sql
SELECT campaign_id,
       COUNT(CASE WHEN action = 'purchase' THEN 1 END)*1.0 /
       COUNT(CASE WHEN action = 'visit' THEN 1 END) AS conversion_rate
FROM events
GROUP BY campaign_id;
```

---

### 95. Query to find overlapping date ranges.

```sql
SELECT a.*, b.*
FROM bookings a
JOIN bookings b ON a.id <> b.id
WHERE a.start_date < b.end_date
  AND a.end_date > b.start_date;
```

---

### 96. Find products that were never sold.

```sql
SELECT p.*
FROM products p
LEFT JOIN sales s ON p.id = s.product_id
WHERE s.product_id IS NULL;
```

---

### 97. Find the median of a numeric column.

```sql
SELECT AVG(val) AS median
FROM (
   SELECT val, ROW_NUMBER() OVER(ORDER BY val) AS rn,
          COUNT(*) OVER() AS cnt
   FROM numbers
) t
WHERE rn IN ((cnt+1)/2, (cnt+2)/2);
```

---

### 98. Count distinct users per region per month.

```sql
SELECT region, DATE_TRUNC('month', login_date) AS month,
       COUNT(DISTINCT user_id) AS active_users
FROM logins
GROUP BY region, DATE_TRUNC('month', login_date);
```

---

### 99. Identify users who purchased in last 2 months but not before.

```sql
SELECT user_id
FROM purchases
GROUP BY user_id
HAVING MAX(CASE WHEN purchase_date < DATEADD(MONTH, -2, GETDATE()) THEN 1 END) IS NULL
   AND MAX(CASE WHEN purchase_date >= DATEADD(MONTH, -2, GETDATE()) THEN 1 END) = 1;
```

---

### 100. Remove HTML tags from strings.

👉 Using regex (if supported, e.g., PostgreSQL):

```sql
SELECT REGEXP_REPLACE(description, '<[^>]*>', '', 'g') AS clean_text
FROM articles;
```

---
