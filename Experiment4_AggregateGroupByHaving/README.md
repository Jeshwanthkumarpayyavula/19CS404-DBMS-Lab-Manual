# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--
<img width="1017" height="533" alt="image" src="https://github.com/user-attachments/assets/a52f8e2f-add2-41c8-a36e-599ba2c59a47" />


```sql
select DoctorID, count(*) as "TotalRecords" 
from MedicalRecords
group by DoctorID;
```

**Output:**
--
<img width="577" height="666" alt="image" src="https://github.com/user-attachments/assets/e0a015fc-50ec-40a2-9455-9b4bec783bb4" />



**Question 2**
---
<img width="617" height="607" alt="image" src="https://github.com/user-attachments/assets/12081dd9-6f7a-4aa3-a018-cef7e6799ca1" />


```sql
select strftime("%H",AppointmentDateTime) as HourOfDay,count(*) as "TotalAppointments"
from Appointments
group by HourOfDay
order by HourOfDay;
```

**Output:**
--
<img width="672" height="571" alt="image" src="https://github.com/user-attachments/assets/c4f00b25-f5bf-49a6-bfe0-6b040dc0e252" />



**Question 3**
---
<img width="968" height="618" alt="image" src="https://github.com/user-attachments/assets/28a831bf-0a64-4bbd-aac5-b778a0e15574" />


```sql
select Medication,AVG(Dosage) as AvgDosage from Prescriptions 
group by Medication; 
```

**Output:**
--
<img width="607" height="788" alt="image" src="https://github.com/user-attachments/assets/a18260ea-f21d-4346-82d7-b021f63adb4b" />



**Question 4**
---
<img width="920" height="453" alt="image" src="https://github.com/user-attachments/assets/ce906369-3740-4789-8473-fddae9b4d241" />


```sql
select sum(purch_amt) as "TOTAL" from orders;
```

**Output:**
--
<img width="332" height="345" alt="image" src="https://github.com/user-attachments/assets/77ca1575-9816-4116-91a1-24e5ebec2771" />


**Question 5**
---
<img width="982" height="506" alt="image" src="https://github.com/user-attachments/assets/9e5fcb15-e91a-4ab8-a1a0-2c2af22ccca7" />


```sql
select count(customer_id) as COUNT from customer
where grade is not null;
```

**Output:**
--
<img width="327" height="340" alt="image" src="https://github.com/user-attachments/assets/c57fbc28-4e8e-49be-8de6-503d87c562a5" />


**Question 6**
---
<img width="852" height="450" alt="image" src="https://github.com/user-attachments/assets/eea0fcf0-a2e1-4b5b-a114-cfebe1ad70d1" />


```sql
select AVG(income) as "avg_income" from employee
WHERE name like "A%";
```

**Output:**
--
<img width="336" height="345" alt="image" src="https://github.com/user-attachments/assets/2d07f21e-f9b6-479d-985f-00876d827c8b" />



**Question 7**
---
<img width="697" height="532" alt="image" src="https://github.com/user-attachments/assets/bdfb0a14-b823-4790-baa8-c2a9f55ca927" />


```sql
select name  as "fruit_name", inventory as "lowest_quantity" from fruits
order by inventory asc
limit 1;
```

**Output:**
--
<img width="648" height="345" alt="image" src="https://github.com/user-attachments/assets/7badcacf-9407-440b-860c-09bbd7d3eda5" />


**Question 8**
---
<img width="1230" height="502" alt="image" src="https://github.com/user-attachments/assets/032846c9-53a7-412c-b10e-aa3e847bc662" />


```sql
SELECT age,MIN(income) AS "MIN(income)"
FROM employee
group by age 
having MIN(income)<400000;
```

**Output:**
--

<img width="560" height="418" alt="image" src="https://github.com/user-attachments/assets/056b4d33-0c70-4769-8ccf-ca8df14d13f1" />


**Question 9**
---
<img width="1208" height="513" alt="image" src="https://github.com/user-attachments/assets/c397acfd-32e6-418e-9a94-13ad82575bde" />


```sql
SELECT occupation,AVG(workhour) AS "AVG(workhour)"
FROM employee1
GROUP BY occupation
HAVING AVG(workhour) BETWEEN 10 AND 12;
```

**Output:**
--
<img width="617" height="366" alt="image" src="https://github.com/user-attachments/assets/20908258-713a-4105-bb2b-448d80184f36" />


**Question 10**
---
<img width="1170" height="553" alt="image" src="https://github.com/user-attachments/assets/b751698a-b8b6-4e7b-aa8b-9c8161b28dd5" />


```sql
select occupation,SUM(workhour) as "SUM(workhour)"
from employee1
group by occupation 
having SUM(workhour)>20;
```

**Output:**
--
<img width="607" height="493" alt="image" src="https://github.com/user-attachments/assets/3f1a548f-ffe0-4fb8-883e-60685b6f466c" />




## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
