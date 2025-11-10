# Experiment 6: Joins

## NAME : HARISH S
## REG.NO: 212224110022

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
 From the following tables write a SQL query to find salespeople who received commissions of more than 12 percent from the company. Return Customer Name, customer city, Salesman, commission.  


```sql
select c.cust_name as 'Customer Name',c.city,s.name as Salesman, s.commission
from customer c
join salesman s on c.salesman_id=s.salesman_id
where s.commission>0.12;
```

**Output:**

<img width="1110" height="679" alt="image" src="https://github.com/user-attachments/assets/d405f6c3-f85b-4c4b-96d2-57962885cd07" />

**Question 2**
---
From the following tables write a SQL query to find those orders where the order amount exists between 500 and 2000. Return ord_no, purch_amt, cust_name, city.


```sql
select o.ord_no,o.purch_amt,c.cust_name,c.city
from customer c
join orders o on c.salesman_id=o.salesman_id
where o.purch_amt between 500 and 2000
group by o.ord_no ;
```


**Output:**

<img width="1130" height="453" alt="image" src="https://github.com/user-attachments/assets/069f382c-fd83-4c91-8362-81f03921fdd4" />

**Question 3**
---
From the following tables write a SQL query to find the details of an order. Return ord_no, ord_date, purch_amt, Customer Name, grade, Salesman, commission. 


```sql
select o.ord_no,o.ord_date,o.purch_amt,c.cust_name as 'Customer Name',c.grade,s.name as 'Salesman',s.commission
from customer c
join orders o on c.customer_id=o.customer_id
join salesman s on c.salesman_id=s.salesman_id;
```

**Output:**

<img width="1066" height="648" alt="image" src="https://github.com/user-attachments/assets/90a3f61c-7cbb-408a-ab9e-43cc26adaa8c" />

**Question 4**
---
Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), with a left join on the "salesman_id" column and a condition filtering for customers in the city 'New York'.


```sql
select s.name from customer c
left join salesman s on c.salesman_id=s.salesman_id
where c.city='New York';
```

**Output:**

<img width="259" height="237" alt="image" src="https://github.com/user-attachments/assets/12944194-9431-4d89-84e5-65f257b28bd3" />

**Question 5**
---
write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.


```sql
select s.name as 'Salesman',c.cust_name,c.city from customer c
join salesman s on c.city=s.city
order by s.salesman_id;
```

**Output:**

<img width="847" height="558" alt="image" src="https://github.com/user-attachments/assets/9c47906e-7f2a-4888-99b9-437184607cc2" />

**Question 6**
---
Write the SQL query that achieves the selection of the "name" column from the "salesman" table (aliased as "s"), the "cust_name," "city," "grade," and "salesman_id" columns from the "customer" table (aliased as "c"), with a left join on the "salesman_id" column and a condition filtering for customers with a grade less than or equal to 100.


```sql
select s.name,c.cust_name,c.city,c.grade,c.salesman_id from customer c
left join salesman s on c.salesman_id=s.salesman_id
where c.grade<=100;
```

**Output:**

<img width="1262" height="476" alt="image" src="https://github.com/user-attachments/assets/2cbd205f-51a9-4306-941e-19b92e514b0b" />

**Question 7**
---
Write the SQL query that accomplishes the selection of all columns from the "patients" table and the first name of doctors from the "doctors" table, with an inner join on the "doctor_id" column.


```sql
select distinct p.*,d.first_name as 'doctor_name' from patients p
inner join doctors d on p.doctor_id=d.doctor_id;
```

**Output:**

<img width="1289" height="489" alt="image" src="https://github.com/user-attachments/assets/e2565706-cb58-4f99-8d68-aab4a9f4ad4d" />

**Question 8**
---
Write the SQL query that achieves the selection of the first name from the "patients" table, with an inner join on the "patient_id" column and a condition filtering for surgeries with a surgery date of '2024-01-15'.:


```sql
select p.first_name from patients p
inner join surgeries s on p.patient_id=s.patient_id
where s.surgery_date='2024-01-15';
```

**Output:**

<img width="481" height="357" alt="image" src="https://github.com/user-attachments/assets/f6ba15f5-c88b-42c7-81f6-6919e23a6487" />

**Question 9**
---
Write the SQL query that achieves the selection of all columns from the "nurses" table (aliased as "n"), with an inner join on the "department_id" column and a condition filtering for nurses in the 'Pediatrics' department.


```sql
select distinct n.* from nurses n
inner join departments d on n.department_id=d.department_id
where d.department_name='Pediatrics';
```

**Output:**

<img width="1038" height="344" alt="image" src="https://github.com/user-attachments/assets/f04a2c8e-a1d1-40a9-a7cf-cd49733093e3" />

**Question 10**
---
 From the following tables write a SQL query to find the salesperson(s) and the customer(s) he represents. Return Customer Name, city, Salesman, commission.


```sql
select c.cust_name as 'Customer Name',c.city,s.name as 'Salesman',s.commission
from customer c
join salesman s on c.salesman_id=s.salesman_id;
```

**Output:**

<img width="1043" height="747" alt="image" src="https://github.com/user-attachments/assets/05d2407c-1741-4eda-a48b-446a98f4ee2e" />


## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
