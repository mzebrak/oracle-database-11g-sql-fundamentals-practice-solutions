## Practice 1

This practice covers the following topics:

> 1. Selecting all data from different tables
> 2. Describing the structure of tables
> 3. Performing arithmetic calculations and specifying column names

***

### Part 1

1. The following `SELECT` statement executes successfully:
   ```sql
   SELECT last_name,
          job_id,
          salary AS Sal
   FROM employees;
   ```
   **Answer:** True


2. The following `SELECT` statement executes successfully:
   ```sql
   SELECT * 
   FROM job_grades;
   ```
   **Answer:** True


3. There are four coding errors in this statement. Can you identify them?
   ```sql
    SELECT employee_id,
           last_name
           sal x 12 ANNUAL SALARY
    FROM employees;
   ```
   > 1. there is no column 'sal' in the employees table
   > 2. 'x' cannot be used as multiplication operator, use '*' instead
   > 3. if column alias contains spaces you must put it in quotation marks
   > 4. a comma is missing after the last_name column

### Part 2

4. Your first task is to determine the ***DEPARTMENTS*** structure of the table and its contents.
   ```sql
   DESCRIBE departments;
   SELECT *
   FROM departments;
   ```

5. You need to determine the structure of the ***EMPLOYEES*** table.
   ```sql
   DESCRIBE employees;
   ```

6. Test your query in the `lab_01_05.sql` file to ensure that it runs correctly.
   ```sql
   SELECT employee_id,
          last_name,
          job_id,
          hire_date startdate
   FROM employees;
   ```

7. The HR department wants a query to display all unique job IDs from the ***EMPLOYEES*** table.
   ```sql
   SELECT DISTINCT job_id
   FROM employees;   
   ```

8. The HR department wants more descriptive column headings for its report on employees. Copy the statement from `
   lab_01_05.sql` to a new SQL Worksheet. Name the column headings ***Emp#***, ***Employee***, ***Job*** and ***Hire
   Date*** respectively. Then run your query again.
   ```sql
   SELECT employee_id "Emp #",
          last_name   "Employee",
          job_id      "Job",
          hire_date   "Hire Date"
   FROM employees;
   ```

9. The HR department has requested a report of all employees and their job IDs. Display the last name concatenated with
   the job ID (separated by a comma and space) and name the column ***Employee and Title***.
   ```sql
   SELECT last_name ||
          ', ' || job_id "Employee and Title"
   FROM employees;
   ```

10. To familiarize yourself with the data in the ***EMPLOYEES*** table, create a query to display all the data from
    the ***EMPLOYEES*** table. Separate each column output with a comma. Name the column as ***THE_OUTPUT***.
    ```sql
    SELECT employee_id ||
           ',' ||
           first_name ||
           ',' ||
           last_name ||
           ',' ||
           email ||
           ',' ||
           phone_number ||
           ',' ||
           job_id ||
           ',' ||
           manager_id ||
           ',' ||
           hire_date ||
           ',' ||
           commission_pct ||
           ',' ||
           department_id the_output
    FROM employees;
    ```

## Practice 2

This practice covers the following topics:
> 1. Selecting data and changing the order of the rows that are displayed
> 2. Restricting rows by using the `WHERE` clause
> 3. Sorting rows by using the `ORDER BY` clause
> 4. Using substitution variables to add flexibility to your SQL `SELECT` statements

***

1. Because of budget issues, the HR department needs a report that displays the last name and salary of employees who
   earn more than $12,000. Save your SQL statement as a file named
   `lab_02_01.sql`. Run your query.
   ```sql
   SELECT last_name,
          salary
   FROM employees
   WHERE salary > 12000;
   ```


2. Open a new SQL Worksheet. Create a report that displays the last name and department number for employee number 176.
   Run the query.
   ```sql
   SELECT last_name,
          department_id
   FROM employees
   WHERE employee_id = 176;
   ```

3. The HR department needs to find high-salary and low-salary employees. Modify `lab_02_01.sql` to display the last name
   and salary for any employee whose salary is not in the range of $5,000 to $12,000. Save your SQL statement
   as `lab_02_03.sql`.
   ```sql
   SELECT last_name, 
          salary
   FROM employees
   WHERE salary NOT BETWEEN 5000 AND 12000;
   ```

4. Create a report to display the last name, job ID, and hire date for employees with the last names of Matos and
   Taylor. Order the query in ascending order by the hire date.
   ```sql
   SELECT last_name,
          job_id,
          hire_date
   FROM employees
   WHERE last_name IN ('Matos', 'Taylor')
   ORDER BY hire_date;
   ```

5. Display the last name and department ID of all employees in departments 20 or 50 in ascending alphabetical order by
   name.
   ```sql
   SELECT last_name,
          department_id
   FROM employees
   WHERE department_id IN (20, 50)
   ORDER BY last_name;
   ```

6. Modify `lab_02_03.sql` to display the last name and salary of employees who earn between $5,000 and $12,000, and are
   in department 20 or 50. Label the columns ***Employee*** and
   ***Monthly Salary***, respectively. Resave `lab_02_03.sql` as `lab_02_06.sql`. Run the statement in `
   lab_02_06.sql`
   ```sql
   SELECT last_name "Employee",
          salary    "Monthly Salary"
   FROM employees
   WHERE salary BETWEEN 5000 AND 12000
   AND department_id IN (20, 50)
   ORDER BY last_name;
   ```

7. The HR department needs a report that displays the last name and hire date for all employees who were hired in 1994.
   ```sql
   SELECT last_name,
          hire_date
   FROM employees
   WHERE hire_date LIKE '94%';
   ```

8. Create a report to display the last name and job title of all employees who do not have a manager.
   ```sql
   SELECT last_name,
          job_id
   FROM employees
   WHERE manager_id IS NULL;
   ```

9. Create a report to display the last name, salary, and commission of all employees who earn commissions. Sort data in
   descending order of salary and commissions. Use the column's numeric position in the `ORDER BY` clause.
   ```sql
   SELECT last_name,
          salary,
          commission_pct
   FROM employees
   WHERE commission_pct IS NOT NULL
   ORDER BY 2 DESC, 3 DESC;
   ```

10. Members of the HR department want to have more flexibility with the queries that you are writing. They would like a
    report that displays the last name and salary of employees who earn more than an amount that the user specifies
    after a prompt. Save this query to a file named `lab_02_10.sql`. If you enter ***12000*** when prompted, the report
    displays the following results:
    ```sql
    SELECT last_name,
           salary
    FROM employees
    WHERE salary > &salary;
    ```

11. The HR department wants to run reports based on a manager. Create a query that prompts the user for a manager ID and
    generates the employee ID, last name, salary, and department for that manager's employees. The HR department wants
    the ability to sort the report on a selected column. You can test the data with the following values:
    ```sql
    SELECT employee_id,
           last_name,
           salary,
           department_id
    FROM employees
    WHERE manager_id = &manager_id
    ORDER BY &order_col;
    ```

12. Display all employee last names in which the third letter of the name is "a".
    ```sql
    SELECT last_name
    FROM employees
    WHERE last_name LIKE '__a%';
    ```

13. Display the last names of all employees who have both an "a" and an "e" in their last name.
    ```sql
    SELECT last_name
    FROM employees
    WHERE last_name LIKE '%a%'
      AND last_name LIKE '%e%';
    ```

14. Display the last name, job, and salary for all employees whose jobs are either those of a sales representative or of
    a stock clerk, and whose salaries are not equal to $2,500, $3,500, or $7,000.
    ```sql
    SELECT last_name,
           job_id,
           salary
    FROM employees
    WHERE job_id IN ('SA_REP', 'ST_CLERK')
      AND salary NOT IN (2500, 3500, 7000);
    ```

15. Modify  `lab_02_06.sql` to display the last name, salary, and commission for all employees whose commission is 20%.
    Resave `lab_02_06.sql` as `lab_02_15.sql`. Rerun the statement in `lab_02_15.sql`.
    ```sql
    SELECT last_name "Employee",
           salary    "Monthly Salary",
           commission_pct
    FROM employees
    WHERE commission_pct = .2;
    ```

### Practice 3

This practice covers the following topics:
> 1. Writing a query that displays the current date
> 2. Creating queries that require the use of numeric, character, and date functions
> 3. Performing calculations of years and months of service for an employee

***

1. Write a query to display the system date. Label the column as ***Date***.
    ```sql
    SELECT sysdate "Date"
    FROM dual;
    ```

2. The HR department needs a report to display the employee number, last name, salary, and salary increased by 15.5% (
   expressed as a whole number) for each employee. Label the column ***New Salary***. Save your SQL statement in a file
   named `lab_03_02.sql`.
    ```sql
    SELECT employee_id,
           last_name,
           salary,
           round (salary * 1.155) "New Salary"
    FROM employees;
    ```

3. Run your query in the file `lab_03_02.sql`.
   > ***AS ABOVE***

4. Modify your query `lab_03_02.sql` to add a column that subtracts the old salary from the new salary. Label the
   column ***Increase***. Save the contents of the file as `lab_03_04.sql`. Run the revised query.
    ```sql
    SELECT employee_id,
           last_name,
           salary,
           round (salary * 1.155)          "New Salary",
           round (salary * 1.155) - salary "Increase"
    FROM employees;
    ```

5. Write a query that displays the last name (with the first letter in uppercase and all the other letters in lowercase)
   and the length of the last name for all employees whose name starts with the letters J, A, or M. Give each column an
   appropriate label. Sort the results by the employees last names.
    ```sql
    SELECT initcap (last_name) "Name",
           length (last_name)  "Length"
    FROM employees
    WHERE last_name LIKE 'J%'
    OR last_name LIKE 'A%'
    OR last_name LIKE 'M%'
    ORDER BY last_name;
    ```

   Rewrite the query so that the user is prompted to enter a letter that starts the last name. For example, if the user
   enters (capitalized) when prompted for a letter, then the output should show all employees whose last name starts
   with the letter H.
   ```sql
    SELECT initcap (last_name) "Name",
           length (last_name)  "Length"
    FROM employees
    WHERE last_name LIKE '&letter%'
    ORDER BY last_name;
    ```

   Modify the query such that the case of the entered letter does not affect the output. The entered letter must be
   capitalized before being processed by the query.
   ```sql
    SELECT initcap (last_name) "Name",
           length (last_name)  "Length"
    FROM employees
    WHERE last_name LIKE upper ('&letter%')
    ORDER BY last_name;
    ```

6. The HR department wants to find the duration of employment for each employee. For each employee, display the last
   name and calculate the number of months between today and the date on which the employee was hired. Label the column
   as ***MONTHS_WORKED***. Order your results by the number of months employed. Round the number of months up to the
   closest whole number.
    ```sql
    SELECT last_name,
           round (months_between (sysdate, hire_date)) months_worked
    FROM employees
    ORDER BY months_worked;
    ```

7. Create a query to display the last name and salary for all employees. Format the salary to be 15 characters long,
   left-padded with the $ symbol. Label the column as ***SALARY***.
    ```sql
    SELECT last_name,
           lpad (salary, 15, '$') salary
    FROM employees;
    ```

8. Create a query that displays the first eight characters of the employees last names and indicates the amounts of
   their salaries with asterisks. Each asterisk signifies a thousand dollars. Sort the data in descending order of
   salary. Label the column ***EMPLOYEES_AND_THEIR_SALARIES***
    ```sql
    SELECT substr (last_name, 1, 8) ||
           rpad (' ', round (salary / 1000) + 1, '*') employees_and_their_salaries
    FROM employees
    ORDER BY salary DESC;
    ```

9. Create a query to display the last name and the number of weeks employed for all employees in department 90. Label
   the number of weeks column as ***TENURE***. Truncate the number of weeks value to 0 decimal places. Show the records
   in descending order of the employees tenure.
   ```sql
   SELECT last_name,
          trunc ( (sysdate - hire_date) / 7) tenure
   FROM employees
   WHERE department_id = 90
   ORDER BY tenure DESC;
    ```

### Practice 4

This practice covers the following topics:
> 1. Creating queries that use `TO_CHAR`, `TO_DATE`, and other `DATE` functions
> 2. Creating queries that use conditional expressions such as `DECODE` and `CASE`

***

1. Create a report that produces the following for each employee:
   ***<employee last name\> earns <salary> monthly but wants <3 times salary\>***. Label the column ***Dream Salaries***
   .
   ```sql
   SELECT last_name ||
          ' earns $' ||
          to_char (salary, 'FM99,999.00') ||
          ' monthly but wants $' ||
          to_char (salary * 3, 'FM99,999.00') "Dream Salaries"
   FROM employees;
    ```

2. Display each employees last name, hire date, and salary review date, which is the first Monday after six months of
   service. Label the column ***REVIEW***. Format the dates to appear in the format similar to Monday, the Thirty-First
   of July, 2000.
   ```sql
   SELECT last_name,
          hire_date,
          to_char (next_day (add_months (hire_date, 6), 1), 'FMDAY, "the" DDSPTH "of" MONTH, YYYY') review
   FROM employees;
    ```

3. Display the last name, hire date, and day of the week on which the employee started. Label the column ***DAY***.
   Order the results by the day of the week, starting with Monday.
   ```sql
   SELECT last_name,
          hire_date,
          to_char (hire_date, 'FMDAY') day
   FROM employees
   ORDER BY to_char (hire_date, 'D');
    ```

4. Create a query that displays the employees last names and commission amounts. If an employee does not earn
   commission, show No Commission. Label the column ***COMM***.
   ```sql
   SELECT last_name,
          nvl (to_char (commission_pct), 'No Commission') comm
   FROM employees;
    ```

5. Using the `DECODE` function, write a query that displays the grade of all employees based on the value of the
   column ***JOB_ID***, using the following data:
   ```sql
   SELECT job_id,
          decode (job_id,
                 'AD_PRES',  'A',
                 'ST_MAN',   'B',
                 'IT_PROG',  'C',
                 'SA_REP',   'D',
                 'ST_CLERL', 'E', 0) grade
   FROM employees;
    ```

6. Rewrite the statement in the preceding exercise using the `CASE` syntax.
   ```sql
   SELECT job_id,
          CASE job_id
              WHEN 'AD_PRES'  THEN 'A'
              WHEN 'ST_MAN'   THEN 'B'
              WHEN 'IT_PROG'  THEN 'C'
              WHEN 'SA_REP'   THEN 'D'
              WHEN 'ST_CLERK' THEN 'E'
              ELSE '0'
          END grade
   FROM employees;
    ```

### Practice 5

This practice covers the following topics:
> 1. Writing queries that use the group functions
> 2. Grouping by rows to achieve more than one result
> 3. Restricting groups by using the `HAVING` clause

***

1. Group functions work across many rows to produce one result per group.

   **Answer:** True


2. Group functions include nulls in calculations.

   **Answer:** False


3. The `WHERE` clause restricts rows before inclusion in a group calculation.

   **Answer:** True


4. Find the highest, lowest, sum, and average salary of all employees. Label the columns as ***Maximum***, ***Minimum***
   , ***Sum***, and ***Average***, respectively. Round your results to the nearest whole number. Save your SQL statement
   as `lab_05_04.sql`. Run the query.
   ```sql
   SELECT round (MAX (salary)) "Maximum",
          round (MIN (salary)) "Minimum",
          round (SUM (salary)) "Sum",
          round (AVG (salary)) "Average"
   FROM employees;
   ```

5. Modify the query in `lab_05_04.sql` to display the minimum, maximum, sum, and average salary for each job type.
   Resave `lab_05_04.sql` as `lab_05_05.sql`. Run the statement in `lab_05_05.sql`.
   ```sql
   SELECT job_id,
          round (MAX (salary)) "Maximum",
          round (MIN (salary)) "Minimum",
          round (SUM (salary)) "Sum",
          round (AVG (salary)) "Average"
   FROM employees
   GROUP BY job_id;
   ```

6. Write a query to display the number of people with the same job.
   ```sql
   SELECT job_id,
          COUNT (*)
   FROM employees
   GROUP BY job_id;
   ```
   Generalize the query so that the user in the HR department is prompted for a job title. Save the script to a file
   named `lab_05_06.sql`. Run the query. Enter ***IT_PROG*** when prompted.
   ```sql
   SELECT job_id,
          COUNT (*)
   FROM employees
   WHERE job_id = upper ('&job_id')
   GROUP BY job_id;
   ```
7. Determine the number of managers without listing them. Label the column as ***Number of Managers***. Hint: Use
   the ***MANAGER_ID*** column to determine the number of managers.
   ```sql
   SELECT COUNT (DISTINCT manager_id) "Number of Managers"
   FROM employees;
   ```

8. Find the difference between the highest and lowest salaries. Label the column ***DIFFERENCE***.
   ```sql
   SELECT MAX (salary) - MIN (salary) difference
   FROM employees;
   ```

9. Create a report to display the manager number and the salary of the lowest-paid employee for that manager. Exclude
   anyone whose manager is not known. Exclude any groups where the minimum salary is $6,000 or less. Sort the output in
   descending order of salary.
   ```sql
   SELECT manager_id,
          MIN (salary)
   FROM employees
   WHERE manager_id IS NOT NULL
   GROUP BY manager_id
   HAVING MIN (salary) > 6000
   ORDER BY MIN (salary) DESC;
   ```

10. Create a query to display the total number of employees and, of that total, the number of employees hired in 1995,
    1996, 1997, and 1998. Create appropriate column headings.
   ```sql
   SELECT COUNT (*)                                               total,
          COUNT (decode (to_char (hire_date, 'YYYY'), 1995, '1')) "1995",
          COUNT (decode (to_char (hire_date, 'YYYY'), 1996, '1')) "1996",
          COUNT (decode (to_char (hire_date, 'YYYY'), 1997, '1')) "1997",
          COUNT (decode (to_char (hire_date, 'YYYY'), 1999, '1')) "1999"
   FROM employees;
   ```

11. Create a matrix query to display the job, the salary for that job based on department number, and the total salary
    for that job, for departments 20, 50, 80, and 90, giving each column an appropriate heading.
   ```sql
   SELECT DISTINCT (job_id)                                 "Job",
                   SUM (decode (department_id, 20, salary)) "Dept 20",
                   SUM (decode (department_id, 50, salary)) "Dept 50",
                   SUM (decode (department_id, 80, salary)) "Dept 80",
                   SUM (decode (department_id, 90, salary)) "Dept 90",
                   SUM (salary)                             total
   FROM employees
   GROUP BY job_id;
   ```

### Practice 6

This practice covers the following topics:
> 1. Joining tables using an equijoin
> 2. Performing outer and self-joins
> 3. Adding conditions

***

1. Write a query for the HR department to produce the addresses of all the departments. Use the ***LOCATIONS*** and
   ***COUNTRIES*** tables. Show the location ID, street address, city, state or province, and country in the output. Use
   a ***NATURAL JOIN*** to produce the results.
   ```sql
   SELECT location_id,
          street_address,
          city,
          state_province,
          country_name
   FROM locations
   NATURAL JOIN countries;
   ```

2. The HR department needs a report of all employees. Write a query to display the last name, department number, and
   department name for all the employees.
   ```sql
   SELECT last_name,
          department_id,
          department_name
   FROM employees
   JOIN departments USING (department_id);
   ```

3. The HR department needs a report of employees in Toronto. Display the last name, job, department number, and the
   department name for all employees who work in Toronto.
   ```sql
   SELECT last_name,
          job_id,
          department_id,
          department_name
   FROM employees
   JOIN departments USING (department_id)
   JOIN locations USING (location_id)
   WHERE city = 'Toronto';
   ```

4. Create a report to display employees last name and employee number along with their managers last name and manager
   number. Label the columns ***Employee***, ***Emp#***, ***Manager***, and ***Mgr#***, respectively. Save your SQL
   statement as `lab_06_04.sql`. Run the query.
   ```sql
   SELECT e.last_name   "Employee",
          e.employee_id "Emp#",
          m.last_name   "Manager",
          m.employee_id "Mgr#"
   FROM employees e
   JOIN employees m ON (e.manager_id = m.employee_id)
   ORDER BY e.employee_id;
   ```

5. Modify `lab_06_04.sql` to display all employees including King, who has no manager. Order the results by the employee
   number. Save your SQL statement as `lab_06_05.sql`. Run the query in `lab_06_05.sql`.
   ```sql
   SELECT e.last_name   "Employee",
          e.employee_id "Emp#",
          m.last_name   "Manager",
          m.employee_id "Mgr#"
   FROM employees e
   LEFT JOIN employees m ON (e.manager_id = m.employee_id)
   ORDER BY e.employee_id;
   ```

6. Create a report for the HR department that displays employee last names, department numbers, and all the employees
   who work in the same department as a given employee. Give each column an appropriate label. Save the script to a file
   named `lab_06_06.sql`.
   ```sql
   SELECT e.department_id department,
          e.last_name     employee,
          c.last_name     colleague
   FROM employees e
   JOIN employees c ON (e.department_id = c.department_id)
   WHERE e.employee_id <> c.employee_id
   ORDER BY department,
            employee,
            colleague;
   ```

7. The HR department needs a report on job grades and salaries. To familiarize yourself with the ***JOB_GRADES***
   table, first show the structure of the ***JOB_GRADES*** table. Then create a query that displays the name, job,
   department name, salary, and grade for all employees.
   ```sql
   SELECT last_name,
          job_id,
          department_name,
          salary,
          grade_level
   FROM employees
   JOIN departments USING (department_id)
   JOIN job_grades ON (salary BETWEEN lowest_sal AND highest_sal)
   ORDER BY salary;
   ```

8. The HR department wants to determine the names of all the employees who were hired after Davies. Create a query to
   display the name and hire date of any employee hired after employee Davies.
   ```sql
   SELECT e.last_name,
          to_char (e.hire_date, 'DD-MON-YY') hire_date
   FROM employees e
   JOIN employees davies ON (davies.last_name = 'Davies')
   WHERE davies.hire_date < e.hire_date;
   ```

9. The HR department needs to find the names and hire dates of all the employees who were hired before their managers,
   along with their managers names and hire dates. Save the script to a file named `lab_06_09.sql`.
   ```sql
   SELECT e.last_name,
          to_char (e.hire_date, 'DD-MON-YY') hire_date,
          m.last_name,
          to_char (m.hire_date, 'DD-MON-YY') hire_date1
   FROM employees e
   JOIN employees m ON (e.manager_id = m.employee_id)
   WHERE e.hire_date < m.hire_date;
   ```

### Practice 7

This practice covers the following topics:
> 1. Creating subqueries to query values based on unknown criteria
> 2. Using subqueries to find out the values that exist in one set of data and not in another

***

1. The HR department needs a query that prompts the user for an employee last name. The query then displays the last
   name and hire date of any employee in the same department as the employee whose name they supply (excluding that
   employee). For example, if the user enters ***Zlotkey***, find all employees who work with Zlotkey (excluding
   Zlotkey).
   ```sql
   SELECT last_name,
          to_char (hire_date, 'DD-MON-YY') hire_date
   FROM employees
   WHERE department_id = (
            SELECT department_id
            FROM employees
            WHERE last_name = initcap ('&&last_name')
      )
         AND last_name <> initcap ('&last_name');
   ```

2. Create a report that displays the employee number, last name, and salary of all employees who earn more than the
   average salary. Sort the results in order of ascending salary.
   ```sql
   SELECT employee_id,
          last_name,
          salary
   FROM employees
   WHERE salary > (
      SELECT AVG (salary)
      FROM employees
   )
   ORDER BY salary;
   ```

3. Write a query that displays the employee number and last name of all employees who work in a department with any
   employee whose last name contains the letter u. Save your SQL statement as `lab_07_03.sql`. Run your query.
   ```sql
   SELECT employee_id,
          last_name
   FROM employees
   WHERE department_id IN (
      SELECT department_id
      FROM employees
      WHERE last_name LIKE '%u%'
   );
   ```   

4. The HR department needs a report that displays the last name, department number, and job ID of all employees whose
   department location ID is 1700.
   ```sql
   SELECT last_name,
          department_id,
          job_id
   FROM employees
   WHERE department_id IN (
      SELECT department_id
      FROM departments
      WHERE location_id = 1700
   )
   ORDER BY department_id;
   ```

   Modify the query so that the user is prompted for a location ID. Save this to a file named `lab_07_04.sql`.
   ```sql
   SELECT last_name,
          department_id,
          job_id
   FROM employees
   WHERE department_id IN (
      SELECT department_id
      FROM departments
      WHERE location_id = &location_id
   )
   ORDER BY department_id;
   ```

5. Create a report for HR that displays the last name and salary of every employee who reports to King.
   ```sql
   SELECT last_name,
          salary
   FROM employees
   WHERE manager_id = (
      SELECT employee_id
      FROM employees
      WHERE last_name = 'King'
   );
   ```

6. Create a report for HR that displays the department number, last name, and job ID for every employee in the Executive
   department.
   ```sql
   SELECT department_id,
          last_name,
          job_id
   FROM employees
   WHERE department_id = (
      SELECT department_id
      FROM departments
      WHERE department_name = 'Executive'
   );
   ```

7. Modify the query in `lab_07_03.sql` to display the employee number, last name, and salary of all employees who earn
   more than the average salary, and who work in a department with any employee whose last name contains a 'u'.
   Resave `lab_07_03.sql` as `lab_07_07.sql`. Run the statement in `lab_07_03.sql`.
   ```sql
   SELECT employee_id,
          last_name,
          salary
   FROM employees
   WHERE salary > (
            SELECT AVG (salary)
            FROM employees
      )
         AND department_id IN (
      SELECT department_id
      FROM employees
      WHERE last_name LIKE '%u%'
   );
   ```

## Practice 8

In this practice, you create reports by using:
> 1. The `UNION` operator
> 2. The `INTERSECTION` operator
> 3. The `MINUS` operator

***

1. The HR department needs a list of department IDs for departments that do not contain the job ID ***ST_CLERK***. Use
   the set operators to create this report.
   ```sql
   SELECT department_id
   FROM departments
   MINUS
   SELECT department_id
   FROM departments
   WHERE department_name = 'ST_CLERK';
   ```

2. The HR department needs a list of countries that have no departments located in them. Display the country ID and the
   name of the countries. Use the set operators to create this report.
   ```sql
   SELECT country_id,
          country_name
   FROM countries
   MINUS
   SELECT country_id,
          country_name
   FROM countries
   JOIN locations USING (country_id);
   ```

3. Produce a list of jobs for departments 10, 50, and 20, in that order. Display the job ID and department ID by using
   the set operators.
   ```sql
   COLUMN ord NOPRINT;
   SELECT job_id,
          department_id,
          1 ord
   FROM employees
   WHERE department_id = 10
   UNION
   SELECT job_id,
          department_id,
          3 ord
   FROM employees
   WHERE department_id = 20
   UNION
   SELECT job_id,
          department_id,
          2 ord
   FROM employees
   WHERE department_id = 50
   ORDER BY ord;
   ```

4. Create a report that lists the employee IDs and job IDs of those employees who currently have a job title that is the
   same as their job title when they were initially hired by the company (that is, they changed jobs but have now gone
   back to doing their original job).
   ```sql
   SELECT employee_id,
          job_id
   FROM employees
   INTERSECT
   SELECT employee_id,
          job_id
   FROM job_history;
   ```

5. The HR department needs a report with the following specifications:
    - Last name and department ID of all employees from the ***EMPLOYEES*** table, regardless of whether or not they
      belong to a department
    - Department ID and department name of all departments from the ***DEPARTMENTS*** table, regardless of whether or
      not they have employees working in them Write a compound query to accomplish this.
   ```sql
   SELECT last_name,
          department_id,
          to_char(NULL)
   FROM employees
   UNION
   SELECT to_char(NULL),
          department_id,
          department_name
   FROM departments;
   ```