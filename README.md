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

### Part 1

1. The following ***SELECT*** statement executes successfully:
   ```sql
   SELECT last_name,
       job_id,
       salary AS Sal
   FROM employees;
   ```
   **Answer:** True


2. The following ***SELECT*** statement executes successfully:
   ```sql
   SELECT * 
   FROM job_grades;
   ```
   **Answer:** True

3. There are four coding errors in this statement. Can you identify them?
   > 1. there is no column 'sal' in the employees table.
   > 2. 'x' cannot be used as multiplication operator, use '*' instead.
   > 3. if column alias contains spaces you must put it in quotation marks.
   > 4. a comma is missing after the last_name column.

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

6. Test your query in the ***lab_01_05.sql*** file to ensure that it runs correctly.
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

8. The HR department wants more descriptive column headings for its report on employees. Copy the statement from ***
   lab_01_05.sql*** to a new SQL Worksheet. Name the column headings ***Emp#***, ***Employee***, ***Job*** and ***Hire
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
       ', ' || job_id "Emplpoyee and Title"
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
