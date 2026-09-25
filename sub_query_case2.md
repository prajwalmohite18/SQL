## ASSIGNMENT ON SUB-QUERY CASE 2

1. WAQTD DNAME OF THE EMPLOYEES WHOSE NAME IS SMITH.
```SQL
SELECT DNAME "DEPARTMENT NAME"
FROM DEPT
WHERE DEPTNO = (SELECT DEPTNO 
                    FROM EMP 
                    WHERE ENAME = 'SMITH');

-- OUTPUT
DEPARTMENT NAM
--------------
RESEARCH
```
---
2. WAQTD DNAME AND LOC OF THE EMPLOYEE WHOSE ENAME IS KING.
```SQL
SELECT DNAME "DEPT NAME", LOC "WORK PLACE"
FROM DEPT
WHERE DEPTNO = (SELECT DEPTNO 
                    FROM EMP 
                    WHERE ENAME = 'KING');

-- OUTPUT
DEPT NAME      WORK PLACE
-------------- -------------
ACCOUNTING     NEW YORK
```
---
3. WAQTD LOC OF THE EMP WHOSE EMPLOYEE NUMBER IS 7902.
```SQL
SELECT LOC "WORK PLACE"
FROM DEPT
WHERE DEPTNO = (SELECT DEPTNO 
                    FROM EMP 
                    WHERE EMPNO = 7902);
```

-- OUTPUT
WORK PLACE
-------------
DALLAS
---
4. WAQTD DNAME AND LOC ALONG WITH DEPTNO OF THE EMPLOYEE WHOSE NAME ENDS WITH 'R'.
```SQL
SELECT DNAME "DEPT NAME", LOC "WORK PLACE", DEPTNO 
FROM DEPT
WHERE DEPTNO IN (SELECT DEPTNO 
                    FROM EMP 
                    WHERE ENAME LIKE '%R');
            
--- OUTPUT
DEPT NAME      WORK PLACE        DEPTNO
-------------- ------------- ----------
ACCOUNTING     NEW YORK              10
SALES          CHICAGO               30
```
---
5. WAQTD DNAME OF THE EMPLOYEE WHOSE DESIGNATION IS PRESIDENT.
```SQL
SELECT DNAME "DEPT NAME" 
FROM DEPT
WHERE DEPTNO IN (SELECT DEPTNO
                    FROM EMP
                    WHERE JOB = 'PRESIDENT');
        
-- OUTPUT
DEPT NAME
--------------
ACCOUNTING
```
---
6. WAQTD NAMES OF THE EMPLOYEES WORKING IN ACCOUNTING DEPARTMENT.
```SQL
SELECT ENAME NAME
FROM EMP
WHERE DEPTNO IN (SELECT DEPTNO 
                    FROM DEPT
                    WHERE DNAME = 'ACCOUNTING');
    
-- OUTPUT
NAME
----------
CLARK
KING
MILLER
```
---
7. WAQTD ENAME AND SALARIES OF THE EMPLOYEES WHO ARE WORKING IN THE LOCATION 'CHICAGO'.
```SQL
SELECT ENAME NAME, SAL SALARY
FROM EMP
WHERE DEPTNO IN (SELECT DEPTNO 
                    FROM DEPT
                    WHERE LOC = 'CHICAGO');

-- OUTPUT
NAME           SALARY
---------- ----------
ALLEN            1600
WARD             1250
MARTIN           1250
BLAKE            2850
TURNER           1500
JAMES             950

6 rows selected.
```
---
8. WAQTD DETAILS OF THE EMPLOYEES WORKING IN SALES.
```SQL
SELECT *
FROM EMP
WHERE DEPTNO IN (SELECT DEPTNO
                    FROM DEPT
                    WHERE DNAME = 'SALES');

-- OUTPUT
     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO
---------- ---------- --------- ---------- --------- ---------- ---------- ----------
      7499 ALLEN      SALESMAN        7698 20-FEB-81       1600        300         30
      7521 WARD       SALESMAN        7698 22-FEB-81       1250        500         30
      7654 MARTIN     SALESMAN        7698 28-SEP-81       1250       1400         30
      7698 BLAKE      MANAGER         7839 01-MAY-81       2850                    30
      7844 TURNER     SALESMAN        7698 08-SEP-81       1500          0         30
      7900 JAMES      CLERK           7698 03-DEC-81        950                    30

6 rows selected.
```
---
9. WAQTD DETAILS OF THE EMP ALONG WITH ANNUAL SALARY IF EMPLOYEES ARE WORKING IN NEW YORK.
```SQL
SELECT EMP.*, (SAL*12) "ANNUAL SALARY"
FROM EMP
WHERE DEPTNO IN (SELECT DEPTNO
                    FROM DEPT
                    WHERE LOC = 'NEW YORK');

-- OUTPUT
     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO ANNUAL SALARY
---------- ---------- --------- ---------- --------- ---------- ---------- ---------- -------------
      7782 CLARK      MANAGER         7839 09-JUN-81       2450                    10         29400
      7839 KING       PRESIDENT            17-NOV-81       5000                    10         60000
      7934 MILLER     CLERK           7782 23-JAN-82       1300                    10         15600
```
---
10. WAQTD NAMES OF EMPLOYEES WORKING IN OPERATIONS DEPARTMENT.
```SQL
SELECT ENAME NAME
FROM EMP
WHERE DEPTNO IN (SELECT DEPTNO 
                    FROM DEPT 
                    WHERE DNAME = 'OPERATIONS');

-- OUTPUT
no rows selected
```
---