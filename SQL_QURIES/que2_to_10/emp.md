## Create table given below: Employee and IncentiveTable

<hr>

**Employee Table**

```
CREATE TABLE Employee (
    Employee_id INT PRIMARY KEY,
    First_name VARCHAR(50),
    Last_name VARCHAR(50),
    Salary INT,
    Joining_date DATE,
    Department VARCHAR(50)
);
```

```
INSERT INTO employee(employee_id, first_name, last_name, salary, joining_date, department)
VALUES(1, 'John', 'Abraham', 1000000, '2023-01-01 12 00 00', 'Banking'),
(4, 'Tom', 'Jose', 600000, '2013-02-01 12:00:00', 'Insurance'),
(5, 'Jerry', 'Pinto', 650000, '2013-02-01 12:00:00', 'Insurance'),
(6, 'Philip', 'Mathew', 750000, '2013-02-01 12:00:00', 'Services'),
(7, 'Naina' , 'Talwar', 650000, '2013-02-01 12:00:00', 'Services'),
(8, 'Kabir', 'Singh', 700000, '2013-02-01 12:00:00', 'Services');
```

## Output Image

![Output-image](emp.png)

**Incentive Table**

```
CREATE TABLE Incentive (
    Employee_ref_id INT,
    Incentive_date DATE,
    Incentive_amount INT
);
```

```
INSERT INTO incentive(employee_ref_id, Incentive_date, Incentive_amount) VALUES
(1, '2013-02-01', 5000),
(2, '2013-02-01', 3000),
(3, '2013-02-01', 4000),
(4, '2013-01-01', 4500),
(5, '2013-01-01', 3500);
```

## Output Image

![Output-image](incentive.png)

<hr>
<hr>

## 3. Get First_Name from employee table using Tom name “Employee Name”.

![Output-image](q3.png)

## 4. Get FIRST_NAME, Joining Date, and Salary from employee table.

```
SELECT first_name, joining_date, salary FROM employee;
```

## Output

![Output-image](q4.png)

## 5. Get all employee details from the employee table order by First_Name Ascending and Salary descending?

```
SELECT* FROM employee
ORDER BY first_name ASC, salary DESC;
```

## Output

![Output-image](q5.png)

## 6. Get employee details from employee table whose first name contains ‘J’.

```
SELECT* FROM employee
WHERE first_name LIKE '%J%';
```

## Output

![Output-image](q6.png)

## 7. Get department wise maximum salary from employee table order by salary ascending?

```
SELECT department, MAX(salary) AS maxsalary
FROM employee
GROUP BY department
ORDER BY maxsalary ASC;
```

## Output

![Output-image](q7.png)

## 9. Select first_name, incentive amount from employee and incentives table for those employees who have incentives and incentive amount greater than 3000

```
SELECT e.first_name, i.Incentive_amount
FROM employee e
JOIN incentive i ON e.employee_id = i.employee_ref_id
WHERE i.Incentive_amount > 3000;
```

## Output

![Output-image](q9.png)

## Create After Insert trigger on Employee table which insert records in view table

**Create_View_Table**

```
CREATE TABLE view_table (
    Employee_Id INT,
    First_Name VARCHAR(50),
    Last_Name VARCHAR(50),
    Salary INT,
    Joining_date DATE,
    Department VARCHAR(50)
);
```

```
CREATE TRIGGER insert_into_view_table
AFTER INSERT ON Employee
FOR EACH ROW
BEGIN
  INSERT INTO view_table (Employee_Id, First_Name, Last_Name, Salary, Joining_date, Department)
  VALUES (NEW.Employee_Id, NEW.First_Name, NEW.Last_Name, NEW.Salary, NEW.Joining_date, NEW.Department);
END;
```

**insert the following record into the Employee table:**

```
INSERT INTO Employee (Employee_Id, First_Name, Last_Name, Salary, Joining_date, Department)
VALUES (9, 'Rachna', 'Pandya', 60000, '2023-11-22', 'IT');
```

**The trigger will automatically insert the following record into the view table**

## Output

![Output-image](trigger.png)
