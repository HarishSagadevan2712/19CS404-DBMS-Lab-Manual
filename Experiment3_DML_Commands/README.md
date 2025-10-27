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
-- Paste Question 1 here
Write a SQL statement to update the product_name as 'Grapefruit' whose product_id is 4 in the products table.

products table

---------------
product_id
product_name
category_id
availability
```sql
-- Paste your SQL code below for Question 1
UPDATE products
SET product_name = 'Grapefruit'
WHERE product_id = 4;

```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/35f818c3-338c-4cca-b152-c4d27c4d0977" />

**Question 2**
---
-- Paste Question 2 here
Write a SQL statement to Update the hire_date of employees in department 50 to 2024-01-24.

Employees table

---------------
employee_id
first_name
last_name
email
phone_number
hire_date
job_id
salary
commission_pct
manager_id
department_id****

```sql
-- Paste your SQL code below for Question 2
UPDATE Employees
SET hire_date = '2024-01-24'
WHERE department_id = 50;

```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/da31ea04-d604-4b41-a96f-a07248b29a3e" />

**Question 3**
---
-- Paste Question 3 here
Change the supplier name to upper case where contact person contains ' Singh' in suppliers table.

name               type
-----------------  ---------------
supplier_id        INT
supplier_name      VARCHAR(100)
contact_person     VARCHAR(100)
phone_number       VARCHAR(20)
email              VARCHAR(100)
address            VARCHAR(250)

```sql
-- Paste your SQL code below for Question 3
UPDATE suppliers
SET supplier_name = UPPER(supplier_name)
WHERE contact_person LIKE '% Singh';

```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/62d7ab50-e439-412f-9d7b-3ef33fe545bb" />

**Question 4**
---
-- Paste Question 4 here
Write a SQL statement to double the availability of the product with product_id 1.

products table

---------------
product_id
product_name
category_id
availability

```sql
-- Paste your SQL code below for Question 4
UPDATE products
SET availability = availability * 2
WHERE product_id = 1;

```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e84840eb-343e-4d77-863a-057ae75da95b" />

**Question 5**
---
-- Paste Question 5 here
Write a SQL statement to Increase the selling price by 10% for all products in the 'Bakery' category in the products table.

Products table

---------------
product_id
product_name
category
cost_price
sell_price
reorder_lvl
quantity
supplier_id

```sql
-- Paste your SQL code below for Question 5
UPDATE Products
SET sell_price = sell_price * 1.10
WHERE category = 'Bakery';
```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/2a8de01a-9631-4778-bcde-51db357603e3" />

**Question 6**
---
-- Paste Question 6 here
Write a SQL query to Delete a Specific Surgery whose ID is 3 or surgeon ID is 4.

```sql
-- Paste your SQL code below for Question 6
DELETE FROM surgeries
WHERE surgery_id = 3 OR surgeon_id = 4;

```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/aa56bb09-b36f-4ca6-97a9-4309cfc88241" />

**Question 7**
---
-- Paste Question 7 here
Write a SQL query to delete a doctor from Doctors table whose Specialization is 'Pediatrics' and First name is 'Michael'.

Sample table: Doctors

attributes : doctor_id, first_name, last_name, specialization
```sql
-- Paste your SQL code below for Question 7
DELETE FROM Doctors
WHERE specialization = 'Pediatrics' AND first_name = 'Michael';
```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/69927d1a-c73a-4eaa-a801-69e227746410" />

**Question 8**
---
-- Paste Question 8 here
Write a SQL query to Delete customers from 'customer' table where 'GRADE' is odd.

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
```sql
-- Paste your SQL code below for Question 8
DELETE FROM Customer
WHERE GRADE % 2 = 1;
```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/fa577e88-244b-477e-b3a6-fc854ea86ec7" />

**Question 9**
---
-- Paste Question 9 here
Write a SQL query to remove rows from the table 'customer' with the following condition -

1. 'cust_country' must be 'India',

2. 'cus_city' must not be 'Chennai',

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
```sql
-- Paste your SQL code below for Question 9
DELETE FROM customer
WHERE cust_country = 'India'
  AND cust_city <> 'Chennai';

```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/aca2afdb-ad49-4718-aed3-c3c934eca632" />

**Question 10**
---
-- Paste Question 10 here
Write a SQL query to remove rows from the table 'customer' with the following condition -

1. 'cust_city' should begin with the letter 'L',

Sample table: Customer

+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+  
|CUST_CODE  | CUST_NAME   | CUST_CITY   | WORKING_AREA | CUST_COUNTRY | GRADE | OPENING_AMT | RECEIVE_AMT | PAYMENT_AMT |OUTSTANDING_AMT| PHONE_NO     | AGENT_CODE |
+-----------+-------------+-------------+--------------+--------------+-------+-------------+-------------+-------------+---------------+--------------+------------+
| C00013    | Holmes      | London      | London       | UK           |     2 |     6000.00 |     5000.00 |     7000.00 |       4000.00 | BBBBBBB      | A003       |
| C00001    | Micheal     | New York    | New York     | USA          |     2 |     3000.00 |     5000.00 |     2000.00 |       6000.00 | CCCCCCC      | A008       |
| C00020    | Albert      | New York    | New York     | USA          |     3 |     5000.00 |     7000.00 |     6000.00 |       6000.00 | BBBBSBB      | A008       |
```sql
-- Paste your SQL code below for Question 10
DELETE FROM customer
WHERE cust_city LIKE 'L%';

```

**Output:**

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/dbaef5fc-e4ee-4f97-8266-12b7588e5c5d" />

## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
