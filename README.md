# sql-challenge
## Data_Modeling &amp; Data_Engineering

![Screenshot 2024-06-19 184946.png]([Screenshot 2024-06-19 184946.png](https://github.com/Keemo162/sql-challenge/blob/Module-1/Screenshot%202024-06-19%20184946.png?raw=true))

<img src="https://github.com/Keemo162/sql-challenge/blob/Module-1/Screenshot%202024-06-19%20184946.png?raw=true">

Assisted by my tutor 

```
departments
-
dept_no PK text
dept_name text 


dept_emp
-
emp_no PK int FK >- employees.emp_no
dept_no string FK >- departments.dept_no


dept_manmager
-
emp_no PK int FK >- employees.emp_no
dept_no string FK >- departments.dept_no


employees
-
emp_no PK int
emp_title_id text FK >- titles.title_id
birth_date date
first_name text
last_name text
sex text
hire_date date

salaries
-
emp_no PK int FK >- employees.emp_no
salary int

titles
-
title_id PK text
title text
```
