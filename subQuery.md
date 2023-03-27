
MySQL에서 서브쿼리(subquery)란, SELECT, INSERT, UPDATE 또는 DELETE 문 안에 포함된 
또 다른 SELECT 문으로, 하나의 SQL 문 내에서 다른 SQL 문을 포함할 수 있는 기능입니다. 서브쿼리는 외부 쿼리와 연관되어 결과를 생성하는데 사용됩니다.

```
select employee_id , last_name , salary , department_id
from employees e
where salary = (select max(salary) from employees where e.department_id = department_id group by department_id)
order by salary desc;
```
