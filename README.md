
# Employee Analysis

This repository contains SQL queries for analyzing employee data in a company database. The queries provide insights into employee information such as their salaries, departments, and demographics.

## Queries

### List the employee number, last name, first name, sex, and salary of each employee.

```sql
SELECT e.emp_no, e.last_name, e.first_name, e.sex, s.salary
FROM employees e
JOIN salaries s ON e.emp_no = s.emp_no;
This query retrieves the employee number, last name, first name, sex, and salary for each employee by joining the "employees" and "salaries" tables.

List the first name, last name, and hire date for the employees who were hired in 1986.

SELECT first_name, last_name, hire_date
FROM employees
WHERE hire_date >= '1986-01-01' AND hire_date <= '1986-12-31';
This query retrieves the first name, last name, and hire date for employees who were hired in the year 1986 by applying a filter based on the "hire_date" column.

List the manager of each department along with their department number, department name, employee number, last name, and first name.

SELECT d.dept_no, d.dept_name, dm.emp_no, e.last_name, e.first_name
FROM departments d
JOIN dept_manager dm ON d.dept_no = dm.dept_no
JOIN employees e ON dm.emp_no = e.emp_no;
This query retrieves the manager of each department along with their department details and personal information by joining the "departments", "dept_manager", and "employees" tables.

List the department number for each employee along with their employee number, last name, first name, and department name.

SELECT e.emp_no, e.last_name, e.first_name, d.dept_no, d.dept_name
FROM employees e
JOIN dept_emp de ON e.emp_no = de.emp_no
JOIN departments d ON de.dept_no = d.dept_no;
This query retrieves the department number for each employee along with their employee details and the corresponding department name by joining the "employees", "dept_emp", and "departments" tables.

List the first name, last name, and sex of each employee whose first name is Hercules and whose last name begins with the letter B.

SELECT first_name, last_name, sex
FROM employees
WHERE first_name = 'Hercules' AND last_name LIKE 'B%';
This query retrieves the first name, last name, and sex of employees whose first name is "Hercules" and whose last name starts with the letter "B" by applying filters on the corresponding columns.

List each employee in the Sales department, including their employee number, last name, and first name.

SELECT e.emp_no, e.last_name, e.first_name
FROM employees e
JOIN dept_emp de ON e.emp_no = de.emp_no
JOIN departments d ON de.dept_no = d.dept_no
WHERE d.dept_name = 'Sales';
This query retrieves each employee in the Sales department along with their employee number, last name, and first name by joining the "employees", "dept_emp", and "departments" tables and applying a filter on the department name.

List the frequency counts, in descending order, of all the employee last names (i.e., how many employees share each last name).

SELECT last_name, COUNT(*) AS frequency
FROM employees
GROUP BY
