# Experiment 5: Subqueries and Views
## Name: Payyavula Jeshwanth Kumar
## Reg.No: 212223240114
## AIM
To study and implement subqueries and views.


## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
--
<img width="1245" height="575" alt="image" src="https://github.com/user-attachments/assets/32e95891-dff9-4722-9eaf-20f3bbee8461" />


```sql
SELECT ord_no,purch_amt,ord_date,customer_id,salesman_id
FROM orders
WHERE salesman_id = (
    SELECT salesman_id
    FROM orders
    WHERE customer_id = 3007
);

```

**Output:**
--
<img width="1237" height="440" alt="image" src="https://github.com/user-attachments/assets/359d41ca-5efe-4579-b117-c1f0992bef8c" />



**Question 2**
---
<img width="983" height="680" alt="image" src="https://github.com/user-attachments/assets/ca9e0098-92e6-410e-a8d4-ba048c5967ea" />


```sql
select * from CUSTOMERS 
WHERE SALARY>4500;
```

**Output:**
--
<img width="1202" height="428" alt="image" src="https://github.com/user-attachments/assets/aba31961-13f4-44a4-9d4e-6094e8dff79f" />



**Question 3**
---
<img width="1077" height="537" alt="image" src="https://github.com/user-attachments/assets/e6c23c51-7a95-4604-ab2f-7491fa507ba8" />


```sql
SELECT name, city FROM customer WHERE city IN (SELECT city FROM customer WHERE id IN (3, 7))
```

**Output:**
--

<img width="547" height="488" alt="image" src="https://github.com/user-attachments/assets/e6aabf38-f47d-481a-90ec-b7ddb4f96b44" />


**Question 4**
---
<img width="1250" height="647" alt="image" src="https://github.com/user-attachments/assets/243600c1-1812-46f4-b3cc-10382f3d2cf8" />


```sql
SELECT student_id, student_name, subject, grade
FROM GRADES g
WHERE grade = (
    SELECT MIN(grade)
    FROM GRADES
    WHERE subject = g.subject
);

```

**Output:**
--
<img width="1202" height="427" alt="image" src="https://github.com/user-attachments/assets/daba31e0-3e19-4b2e-96b0-c2142ea142ea" />


**Question 5**
---
<img width="1277" height="716" alt="image" src="https://github.com/user-attachments/assets/12ad7c10-eaed-4fcf-a659-1d4130270ac6" />


```sql
SELECT
    o.ord_no,
    o.purch_amt,
    o.ord_date,
    o.customer_id,
    o.salesman_id
FROM
    orders o
JOIN
    salesman s ON o.salesman_id = s.salesman_id
WHERE
    s.city = 'New York';
```

**Output:**

<img width="1115" height="446" alt="image" src="https://github.com/user-attachments/assets/962963f7-7300-4bdb-b52b-1b6776f15eaf" />


**Question 6**
---
<img width="1226" height="578" alt="image" src="https://github.com/user-attachments/assets/0a207fb4-0a64-4a95-8dd4-76f3d37e8a3b" />


```sql
SELECT student_name, grade
FROM GRADES g
WHERE grade = (
    SELECT MIN(grade)
    FROM GRADES
    WHERE subject = g.subject
);

```

**Output:**
--
<img width="655" height="427" alt="image" src="https://github.com/user-attachments/assets/e902a398-306d-4621-af8a-eea691868235" />


**Question 7**
---
<img width="1165" height="432" alt="image" src="https://github.com/user-attachments/assets/a1f1e393-32ac-4203-a339-8dd2df0ecc5b" />


```sql
SELECT grade, COUNT(*)
FROM customer
WHERE grade>(
    SELECT AVG(grade)   
    FROM customer 
    WHERE city='New York'
)
GROUP BY grade;
```

**Output:**
--
<img width="497" height="336" alt="image" src="https://github.com/user-attachments/assets/e4b3afa9-cf1c-4d7a-aae7-84b365b754a9" />


**Question 8**
---
<img width="1012" height="428" alt="image" src="https://github.com/user-attachments/assets/c25d7db3-547c-46b5-bd4c-a95b6419db0a" />


```sql
SELECT department_id, department_name
FROM Departments
WHERE LENGTH(department_name) > (SELECT AVG(LENGTH(department_name)) FROM Departments);
```

**Output:**
--
<img width="496" height="392" alt="image" src="https://github.com/user-attachments/assets/3abfa893-b6ff-4254-852a-b0277e655687" />



**Question 9**
---
<img width="1262" height="631" alt="image" src="https://github.com/user-attachments/assets/ecb4bb5e-1aa5-4b76-b0d1-46deb7a99d8b" />


```sql
SELECT
    o.ord_no,
    o.purch_amt,
    o.ord_date,
    o.customer_id,
    o.salesman_id
FROM
    orders o
JOIN
    salesman s ON o.salesman_id = s.salesman_id
WHERE
    s.city = 'London';
```

**Output:**
--
<img width="1113" height="405" alt="image" src="https://github.com/user-attachments/assets/79a5ca10-566c-47ee-967e-70d341ac31ec" />


**Question 10**
---
<img width="963" height="653" alt="image" src="https://github.com/user-attachments/assets/5483c0e8-d374-4361-a414-38a4515389eb" />


```sql
SELECT *
FROM CUSTOMERS
WHERE SALARY > 1500;
```

**Output:**
--
<img width="1091" height="578" alt="image" src="https://github.com/user-attachments/assets/13e5fb0b-2e9d-4dbf-974c-e71a43315f48" />

**Result**
--
<img width="1460" height="86" alt="image" src="https://github.com/user-attachments/assets/9ac903a8-2489-47ef-938f-0f221d0840ee" />




## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
