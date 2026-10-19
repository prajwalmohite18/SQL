## ASSIGNMENT ON PARTITION BY CLAUSE

1. WAQTD EACH EMPLOYEE'S NAME, THEIR SALARY, THEIR DEPARTMENT NUMBER, AND THE TOTAL SALARY BUDGET OF THEIR ENTIRE DEPARTMENT NEXT TO EVERY ROW.
```SQL
SELECT 
    ENAME NAME, 
    SAL SALARY, 
    DEPTNO,
    SUM(SAL) OVER(PARTITION BY DEPTNO) DEPT_BUDGET
FROM 
    EMP
ORDER BY 
    DEPTNO;

-- OUTPUT
NAME           SALARY     DEPTNO DEPT_BUDGET
---------- ---------- ---------- -----------
CLARK            2450         10        8750
MILLER           1300         10        8750
KING             5000         10        8750
FORD             3000         20       10875
SCOTT            3000         20       10875
JONES            2975         20       10875
SMITH             800         20       10875
ADAMS            1100         20       10875
WARD             1250         30        9400
MARTIN           1250         30        9400
TURNER           1500         30        9400
JAMES             950         30        9400
ALLEN            1600         30        9400
BLAKE            2850         30        9400

14 rows selected.

```
---
2. WAQTD THE EMPLOYEE NAME, HIRE DATE, DEPARTMENT NUMBER, AND THE DATE OF THE EARLIEST HIRED PERSON (OLDEST EMPLOYEE) IN THAT SPECIFIC DEPARTMENT ON EVERY ROW.
```SQL
SELECT 
    ENAME NAME,
    DEPTNO,
    MIN(HIREDATE) OVER(PARTITION BY DEPTNO) "OLDEST EMP_HIREDATE"
FROM 
    EMP;

-- OUTPUT
NAME           DEPTNO OLDEST EM
---------- ---------- ---------
CLARK              10 09-JUN-81
MILLER             10 09-JUN-81
KING               10 09-JUN-81
FORD               20 17-DEC-80
SCOTT              20 17-DEC-80
JONES              20 17-DEC-80
SMITH              20 17-DEC-80
ADAMS              20 17-DEC-80
WARD               30 20-FEB-81
MARTIN             30 20-FEB-81
TURNER             30 20-FEB-81
JAMES              30 20-FEB-81
ALLEN              30 20-FEB-81
BLAKE              30 20-FEB-81

14 rows selected.

```
---
3. WAQTD THE EMPLOYEE NAME, JOB TITLE (JOB), SALARY, AND THE AVERAGE SALARY OF ALL EMPLOYEES SHARING THAT SAME JOB TITLE.
```SQL
SELECT 
    ENAME NAME,
    JOB "JOB TITLE",
    SAL SALARY,
    AVG(SAL) OVER(PARTITION BY JOB) JOB_AVG_SAL
FROM 
    EMP;

-- OUTPUT
NAME       JOB TITLE     SALARY JOB_AVG_SAL
---------- --------- ---------- -----------
FORD       ANALYST         3000        3000
SCOTT      ANALYST         3000        3000
SMITH      CLERK            800      1037.5
JAMES      CLERK            950      1037.5
ADAMS      CLERK           1100      1037.5
MILLER     CLERK           1300      1037.5
BLAKE      MANAGER         2850  2758.33333
JONES      MANAGER         2975  2758.33333
CLARK      MANAGER         2450  2758.33333
KING       PRESIDENT       5000        5000
TURNER     SALESMAN        1500        1400
ALLEN      SALESMAN        1600        1400
WARD       SALESMAN        1250        1400
MARTIN     SALESMAN        1250        1400

14 rows selected.
```

---
4.WAQTD THE EMPLOYEE NAME, DEPARTMENT NUMBER, AND THE TOTAL COUNT OF EMPLOYEES WORKING IN THAT DEPARTMENT NEXT TO EACH NAME.
```SQL
SELECT 
    ENAME NAME,
    DEPTNO,
    COUNT(*) OVER(PARTITION BY DEPTNO) "NO OF EMP IN DEPT"
FROM 
    EMP;

-- OUTPUT
NAME           DEPTNO NO OF EMP IN DEPT
---------- ---------- -----------------
CLARK              10                 3
MILLER             10                 3
KING               10                 3
FORD               20                 5
SCOTT              20                 5
JONES              20                 5
SMITH              20                 5
ADAMS              20                 5
WARD               30                 6
MARTIN             30                 6
TURNER             30                 6
JAMES              30                 6
ALLEN              30                 6
BLAKE              30                 6

14 rows selected.
```
---
5. WAQTD THE EMPLOYEE NAME, DEPARTMENT NUMBER, HIRE DATE, AND A RUNNING COUNT OF EMPLOYEES IN THAT DEPARTMENT, ORDERED CHRONOLOGICALLY FROM THE EARLIEST HIRED TO THE LATEST HIRED.
```SQL
SELECT
    ENAME NAME,
    DEPTNO,
    HIREDATE,
    COUNT(*) OVER(PARTITION BY DEPTNO ORDER BY HIREDATE) RUNNING_EMP_COUNT
FROM 
    EMP;

-- OUTPUT
NAME           DEPTNO HIREDATE  RUNNING_EMP_COUNT
---------- ---------- --------- -----------------
CLARK              10 09-JUN-81                 1
KING               10 17-NOV-81                 2
MILLER             10 23-JAN-82                 3
SMITH              20 17-DEC-80                 1
JONES              20 02-APR-81                 2
FORD               20 03-DEC-81                 3
SCOTT              20 19-APR-87                 4
ADAMS              20 23-MAY-87                 5
ALLEN              30 20-FEB-81                 1
WARD               30 22-FEB-81                 2
BLAKE              30 01-MAY-81                 3
TURNER             30 08-SEP-81                 4
MARTIN             30 28-SEP-81                 5
JAMES              30 03-DEC-81                 6

14 rows selected.
```
---
6. WAQTD THE EMPLOYEE NAME, SALARY, AND A RUNNING TOTAL OF SALARIES ACROSS THE ENTIRE COMPANY (NOT PARTITIONED BY DEPARTMENT), SORTED FROM THE LOWEST SALARY TO THE HIGHEST SALARY.
```SQL
SELECT 
    ENAME NAME,
    SAL SALARY,
    SUM(SAL) OVER(ORDER BY SAL) CUMMULATIVE_SAL
FROM 
    EMP;
ORDER BY 
    SAL;

-- OUTPUT
NAME           DEPTNO        SAL CUMMULATIVE_SAL
---------- ---------- ---------- ---------------
SMITH              20        800             800
JAMES              30        950            1750
ADAMS              20       1100            2850
MARTIN             30       1250            5350
WARD               30       1250            5350
MILLER             10       1300            6650
TURNER             30       1500            8150
ALLEN              30       1600            9750
CLARK              10       2450           12200
BLAKE              30       2850           15050
JONES              20       2975           18025
FORD               20       3000           24025
SCOTT              20       3000           24025
KING               10       5000           29025

14 rows selected.

```
---
7. WAQTD THE EMPLOYEE NAME, DEPARTMENT NUMBER, SALARY, AND THE HIGHEST SALARY SEEN SO FAR WITHIN THEIR DEPARTMENT, SORTING THE ROWS FROM LOWEST SALARY TO HIGHEST SALARY.
```SQL
SELECT  
    ENAME NAME,
    DEPTNO,
    SAL SALARY,
    MAX(SAL) OVER(PARTITION BY DEPTNO) DEPT_MAX_SAL
FROM 
    EMP
ORDER BY
    DEPT_SAL;

-- OUTPUT
NAME           DEPTNO     SALARY DEPT_MAX_SAL
---------- ---------- ---------- ------------
MARTIN             30       1250         2850
WARD               30       1250         2850
ALLEN              30       1600         2850
BLAKE              30       2850         2850
JAMES              30        950         2850
TURNER             30       1500         2850
ADAMS              20       1100         3000
JONES              20       2975         3000
SCOTT              20       3000         3000
FORD               20       3000         3000
SMITH              20        800         3000
MILLER             10       1300         5000
CLARK              10       2450         5000
KING               10       5000         5000

14 rows selected.
```
---
8. WAQTD THE EMPLOYEE NAME, JOB TITLE (JOB), HIRE DATE, AND A RUNNING AVERAGE SALARY WITHIN EACH JOB CATEGORY AS TIME PASSES (ORDERED BY HIRE DATE).
```SQL
SELECT
    ENAME NAME,
    JOB "JOB TITLE",
    HIREDATE,
    AVG(SAL) OVER(PARTITION BY JOB ORDER BY HIREDATE) JOB_CUMMULATIVE_AVG_SAL
FROM 
    EMP
ORDER BY 
    JOB,
    JOB_CUMMULATIVE_AVG_SAL;

-- OUTPUT
NAME       JOB TITLE  HIREDATE  JOB_CUMMULATIVE_AVG_SAL
---------- ---------- --------- -----------------------
FORD       ANALYST    03-DEC-81                    3000
SCOTT      ANALYST    19-APR-87                    3000
SMITH      CLERK      17-DEC-80                     800
JAMES      CLERK      03-DEC-81                     875
MILLER     CLERK      23-JAN-82              1016.66667
ADAMS      CLERK      23-MAY-87                  1037.5
CLARK      MANAGER    09-JUN-81              2758.33333
BLAKE      MANAGER    01-MAY-81                  2912.5
JONES      MANAGER    02-APR-81                    2975
KING       PRESIDENT  17-NOV-81                    5000
MARTIN     SALESMAN   28-SEP-81                    1400
WARD       SALESMAN   22-FEB-81                    1425
TURNER     SALESMAN   08-SEP-81                    1450
ALLEN      SALESMAN   20-FEB-81                    1600

14 rows selected.
```
---
9. WAQTD the employee name, department number, salary, a running total of salaries in that department (ordered by salary), AND the absolute total salary of that department as two separate columns in the same output.
```SQL
SELECT
    ENAME NAME,
    DEPTNO,
    SAL SALARY,
    SUM(SAL) OVER(PARTITION BY DEPTNO ORDER BY SAL) CUMMULATIVE_SALARY,
    SUM(SAL) OVER(PARTITION BY DEPTNO) DEPT_TOTAL_SAL
FROM 
    EMP
ORDER BY 
    DEPTNO, SAL;

-- OUTPUT
NAME           DEPTNO     SALARY CUMMULATIVE_SALARY DEPT_TOTAL_SAL
---------- ---------- ---------- ------------------ --------------
MILLER             10       1300               1300           8750
CLARK              10       2450               3750           8750
KING               10       5000               8750           8750
SMITH              20        800                800          10875
ADAMS              20       1100               1900          10875
JONES              20       2975               4875          10875
SCOTT              20       3000              10875          10875
FORD               20       3000              10875          10875
JAMES              30        950                950           9400
MARTIN             30       1250               3450           9400
WARD               30       1250               3450           9400
TURNER             30       1500               4950           9400
ALLEN              30       1600               6550           9400
BLAKE              30       2850               9400           9400

14 rows selected.

-- OR 
-- To avoid same cummulative salary to duplicate salaries for eg: SCOTT and FORD in DEPTNO 20 and MARTIN and WARD in DEPTNO 30.

-- METHOD 1:
SELECT
    ENAME NAME,
    DEPTNO,
    SAL SALARY,
    SUM(SAL) OVER(PARTITION BY DEPTNO ORDER BY SAL, ENAME) CUMMULATIVE_SALARY,
    SUM(SAL) OVER(PARTITION BY DEPTNO) DEPT_TOTAL_SAL
FROM 
    EMP
ORDER BY 
    DEPTNO, SAL;

-- METHOD 2:
SELECT
    ENAME NAME,
    DEPTNO,
    SAL SALARY,
    SUM(SAL) OVER(PARTITION BY DEPTNO ORDER BY SAL ROWS BETWEEN UNBOUNDED PRECEEDING AND CURRENT ROW) CUMMULATIVE_SALARY,
    SUM(SAL) OVER(PARTITION BY DEPTNO) DEPT_TOTAL_SAL
FROM 
    EMP
ORDER BY 
    DEPTNO, SAL;

-- OUTPUT
NAME           DEPTNO     SALARY CUMMULATIVE_SALARY DEPT_TOTAL_SAL
---------- ---------- ---------- ------------------ --------------
MILLER             10       1300               1300           8750
CLARK              10       2450               3750           8750
KING               10       5000               8750           8750
SMITH              20        800                800          10875
ADAMS              20       1100               1900          10875
JONES              20       2975               4875          10875
FORD               20       3000               7875          10875
SCOTT              20       3000              10875          10875
JAMES              30        950                950           9400
MARTIN             30       1250               2200           9400
WARD               30       1250               3450           9400
TURNER             30       1500               4950           9400
ALLEN              30       1600               6550           9400
BLAKE              30       2850               9400           9400

14 rows selected.
```
---
10. WAQTD the employee name, hire date, department number, the running count of employees hired so far in that department (ordered by hire date), AND the final total count of employees in that department as two separate columns.
```SQL
SELECT 
    ENAME NAME,
    HIREDATE,
    DEPTNO,
    COUNT(*) OVER(PARTITION BY DEPTNO ORDER BY HIREDATE) RUNNING_EMP_COUNT,
    COUNT(*) OVER(PARTITION BY DEPTNO) TOTAL_EMP_IN_DEPT
FROM
    EMP
ORDER BY DEPTNO, HIREDATE;

-- OR (INCASE OF EMPLOYEES ON SAME DAY)
-- #1
SELECT 
    ENAME NAME,
    HIREDATE,
    DEPTNO,
    COUNT(*) OVER(PARTITION BY DEPTNO ORDER BY HIREDATE, EMPNO) RUNNING_EMP_COUNT,
    COUNT(*) OVER(PARTITION BY DEPTNO) TOTAL_EMP_IN_DEPT
FROM
    SCOTT.EMP
ORDER BY DEPTNO, HIREDATE;
-- #2
SELECT 
    ENAME NAME,
    HIREDATE,
    DEPTNO,
    COUNT(*) OVER(PARTITION BY DEPTNO ORDER BY HIREDATE ROWS BETWEEN UNBOUNDED PRECEEDING AND CURRENT ROW) RUNNING_EMP_COUNT,
    COUNT(*) OVER(PARTITION BY DEPTNO) TOTAL_EMP_IN_DEPT
FROM
    SCOTT.EMP
ORDER BY DEPTNO, HIREDATE;

-- OUTPUT
NAME       HIREDATE      DEPTNO RUNNING_EMP_COUNT TOTAL_EMP_IN_DEPT
---------- --------- ---------- ----------------- -----------------
CLARK      09-JUN-81         10                 1                 3
KING       17-NOV-81         10                 2                 3
MILLER     23-JAN-82         10                 3                 3
SMITH      17-DEC-80         20                 1                 5
JONES      02-APR-81         20                 2                 5
FORD       03-DEC-81         20                 3                 5
SCOTT      19-APR-87         20                 4                 5
ADAMS      23-MAY-87         20                 5                 5
ALLEN      20-FEB-81         30                 1                 6
WARD       22-FEB-81         30                 2                 6
BLAKE      01-MAY-81         30                 3                 6
TURNER     08-SEP-81         30                 4                 6
MARTIN     28-SEP-81         30                 5                 6
JAMES      03-DEC-81         30                 6                 6

14 rows selected.
```