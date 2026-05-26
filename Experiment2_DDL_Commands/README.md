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

<img width="952" height="395" alt="597337637-b607c9d0-44e8-43e7-8930-fd40b28dfe3a" src="https://github.com/user-attachments/assets/6fbe05ac-24e0-4861-9db9-8626ea0cd373" />


```sql
INSERT INTO Products(Name,Category,Price,Stock)VALUES
("Smartphone","Electronics",800,150),
("Headphones","Accessories",200,300);
```

**Output:**

<img width="1192" height="341" alt="597337664-2a546bc7-57f6-4c83-ac82-35ced1d1340d" src="https://github.com/user-attachments/assets/6574d11f-04ad-4dc0-8bd8-22744162c8ad" />


**Question 2**
---

<img width="955" height="450" alt="597337674-6cf5c883-3079-44a0-9cbf-c7023a1c4873" src="https://github.com/user-attachments/assets/f66c4aa7-214a-4745-9668-c7d37cf8b1e6" />

```sql

ALTER TABLE books ADD COLUMN ISBN varchar(30);
ALTER TABLE books ADD COLUMN domain_dep varchar(30);
```

**Output:**

<img width="1192" height="372" alt="597337691-93b87fa7-ce35-42a7-8e5a-c3a12b21ce58" src="https://github.com/user-attachments/assets/6802a1ff-6928-43ec-8932-fe60c799fff2" />


**Question 3**
---

<img width="1006" height="255" alt="597337701-b8666e9c-594c-434e-a81e-7879771dbc8a" src="https://github.com/user-attachments/assets/223f9d78-5ecd-4f92-b6ca-83c74d9fa323" />

```sql
create table Orders
(
OrderID  INTEGER primary key,
OrderDate  DATE  not NULL,
CustomerID  INTEGER  references Customers(CustomerID)
);

```

**Output:**

<img width="1293" height="160" alt="597337747-ded37fee-cedf-4894-99b6-e754286f1c5d" src="https://github.com/user-attachments/assets/7a5ec051-b6be-4ffe-a9d4-e4feeadb59cc" />


**Question 4**
---
<img width="947" height="218" alt="597337758-e8470340-21eb-4788-90ae-af16fbf8bc5f" src="https://github.com/user-attachments/assets/75d508d5-af3d-4c15-b1f6-6e68675677e2" />


```sql
ALTER TABLE employee ADD first_name varchar(50);
ALTER TABLE employee ADD last_name varchar(50);

```

**Output:**

<img width="1152" height="187" alt="597337784-528255a2-8222-49c2-af1f-9e3f5cd9a9eb" src="https://github.com/user-attachments/assets/d3ce9e3f-b2aa-436d-837f-15bfdf878bf9" />


**Question 5**
---
<img width="571" height="246" alt="597337792-0ff6b049-989f-4b5d-a5ef-5911686f1875" src="https://github.com/user-attachments/assets/b691f2c1-85b0-4269-80c3-5a524f9d39f6" />


```sql
INSERT INTO Products(ProductID, ProductName, Price, Stock)
select ProductID, ProductName, Price, Stock FROM Discontinued_products;

```

**Output:**


<img width="851" height="165" alt="597338091-c702839e-d7ab-4aca-97ca-4efa3fee0514" src="https://github.com/user-attachments/assets/28b8ecd3-e91f-4bcb-93ef-f42437692bd3" />


**Question 6**
---


<img width="1047" height="252" alt="597337818-4e26021c-08b6-4992-a5ae-250cb9c06052" src="https://github.com/user-attachments/assets/677ef4da-02c0-427b-b51c-2b18a95f303d" />

```sql

create table Attendance (
AttendanceID INTEGER primary key,
EmployeeID  INTEGER  references Employees(EmployeeID),
AttendanceDate  DATE,
Status  TEXT check(status=='Present' or status=='Absent' or status=='Leave')
);

```

**Output:**


<img width="1302" height="182" alt="597337845-3bfc3e25-2e2c-4d4a-b033-605c9f681bce" src="https://github.com/user-attachments/assets/838296ab-d219-42ab-9df7-650f1f6f8be4" />


**Question 7**
---
<img width="872" height="273" alt="597337854-12be9621-1963-458d-bfa4-836dccf5faf0" src="https://github.com/user-attachments/assets/851ec9c8-4077-475f-8b68-8a47a767ea8e" />


```sql
create table Employees(
EmployeeID INTEGER primary key,
FirstName varchar(30) NOT NULL,
LastName varchar(30) NOT NULL,
Email varchar(30) UNIQUE,
Salary INTEGER CHECK(Salary>0),
DepartmentID  INTEGER references  Departments(DepartmentID)
);

```

**Output:**

<img width="1301" height="258" alt="597337868-cf4cba1a-8141-494c-ac03-057e0524e186" src="https://github.com/user-attachments/assets/b5e32d87-4ba5-4d7f-9b6f-bb45e715755d" />


**Question 8**
---

<img width="807" height="155" alt="597337877-f3df76c0-fe2a-4b1c-a1a3-9945863cdefc" src="https://github.com/user-attachments/assets/d15748c0-348f-46e2-a709-e1432598ab9b" />


```sql
INSERT INTO Student_details(RollNo,Name,Gender,Subject,MARKS)
values(201,"David Lee","M","Physics",92);

```

**Output:**

<img width="1120" height="136" alt="597337891-d93b6767-36cb-4fe9-b787-b165b69e2212" src="https://github.com/user-attachments/assets/d0e2ef89-99cf-44e2-af0b-c8b71ee62a0d" />


**Question 9**
---

<img width="1310" height="167" alt="597337904-9ad08017-6e54-4bdd-b0db-4073b31568ef" src="https://github.com/user-attachments/assets/74f3ae25-3d7d-441e-87ff-b1a2da6946b8" />

```sql
create table jobs(
job_id INTEGER , 
job_title varchar(30) DEFAULT "",
min_salary INTEGER DEFAULT 8000,
max_salary INTEGER DEFAULT NULL
);


```

**Output:**

<img width="1298" height="215" alt="597337925-9240fc38-bc20-4b2f-a9a3-77db4294f1a7" src="https://github.com/user-attachments/assets/e886ec24-8a3a-4597-8a69-deaa5353d0ae" />


**Question 10**
---

<img width="757" height="237" alt="597337937-aa89ddcc-4467-4a3f-87fc-2872ed081776" src="https://github.com/user-attachments/assets/6e121ba9-7949-448e-92e8-442124df96d9" />

```sql
CREATE TABLE Departments
(DepartmentID  INTEGER,
DepartmentName TEXT
);


```

**Output:**

<img width="1197" height="207" alt="597337961-469a4a55-6384-4cfc-89e1-5658bff7ee44" src="https://github.com/user-attachments/assets/c05fa171-146e-4432-9381-2f0fb1f8b181" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.

<img width="1151" height="77" alt="image" src="https://github.com/user-attachments/assets/0dff6481-7b62-4f0a-b760-3fa5db7e7b1b" />
