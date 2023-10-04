# EX-05 Creating Cursors using PL/SQL

### AIM:
To create a cursor using PL/SQL.

### Steps:
1. Create employee table with following attributes (empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);
2. Create a cursor named as employee_cursor
3. Using cursor read each record and display the result
4. Close the cursor

### Program:
#### Create employee table
```sql
CREATE TABLE employeee(empid NUMBER,empname VARCHAR2(10),dept VARCHAR2(10),salary NUMBER);
INSERT INTO employeee (empid, empname, dept, salary) VALUES (1, 'John', 'HR', 50000);
INSERT INTO employeee (empid, empname, dept, salary) VALUES (2, 'Joe', 'IT', 65000);
INSERT INTO employeee (empid, empname, dept, salary) VALUES (3, 'Bob', 'Finance', 55000);
```
#### PLSQL Cursor code
```sql
SET SERVEROUTPUT ON
DECLARE
    CURSOR employee_cursor IS
        SELECT empid, empname, dept, salary
        FROM employee;
    empid NUMBER;
    empname VARCHAR2(90);
    dept VARCHAR2(90);
    salary NUMBER;
BEGIN
    OPEN employee_cursor;
    LOOP
        FETCH employee_cursor INTO empid, empname, dept, salary;
        EXIT WHEN employee_cursor%NOTFOUND;
        DBMS_OUTPUT.PUT_LINE('Employee ID: ' || empid);
        DBMS_OUTPUT.PUT_LINE('Employee Name: ' || empname);
        DBMS_OUTPUT.PUT_LINE('Department: ' || dept);
        DBMS_OUTPUT.PUT_LINE('Salary: ' || salary);
        DBMS_OUTPUT.PUT_LINE('------------------------');
    END LOOP;
    CLOSE employee_cursor;
END;
/
```
### Output:
![271705907-d128b2d0-f16f-4c4e-92d0-1630d0e2f0b8](https://github.com/Janarthanan2/Ex-no-6-Creating-Cursors-using-PL-SQL/assets/119393515/975b03ef-b339-42b8-a209-9eb0674814e8)

### Result:
Hence a cursor using PL/SQL is created successfully.
