
## ASSIGNMENT ON EMP AND MANAGER RELATION:

1. WAQTD SMITHS REPORTING MANAGER'S NAME.
```SQL
SELECT ENAME "MANAGER NAME"
FROM EMP
WHERE EMPNO = (SELECT MGR 
                FROM EMP 
                WHERE ENAME = 'SMITH');

-- OUTPUT
MANAGER NA
----------
FORD
```
---
2. WAQTD ADAMS MANAGER'S MANAGER NAME.
```SQL
SELECT ENAME
FROM EMP 
WHERE EMPNO = (SELECT MGR 
                    FROM EMP 
                    WHERE EMPNO = (SELECT MGR 
                                    FROM EMP 
                                    WHERE ENAME = 'ADAMS'));

-- OUTPUT
ENAME
----------
JONES
```
---
3. WAQTD DNAME OF JONES MANAGER.
```SQL
SELECT DNAME "DEPT NAME"
FROM DEPT
WHERE DEPTNO = (SELECT DEPTNO 
                    FROM EMP 
                    WHERE EMPNO = (SELECT MGR 
                                    FROM EMP 
                                    WHERE ENAME = 'JONES'
                                    )
                );

-- OUTPUT
DEPT NAME
--------------
ACCOUNTING
```
---
4. WAQTD MILLER'S MANAGER'S SALARY.
```SQL
SELECT SAL "MILLER'S MGR'S SAL"
FROM EMP
WHERE EMPNO = (SELECT MGR FROM EMP WHERE ENAME = 'MILLER');

--- OUTPUT
MILLER'S MGR'S SAL
------------------
              2450
```
---
5. WAOTD LOC OF SMITH'S MANAGER'S MANAGER.
```SQL
SELECT LOC "SMITH'S MGR'S LOC"
FROM DEPT
WHERE DEPTNO = (SELECT DEPTNO 
                    FROM EMP 
                    WHERE EMPNO = (SELECT MGR 
                                        FROM EMP 
                                        WHERE ENAME = 'SMITH'
                                    )
                );

-- OUTPUT
SMITH'S MGR'S
-------------
DALLAS
```
---
6. WAQTD NAME OF THE EMPLOYEES REPORTING TO BLAKE.
```SQL
SELECT ENAME NAME
FROM EMP
WHERE MGR = (SELECT EMPNO 
                FROM EMP 
                WHERE ENAME = 'BLAKE');

-- OUTPUT
NAME
----------
ALLEN
WARD
MARTIN
TURNER
JAMES
```
---
7. WAQTD NUMBER OF EMPLPOYEES REPORTING TO KING.
```SQL
SELECT COUNT(*) "NO OF EMPs REPORTING TO KING"
FROM EMP
WHERE MGR = (SELECT EMPNO 
                FROM EMP 
                WHERE ENAME = 'KING');

-- OUTPUT
NO OF EMPs REPORTING TO KING
----------------------------
                           3
```
---
8. WAQTD DETAILS OF THE EMPLOYEES REPORTING TO JONES.
```SQL
SELECT *
FROM EMP
WHERE MGR = (SELECT EMPNO 
                FROM EMP 
                WHERE ENAME = 'JONES');

-- OUTPUT
     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO
---------- ---------- --------- ---------- --------- ---------- ---------- ----------
      7788 SCOTT      ANALYST         7566 19-APR-87       3000                    20
      7902 FORD       ANALYST         7566 03-DEC-81       3000                    20
```
---
9. WAQTD ENAMES OF THE EMPLOYEES REPORTING TO BLAKE'S MANAGER.
```SQL
SELECT ENAME NAME
FROM EMP
WHERE MGR = (SELECT MGR 
                FROM EMP 
                WHERE ENAME = 'BLAKE');

-- OUTPUT
NAME
----------
JONES
BLAKE
CLARK
```
---
10. WAQTD NUMBER OF EMPLOYEES REPORTING TO FORD'S MANAGER.
```SQL
SELECT COUNT(*) "NO OF EMPs REPT TO FORD'S MGR"
FROM EMP
WHERE MGR = (SELECT MGR 
                FROM EMP 
                WHERE ENAME = 'FORD');
    
-- OUTPUT
NO OF EMPs REPT TO FORD'S MGR
-----------------------------
                            2
```
---
