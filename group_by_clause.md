## ASSIGNMENT ON GROUP BY CLAUSE

1. WAQTD NUMBER OF EMPLOYEES WORKING IN EACH DEPARTMENT EXCLUDING PRESIDENT.
```SQL
SELECT DEPTNO, COUNT(*) "NO OF EMPLOYEES"
FROM EMP
GROUP BY DEPTNO;

-- OUTPUT
    DEPTNO NO OF EMPLOYEES
---------- ---------------
        30               6
        20               5
        10               3
```
---
2. WAQTD TOTAL SALARY NEEDED TO PAY ALL THE EMPLOYEES IN EACH JOB. 
```SQL
SELECT JOB, SUM(SAL) "TOTAL SALARY"
FROM EMP
GROUP BY JOB;

-- OUTPUT
JOB       TOTAL SALARY
--------- ------------
CLERK             4150
SALESMAN          5600
PRESIDENT         5000
MANAGER           8275
ANALYST           6000
```
---
3. WAQTD NUMBER OF EMPLOYEES WORKING AS MANAGER IN EACH DEPARTMENT.
```SQL
SELECT DEPTNO, COUNT(*) "NO OF MANAGERS"
FROM EMP
WHERE JOB = 'MANAGER'
GROUP BY DEPTNO;

-- OUTPUT
    DEPTNO NO OF MANAGERS
---------- --------------
        30              1
        20              1
        10              1
```
---
4. WAQTD AVERAGE SALARY NEEDED TO PAY ALL THE EMPLOYEES IN EACH DEPARTMENT EXCLUDING DEPTNO 20.
```SQL
SELECT DEPTNO, AVG(SAL) "AVERAGE SALARY OF EMPLOYEES"
FROM EMP
WHERE DEPTNO <> 20
GROUP BY DEPTNO;

-- OUTPUT
    DEPTNO AVERAGE SALARY OF EMPLOYEES
---------- ---------------------------
        30                  1566.66667
        10                  2916.66667
```
---
5. WAQTD NUMBER OF EMPLOYEES HAVING CHARACTER 'A' IN THEIR NAMES IN EACH JOB.
```SQL
SELECT JOB, COUNT(*) "NO OF EMPs, 'A' IN NAME"
FROM EMP
WHERE ENAME LIKE '%A%'
GROUP BY JOB;

-- OUTPUT
JOB       NO OF EMPs, 'A' IN NAME
--------- -----------------------
SALESMAN                        3
CLERK                           2
MANAGER                         2
```
---
6. WAQTD NUMBER OF EMPLOYEES AND AVERAGE SALARY NEEDED TO PAY THE EMPLOYEES WHOSE SALARY IS GREATER THAN 2000 IN EACH DEPARTMENT. 
```SQL
SELECT DEPTNO, COUNT(*) "NO OF EMPLOYEES", AVG(SAL) "AVERAGE SALARY"
FROM EMP
WHERE SAL > 2000
GROUP BY DEPTNO;

-- OUTPUT
    DEPTNO NO OF EMPLOYEES AVERAGE SALARY
---------- --------------- --------------
        30               1           2850
        20               3     2991.66667
        10               2           3725
```
---
7. WAQTD TOTAL SALARY NEEDED TO PAY AND NUMBER OF SALESMEN IN EACH DEPARTMENT.
```SQL
SELECT DEPTNO, SUM(SAL) "TOTAL SAL OF ALL SALESMAN", COUNT(*) "NO OF SALESMAN"
FROM EMP
WHERE JOB = 'SALESMAN'
GROUP BY DEPTNO;

-- OUTPUT
    DEPTNO TOTAL SAL OF ALL SALESMAN NO OF SALESMAN
---------- ------------------------- --------------
        30                      5600              4
```
---
8. WAQTD NUMBER OF EMPLOYEES WITH THEIR MAXIMUM SALARIES IN EACH JOB.
```SQL
SELECT JOB, COUNT(*) "NO OF EMPLOYEES", MAX(SAL) "MAXIMUM SAL OF JOB"
FROM EMP
GROUP BY JOB;

-- OUTPUT
JOB       NO OF EMPLOYEES MAXIMUM SAL OF JOB
--------- --------------- ------------------
CLERK                   4               1300
SALESMAN                4               1600
PRESIDENT               1               5000
MANAGER                 3               2975
ANALYST                 2               3000
```
--- 
9. WAQTD MAXIMUM SALARY GIVEN TO AN EMPLOYEE WORKING IN EACH DEPARTMENT.
```SQL
SELECT DEPTNO, MAX(SAL) "MAXIMUM SALARY IN DEPT"
FROM EMP
GROUP BY DEPTNO;

-- OUTPUT
    DEPTNO MAXIMUM SALARY IN DEPT
---------- ----------------------
        30                   2850
        20                   3000
        10                   5000
```
----
10. WAQTD NUMBER OF TIMES EACH SALARY IS PRESENT IN THE EMPLOYEE TABLE.
```SQL
SELECT COUNT(*) "EMPLOYEE'S SALARY COUNT"
FROM EMP
GROUP BY SAL;

-- OUTPUT
EMPLOYEE'S SALARY COUNT
-----------------------
                      1
                      1
                      1
                      2
                      1
                      1
                      1
                      2
                      1
                      1
                      1
                      1

12 rows selected.
```
---