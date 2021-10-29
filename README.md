# oracle-database-11g-sql-fundamentals-practice-solutions

My solutions to all of the **Oracle Database 11g: SQL Fundamentals I / II / III** practices

Feel free to use and if u have any suggestions don't hesitate to contact me . 😃

## Sections

- [Practice 1](#practice-1)
- [Practice 2](#practice-2)
- [Practice 3](#practice-3)
- [Practice 4](#practice-4)
- [Practice 5](#practice-5)
- [Practice 6](#practice-6)
- [Practice 7](#practice-7)
- [Practice 8](#practice-8)
- [Practice 9](#practice-9)

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
           round(salary * 1.155) "New Salary"
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
           round(salary * 1.155)          "New Salary",
           round(salary * 1.155) - salary "Increase"
    FROM employees;
    ```

5. Write a query that displays the last name (with the first letter in uppercase and all the other letters in lowercase)
   and the length of the last name for all employees whose name starts with the letters J, A, or M. Give each column an
   appropriate label. Sort the results by the employees last names.
    ```sql
    SELECT initcap(last_name) "Name",
           length(last_name)  "Length"
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
    SELECT initcap(last_name) "Name",
           length(last_name)  "Length"
    FROM employees
    WHERE last_name LIKE '&letter%'
    ORDER BY last_name;
    ```

   Modify the query such that the case of the entered letter does not affect the output. The entered letter must be
   capitalized before being processed by the query.
   ```sql
    SELECT initcap(last_name) "Name",
           length(last_name)  "Length"
    FROM employees
    WHERE last_name LIKE upper('&letter%')
    ORDER BY last_name;
    ```

6. The HR department wants to find the duration of employment for each employee. For each employee, display the last
   name and calculate the number of months between today and the date on which the employee was hired. Label the column
   as ***MONTHS_WORKED***. Order your results by the number of months employed. Round the number of months up to the
   closest whole number.
    ```sql
    SELECT last_name,
           round(months_between(sysdate, hire_date)) months_worked
    FROM employees
    ORDER BY months_worked;
    ```

7. Create a query to display the last name and salary for all employees. Format the salary to be 15 characters long,
   left-padded with the $ symbol. Label the column as ***SALARY***.
    ```sql
    SELECT last_name,
           lpad(salary, 15, '$') salary
    FROM employees;
    ```

8. Create a query that displays the first eight characters of the employees last names and indicates the amounts of
   their salaries with asterisks. Each asterisk signifies a thousand dollars. Sort the data in descending order of
   salary. Label the column ***EMPLOYEES_AND_THEIR_SALARIES***
    ```sql
    SELECT substr(last_name, 1, 8) ||
           rpad(' ', round(salary / 1000) + 1, '*') employees_and_their_salaries
    FROM employees
    ORDER BY salary DESC;
    ```

9. Create a query to display the last name and the number of weeks employed for all employees in department 90. Label
   the number of weeks column as ***TENURE***. Truncate the number of weeks value to 0 decimal places. Show the records
   in descending order of the employees tenure.
    ```sql
    SELECT last_name,
          trunc((sysdate - hire_date) / 7) tenure
   FROM employees
   WHERE department_id = 90
   ORDER BY tenure DESC;
    ```
