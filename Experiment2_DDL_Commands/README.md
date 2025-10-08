# Experiment 2: DDL Commands

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
Write a SQL Query  to add attribute ISBN as varchar(30) and domain_dept as varchar(30) in the table 'books'

 

 

For example:

Test	Result
pragma table_info('books');
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           book_id     INT         0                       1
1           title       VARCHAR(15  0                       0
2           author      VARCHAR(10  0                       0
3           genre       VARCHAR(50  0                       0
4           publicatio  INT         0                       0
5           ISBN        varchar(30  0                       0
6           domain_dep  varchar(30  0                       0

```sql
ALTER TABLE books ADD COLUMN ISBN varchar(30);
ALTER TABLE books ADD COLUMN domain_dept varchar(30);
```

**Output:**

<img width="1920" height="1140" alt="image" src="https://github.com/user-attachments/assets/417d0de2-a1be-47a3-85f9-83954d0c600c" />


**Question 2**
---
Insert the following products into the Products table:

Name        Category     Price       Stock
----------  -----------  ----------  ----------
Smartphone  Electronics  800         150
Headphones  Accessories  200         300
For example:

Test	Result
SELECT Name, Category, Price, Stock FROM Products;

Name        Category     Price       Stock
----------  -----------  ----------  ----------
Smartphone  Electronics  800         150
Headphones  Accessories  200         300


```sql
INSERT INTO Products (Name, Category, Price, Stock)
VALUES
    ('Smartphone', 'Electronics', 800, 150),
    ('Headphones', 'Accessories', 200, 300);
```

**Output:**

<img width="1920" height="1140" alt="image" src="https://github.com/user-attachments/assets/6aeda188-904c-4b3c-b5b7-3a775452e505" />


**Question 3**
---
Create a table named Shipments with the following constraints:
ShipmentID as INTEGER should be the primary key.
ShipmentDate as DATE.
SupplierID as INTEGER should be a foreign key referencing Suppliers(SupplierID).
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).
For example:

Test	Result
INSERT INTO Shipments (ShipmentID, ShipmentDate, SupplierID, OrderID) VALUES (2, '2024-08-03', 99, 1);
Error: FOREIGN KEY constant

```sql
CREATE TABLE Shipments (
    ShipmentID   INTEGER PRIMARY KEY,
    ShipmentDate DATE,
    SupplierID   INTEGER,
    OrderID      INTEGER,
    FOREIGN KEY (SupplierID) REFERENCES Suppliers(SupplierID),
    FOREIGN KEY (OrderID) REFERENCES Orders(OrderID)
);
```

**Output:**

<img width="1920" height="1140" alt="image" src="https://github.com/user-attachments/assets/bff0e60e-b679-4a6d-8689-e0c6ee50e08b" />


**Question 4**
---
Insert all employees from Former_employees into Employee

Table attributes are EmployeeID, Name, Department, Salary

For example:

Test	Result
select * from Employee;
EmployeeID  Name        Department  Salary
----------  ----------  ----------  ----------
201         John Doe    HR          50000
202         Jane Smith  Engineerin  75000
203         Emily Davi  Marketing   60000

```sql
INSERT INTO Employee (EmployeeID, Name, Department, Salary)
SELECT EmployeeID, Name, Department, Salary
FROM Former_employees;
```

**Output:**

<img width="1920" height="1140" alt="image" src="https://github.com/user-attachments/assets/0a0f2fb6-2b4b-4051-970c-de7d655b813e" />


**Question 5**
---
Create a table named Department with the following constraints:
DepartmentID as INTEGER should be the primary key.
DepartmentName as TEXT should be unique and not NULL.
Location as TEXT.
For example:

Test	Result
INSERT INTO Department (DepartmentID, DepartmentName, Location) VALUES (1, 'Human Resources', 'New York');
select * from Department;
DepartmentID  DepartmentName   Location
------------  ---------------  ----------
1             Human Resources  New York

```sql
CREATE TABLE Department (
    DepartmentID   INTEGER PRIMARY KEY,
    DepartmentName TEXT UNIQUE NOT NULL,
    Location       TEXT
);
```

**Output:**

<img width="1920" height="1140" alt="image" src="https://github.com/user-attachments/assets/7b8a185e-ff4a-4b6f-aa46-10ce2fc3baef" />


**Question 6**
---
create a table named jobs including columns job_id, job_title, min_salary and max_salary, and make sure that, the default value for job_title is blank and min_salary is 8000 and max_salary is NULL will be entered automatically at the time of insertion if no value assigned for the specified columns.
For example:

Test	Result
INSERT INTO jobs (job_id, job_title, min_salary, max_salary) VALUES (1, 'Software Engineer', 9000, 15000);
SELECT * FROM jobs;
job_id      job_title          min_salary  max_salary
----------  -----------------  ----------  ----------
1           Sof

```sql
CREATE TABLE jobs (
    job_id     INTEGER PRIMARY KEY,
    job_title  TEXT DEFAULT '',
    min_salary INTEGER DEFAULT 8000,
    max_salary INTEGER DEFAULT NULL
);
```

**Output:**

<img width="1920" height="1140" alt="image" src="https://github.com/user-attachments/assets/d321c6e1-d73a-46f2-ab49-f56d3fed0f45" />

**Question 7**
---
Write an SQL query to add a new column salary of type INTEGER to the Employees table, with a CHECK constraint that ensures the value in this column is greater than 0.

 

 

For example:

Test	Result
pragma table_info('employees');
cid         name        type        notnull     dflt_value  pk
----------  ----------  ----------  ----------  ----------  ----------
0           id          INTEGER     0                       1
1           name        TEXT        1                       0
2           salary      INTEGER     0                       0


```sql
ALTER TABLE Employees
ADD COLUMN salary INTEGER CHECK (salary > 0);
```

**Output:**

<img width="1920" height="1140" alt="image" src="https://github.com/user-attachments/assets/07336c43-fa53-4480-b891-3498d89d9641" />


**Question 8**
---
Create a table named Locations with the following columns:

LocationID as INTEGER
LocationName as TEXT
Address as TEXT
For example:

Test	Result
pragma table_info('Locations');
cid       name             type        notnull     dflt_value  pk
--------  ---------------  ----------  ----------  ----------  ----------
0         LocationID       INTEGER     0                       0
1         LocationName     TEXT        0                       0
2         Address          TEXT        0                       0


```sql
Create a table named Locations with the following columns:

LocationID as INTEGER
LocationName as TEXT
Address as TEXT
For example:

Test	Result
pragma table_info('Locations');
cid       name             type        notnull     dflt_value  pk
--------  ---------------  ----------  ----------  ----------  ----------
0         LocationID       INTEGER     0                       0
1         LocationName     TEXT        0                       0
2         Address          TEXT        0                       0
```

**Output:**

<img width="1920" height="1140" alt="image" src="https://github.com/user-attachments/assets/83cafabc-c14a-465b-b5d1-fa2df4666f47" />


**Question 9**
---
Insert the below data into the Customers table, allowing the City and ZipCode columns to take their default values.

CustomerID  Name          Address
----------  ------------  ----------
304         Peter Parker  Spider St      

Note: The City and ZipCode columns will use their default values.
 
For example:

Test	Result
SELECT CustomerID, Name, Address
FROM Customers;
CustomerID  Name          Address
----------  ------------  ----------
304         Peter Parker  Spider St


```sql
INSERT INTO Customers (CustomerID, Name, Address)
VALUES (304, 'Peter Parker', 'Spider St');
```

**Output:**

<img width="1920" height="1140" alt="image" src="https://github.com/user-attachments/assets/8336d415-0f68-4c04-9be5-eeb9ae19be33" />


**Question 10**
---
Create a table named ProjectAssignments with the following constraints:
AssignmentID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
AssignmentDate as DATE should be NOT NULL.
For example:

Test	Result
INSERT INTO ProjectAssignments (AssignmentID, EmployeeID, ProjectID, AssignmentDate) VALUES (2, 99, 1, '2024-01-03');
Error: FO
```sql
-Create a table named ProjectAssignments with the following constraints:
AssignmentID as INTEGER should be the primary key.
EmployeeID as INTEGER should be a foreign key referencing Employees(EmployeeID).
ProjectID as INTEGER should be a foreign key referencing Projects(ProjectID).
AssignmentDate as DATE should be NOT NULL.
For example:

Test	Result
INSERT INTO ProjectAssignments (AssignmentID, EmployeeID, ProjectID, AssignmentDate) VALUES (2, 99, 1, '2024-01-03');
Error: FO
```

**Output:**

<img width="1920" height="1140" alt="image" src="https://github.com/user-attachments/assets/ebdd2297-e740-437d-b3e8-28f8da6cd8a4" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
