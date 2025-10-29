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
<img width="997" height="522" alt="image" src="https://github.com/user-attachments/assets/c1f16dfa-0de7-48c6-b73e-97aa44fbec10" />

```sql
SELECT DoctorID,COUNT(*) AS TotalRecords
FROM MedicalRecords
GROUP BY DoctorID;
```

**Output:**

<img width="612" height="620" alt="image" src="https://github.com/user-attachments/assets/73001b8a-2706-4f59-a275-52be53198292" />

**Question 2**
---
<img width="1189" height="544" alt="image" src="https://github.com/user-attachments/assets/72be10a7-0bf0-4240-8a3d-2f1c0de3c2b6" />

```sql
SELECT Specialty,Gender, COUNT(*) AS TotalDoctors
FROM Doctors
GROUP BY Specialty,Gender ;
```

**Output:**

<img width="925" height="589" alt="image" src="https://github.com/user-attachments/assets/2e6f4808-7024-4e9b-b306-75b45ae301f6" />

**Question 3**
---
<img width="974" height="648" alt="image" src="https://github.com/user-attachments/assets/1841ab68-570f-428a-8b4c-3b34694a23d7" />

```sql
SELECT DoctorID,COUNT(*) AS TotalPrescriptions
FROM Prescriptions
GROUP BY DoctorID;
```

**Output:**

<img width="748" height="722" alt="image" src="https://github.com/user-attachments/assets/0068823b-ed51-4b45-a961-ec6633e11dbe" />

**Question 4**
---
<img width="921" height="463" alt="image" src="https://github.com/user-attachments/assets/de7c2a2c-0003-40d2-976a-aef89b4d63aa" />

```sql
SELECT SUM(income) AS total_income
FROM employee
WHERE age>=40;
```

**Output:**

<img width="521" height="295" alt="image" src="https://github.com/user-attachments/assets/b64c78d3-41bd-4c9d-9bb1-741a1cc81054" />

**Question 5**
---
<img width="656" height="532" alt="image" src="https://github.com/user-attachments/assets/9276b2df-4fd4-4ff5-a440-2043514a01dd" />

```sql
SELECT name AS fruit_name, inventory AS lowest_quantity
FROM fruits
ORDER BY inventory ASC
LIMIT 1;
```

**Output:**

<img width="730" height="299" alt="image" src="https://github.com/user-attachments/assets/45f0093f-9ebb-45bb-a3ed-2333e42cef9b" />

**Question 6**
---
<img width="749" height="454" alt="image" src="https://github.com/user-attachments/assets/fb7b9bf9-d816-4a74-870d-7f30bf23da1b" />

```sql
SELECT AVG(LENGTH(email)) AS avg_email_length
FROM customer
```

**Output:**

<img width="462" height="302" alt="image" src="https://github.com/user-attachments/assets/32dbe5f8-a782-4458-9c62-a55562262b0f" />

**Question 7**
---
<img width="1026" height="539" alt="image" src="https://github.com/user-attachments/assets/abd2fa4f-85db-4cb2-9646-483669cd7eeb" />

```sql
SELECT MAX(price)-MIN(price) AS price_diff
FROM fruits
```

**Output:**

<img width="577" height="339" alt="image" src="https://github.com/user-attachments/assets/99061384-5429-48a0-bfa6-6b8ea140d509" />

**Question 8**
---
<img width="1199" height="281" alt="image" src="https://github.com/user-attachments/assets/68d3b094-d359-49f6-a64c-7ee70d763a7c" />

```sql
SELECT age, SUM(income) 
FROM employee
GROUP BY age
HAVING SUM(income) > 1000000;
```

**Output:**

<img width="617" height="403" alt="image" src="https://github.com/user-attachments/assets/3c702956-8c4f-445c-b11a-8e7e33cdfa6f" />

**Question 9**
---
<img width="1182" height="542" alt="image" src="https://github.com/user-attachments/assets/20640768-9d7c-44dd-86bd-9d32b80a5082" />

```sql
SELECT occupation, SUM(workhour) 
FROM employee1
GROUP BY occupation
HAVING SUM(workhour) > 20;
```

**Output:**

<img width="705" height="449" alt="image" src="https://github.com/user-attachments/assets/54e1caeb-6a24-49ef-a8bb-07bc107ece79" />

**Question 10**
---
<img width="1229" height="462" alt="image" src="https://github.com/user-attachments/assets/5326e28e-817c-4cf0-a3da-b2ead9d7125e" />

```sql
SELECT (age / 5) * 5 AS age_group, MIN(age)
FROM customer1
GROUP BY age_group
Having MIN(age)<25;
```

**Output:**

<img width="570" height="289" alt="image" src="https://github.com/user-attachments/assets/088159d0-7362-4bd8-bccc-0a7f1fed9a05" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
