# Experiment 2: DDL Commands

### Name : Payyavula Jeshwanth Kumar
### Register Number : 212223240114

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
Insert all books from Out_of_print_books into Books

Table attributes are ISBN, Title, Author, Publisher, YearPublished

```sql
INSERT INTO Books
(ISBN,Title,Author,publisher,YearPublished)                                                                                                                                                                                                                                                 
SELECT ISBN,Title,Author,publisher,YearPublished
FROM Out_of_print_books;

```

**Output:**
![WhatsApp Image 2025-10-08 at 05 56 34_2ae77c28](https://github.com/user-attachments/assets/8bbeceef-2075-4e17-8809-40dd69064a11)



**Question 2**
---
Create a table named Orders with the following columns:

OrderID as INTEGER
OrderDate as TEXT
CustomerID as INTEGER

```sql
CREATE TABLE Orders (
     OrderID INTEGER,
     OrderDate TEXT,
     CustomerID INTEGER
);


```

**Output:**

![WhatsApp Image 2025-10-08 at 05 57 53_825216f5](https://github.com/user-attachments/assets/6bcc239e-ba10-40e6-86fd-11025c435e35)




**Question 3**
---
Create a new table named products with the following specifications:
product_id as INTEGER and primary key.
product_name as TEXT and not NULL.
list_price as DECIMAL (10, 2) and not NULL.
discount as DECIMAL (10, 2) with a default value of 0 and not NULL.
A CHECK constraint at the table level to ensure:
list_price is greater than or equal to discount
discount is greater than or equal to 0
list_price is greater than or equal to 0

```sql
CREATE TABLE products(
  product_id INTEGER PRIMARY KEY,
  product_name TEXT NOT NULL,
  list_price DECIMAL(10,2) NOT NULL,
  discount DECIMAL(10,2) NOT NULL DEFAULT 0,
  CHECK (list_price>=discount AND discount>=0 AND list_price>=0)
);
  
```

**Output:**
![WhatsApp Image 2025-10-08 at 05 59 01_1b65884c](https://github.com/user-attachments/assets/bf654c31-7f6f-4fa8-91eb-3bafcf083339)



**Question 4**
---
Write a SQL query to Add a new column mobilenumber as number in the Student_details table.


```sql
ALTER TABLE Student_details
ADD COLUMN mobilenumber number;
```

**Output:**
![WhatsApp Image 2025-10-08 at 06 00 16_1fe49a86](https://github.com/user-attachments/assets/e5d5f3ac-9094-4a9a-b4c5-a9c47d306495)



**Question 5**
---
Create a table named Invoices with the following constraints:
InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
Amount as REAL should be greater than 0.
DueDate as DATE should be greater than the InvoiceDate.
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

```sql
CREATE TABLE Invoices(
   InvoiceID INTEGER PRIMARY KEY,
   InvoiceDate DATE,
   Amount REAL CHECK(Amount > 0),
   DueDate DATE CHECK(DueDate > InvoiceDate),
   OrderID INTEGER,
   FOREIGN KEY (orderID) REFERENCES Orders(OrderID)
);
```

**Output:**
![WhatsApp Image 2025-10-08 at 06 01 13_58450a4f](https://github.com/user-attachments/assets/b1a794a2-8af7-4fc3-81e0-46e3d788a47a)



**Question 6**
---
Create a new table named contacts with the following specifications:
contact_id as INTEGER and primary key.
first_name as TEXT and not NULL.
last_name as TEXT and not NULL.
email as TEXT.
phone as TEXT and not NULL with a check constraint to ensure the length of phone is at least 10 characters.

```sql
CREATE TABLE contacts(
    contact_id INTEGER PRIMARY KEY,
    first_name TEXT NOT NULL,
    last_name TEXT NOT NULL,
    email TEXT,
    phone TEXT NOT NULL CHECK (LENGTH(phone)>=10)
);
```

**Output:**
![WhatsApp Image 2025-10-08 at 06 02 14_9d591f2d](https://github.com/user-attachments/assets/4e048a99-e1af-496a-8d03-b0e7542c6d5e)



**Question 7**
---
Create a table named Department with the following constraints: DepartmentID as INTEGER should be the primary key. DepartmentName as TEXT should be unique and not NULL. Location as TEXT.

```sql
CREATE TABLE Department (
    DepartmentID   INTEGER PRIMARY KEY,
    DepartmentName TEXT UNIQUE NOT NULL,
    Location       TEXT
);
```

**Output:**

<img width="1209" height="177" alt="Screenshot 2025-09-29 134428" src="https://github.com/user-attachments/assets/6eca3392-73be-4de4-a6c0-3dab2991f36a" />


**Question 8**
---
Insert a record with EmployeeID 001, Name Sarah Parker, Position Manager, Department HR, and Salary 60000 into the Employee table.

```sql
INSERT INTO Employee(EmployeeID,Name,Position,Department,Salary)
VALUES (001,'Sarah Parker','Manager','HR',60000);
```

**Output:**
![WhatsApp Image 2025-10-08 at 06 03 47_53e4c582](https://github.com/user-attachments/assets/bb822c61-893b-4769-b8ff-72491fe5b12c)



**Question 9**
---
Insert the following employees into the Employee table:

EmployeeID  Name        Position    Department  Salary
----------  ----------  ----------  ----------  ----------
2           John Smith  Developer   IT          75000
3           Anna Bell   Designer    Marketing   68000

```sql
INSERT INTO Employee(EmployeeID,Name,Position,Department,Salary)
VALUES (002,'John Smith','Developer','IT',75000);
INSERT INTO Employee(EmployeeID,Name,Position,Department,Salary)
VALUES (003,'Anna Bell','Designer','Marketing',68000);
```

**Output:**

![WhatsApp Image 2025-10-08 at 06 05 07_6d56bd85](https://github.com/user-attachments/assets/fc156343-67a4-4564-93be-d1b899aff419)



**Question 10**
---
Write an SQL Query to add the attributes designation, net_salary, and dob to the Companies table with the following data types:
designation as VARCHAR(50)
net_salary as NUMBER
dob as DATE

```sql
ALTER TABLE Companies 
ADD COLUMN designation varchar(50);
ALTER TABLE Companies 
ADD COLUMN net_salary number;
ALTER TABLE Companies 
ADD COLUMN dob date;
```

**Output:**

![image](https://github.com/user-attachments/assets/0c063267-1d3c-486d-9b6a-4770063e4b2c)



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
