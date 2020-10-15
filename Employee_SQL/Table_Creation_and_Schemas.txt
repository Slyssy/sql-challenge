CREATE TABLE "titles" (
  "title_id" char(5) PRIMARY KEY,
  "title" varchar(30)
);

CREATE TABLE "employees" (
  "emp_no" INT PRIMARY KEY,
  "emp_title_id" char(5),
  "birth_date" date,
  "first_name" varchar(30),
  "last_name" varchar(30),
  "sex" char(1),
  "hire_date" date
);

CREATE TABLE "dept_emp" (
  "emp_no" INT,
  "dept_no" char(4)
);

CREATE TABLE "dept_manager" (
  "dept_no" char(4),
  "emp_no" INT PRIMARY KEY
);

CREATE TABLE "salaries" (
  "emp_no" INT PRIMARY KEY,
  "salary" INT
);

CREATE TABLE "departments" (
  "dept_no" char(4) PRIMARY KEY,
  "dept_name" varchar(30)
);

ALTER TABLE "dept_manager" ADD FOREIGN KEY ("emp_no") REFERENCES "employees" ("emp_no");

ALTER TABLE "titles" ADD FOREIGN KEY ("title_id") REFERENCES "employees" ("emp_title_id");

ALTER TABLE "dept_emp" ADD FOREIGN KEY ("emp_no") REFERENCES "employees" ("emp_no");

ALTER TABLE "dept_emp" ADD FOREIGN KEY ("dept_no") REFERENCES "departments" ("dept_no");

ALTER TABLE "dept_manager" ADD FOREIGN KEY ("dept_no") REFERENCES "departments" ("dept_no");

ALTER TABLE "salaries" ADD FOREIGN KEY ("emp_no") REFERENCES "dept_manager" ("emp_no");