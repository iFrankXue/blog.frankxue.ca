---
title: How to Use Window Functions in SQL
description: Let's talk about the Window Functions in SQL, including 'Ranking Functions', 'Distribution Function', 'Analytic Functions' and 'Aggregate Functions'. Meanwhile, I will also show some example codes by querying an example table.
author: frank
date: 2024-08-10 19:03:10 -0700
categories: [Data Analyst, SQL]
tags: [sql, window functions, syntax]
pin: false
math: false
mermaid: true
image:
  path: /assets/img/2024/08-10-over-clause-sql-title.png
  lqip: /assets/img/2024/08-10-over-clause-sql-title.png # or base64 URI
  alt: Partition By of SQL
---

## Introduction

The `OVER` clause in SQL is used to define a window, or a set of rows, for functions to operate over. This clause is essential in window functions, which perform calculations across a set of table rows that are somehow related to the current row. Unlike aggregate functions, which return a single result for a group of rows, window functions return a value for each row based on the defined window.

## Common Uses of 'OVER':
1. **Partitioning**: The `PARTITION BY` clause within `OVER` divides the result set into partitions to which the window function is applied independently.
   
   Example:
   ```sql
   SUM(sales) OVER (PARTITION BY region)
   ```
   This calculates the sum of `sales` for each `region`.

2. **Ordering**: The `ORDER BY` clause within `OVER` specifies the order of rows within each partition.
   
   Example:
   ```sql
   ROW_NUMBER() OVER (ORDER BY date)
   ```
   This assigns a unique sequential integer to rows within a result set, ordered by `date`.

3. **Range or Rows**: The `RANGE` or `ROWS` clauses within `OVER` allow you to define a specific frame of rows relative to the current row.

   Example:
   ```sql
   SUM(sales) OVER (ORDER BY date ROWS BETWEEN 1 PRECEDING AND 1 FOLLOWING)
   ```
   This calculates a moving sum, including the current row, the previous row, and the next row.

### Examples of Window Functions Using 'OVER':
- **Ranking Functions**: `ROW_NUMBER()`, `RANK()`, `DENSE_RANK()`
  
  Example:
  ```sql
  SELECT employee_id, salary,
         RANK() OVER (ORDER BY salary DESC) AS salary_rank
  FROM employees;
  ```

- **Aggregate Functions**: `SUM()`, `AVG()`, `MIN()`, `MAX()`
  
  Example:
  ```sql
  SELECT department, employee_id, salary,
         SUM(salary) OVER (PARTITION BY department) AS department_total
  FROM employees;
  ```

- **Offset Functions**: `LAG()`, `LEAD()`
  
  Example:
  ```sql
  SELECT employee_id, salary,
         LAG(salary, 1) OVER (ORDER BY hire_date) AS previous_salary
  FROM employees;
  ```

In summary, the `OVER` clause defines the context or "window" within which a window function operates, allowing you to perform complex calculations and analysis that consider each row's relationship to others.



## Examples of Using 'OVER' Clause

 The `OVER` clause is quite powerful in SQL, and it's used in a variety of scenarios to perform calculations across a set of rows related to the current row. Below are more detailed explanations and examples of different ways to use the `OVER` clause in SQL.


### Sample Table: 

Table: `EmployeeSalaries`

| EmployeeID | Name      | Department | Salary | HireDate   |
|------------|-----------|------------|--------|------------|
| 1          | Alice     | HR         | 50000  | 2020-01-15 |
| 2          | Bob       | IT         | 60000  | 2019-11-10 |
| 3          | Charlie   | HR         | 55000  | 2021-03-22 |
| 4          | David     | IT         | 70000  | 2018-06-01 |
| 5          | Eva       | IT         | 75000  | 2019-04-19 |
| 6          | Frank     | HR         | 52000  | 2021-08-03 |
| 7          | Grace     | IT         | 69000  | 2020-12-11 |
| 8          | Henry     | IT         | 60000  | 2022-02-15 |
| 9          | Irene     | HR         | 52000  | 2022-05-10 |


### Example 1: **SUM() Function with 'OVER' Clause**

The `SUM()` function, when used with the `OVER` clause in SQL, allows you to perform cumulative or running totals, or sum values across a specified partition of data without collapsing the rows into a single output. This is very useful when you need to **calculate totals while still retaining the detail of each row**.

```sql
SELECT 
    EmployeeID,
    Name,
    Department,
    Salary,
    SUM(Salary) OVER (PARTITION BY Department) AS DepartmentTotal
FROM EmployeeSalaries;
```

**Result**:

| EmployeeID | Name    | Department | Salary | DepartmentTotal |
|------------|---------|------------|--------|-----------------|
| 1          | Alice   | HR         | 50000  | 209000          |
| 3          | Charlie | HR         | 55000  | 209000          |
| 6          | Frank   | HR         | 52000  | 209000          |
| 9          | Irene   | HR         | 52000  | 209000          |
| 2          | Bob     | IT         | 60000  | 334000          |
| 4          | David   | IT         | 70000  | 334000          |
| 5          | Eva     | IT         | 75000  | 334000          |
| 7          | Grace   | IT         | 69000  | 334000          |
| 8          | Henry   | IT         | 60000  | 334000          |

**Explanation**: The `SUM(Salary) OVER (PARTITION BY Department)` calculates the total salary within each department and displays that total for each row within the department.

### Example 2: **ROW_NUMBER() Function with 'OVER' Clause**

The `ROW_NUMBER()` function in SQL is used to assign a unique sequential integer to rows within a result set. When combined with the `OVER` clause, it allows you to determine the order in which the rows are numbered. The numbering starts at 1 and increments by 1 for each row.

The `ROW_NUMBER()` function with the `OVER` clause is a versatile tool in SQL for **ranking, partitioning, and filtering data, providing a flexible way to analyze and manipulate rows in a dataset**.

```sql
SELECT 
    EmployeeID,
    Name,
    Department,
    Salary,
    ROW_NUMBER() OVER (PARTITION BY Department ORDER BY Salary DESC) AS SalaryRank
FROM EmployeeSalaries;
```

**Result**:

| EmployeeID | Name    | Department | Salary | SalaryRank |
|------------|---------|------------|--------|------------|
| 3          | Charlie | HR         | 55000  | 1          |
| 6          | Frank   | HR         | 52000  | 2          |
| 9          | Irene   | HR         | 52000  | 3          |
| 1          | Alice   | HR         | 50000  | 4          |
| 5          | Eva     | IT         | 75000  | 1          |
| 4          | David   | IT         | 70000  | 2          |
| 7          | Grace   | IT         | 69000  | 3          |
| 2          | Bob     | IT         | 60000  | 4          |
| 8          | Henry   | IT         | 60000  | 5          |

**Explanation**: The `ROW_NUMBER()` function assigns a unique rank within each department based on the salary, with the highest salary getting a rank of 1.

### Example 3. **RANK() Function with 'OVER' Clause**

The `RANK()` function with the `OVER` clause in SQL assigns a rank to each row within a result set based on the order specified in the `OVER` clause. If there are ties (rows with the same values in the ranking criteria), `RANK()` assigns the same rank to those rows, but the next rank is skipped. This function is useful for **ranking items within partitions of data**, such as determining the top performers within each department.

```sql
SELECT 
    EmployeeID,
    Name,
    Department,
    Salary,
    RANK() OVER (PARTITION BY Department ORDER BY Salary DESC) AS SalaryRank
FROM EmployeeSalaries;
```

**Result**:

| EmployeeID | Name    | Department | Salary | SalaryRank |
|------------|---------|------------|--------|------------|
| 3          | Charlie | HR         | 55000  | 1          |
| 6          | Frank   | HR         | 52000  | 2          |
| 9          | Irene   | HR         | 52000  | 2          |
| 1          | Alice   | HR         | 50000  | 4          |
| 5          | Eva     | IT         | 75000  | 1          |
| 4          | David   | IT         | 70000  | 2          |
| 7          | Grace   | IT         | 69000  | 3          |
| 2          | Bob     | IT         | 60000  | 4          |
| 8          | Henry   | IT         | 60000  | 4          |

**Explanation**: The `RANK()` function ranks employees within their departments by salary. Tied salaries would receive the same rank, but the next rank would be skipped.

### Example 4. **DENSE_RANK() Function with 'OVER' Clause**


The `DENSE_RANK()` function with the `OVER` clause in SQL assigns a rank to each row within a result set, similar to `RANK()`, but without skipping any ranks when there are ties. If multiple rows have the same rank, the next rank in the sequence is not skipped. This function is useful for **ranking items in a dense manner** within partitions of data, such as **listing top salespeople** without gaps in ranking numbers.

```sql
SELECT 
    EmployeeID,
    Name,
    Department,
    Salary,
    DENSE_RANK() OVER (PARTITION BY Department ORDER BY Salary DESC) AS DenseSalaryRank
FROM EmployeeSalaries;
```

**Result**:

| EmployeeID | Name    | Department | Salary | DenseSalaryRank |
|------------|---------|------------|--------|-----------------|
| 3          | Charlie | HR         | 55000  | 1               |
| 6          | Frank   | HR         | 52000  | 2               |
| 9          | Irene   | HR         | 52000  | 2               |
| 1          | Alice   | HR         | 50000  | 3               |
| 5          | Eva     | IT         | 75000  | 1               |
| 4          | David   | IT         | 70000  | 2               |
| 7          | Grace   | IT         | 69000  | 3               |
| 2          | Bob     | IT         | 60000  | 4               |
| 8          | Henry   | IT         | 60000  | 4               |

**Explanation**: The `DENSE_RANK()` function also ranks employees by salary within their department but doesn’t skip any ranks if there are ties.

### Example 5. **NTILE() Function with 'OVER' Clause**

The `NTILE()` function with the `OVER` clause in SQL divides the result set into a specified number of approximately equal groups, or "tiles," and assigns a number to each row indicating the tile it belongs to. This function is useful for **creating quartiles, deciles, or any other form of data segmentation**.

```sql
SELECT 
    EmployeeID,
    Name,
    Department,
    Salary,
    NTILE(3) OVER (ORDER BY Salary DESC) AS SalaryQuartile
FROM EmployeeSalaries;
```

**Result**:

| EmployeeID | Name    | Department | Salary | SalaryQuartile |
|------------|---------|------------|--------|----------------|
| 5          | Eva     | IT         | 75000  | 1              |
| 4          | David   | IT         | 70000  | 1              |
| 7          | Grace   | IT         | 69000  | 1              |
| 3          | Charlie | HR         | 55000  | 2              |
| 6          | Frank   | HR         | 52000  | 2              |
| 9          | Irene   | HR         | 52000  | 2              |
| 2          | Bob     | IT         | 60000  | 3              |
| 8          | Henry   | IT         | 60000  | 3              |
| 1          | Alice   | HR         | 50000  | 3              |

**Explanation**: The `NTILE(3)` function divides the rows into three groups based on the salary. The highest salaries go into the first group, and so on.

### Example 6. **CUME_DIST() Function with 'OVER' Clause**

The `CUME_DIST()` function with the `OVER` clause in SQL calculates the cumulative distribution of a value within a result set. It returns a value between 0 and 1, representing the proportion of rows with values less than or equal to the current row's value. This function is useful for understanding the relative standing of a row within a set of values.

```sql
SELECT 
    EmployeeID,
    Name,
    Department,
    Salary,
    CUME_DIST() OVER (ORDER BY Salary DESC) AS CumulativeDistribution
FROM EmployeeSalaries;
```

**Result**:

| EmployeeID | Name    | Department | Salary | CumulativeDistribution |
|------------|---------|------------|--------|------------------------|
| 5          | Eva     | IT         | 75000  | 0.1111                 |
| 4          | David   | IT         | 70000  | 0.2222                 |
| 7          | Grace   | IT         | 69000  | 0.3333                 |
| 3          | Charlie | HR         | 55000  | 0.5556                 |
| 6          | Frank   | HR         | 52000  | 0.7778                 |
| 9          | Irene   | HR         | 52000  | 0.7778                 |
| 2          | Bob     | IT         | 60000  | 0.7778                 |
| 8          | Henry   | IT         | 60000  | 0.7778                 |
| 1          | Alice   | HR         | 50000  | 1.0000                 |

**Explanation**:
- **CUME_DIST()** calculates the cumulative distribution by dividing the rank of the current row by the total number of rows.
- **Eva** has the highest salary (75,000), so her `CumulativeDistribution` is `1/9 = 0.1111`, indicating that 11.11% of the employees have a salary less than or equal to hers.
- **David** is next with a salary of 70,000, so his `CumulativeDistribution` is `2/9 = 0.2222`, indicating that 22.22% of the employees have a salary less than or equal to his.
- **Grace** follows with a salary of 69,000, giving her a `CumulativeDistribution` of `3/9 = 0.3333`.
- **Charlie** has a salary of 55,000, and his `CumulativeDistribution` is `5/9 = 0.5556`.
- **Frank** and **Irene** have the same salary of 52,000, and since they are tied, they share the same `CumulativeDistribution` of `7/9 = 0.7778`.
- **Bob** and **Henry** also share a salary of 60,000, so their `CumulativeDistribution` is also `7/9 = 0.7778`.
- **Alice** has the lowest salary (50,000), and her `CumulativeDistribution` is `9/9 = 1.0000`, indicating that all employees have a salary less than or equal to hers.


### Example 7. **LEAD() and LAG() with 'OVER' Clause**

The `LEAD()` and `LAG()` functions with the `OVER` clause in SQL are used to access data from subsequent or previous rows in a result set, respectively.

 - `LAG()` retrieves data from a specified number of rows before the current row.
 - `LEAD()` retrieves data from a specified number of rows after the current row.

These functions are useful for comparing values between rows, such as tracking changes over time or calculating differences between consecutive records.

```sql
SELECT 
    EmployeeID,
    Name,
    Department,
    Salary,
    LAG(Salary, 1) OVER (ORDER BY Salary DESC) AS PreviousSalary,
    LEAD(Salary, 1) OVER (ORDER BY Salary DESC) AS NextSalary
FROM EmployeeSalaries;
```

**Result**:

| EmployeeID | Name    | Department | Salary | PreviousSalary | NextSalary |
|------------|---------|------------|--------|----------------|------------|
| 5          | Eva     | IT         | 75000  | NULL           | 70000      |
| 4          | David   | IT         | 70000  | 75000          | 69000      |
| 7          | Grace   | IT         | 69000  | 70000          | 60000      |
| 2          | Bob     | IT         | 60000  | 69000          | 60000      |
| 8          | Henry   | IT         | 60000  | 60000          | 55000      |
| 3          | Charlie | HR         | 55000  | 60000          | 52000      |
| 6          | Frank   | HR         | 52000  | 55000          | 52000      |
| 9          | Irene   | HR         | 52000  | 52000          | 50000      |
| 1          | Alice   | HR         | 50000  | 52000          | NULL       |

**Explanation**: `LAG()` retrieves the salary of the previous employee (in descending salary order), while `LEAD()` retrieves the salary of the next employee. This can be useful for calculating differences or trends between rows.

### Example 8. **PERCENT_RANK() with 'OVER' Clause**

The `PERCENT_RANK()` function with the `OVER` clause in SQL calculates the relative rank of a row as a percentage of the total number of rows in the result set. It returns a value between 0 and 1, representing where a row stands in relation to others, with the first row being 0 and the last row being 1. This function is useful for **understanding the relative position of a value** within a dataset.

```sql
SELECT 
    EmployeeID,
    Name,
    Department,
    Salary,
    PERCENT_RANK() OVER (ORDER BY Salary DESC) AS PercentRank
FROM EmployeeSalaries;
```

**Result**:

| EmployeeID | Name    | Department | Salary | PercentRank |
|------------|---------|------------|--------|-------------|
| 5          | Eva     | IT         | 75000  | 0.0000      |
| 4          | David   | IT         | 70000  | 0.1250      |
| 7          | Grace   | IT         | 69000  | 0.2500      |
| 2          | Bob     | IT         | 60000  | 0.5000      |
| 8          | Henry   | IT         | 60000  | 0.5000      |
| 3          | Charlie | HR         | 55000  | 0.7500      |
| 6          | Frank   | HR         | 52000  | 0.8750      |
| 9          | Irene   | HR         | 52000  | 0.8750      |
| 1          | Alice   | HR         | 50000  | 1.0000      |

**Explanation**: The `PERCENT_RANK()` function gives each row's rank as a percentage of the total number of rows, ranging from 0 to 1.

## Conclusion

The `OVER` clause in SQL is incredibly versatile and can be combined with various functions to perform advanced calculations on your data. These examples cover many common scenarios where you might use the `OVER` clause, such as ranking, cumulative distribution, and moving averages. Understanding how to use `OVER` can significantly enhance your ability to analyze and manipulate data in SQL.
