# Experiment 8: PL/SQL Cursor Programs

## AIM
To write and execute PL/SQL programs using cursors and exception handling to manage runtime errors effectively and display appropriate messages.

## THEORY

In PL/SQL, cursors are used to handle query result sets row-by-row. 

There are two types of cursors:

- Implicit Cursors: Automatically created by PL/SQL for single-row queries.
- Explicit Cursors: Declared and controlled by the programmer for multi-row queries.

Types of Explicit Cursors:

1. Simple Cursor: Basic cursor to iterate over multiple rows.

2. Parameterized Cursor: Accepts parameters to filter the result dynamically.

3. Cursor FOR Loop: Simplifies cursor operations (open, fetch, close).

4. %ROWTYPE Cursor: Fetches entire row into a record using %ROWTYPE.

5. Cursor with FOR UPDATE: Used for row-level locking and updating the rows while looping.

**Syntax:**
```sql
DECLARE 
   <declarations section> 
BEGIN 
   <executable command(s)>
EXCEPTION 
   <exception handling> 
END;
```

### Basic Components of PL/SQL Block:

- DECLARE: Section to declare variables and constants.
- BEGIN: The execution section that contains PL/SQL statements.
- EXCEPTION: Handles errors or exceptions that occur in the program.
- END: Marks the end of the PL/SQL block.

**Exception Handling**

PL/SQL provides a robust mechanism to handle runtime errors using exception handling blocks. When an error occurs during execution, control is passed to the EXCEPTION section, where specific or general errors can be handled gracefully.

### Components of Exception Handling:
- Predefined Exceptions: Automatically raised by PL/SQL for common errors (e.g., NO_DATA_FOUND, TOO_MANY_ROWS, ZERO_DIVIDE).
- User-defined Exceptions: Declared explicitly in the declaration section using the EXCEPTION keyword.
- WHEN OTHERS: A generic handler for all exceptions not handled explicitly.

```sql
BEGIN
   -- Statements
EXCEPTION
   WHEN exception_name THEN
      -- Handling code
   WHEN OTHERS THEN
      -- Handling for unknown errors
END;
```

### **Question 1: Simple Cursor with Exception Handling**

**Write a PL/SQL program using a simple cursor to fetch employee names and designations from the `employees` table. Implement exception handling for the following cases:**

1. **NO_DATA_FOUND**: When no rows are fetched.
2. **OTHERS**: Any other unexpected errors during execution.

## Program:

```
CREATE TABLE employees (
    emp_id      NUMBER PRIMARY KEY,
    emp_name    VARCHAR2(100),
    designation VARCHAR2(100)
);


BEGIN
    INSERT INTO employees VALUES (1, 'Alice', 'Manager');
    INSERT INTO employees VALUES (2, 'Bob', 'Developer');
    INSERT INTO employees VALUES (3, 'Charlie', 'Analyst');
    COMMIT;
END;



DECLARE
    CURSOR emp_cursor IS
        SELECT emp_name, designation FROM employees;

    v_name        employees.emp_name%TYPE;
    v_designation employees.designation%TYPE;
    v_found       BOOLEAN := FALSE;
BEGIN
    OPEN emp_cursor;
    LOOP
        FETCH emp_cursor INTO v_name, v_designation;
        EXIT WHEN emp_cursor%NOTFOUND;

        v_found := TRUE;

        DBMS_OUTPUT.PUT_LINE('Name: ' || v_name || ', Designation: ' || v_designation);
    END LOOP;
    CLOSE emp_cursor;

    IF NOT v_found THEN
        RAISE NO_DATA_FOUND;
    END IF;

EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('No employee records found.');
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('An unexpected error occurred: ' || SQLERRM);
END;
```
**Output:**  

![image](https://github.com/user-attachments/assets/265b2712-1527-430f-bb4e-5fb0c7ba1ffe)



### **Question 2: Parameterized Cursor with Exception Handling**

**Write a PL/SQL program using a parameterized cursor to retrieve and display employees with a salary in a given range. Implement exception handling for the following errors:**

1. **NO_DATA_FOUND**: When no employees meet the salary criteria.
2. **OTHERS**: For any unexpected errors during the execution.
   
## Program:
```
ALTER TABLE employees ADD (salary NUMBER);

BEGIN
    UPDATE employees SET salary = 80000 WHERE emp_id = 1; -- Alice
    UPDATE employees SET salary = 50000 WHERE emp_id = 2; -- Bob
    UPDATE employees SET salary = 60000 WHERE emp_id = 3; -- Charlie
    COMMIT;
END;


DECLARE
    -- Parameterized cursor
    CURSOR emp_cursor(min_salary NUMBER, max_salary NUMBER) IS
        SELECT emp_name, designation, salary
        FROM employees
        WHERE salary BETWEEN min_salary AND max_salary;

    -- Variables to hold fetched data
    v_name        employees.emp_name%TYPE;
    v_designation employees.designation%TYPE;
    v_salary      employees.salary%TYPE;
    v_found       BOOLEAN := FALSE;

    -- Salary range input
    v_min_salary  NUMBER := 55000;
    v_max_salary  NUMBER := 90000;

BEGIN
    OPEN emp_cursor(v_min_salary, v_max_salary);
    LOOP
        FETCH emp_cursor INTO v_name, v_designation, v_salary;
        EXIT WHEN emp_cursor%NOTFOUND;

        v_found := TRUE;
        DBMS_OUTPUT.PUT_LINE('Name: ' || v_name || ', Designation: ' || v_designation || ', Salary: ' || v_salary);
    END LOOP;
    CLOSE emp_cursor;

    -- Raise NO_DATA_FOUND manually if no employees matched
    IF NOT v_found THEN
        RAISE NO_DATA_FOUND;
    END IF;

EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('No employees found in the given salary range.');
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('An unexpected error occurred: ' || SQLERRM);
END;

```

**Output:**  

![image](https://github.com/user-attachments/assets/3624b7d3-9d10-428b-b362-e56c188861a6)

---

### **Question 3: Cursor FOR Loop with Exception Handling**

**Write a PL/SQL program using a cursor FOR loop to retrieve and display all employee names and their department numbers from the `employees` table. Implement exception handling for the following cases:**

1. **NO_DATA_FOUND**: If no employees are found in the database.
2. **OTHERS**: For any other unexpected errors.

## Program:
```
DECLARE
    v_found BOOLEAN := FALSE;

BEGIN
    -- Cursor FOR loop to iterate through employee records
    FOR emp_rec IN (
        SELECT emp_name, dept_no FROM employees
    ) LOOP
        v_found := TRUE;
        DBMS_OUTPUT.PUT_LINE('Name: ' || emp_rec.emp_name || ', Dept No: ' || emp_rec.dept_no);
    END LOOP;

    -- Check if no records were found and raise NO_DATA_FOUND manually
    IF NOT v_found THEN
        RAISE NO_DATA_FOUND;
    END IF;

EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('No employee records found.');
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('An unexpected error occurred: ' || SQLERRM);
END;
```

**Output:**  

![image](https://github.com/user-attachments/assets/1ce602a4-db1e-4c4b-9353-2bbc4b2084c3)


### **Question 4: Cursor with `%ROWTYPE` and Exception Handling**

**Write a PL/SQL program that uses a cursor with `%ROWTYPE` to fetch and display complete employee records (emp_id, emp_name, designation, salary). Implement exception handling for the following errors:**

1. **NO_DATA_FOUND**: When no employees are found in the database.
2. **OTHERS**: For any other errors that occur.

## Program:
```
DECLARE
    CURSOR emp_cursor IS
        SELECT * FROM employees;

    emp_record employees%ROWTYPE;
    v_found    BOOLEAN := FALSE;

BEGIN
    OPEN emp_cursor;
    LOOP
        FETCH emp_cursor INTO emp_record;
        EXIT WHEN emp_cursor%NOTFOUND;

        v_found := TRUE;
        DBMS_OUTPUT.PUT_LINE('ID: ' || emp_record.emp_id || 
                             ', Name: ' || emp_record.emp_name || 
                             ', Designation: ' || emp_record.designation || 
                             ', Salary: ' || emp_record.salary);
    END LOOP;
    CLOSE emp_cursor;

    IF NOT v_found THEN
        RAISE NO_DATA_FOUND;
    END IF;

EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('No employee records found.');
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('An unexpected error occurred: ' || SQLERRM);
END;
```


**Output:**  
![image](https://github.com/user-attachments/assets/0caec902-cae9-4657-953a-8123620f2ea2)


### **Question 5: Cursor with FOR UPDATE Clause and Exception Handling**

**Write a PL/SQL program using a cursor with the `FOR UPDATE` clause to update the salary of employees in a specific department. Implement exception handling for the following cases:**

1. **NO_DATA_FOUND**: If no rows are affected by the update.
2. **OTHERS**: For any unexpected errors during execution.

## Program:
```
DECLARE
    -- Set the department number for which salaries should be updated
    v_dept_no  NUMBER := 10;

    -- Cursor to select and lock employees from the specified department
    CURSOR emp_cursor IS
        SELECT emp_id, salary
        FROM employees
        WHERE dept_no = v_dept_no
        FOR UPDATE;

    v_emp_id  employees.emp_id%TYPE;
    v_salary  employees.salary%TYPE;
    v_count   NUMBER := 0;

BEGIN
    OPEN emp_cursor;

    LOOP
        FETCH emp_cursor INTO v_emp_id, v_salary;
        EXIT WHEN emp_cursor%NOTFOUND;

        -- Increase salary by 10%
        UPDATE employees
        SET salary = v_salary * 1.1
        WHERE emp_id = v_emp_id;

        v_count := v_count + 1;
    END LOOP;

    CLOSE emp_cursor;

    -- If no records were updated, raise NO_DATA_FOUND
    IF v_count = 0 THEN
        RAISE NO_DATA_FOUND;
    END IF;

    COMMIT;

    DBMS_OUTPUT.PUT_LINE(v_count || ' employee(s) salary updated successfully in department ' || v_dept_no);

EXCEPTION
    WHEN NO_DATA_FOUND THEN
        DBMS_OUTPUT.PUT_LINE('No employees found in department ' || v_dept_no || '.');

    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('Unexpected error: ' || SQLERRM);
        ROLLBACK;
END;
```

**Output:**  
![image](https://github.com/user-attachments/assets/231d67e3-43ed-4728-a917-6735c40514ba)


## RESULT
Thus, the program successfully executed and displayed employee details using a cursor. 

