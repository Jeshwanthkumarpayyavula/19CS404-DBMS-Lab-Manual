# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
--
<img width="682" height="417" alt="image" src="https://github.com/user-attachments/assets/be972849-03da-44ea-93bd-9eff61b23211" />


```sql
update Employees
set hire_date='2024-01-24'
where department_id=50;
```

**Output:**
---

<img width="776" height="222" alt="image" src="https://github.com/user-attachments/assets/6424dc05-0812-4023-a983-6767d4417210" />


**Question 2**
---
<img width="581" height="550" alt="image" src="https://github.com/user-attachments/assets/3caa367e-001f-4d36-87b7-4709aff8c93c" />


```sql
update SALES
set sell_price=sell_price+3
where product_id IN (select product_id  from PRODUCTS where supplier_id=4);
```

**Output:**
---
<img width="772" height="282" alt="image" src="https://github.com/user-attachments/assets/241291b1-d3d3-41f7-a43f-da4823300861" />



**Question 3**
---
<img width="747" height="365" alt="image" src="https://github.com/user-attachments/assets/d72e6d02-b356-4814-8bec-1bd74c2bd638" />


```sql
update products
set sell_price=CAST(cost_price*1.35 AS INT) 
where((sell_price-cost_price)/sell_price)*100<30;
```

**Output:**
---
<img width="707" height="242" alt="image" src="https://github.com/user-attachments/assets/384eafd6-b4d4-40a5-b956-b3af27736c13" />



**Question 4**
---
<img width="685" height="381" alt="image" src="https://github.com/user-attachments/assets/ec3b8a4d-cac2-410b-af08-1a02c5776999" />


```sql
update Products 
set category='Household'
where product_name like '%Detergent%';
```

**Output:**
---
<img width="735" height="282" alt="image" src="https://github.com/user-attachments/assets/e8a50a25-0ca0-4df4-9942-a7c4aebbd0d2" />



**Question 5**
---
<img width="682" height="213" alt="image" src="https://github.com/user-attachments/assets/7708a919-9962-405c-8564-8235917e596d" />


```sql
update suppliers
set supplier_name='A1 Suppliers'
where supplier_id=8;
```

**Output:**
---
<img width="671" height="227" alt="image" src="https://github.com/user-attachments/assets/b12629cd-46ac-436a-b160-1ce6082a1cb3" />



**Question 6**
---
<img width="777" height="732" alt="image" src="https://github.com/user-attachments/assets/ab76622e-3ff0-437a-8820-a2341d4657ca" />


```sql
delete from customer
where AGENT_CODE='A003' or  AGENT_CODE='A008';
```

**Output:**
---

<img width="480" height="770" alt="image" src="https://github.com/user-attachments/assets/a3ca67fc-9f81-4879-bcf1-75cb12398a85" />


**Question 7**
---
<img width="768" height="356" alt="image" src="https://github.com/user-attachments/assets/c3c11e6d-677b-4590-9ce8-1eb4833dab09" />


```sql
delete from  Doctors
where (specialization='Pediatrics' or specialization='Cardiology') and last_name  like 'Brown'; 
```

**Output:**
---

<img width="762" height="677" alt="image" src="https://github.com/user-attachments/assets/4cab9ef9-edf3-4309-8fbc-28769be6ad1d" />


**Question 8**
---
<img width="777" height="491" alt="image" src="https://github.com/user-attachments/assets/1a7c3749-9f57-46e3-8bef-5b3febacbb00" />



```sql
delete from Customer
where CUST_CITY like "l%";
```

**Output:**
---

<img width="777" height="761" alt="image" src="https://github.com/user-attachments/assets/f5ff3ccd-00a0-4d9f-b370-c19bf08939bc" />


**Question 9**
---
<img width="772" height="457" alt="image" src="https://github.com/user-attachments/assets/5ac99887-e01b-4300-8860-9b75521f49b1" />


```sql
delete from Customer
where CUST_NAME like "______";
```

**Output:**
---

<img width="767" height="541" alt="image" src="https://github.com/user-attachments/assets/e171e633-543c-4e61-a394-0ce1472f2d45" />


**Question 10**
---
<img width="773" height="122" alt="image" src="https://github.com/user-attachments/assets/17775a5a-a772-4cd9-9fae-ba9f2ff70db4" />


```sql
delete from Doctors
where Specialization like 'Pediatrics' and first_name like 'Michael';
```

**Output:**
---
<img width="765" height="291" alt="image" src="https://github.com/user-attachments/assets/7570f9ea-7dfc-4842-9f13-282101eb3ab8" />



## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
