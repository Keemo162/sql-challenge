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

``
CREATE TABLE IF NOT EXISTS public.employees
(
    emp_no integer NOT NULL,
    emp_title_id text COLLATE pg_catalog."default" NOT NULL,
    birth_date date NOT NULL,
    first_name text COLLATE pg_catalog."default" NOT NULL,
    last_name text COLLATE pg_catalog."default" NOT NULL,
    sex text COLLATE pg_catalog."default" NOT NULL,
    hire_date date NOT NULL,
    CONSTRAINT pk_employees PRIMARY KEY (emp_no),
    CONSTRAINT fk_employees_emp_no FOREIGN KEY (emp_no)
        REFERENCES public.salaries (emp_no) MATCH SIMPLE
        ON UPDATE NO ACTION
        ON DELETE NO ACTION,
    CONSTRAINT fk_employees_emp_title_id FOREIGN KEY (emp_title_id)
        REFERENCES public.titles (title_id) MATCH SIMPLE
        ON UPDATE NO ACTION
        ON DELETE NO ACTION
)

TABLESPACE pg_default;

ALTER TABLE IF EXISTS public.employees
    OWNER to postgres;
``

``
CREATE TABLE IF NOT EXISTS public.departments
(
    dept_no text COLLATE pg_catalog."default" NOT NULL,
    dept_name text COLLATE pg_catalog."default" NOT NULL,
    CONSTRAINT pk_departments PRIMARY KEY (dept_no)
)

TABLESPACE pg_default;

ALTER TABLE IF EXISTS public.departments
    OWNER to postgres;
``

``
CREATE TABLE IF NOT EXISTS public.dept_emp
(
    emp_no integer NOT NULL,
    dept_no text COLLATE pg_catalog."default" NOT NULL,
    CONSTRAINT pk_dept_emp PRIMARY KEY (emp_no, dept_no),
    CONSTRAINT fk_dept_emp_dept_no FOREIGN KEY (dept_no)
        REFERENCES public.departments (dept_no) MATCH SIMPLE
        ON UPDATE NO ACTION
        ON DELETE NO ACTION,
    CONSTRAINT fk_dept_emp_emp_no FOREIGN KEY (emp_no)
        REFERENCES public.employees (emp_no) MATCH SIMPLE
        ON UPDATE NO ACTION
        ON DELETE NO ACTION
)

TABLESPACE pg_default;

ALTER TABLE IF EXISTS public.dept_emp
    OWNER to postgres;
``

''
CREATE TABLE IF NOT EXISTS public.dept_manmager
(
    emp_no integer NOT NULL,
    dept_no text COLLATE pg_catalog."default" NOT NULL,
    CONSTRAINT pk_dept_manmager PRIMARY KEY (emp_no),
    CONSTRAINT fk_dept_manmager_dept_no FOREIGN KEY (dept_no)
        REFERENCES public.departments (dept_no) MATCH SIMPLE
        ON UPDATE NO ACTION
        ON DELETE NO ACTION,
    CONSTRAINT fk_dept_manmager_emp_no FOREIGN KEY (emp_no)
        REFERENCES public.employees (emp_no) MATCH SIMPLE
        ON UPDATE NO ACTION
        ON DELETE NO ACTION
)

TABLESPACE pg_default;

ALTER TABLE IF EXISTS public.dept_manmager
    OWNER to postgres;
''

``
CREATE TABLE IF NOT EXISTS public.salaries
(
    emp_no integer NOT NULL,
    salary integer NOT NULL,
    CONSTRAINT pk_salaries PRIMARY KEY (emp_no)
)

TABLESPACE pg_default;

ALTER TABLE IF EXISTS public.salaries
    OWNER to postgres;
``

``
CREATE TABLE IF NOT EXISTS public.titles
(
    title_id text COLLATE pg_catalog."default" NOT NULL,
    title text COLLATE pg_catalog."default" NOT NULL,
    CONSTRAINT pk_titles PRIMARY KEY (title_id)
)

TABLESPACE pg_default;

ALTER TABLE IF EXISTS public.titles
    OWNER to postgres;
``







