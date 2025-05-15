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
![image](https://github.com/user-attachments/assets/5a95743e-fa02-4845-bbc7-4a6447d71816)


```sql
ALTER TABLE Student_details
ADD COLUMN "mobilenumber" number;
```

**Output:**

![image](https://github.com/user-attachments/assets/61765f05-468b-4bf4-bff8-1bff0b4fe478)

**Question 2**
---
![image](https://github.com/user-attachments/assets/c0a40f92-6b36-4941-8924-1d906bbed58d)


```sql
INSERT INTO Employee(EmployeeID,Name,Position,Department,Salary)
values
(5,"George Clark","Consultant",NULL,NULL),
(7,"Noah Davis","Manager","HR",60000),
(8,"Ava Miller","Consultant","IT",NULL)
;
```

**Output:**

![image](https://github.com/user-attachments/assets/ef4fbef8-708d-42fd-998c-a6f9a2bed81c)


**Question 3**
---
![image](https://github.com/user-attachments/assets/05e9e7dc-2cc9-47ee-ad0c-f061bec7558a)


```sql
CREATE TABLE Department(
DepartmentID INTEGER PRIMARY KEY,
DepartmentName TEXT UNIQUE NOT NULL,
Location  TEXT
);
```

**Output:**

![image](https://github.com/user-attachments/assets/ee7112ca-a8a1-4f97-9e26-d05bad74606f)


**Question 4**
---
![image](https://github.com/user-attachments/assets/70ac9055-2e7a-4175-8b06-965711d062d8)


```sql
CREATE TABLE item(
item_id TEXT PRIMARY KEY,
item_desc TEXT,
rate INTEGER,
icom_id TEXT (4),
   FOREIGN KEY (icom_id) references company(com_id)
   on update  cascade
   on delete cascade
)
```

**Output:**

![image](https://github.com/user-attachments/assets/2c8af5cb-9df5-4608-9180-3fec1bda807a)

**Question 5**
---
![image](https://github.com/user-attachments/assets/281bdb90-d636-4875-b6f8-61137a39236b)


```sql
INSERT INTO Books(ISBN,Title,Author,Publisher,Year)
Values("978-1234567890","Data Science Essentials","Jane Doe","TechBooks",2024);
```

**Output:**

![image](https://github.com/user-attachments/assets/b19312b7-99c4-423e-8596-c9dc6729afa5)


**Question 6**
---
![image](https://github.com/user-attachments/assets/297d28ff-44a5-4714-837e-a6042a1a02bd)

```sql
create table products(
product_id INTEGER PRIMARY KEY,
product_name TEXT NOT NULL,
list_price DECIMAL(10,2) NOT NULL check(list_price>=discount and list_price>=0),
discount DECIMAL(10,2) DEFAULT 0 NOT NULL check(discount>=0)
);
```

**Output:**

![image](https://github.com/user-attachments/assets/f852440a-8e82-432d-adcb-447870a4a951)


**Question 7**
---
![image](https://github.com/user-attachments/assets/3d95093b-1b6d-4658-a5cb-7d5acc157c12)


```sql
ALTER TABLE customer
RENAME COLUMN city to location;
```

**Output:**


**Question 8**
---
![image](https://github.com/user-attachments/assets/2ef46c26-4087-4224-879d-9019e1441763)


```sql
CREATE TABLE Orders(
OrderID INTEGER PRIMARY KEY,
OrderDate DARE NOT NULL,
CustomerID INTEGER,
FOREIGN KEY(CustomerID) references Customers(CustomerID)
);
```

**Output:**

![image](https://github.com/user-attachments/assets/35c16cff-a2fc-4413-912b-4b9ee0752662)


**Question 9**
---
![image](https://github.com/user-attachments/assets/664b96c4-b6a5-49bf-8cf6-7bb83f1d7837)


```sql
select * from Former_employees
union all
select * from Employee
```

**Output:**

![image](https://github.com/user-attachments/assets/440a6001-558e-4999-8b55-b23bb52f70d3)


**Question 10**
---
![image](https://github.com/user-attachments/assets/3a04cc3b-fca6-4503-98c0-23aa2ac65d5d)


```sql
CREATE TABLE Members(
MemberID INTEGER,
MemberName TEXT,
JoinDate DATE
);
```

**Output:**

![image](https://github.com/user-attachments/assets/cf8be135-9a29-4111-979a-9be65a204dcc)



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
