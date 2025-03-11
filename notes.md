# SQL Commands
SQL in no case sensitive

## SELECT Clause
```SQL
select job from emp;
select distinct job from emp;*
```

*Distinct(not repeated rows)

## WHERE Clause
```SQL
select *
from emp
where job = 'MANAGER'
and sal >= 2850
and sal <= 2950;
```

## Operators
<, >, <=, >=, =, 1=

## WHERE, AND, OR
```SQL
select * from emp
where sal > 900
and job = 'CLERK'
or job = 'SALESMAN';

select ENAME from emp
where sal >= 2000
and job != 'MANAGER'
AND job != 'SALESMAN';

select ENAME, HIREDATE from emp
where DEPTNO = 20 or DEPTNO = 30;

select ENAME, HIREDATE from emp
join dept on emp.deptno = dept.deptno
where loc = 'CHICAGO' or loc = 'DALLAS';
```

## BETWEEN, IN and NULL
```SQL
select ENAME, HIREDATE from emp
where DEPTNO in (20, 30);

select ENAME, HIREDATE from emp
JOIN dept on emp.deptno = dept.deptno
where loc in ('CHICAGO', 'DALLAS');

select * from emp
where sal > 1300
and job not in ('CLERK', 'SALESMAN');

select * from emp
where sal between 1300 and 2000;

select * from emp
where hiredate not between '01/01/1981' and '12/09/1982';

select * from emp
where comm is null;

select * from emp
where comm is not null;

select * from emp
where comm is null
and (sal between 1100 and 5000)
and sal <> 3000;

select * from emp
where comm is null
and (sal > 1100 and sal < 5000)
and sal != 3000;
```

## Operator Precedence
```SQL
select * from emp
where (comm is null or comm = 0)
and (sal > 1100 and sal < 5000)
and sal != 3000;

select * from emp
where job = 'SALESMAN'
and (comm = 300 or comm > 1000);

select * from emp
where job like '%M%'

select * from emp
where 1 = 1
AND (ename like '%K%'
or ename like '%I%')
```

## Ordering Concatenating and Aliasing
```SQL
select ename "Employee Name", sal as Salary, comm Commission
from emp;

select 'Hello, my name is ' || ename as "Concatenated Value"
from emp;

select ename || ' makes $' || sal || ' per month'
as "Concatenated Salary"
from emp;

select ename, sal
from emp
order by ename;

select ename, sal
from emp
order by sal desc;
```

## Single Row Functions (SRF) and The Dual Table
```SQL
select 'my name is ' || ename
from emp;

select concat('my name is ', ename) as Sentence
from emp;

select upper('hello')
from emp;

select upper('hello')
from dual;

select * from dual;

select concat(concat(lower(ename), upper(' is the name')), concat(' and their job is: ', job)) as sentence
from emp
where deptno = 20;
```

## Functions in WHERE clause and other SRF
```SQL
select *
from emp
where lower(job) = 'manager';

select initcap('hello my name is mark') as sentence
from dual;

select length('hello my name is mark') as sentence
from dual;

select length(ename) as sentence
from emp;

select ename, length(ename)
from emp
where length(ename) = 6;

select ename, substr(ename, 3, 1) as substring
from emp;

-- left padding
select lpad(ename, 10, '-')
from emp;

-- left trim
select ltrim('hhhhhello', 'h')
from dual;
```

## Numeric and Date SRF
```SQL
select round(107.1234, 2) from dual;

select trunc(107.9294, 2) from dual;

select sysdate from dual;

select systimestamp from dual;

select add_months('11/17/2012', 10) from dual;

select months_between('12/4/2025', sysdate) from dual;

select trunc(sysdate, 'YEAR') from dual;

select ename, hiredate, trunc(hiredate, 'MONTH')
from EMP
where trunc(hiredate, 'YEAR') = '01/01/1982';
```

## Conversion SRF and Date Formatting
```SQL
select sysdate from dual;
select to_char(sysdate, 'mm-dd-yyyy') from dual;
select to_char(sysdate, 'dd-mm-yyyy') from dual;
select to_char(sysdate, 'ddth "of" month, yyyy') from dual;
select to_char(3456.1, '$99,999.99') from dual;
select ename, to_char(sal, '$99,999') as salaries from emp;
select to_date('2012-08-27', 'yyyy-mm-dd') from dual;
select add_months(to_date('2012-08-27', 'yyyy-mm-dd'), 2) from dual;
select last_day(sysdate) from dual;
select next_day(sysdate, 1) from dual;
```

## NVL and NULL_IF functions
```SQL
select ename, job, sal, nvl(comm, 0)
from emp
where empno in (7839, 7698, 7566, 7654);

select ename, job, sal, NVL(to_char(comm), 'no data found')
from emp
where empno in (7839, 7698, 7566, 7654);

select ename, length(ename), NVL(to_char(nullif(length(ename), 5)), 'length equal to 5')
from emp;
```
