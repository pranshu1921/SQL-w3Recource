-- SQL Joins Exercises w3resource
-- Link: https://www.w3resource.com/sql-exercises/sql-joins-exercises.php

/*1. From the following tables, write a SQL query to find the first name, last name, department number, and department name for each employee. 
*/

select e.first_name, e.last_name, e.department_id, d.department_name
from employees e
join departments d
on e.department_id = d.department_id

/*2. From the following tables, write a SQL query to find the first name, last name, department, city, and state province for each employee.
*/

select e.first_name, e.last_name, d.department_name, l.city, l.state
from departments d
join employees e on d.department_id = e.department_id
join locations l on d.location_id = l.location_id;

/*3.  From the following table, write a SQL query to find the first name, last name, salary, and job grade for all employees.
| EMPLOYEE_ID | FIRST_NAME  | LAST_NAME   | EMAIL    | PHONE_NUMBER       | HIRE_DATE  | JOB_ID     | SALARY   | COMMISSION_PCT | MANAGER_ID | DEPARTMENT_ID |
+-------------+-------------+-------------+----------+--------------------+------------+------------+----------+----------------+------------+---------------+
|         100 | Steven      | King        | SKING    | 515.123.4567       | 2003-06-17 | AD_PRES    | 24000.00 |           0.00 |          0 |            90 |
|         101 | Neena       | Kochhar     | NKOCHHAR | 515.123.4568       | 2005-09-21 | AD_VP      | 17000.00 |           0.00 |        100 |            90 |
|         102 | Lex         | De Haan     | LDEHAAN  | 515.123.4569       | 2001-01-13 | AD_VP      | 17000.00 |           0.00 |        100 |            90 |
|         103 | Alexander   | Hunold      | AHUNOLD  | 590.423.4567       | 2006-01-03 | IT_PROG    |  9000.00 |           0.00 |        102 |            60 |
|         104 | Bruce       | Ernst       | BERNST   | 590.423.4568       | 2007-05-21 | IT_PROG    |  6000.00 |           0.00 |        103 |            60 |


GRADE_LEVEL  LOWEST_SAL HIGHEST_SAL
------------ ---------- -----------
A              1000        2999
B              3000        5999
C              6000        9999
D             10000       14999
E             15000       24999
F             25000       40000

*/

select e.first_name, e.last_name, e.salary, j.grade_level
from employees e
join job_grades j
on e.salary between j.lowest_sal and j.highest_sal;

/*4. From the following tables, write a SQL query to find all those employees who work in department ID 80 or 40. Return first name, last name, department number and department name. 
*/

select e.first_name, e.last_name, d.department_name, e.department_id
from employees e
join departments d
on e.department_id = d.department_id
and e.department_id in (80, 40)
order by e.last_name;

/*5.  From the following tables, write a SQL query to find those employees whose first name contains a letter ‘z’. Return first name, last name, department, city, and state province.*/

select e.first_name, e.last_name, d.department, l.city, l.state_province
from departments d
join employees e on d.department_id = e.department_id
join location l on d.location_id = l.location_id
where e.first_name like '%z%';

/*6. From the following table, write a SQL query to find all departments including those without any employee. Return first name, last name, department ID, department name.*/

select e.first_name, e.last_name, d.department_id, d.department_name
from employees e
right outer join departments d on e.department_id = d.department_id;

/*7. From the following table, write a SQL query to find those employees who earn less than the employee of ID 182. Return first name, last name and salary.*/

select e.first_name, e.last_name, e.salary
from employees e 
where e.salary < (select salary from employees where employee_id  = 182);

select e.first_name, e.last_name, e.salary
from employees e
join employees s
on e.salary < s.salary
and s.employee_id = 182;

/*8. From the following table, write a SQL query to find the employees and their managers. Return the first name of the employee and manager.*/

select e.first_name, m.first_name 
from employees e
join employees m
on e.manager_id = m.employee_id;

/* 9. From the following tables, write a SQL query to display the department name, city, and state province for each department.*/

select d.department_name, l.city, l.state_province
from departments d
join locations l
on d.location_id = l.location_id
group by d.department_name;

/* 10. From the following tables, write a SQL query to find those employees who have or not any department. Return first name, last name, department ID, department name. */

select e.first_name, e.last_name, e.department_id, d.department_name
from employees e
join department d
on e.department_id = d.department_id
where e.department_id is null;

/*11. From the following table, write a SQL query to find the employees and their managers. These managers do not work under any manager. Return the first name of the employee and manager.*/

select e.first_name as 'employee_name', d.first_name as 'manager_name'
from employees e
left outer join employees d
on e.manager_id = d.employee_id;

/*12. From the following tables, write a SQL query to find those employees who work in a department where the employee of last name 'Taylor' works. Return first name, last name and department ID.*/

select e.first_name, e.last_name, e.department_id
from employees e
join employees s
on e.department_id = s.department_id
and s.last_name like '%Taylor';

/*13. From the following tables, write a SQL query to find those employees who joined on 1st January 1993 and leave on or before 31 August 1997. Return job title, department name, employee name, and joining date of the job. */

select jt.job_title, d.department_name, e.first_name ||' '|| e.last_name as employee_name, j.start_date as joining_date
from employees e
join job_history j on e.employee_id = j.employee_id
join jobs jt on jt.job_id = j.job_id
join departments d on d.department_id = e.department_id
where joining_date >= '1993-01-01' and j.end_date <= '1997-08-31';

/*14. From the following tables, write a SQL query to find the difference between maximum salary of the job and salary of the employees. Return job title, employee name, and salary difference.*/

select j.job_title, j.max_salary - e.salary from employees e
join jobs j on e.job_id = j.job_id;

/*15. From the following table, write a SQL query to compute the average salary, number of employees received commission in that department. Return department name, average salary and number of employees. */

select d.department_name, avg(e.salary), count(comission_pct) from employees e
join departments d on e.department_id = d.department_id
group by d.department_name;

/*16. From the following tables, write a SQL query to compute the difference between maximum salary and salary of all the employees who works the department of ID 80. Return job title, employee name and salary difference.*/

select j.job_title, e.first_name || ' ' || w.last_name as employee_name, j.max_salary - e.salary as salary_diff
from employees e
join jobs j on e.job_id = j.job_id
where e.department_id = 80;

/*17. From the following table, write a SQL query to find the name of the country, city, and departments, which are running there.

select c.country_name, l.city, d.department_name from countries c
join locations l on c.country_id = l.country_id
join departments d on l.location_id = d.location_id;


/*18. From the following tables, write a SQL query to find the department name and the full name (first and last name) of the manager. */

select d.department_name, e.first_name || ' ' || e.last_name
from employees e
join departments d on d.manager_id = e.employee_id;

/*19. From the following table, write a SQL query to compute the average salary of employees for each job title. */

select j.job_title, avg(e.salary) as avg_salary
from employees e 
join jobs j on e.job_id = j.job_id
group by j.job_title;

/*20. From the following table, write a SQL query to find those employees who earn $12000 and above. Return employee ID, starting date, end date, job ID and department ID. */

select e.employee_id, j.start_date, j.end_date, e.job_id, e.department_id
from employees e
join job_history j on e.employee_id = j.employee_id
where e.salary >= 12000;

/*21. From the following tables, write a SQL query to find those departments where at least 2 employees work. Group the result set on country name and city. Return country name, city, and number of departments. */

select c.country_name, l.city, count(d.department_id) as number_of_departments
from countries c join locations l on c.country_id = l.country_id
join departments d on l.location_id = d.location_id
where department_id in (select department_id from employees group by department_id
having count(d.department_id) >= 2)
group by country_name, city;

/*22. From the following tables, write a SQL query to find the department name, full name (first and last name) of the manager and their city. */

select d.department_name, e.first_name || ' ' || e.last_name as manager_name, l.city
from employees e join departments d on e.employee_id = d.manager_id
join locations l on d.location_id = l.location_id;

/*23. From the following tables, write a SQL query to compute the number of days worked by employees in a department of ID 80. Return employee ID, job title, number of days worked. */

select jh.employee_id, j.job_title, jh.end_date - jh.start_date as days
from job_history jh 
join jobs j on jh.job_id= j.job_id
where department_id = 80;

/*24. From the following tables, write a SQL query to find full name (first and last name), and salary of those employees who work in any department located in 'London' city. */

select e.first_name || ' ' || e.last_name as employee_name, e.salary 
from employees e
join departments d on e.department_id = d.department_id
join locations l on d.location_id = l.location_id
where l.city = 'London';

/*25. From the following tables, write a SQL query to find full name (first and last name), job title, starting and ending date of last jobs of employees who worked without a commission percentage. */

select e.first_name || ' ' || e.last_name, j.job_title, jh.start_date, jh.end_date
from employees e 
join jobs on e.job_id = j.job_id
join job_history jh on j.job_id = jh.job_id
where e.commission_pct is null;

/*26. From the following tables, write a SQL query to find the department name, department ID, and number of employees in each department. */

select d.departmnent_name, e.department_id, count(*) as num_of_employees
from employees e
join departments d on e.department_id = d.department_id
group by d.department_name;

/*27. From the following tables, write a SQL query to find the full name (first and last name) of the employee with ID and name of the country presently where he/she is working. */

select e.first_name || ' ' || e.last_name as 'employee_name', e.employee_id, c.country_name
from employees e 
join locations l on e.location_id = l.location_id
join countries c on l.country_id = c.country_id;


--------------------
--END
--------------------








