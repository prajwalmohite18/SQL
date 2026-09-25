
## ASSIGNMENT ON SUB-QUERY TYPES

1. WAQTD NAME OF THE EMPLOYEES EARNING SALARY MORE THAN THE ALL SALESMAN.
```SQL
SELECT ENAME NAME
FROM EMP
WHERE SAL > ALL(SELECT SAL 
                    FROM EMP 
                    WHERE JOB = 'SALESMAN');

-- OUTPUT
NAME
----------
CLARK
BLAKE
JONES
SCOTT
FORD
KING

6 rows selected.
```
--- 
2. WAQTD DETAILS OF THE EMPLOYEES HIRED AFTER ALL THE CLERKS.
```SQL
SELECT * 
FROM EMP
WHERE HIREDATE > ALL(SELECT HIREDATE 
                        FROM EMP 
                        WHERE JOB = 'CLERK');

-- OUTPUT
no rows selected
```
--- 
3. WAQTD NAME AND SALARY FOR ALL THE EMPLOYEES IF THEY ARE EARNING LESS THAN ATLEST A MANAGER.
```SQL
SELECT ENAME NAME, SAL SALARY
FROM EMP 
WHERE SAL < ANY(SELECT SAL 
                    FROM EMP 
                    WHERE JOB = 'MANAGER');

-- OUTPUT
NAME           SALARY
---------- ----------
SMITH             800
JAMES             950
ADAMS            1100
WARD             1250
MARTIN           1250
MILLER           1300
TURNER           1500
ALLEN            1600
CLARK            2450
BLAKE            2850

10 rows selected.
```
---
4. WAQTD NAME AND HIREDATE OF EMPLOYEES HIRED BEFORE ALL THE MANAGERS.
```SQL
SELECT ENAME NAME, HIREDATE 
FROM EMP
WHERE HIREDATE > ALL(SELECT HIREDATE 
                        FROM EMP
                        WHERE JOB = 'MANAGER');

-- OUTPUT
NAME       HIREDATE
---------- ---------
TURNER     08-SEP-81
MARTIN     28-SEP-81
KING       17-NOV-81
JAMES      03-DEC-81
FORD       03-DEC-81
MILLER     23-JAN-82
SCOTT      19-APR-87
ADAMS      23-MAY-87

8 rows selected.
```
---
5. WAQTD NAMES OF THE EMPLOYEES HIRED AFTER ALL THE MANAGERS AND EARNING SALARY MORE THAN ALL THE CLERKS.
```SQL
SELECT ENAME NAME
FROM EMP
WHERE HIREDATE > ALL(SELECT HIREDATE 
                        FROM EMP
                        WHERE JOB = 'MANAGER')
AND SAL > ALL(SELECT SAL 
                FROM EMP W
                HERE JOB = 'CLERK');

-- OUTPUT
NAME
----------
TURNER
KING
FORD
SCOTT
```
---
6. WAQTD DETAILS OF THE EMPLOYEES WORKING AS CLERK AND HIRED BEFORE ATLEST A SALESMAN.
```SQL
SELECT *
FROM EMP 
WHERE JOB = 'CLERK'
AND HIREDATE < ANY(SELECT HIREDATE 
                        FROM EMP 
                        WHERE JOB = 'SALESMAN');

-- OUTPUT
     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO
---------- ---------- --------- ---------- --------- ---------- ---------- ----------
      7369 SMITH      CLERK           7902 17-DEC-80        800                    20
```
---
7. WAQTD DETAILS OF EMPLOYEES WORKING IN ACCOUNTING OR SALES DEPT
```SQL
SELECT *
FROM EMP
WHERE DEPTNO IN (SELECT DEPTNO 
                    FROM DEPT
                    WHERE DNAME IN ('ACCOUNTING', 'SALES')  
                    );
    
-- OUTPUT
     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO
---------- ---------- --------- ---------- --------- ---------- ---------- ----------
      7499 ALLEN      SALESMAN        7698 20-FEB-81       1600        300         30
      7521 WARD       SALESMAN        7698 22-FEB-81       1250        500         30
      7654 MARTIN     SALESMAN        7698 28-SEP-81       1250       1400         30
      7698 BLAKE      MANAGER         7839 01-MAY-81       2850                    30
      7782 CLARK      MANAGER         7839 09-JUN-81       2450                    10
      7839 KING       PRESIDENT            17-NOV-81       5000                    10
      7844 TURNER     SALESMAN        7698 08-SEP-81       1500          0         30
      7900 JAMES      CLERK           7698 03-DEC-81        950                    30
      7934 MILLER     CLERK           7782 23-JAN-82       1300                    10

9 rows selected.
```
---
8. WAQTD DEPARTMENT NAMES OF THE EMPOYEES WITH NAME SMITH. KING AND MILLER.
```SQL
SELECT DNAME "DEPT NAME"
FROM DEPT
WHERE DEPTNO IN (SELECT DEPTNO
                    FROM EMP 
                    WHERE ENAME IN ('SMITH','KING', 'MILLER'));

-- OUTPUT
DEPT NAME
--------------
RESEARCH
ACCOUNTING
```
---
9. WAQTD DETAILS OF EMPLOYEES WORKING IN NEW YORK OR CHICAGO
```SQL
SELECT * 
FROM EMP 
WHERE DEPTNO IN (SELECT DEPTNO 
                        FROM DEPT 
                        WHERE LOC IN ('NEW YORK', 'CHICAGO'));

-- OUTPUT
     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO
---------- ---------- --------- ---------- --------- ---------- ---------- ----------
      7499 ALLEN      SALESMAN        7698 20-FEB-81       1600        300         30
      7521 WARD       SALESMAN        7698 22-FEB-81       1250        500         30
      7654 MARTIN     SALESMAN        7698 28-SEP-81       1250       1400         30
      7698 BLAKE      MANAGER         7839 01-MAY-81       2850                    30
      7782 CLARK      MANAGER         7839 09-JUN-81       2450                    10
      7839 KING       PRESIDENT            17-NOV-81       5000                    10
      7844 TURNER     SALESMAN        7698 08-SEP-81       1500          0         30
      7900 JAMES      CLERK           7698 03-DEC-81        950                    30
      7934 MILLER     CLERK           7782 23-JAN-82       1300                    10

9 rows selected.
```
---
10. WAQTD EMP NAMES IF EMPLOYE EMPLOYEES ARE HIRED AFTER ALL THE EMPLOYEES OF DEPT 10.
```SQL
SELECT ENAME NAME
FROM EMP
WHERE HIREDATE > ALL (SELECT HIREDATE FROM EMP WHERE DEPTNO = 10);

-- OUTPUT
NAME
----------
SCOTT
ADAMS
```
---

