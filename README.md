<!DOCTYPE html>
<html>
<head>
  <title>Employee Analysis</title>
</head>
<body>
  <h1>Employee Analysis</h1>
  <p>This repository contains SQL queries for analyzing employee data in a company database. The queries provide insights into employee information such as their salaries, departments, and demographics.</p>
  <h2>Queries</h2>
  <h3>List the employee number, last name, first name, sex, and salary of each employee.</h3>
  <pre>
    <code>SELECT e.emp_no, e.last_name, e.first_name, e.sex, s.salary
FROM employees e
JOIN salaries s ON e.emp_no = s.emp_no;</code>
  </pre>
  <p>This query retrieves the employee number, last name, first name, sex, and salary for each employee by joining the "employees" and "salaries" tables.</p>
  <h3>List the first name, last name, and hire date for the employees who were hired in 1986.</h3>
  <pre>
    <code>SELECT first_name, last_name, hire_date
FROM employees
WHERE hire_date >= '1986-01-01' AND hire_date <= '1986-12-31';</code>
  </pre>
  <p>This query retrieves the first name, last name, and hire date for employees who were hired in the year 1986 by applying a filter based on the "hire_date" column.</p>
  <h3>List the manager of each department along with their department number, department name, employee number, last name, and first name.</h3>
  <pre>
    <code>SELECT d.dept_no, d.dept_name, dm.emp_no, e.last_name, e.first_name
FROM departments d
JOIN dept_manager dm ON d.dept_no = dm.dept_no
JOIN employees e ON dm.emp_no = e.emp_no;</code>
  </pre>
  <p>This query retrieves the manager of each department along with their department details and personal information by joining the "departments", "dept_manager", and "employees" tables.</p>
  <h3>List the department number for each employee along with their employee number, last name, first name, and department name.</h3>
  <pre>
    <code>SELECT e.emp_no, e.last_name, e.first_name, d.dept_no, d.dept_name
FROM employees e
JOIN dept_emp de ON e.emp_no = de.emp_no
JOIN departments d ON de.dept_no = d.dept_no;</code>
  </pre>
  <p>This query retrieves the department number for each employee along with their employee details and the corresponding department name by joining the "employees", "dept_emp", and "departments" tables.</p>
  <h3>List the first name, last name, and sex of each employee whose first name is Hercules and whose last name begins with the letter B.</h3>
  <pre>
    <code>SELECT first_name, last_name, sex
FROM employees
WHERE first_name = 'Hercules' AND last_name LIKE 'B%';</code>
  </pre>
  <p>This query retrieves the first name, last name, and sex of employees whose first name is "Hercules" and whose last name starts with the letter "B" by applying filters on the corresponding columns.</p>
  <h3>List each employee in the Sales department, including their employee number, last name, and first name.</h3>
  <pre>
    <code>SELECT e.emp_no, e.last_name, e.first_name
FROM employees e
JOIN dept_emp de ON e.emp_no = de.emp_no
JOIN departments d ON de.dept_no = d.dept_no
WHERE d.dept_name = 'Sales';</code>
  </pre>
  <p>This query retrieves each employee in the Sales department along with their employee number, last name, and first name by joining the "employees", "dept_emp", and "departments" tables and applying a filter on the department name.</p>
  <h3>List the frequency counts, in descending order, of all the employee last names (i.e., how many employees share each last name).</h3>
  <pre>
    <code>SELECT last_name, COUNT(*) AS frequency
FROM employees
GROUP BY last_name
ORDER BY frequency DESC;</code>
  </pre>
  <p>This query retrieves the frequency counts, in descending order, of all the employee last names by grouping the records based on the last_name column and applying the COUNT(*) function.</p>
  <h2>License</h2>
  <p>This project is licensed under the MIT License.</p>
  <p>Feel free to customize the README file further based on your specific needs, such as adding a p</p>
</body>
</html>
