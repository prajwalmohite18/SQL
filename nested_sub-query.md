## ASSIGNMENT ON NESTED SUBOUERY:

1. WAQTD 2ND MINIMUM SALARY.
```SQL
SELECT MAX(SAL) 
FROM EMP 
WHERE SAL < (SELECT MAX(SAL) FROM EMP);

-- OUTPUT
2ND MAX SALARY
--------------
          3000
```
---
2. WAQTD 5TH MAXIMUM SALARY.
```SQL
SELECT MAX(SAL) "5TH MAX SALARY"
FROM EMP
WHERE SAL < (SELECT MAX(SAL) 
                FROM EMP 
                WHERE SAL < (SELECT MAX(SAL) 
                                FROM EMP    
                                WHERE SAL < (SELECT MAX(SAL) 
                                                FROM EMP 
                                                WHERE SAL < (SELECT MAX(SAL)
                                                                FROM EMP
                                                            )
                                            )
                            )
            )

-- OUTPUT
5TH MAX SALARY
-----------
       2450
```
---
3. WAQTD NAME OF THE EMPLOYEE EARNING 3RD MAXIMUM SALARY.
```SQL
SELECT ENAME NAME
FROM EMP
WHERE SAL < (SELECT MAX(SAL) 
                FROM EMP 
                WHERE SAL < (SELECT MAX(SAL) 
                                FROM EMP 
                                WHERE SAL <(SELECT MAX(SAL) 
                                                FROM EMP 
                                            )
                            ) 
            )

-- OUTPUT
NAME
----------
JONES
```
---
4. WAQTD EMPNO OF THE EMPLOYEE EARNING 2ND MAXIMUM SALARY.
```SQL
SELECT EMPNO "EMPLOYEE NO"
FROM EMP 
WHERE SAL = (SELECT MAX(SAL) 
                FROM EMP 
                WHERE SAL < (SELECT MAX(SAL) 
                                FROM EMP
                            )
            );

-- OUTPUT
EMPLOYEE NO
-----------
       7788
       7902
```
---
5. WAQTD DEPARTMENT NAME OF AN EMPLOYEE GETTING 4TH MAX SAL.
```SQL
SELECT DNAME "DEPT NAME"
FROM DEPT
WHERE DEPTNO IN (SELECT DEPTNO 
                    FROM EMP 
                    WHERE SAL = (SELECT MAX(SAL) 
                                    FROM EMP WHERE SAL < (SELECT MAX(SAL) 
                                                            FROM EMP WHERE SAL < (SELECT MAX(SAL) 
                                                                                    FROM EMP WHERE SAL <(SELECT MAX(SAL) 
                                                                                                            FROM EMP
                                                                                                            )
                                                                                    )
                                                            )
                                    )
                    );

-- OUTPUT
DEPT NAME
--------------
SALES
```
---
6. WAQTD DETAILS OF THE EMPLOYEE WHO WAS HIRED 2ND.
```SQL
SELECT *
FROM EMP 
WHERE HIREDATE = (SELECT MIN(HIREDATE) 
                    FROM EMP WHERE HIREDATE > (SELECT MIN(HIREDATE) FROM EMP)
                    );

-- OUTPUT
     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO
---------- ---------- --------- ---------- --------- ---------- ---------- ----------
      7499 ALLEN      SALESMAN        7698 20-FEB-81       1600        300         30
```
---
7. WAQTD NAME OF THE EMPLOYEE HIRED BEFORE THE LAST EMPLOYEE.
```SQL
SELECT ENAME
FROM EMP
WHERE HIREDATE = (SELECT MAX(HIREDATE) 
                    FROM EMP 
                    WHERE HIREDATE < (SELECT MAX(HIREDATE) FROM EMP)
                    );

-- OUTPUT
ENAME
----------
SCOTT
```
---
8. WAQTD LOC OF THE EMPLOYEE WHO WAS HIRED FIRST.
```SQL
SELECT LOC "WORK PLACE"
FROM DEPT
WHERE DEPTNO = (SELECT DEPTNO 
                    FROM EMP 
                    WHERE HIREDATE = (SELECT MIN(HIREDATE) FROM EMP)
                );

-- OUTPUT
WORK PLACE
-------------
DALLAS
```
---
9. WAQTD DETAILS OF THE EMPLOYEE EARNING 7TH MINIMUM SALARY.
```SQL
SELECT *
FROM EMP
WHERE SAL = (SELECT MIN(SAL) 
                FROM EMP 
                WHERE SAL > (SELECT MIN(SAL) 
                                FROM EMP 
                                WHERE SAL > (SELECT MIN(SAL) 
                                                FROM EMP 
                                                WHERE SAL > (SELECT MIN(SAL) 
                                                                FROM EMP WHERE SAL > (SELECT MIN(SAL) 
                                                                                        FROM EMP 
                                                                                        WHERE SAL > (SELECT MIN(SAL) 
                                                                                                        FROM EMP 
                                                                                                        WHERE SAL > (SELECT MIN(SAL) FROM EMP)
                                                                                                    )
                                                                                      )
                                                                )
                                            )
                                )
                );

-- OUTPUT
     EMPNO ENAME      JOB              MGR HIREDATE         SAL       COMM     DEPTNO
---------- ---------- --------- ---------- --------- ---------- ---------- ----------
      7499 ALLEN      SALESMAN        7698 20-FEB-81       1600        300         30
```
---
10. WAQTD DNAME OF EMPLOYEE GETTING 2ND MAXIMUM SALARY.
```SQL
SELECT DNAME "DEPT NAME"
FROM DEPT
WHERE DEPTNO IN (SELECT DEPTNO  
                FROM EMP 
                WHERE SAL = (SELECT MAX(SAL) 
                                FROM EMP 
                                WHERE SAL < (SELECT MAX(SAL) FROM EMP)
                            )
                );

--  OUTPUT
DEPT NAME
--------------
RESEARCH
```
---
