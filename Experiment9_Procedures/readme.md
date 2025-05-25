# Experiment 9: PL/SQL – Procedures and Functions

## AIM
To understand and implement procedures and functions in PL/SQL for performing various operations such as calculations, decision-making, and looping.

---

## THEORY

PL/SQL (Procedural Language/SQL) extends SQL by adding procedural constructs like variables, conditions, loops, procedures, and functions. Procedures and functions are subprograms that help modularize the code and improve reusability.

### **Procedure**
A PL/SQL **procedure** is a subprogram that performs a specific action. It does not return a value directly but can return values using `OUT` parameters.

**Syntax:**
```sql
CREATE OR REPLACE PROCEDURE procedure_name (parameters)
IS
BEGIN
   -- statements
END;
```

To call the procedure

```sql
EXEC procedure_name(arguments);
```

### **Function**
A PL/SQL **function** is a subprogram that returns a single value using the RETURN keyword.

```sql
CREATE OR REPLACE FUNCTION function_name (parameters)
RETURN datatype
IS
BEGIN
   -- statements
   RETURN value;
END;
```

To call the function:

```sql
SELECT function_name(arguments) FROM DUAL;
```

Key Differences:

-A procedure does not return a value, whereas a function must return a value.
-Functions can be called from SQL queries, procedures cannot (in most cases).

## 1. Write a PL/SQL Procedure to Find the Square of a Number
## PROGRAM:
```
SET SERVEROUTPUT ON;

CREATE OR REPLACE PROCEDURE square_number (
    p_num IN NUMBER
) AS
    v_square NUMBER;
BEGIN
    v_square := p_num * p_num;
    DBMS_OUTPUT.PUT_LINE('The square of ' || p_num || ' is ' || v_square);
END;

BEGIN
    square_number(8);  
END;

```
## OUTPUT:
![image](https://github.com/user-attachments/assets/917d1534-d800-4a5a-a3d6-c54f71e2d6d6)


## 2. Write a PL/SQL Function to Return the Factorial of a Number
## PROGRAM:
```
SET SERVEROUTPUT ON;

-- Function to calculate factorial
CREATE OR REPLACE FUNCTION factorial (p_num IN NUMBER) RETURN NUMBER IS
    v_fact NUMBER := 1;
BEGIN
    IF p_num < 0 THEN
        RAISE_APPLICATION_ERROR(-20001, 'Factorial is not defined for negative numbers');
    ELSIF p_num = 0 OR p_num = 1 THEN
        RETURN 1;
    ELSE
        FOR i IN 2 .. p_num LOOP
            v_fact := v_fact * i;
        END LOOP;
        RETURN v_fact;
    END IF;
END;


-- Anonymous block to call the function and display result
BEGIN
    DBMS_OUTPUT.PUT_LINE('Factorial of 8 is: ' || factorial(8));
END;

```
## OUTPUT:
![image](https://github.com/user-attachments/assets/716d8e3d-966a-402b-82f2-2adf808acb8a)

## 3. Write a PL/SQL Procedure to Check Whether a Number is Even or Odd

## PROGRAM:
```
SET SERVEROUTPUT ON;

CREATE OR REPLACE PROCEDURE check_even_odd (
    p_num IN NUMBER
) AS
BEGIN
    IF MOD(p_num, 2) = 0 THEN
        DBMS_OUTPUT.PUT_LINE(p_num || ' is Even');
    ELSE
        DBMS_OUTPUT.PUT_LINE(p_num || ' is Odd');
    END IF;
END;
/

BEGIN
    check_even_odd(8);  -- Change 8 to any number you want to test
END;
/


```
## OUTPUT:
![image](https://github.com/user-attachments/assets/4f852486-91c9-46e7-a6af-3f091f00bcf4)

## 4. Write a PL/SQL Function to Return the Reverse of a Number

## PROGRAM:
```
CREATE OR REPLACE FUNCTION reverse_number(p_num IN NUMBER) RETURN NUMBER IS
    v_num      NUMBER := p_num;
    v_reverse  NUMBER := 0;
    v_digit    NUMBER;
BEGIN
    WHILE v_num > 0 LOOP
        v_digit := MOD(v_num, 10);
        v_reverse := v_reverse * 10 + v_digit;
        v_num := TRUNC(v_num / 10);
    END LOOP;

    RETURN v_reverse;
END;


SET SERVEROUTPUT ON;

DECLARE
    v_result NUMBER;
BEGIN
    v_result := reverse_number(12345);
    DBMS_OUTPUT.PUT_LINE('Reversed number: ' || v_result);
END;


```
## OUTPUT:
![image](https://github.com/user-attachments/assets/225e29a5-8d6e-4a8b-8377-3139eefd741e)


## 5. Write a PL/SQL Procedure to Display the Multiplication Table of a Number

## PROGRAM:
```
SET SERVEROUTPUT ON;

CREATE OR REPLACE PROCEDURE display_multiplication_table (
    p_num IN NUMBER
) AS
BEGIN
    FOR i IN 1 .. 10 LOOP
        DBMS_OUTPUT.PUT_LINE(p_num || ' x ' || i || ' = ' || (p_num * i));
    END LOOP;
END;
/
BEGIN
    display_multiplication_table(8);  -- Change 8 to any number
END;
/

```
## OUTPUT:
![image](https://github.com/user-attachments/assets/a5ab8e74-cd19-4732-94fc-be5aeeff20be)

## RESULT
Thus, the PL/SQL programs using procedures and functions were written, compiled, and executed successfully.
