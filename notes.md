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
and sal <= 2950
```
