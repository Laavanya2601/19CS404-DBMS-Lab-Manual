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

<img width="1017" height="533" alt="597339240-648a1be1-d713-4348-9f2f-e5a2fbe48c6a" src="https://github.com/user-attachments/assets/eb0f81e2-caf0-4ead-a8e7-20c45519db46" />

```sql

select DoctorID, count(*) as "TotalRecords" 
from MedicalRecords
group by DoctorID;

```

**Output:**

<img width="577" height="666" alt="597339255-17dc1691-80cf-4a7c-a6e9-e7af7a080e39" src="https://github.com/user-attachments/assets/01edc41f-c4a0-426f-b902-05b09e583985" />



**Question 2**
---


<img width="617" height="607" alt="597339261-54ae4332-ab23-40b5-8daa-8538474d5499" src="https://github.com/user-attachments/assets/d1a5f5ba-6c29-4ba4-917d-bdb4dc6696d2" />

```sql

select strftime("%H",AppointmentDateTime) as HourOfDay,count(*) as "TotalAppointments"
from Appointments
group by HourOfDay
order by HourOfDay;

```

**Output:**



<img width="672" height="571" alt="597339275-026eaff2-44d5-48a1-9327-c0240b231ed1" src="https://github.com/user-attachments/assets/e63f17c7-b017-4c63-a780-ef264050a4a7" />

**Question 3**
---


<img width="968" height="618" alt="597339289-4b113828-68a2-4911-a2a8-ae0195d36702" src="https://github.com/user-attachments/assets/c3eaa8e0-7219-4430-896d-c1d69a5b29f2" />

```sql

select Medication,AVG(Dosage) as AvgDosage from Prescriptions 
group by Medication; 

```

**Output:**

<img width="607" height="788" alt="597339305-a48b8072-1513-4e46-8769-2f964055809a" src="https://github.com/user-attachments/assets/c521fb66-c4a7-4d57-93f1-45526d298595" />



**Question 4**
---


<img width="920" height="453" alt="597339312-523a9881-e8dc-4df2-8936-c52c53af3082" src="https://github.com/user-attachments/assets/11ba6cd9-066f-4ea1-af77-c4b5799f3b00" />

```sql

select sum(purch_amt) as "TOTAL" from orders;
```

**Output:**

<img width="332" height="345" alt="597339329-fcbb5ea8-5b13-410a-befe-052895e1d8e2" src="https://github.com/user-attachments/assets/94d2ae40-030a-42f5-b582-86c3ecbf3966" />

**Question 5**
---

<img width="982" height="506" alt="597339334-b70d4f13-d35e-4745-8c29-e06074a6c5e1" src="https://github.com/user-attachments/assets/5acf3e0a-6025-4cbb-8004-0ad891a5ba5a" />


```sql

select count(customer_id) as COUNT from customer
where grade is not null;

```

**Output:**

<img width="327" height="340" alt="597339349-cf245417-5b7f-40ea-bf95-00d2fa4030cb" src="https://github.com/user-attachments/assets/e14ced85-4fde-4205-9341-9b4ac39bf39f" />

**Question 6**
---

<img width="852" height="450" alt="597339354-aec620d1-46e3-4d19-adf0-f10396edca9e" src="https://github.com/user-attachments/assets/166a89e7-3ffd-4f02-a694-4d1a0dbdb6d8" />


```sql

select AVG(income) as "avg_income" from employee
WHERE name like "A%";

```

**Output:**

<img width="336" height="345" alt="597339380-3232dcca-e0c3-4106-be3a-4f01ac05a14b" src="https://github.com/user-attachments/assets/05c7e7b6-516e-4db6-a8fa-2a44c100af72" />

**Question 7**
---

<img width="697" height="532" alt="597339390-15741407-c222-4821-8ca5-ffb96fb2ec5e" src="https://github.com/user-attachments/assets/7075c40a-7eab-458e-8c6b-395a0e581052" />

```sql

select name  as "fruit_name", inventory as "lowest_quantity" from fruits
order by inventory asc
limit 1;

```

**Output:**

<img width="648" height="345" alt="597339408-10a3a02a-97f0-413a-a1f4-c8375fe6adad" src="https://github.com/user-attachments/assets/30c1c08d-f973-43a5-8913-ae0e21d2268c" />

**Question 8**
---

<img width="1230" height="502" alt="597339413-66a7bd80-a5c0-4d80-a48e-d7682b5670a3" src="https://github.com/user-attachments/assets/861cb6cb-7f06-447e-bf88-bb1c9a09d814" />

```sql

SELECT age,MIN(income) AS "MIN(income)"
FROM employee
group by age 
having MIN(income)<400000;

```

**Output:**

<img width="560" height="418" alt="597339428-ac5db882-857b-4b0e-b5ed-5ffa3b6015c0" src="https://github.com/user-attachments/assets/eaf86f32-5724-42d6-a2e8-0f0128942250" />

**Question 9**
---

<img width="1208" height="513" alt="597339433-2c67479d-2d6e-4f03-b12e-4e750b986a72" src="https://github.com/user-attachments/assets/12c9cc7a-d338-44f7-bf1f-2c96253a210d" />

```sql

SELECT occupation,AVG(workhour) AS "AVG(workhour)"
FROM employee1
GROUP BY occupation
HAVING AVG(workhour) BETWEEN 10 AND 12;

```

**Output:**


<img width="617" height="366" alt="597339458-446ed824-1d6c-4ab4-b0bc-109963785143" src="https://github.com/user-attachments/assets/1bbb492b-1b8d-45fc-96c4-a965c6ed675e" />


**Question 10**
---

<img width="1170" height="553" alt="597339478-08b35c7a-93a1-47a9-88cf-101d1b451cc1" src="https://github.com/user-attachments/assets/4e4865d9-d404-4728-9f27-e0d30eac3bc7" />

```sql

select occupation,SUM(workhour) as "SUM(workhour)"
from employee1
group by occupation 
having SUM(workhour)>20;

```

**Output:**



<img width="607" height="493" alt="597339502-5f48d76a-b5fa-4533-ae2c-b9ed29dba0d9" src="https://github.com/user-attachments/assets/bcab8abc-5bed-467f-ad02-e7315fe8394e" />


## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.

<img width="1178" height="116" alt="image" src="https://github.com/user-attachments/assets/dec28dd7-b685-451e-8567-66797f2ab782" />

