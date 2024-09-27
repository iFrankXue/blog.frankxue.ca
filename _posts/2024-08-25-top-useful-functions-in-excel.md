---
title: Top Useful Functions in EXCEL
description: There are hundreds of functions in Excel, and playing different roles in manipulating cells in Excel. I listed the most important functions to help me and viewers to get familia with them.
author: frank
date: 2024-08-25 21:00:00 -0700
categories: [Excel, functions]
tags: [excel, function, date, time, financial, information, logical, lookup, mathematical, statistical, text]
pin: false
math: false
mermaid: true
image:
  path: /assets/img/2024/08-25-title-excel-function.png
  lqip: /assets/img/2024/08-25-title-excel-function.png # or base64 URI
  alt: Top useful functions in Excel
---

## **Introduction**

As someone with a background in computer science and experience in data analysis, I've always valued the versatility of Excel as a tool for both personal and professional use. Whether it's crunching numbers, managing data, or simplifying complex calculations, Excel has been a cornerstone in my daily work-especially as I've transitioned into marketing coordination and explored data analysis more deeply. In this article, I'll be sharing some of the top useful Excel functions that consistently helped me tackle data-related challenges efficiently and effectively.

In this article, I will categorize the various Excel functions into different groups, providing a clear explanation of each specific function along with its syntax. Additionally, I will present practical example to illustrate their usage, ensuring that both beginners and experienced users can benefit. Along the way, I'll also share some useful tips for optimizing these functions to enhance your productivity and streamline your work in Excel.

OK, let hop into the Excel's functions world!

## **1. Date and Time** Functions

![Date and Time](/assets/img/2024/08-25-function-date-and-time.png){: width="150" .w-20 .right}

Date and time functions are essential when working with dates, times, and durations in Excel, offering a wide range of capabilities for handling temporal data. These functions allow you to easily calculate the number of days, months, or even years between two dates, which is especially useful for project management, aging reports, or financial forecasting. 

Additionally, they enable you to automate the insertion of the current date and time using functions like `TODAY()` and `NOW()`, ensuring your date is always up to date without manual input. You can use these functions to extract specific parts of a date, such as the year, month, or day, or to combine separate values - such as day, month, and year - into a single cohesive date using functions like `DATE()`. Furthermore, advanced functions like `WORKDAY()` and `NETWORKDAYS()` help calculate workdays or exclude weekends and holidays, which is critical for scheduling and time-sensitive tasks.



- Function: **TODAY**, **NOW**, **DATE**, **DATEDIF**.

| Function       | Description                            | Syntax                            |
|----------------|----------------------------------------|-----------------------------------|
| **TODAY**      | Returns the current system date.       | =TODAY() - with no arguments.      |
| **NOW**        | Returns the current date and time.     | =NOW() - with no arguments.        |
| **DATE**       | Returns a date based on the arguments: year, month and day.  | =DATE(year,month,day)    |
| **DATEDIF**    | Calculates the number of days, months, or years between <br />two dates.  | =DATEDIF(start_date,end_date,unit)    |


-  Function: **YEAR**, **MONTH**, **EOMONTH**, **DAY**.

| Function      | Description                                             | Syntax                      |
|---------------|---------------------------------------------------------|-----------------------------|
| **YEAR**      | Returns the year of a date.                             | =YEAR(serial_number)         |
| **MONTH**     | Returns the month of a date.                            | =MONTH(serial_number)        |
| **DAY**       | Returns the day of a date.                              | =DAY(serial_number)          |
| **EOMONTH**   | Returns the serial number for the last day of the month <br /> that is the indicated number of months before or after <br />start_date. | =EOMONTH(start_date, months)  |

- Function: **WEEKDAY**, **NETWORKDAYS**.

| Function         | Description                                          | Syntax                      |
|------------------|------------------------------------------------------|-----------------------------|
| **WEEKDAY**      | Returns the day of the week corresponding to a date. <br />The day is given as an integer, ranging from 1 (Sunday) <br />to 7 (Saturday), by default. | =WEEKDAY(serial_number,<br />[return_type])     |
| **NETWORKDAYS**  | Returns the number of whole working days between <br />start_date and end_date. | =NETWORKDAYS(start_date, <br />end_date, [holidays])   |

Find more detailed explanation and examples, please visit the following link:<br /> 
[Top 10 Date and Time Functions in Excel I Learned](/posts/top-10-data-and-time-functions-in-excel-i-learned/)

## **2. Financial** Functions

Financial functions in Excel are powerful tolls designed to help you perform a variety of financial calculations. These functions allows you to analyze investments, calculate loan payments, assess future cash flows, and determine the value of investments. These following functions are essential for anyone involved in finance, accounting, or business decision-making, as they streamline complex calculations and provide accurate results efficiently.

- Function: **PV**, **FV**, **NPV**, **RATE**, **PMT**, **NPER**.

| Function    | Description                                              | Syntax              |
|-------------|----------------------------------------------------------|---------------------|
| **PV**      | Calculates the present value of a loan or an investment, based on a <br />constant interest rate.       | =PV(rate, nper, pmt, [fv], [type])      |
| **FV**      | Calculates the future value of a an investment based on a constant <br />interest rate.           | =FV(rate,nper,pmt,[pv],[type])     |
| **NPV**     | Calculates the net present value of a investment by using a discount <br />rate and a series of future payments (negative values) and income <br />(positive values).     | =NPV(rate,value1,[value2],...)       |
| **RATE**    | Returns the interest rate per period of an annuity.     | =RATE(nper, pmt, pv, [fv], [type], <br />[guess]) |
| **PMT**     | Calculates the payment for a loan based on constant payments and a <br />constant interest rate.    | =PMT(rate, nper, pv, [fv], [type])  |
| **NPER**    | Returns the number of periods for a investment based on periodic, <br />constant payments and a constant interest rate.   | =NPER(rate,pmt,pv,[fv],[type])   |

Find more detailed explanation and examples, please visit the following link:<br /> 
[Top 6 Useful Functions for Financial Operations in Excel](/posts/top-6-useful-functions-for-financial-operations-in-excel/)


## **3. Information** Functions

Information functions stand out as powerful tools that help you understand and validate the content of your cells. Whether you're identifying the style of data, checking for errors, or retrieving metadata about your cells, these functions empower you to ensure your data is both clean and reliable.

- Function: **ISBLANK**, **ISNUMBER**, **ISTEXT**, **ISFORMULA**, **ISLOGICAL**.

| Function         | Description                                              | Syntax              |
|------------------|----------------------------------------------------------|---------------------|
| **ISBLANK**      | Returns `TRUE` if `value` refers to an empty cell.       | =ISBLANK(value)      |
| **ISNUMBER**     | Returns `TRUE` if `value` refers to a number.            | =ISNUMBER(value)     |
| **ISTEXT**       | Returns `TRUE` if `value` refers to text.                | =ISTEXT(value)       |
| **ISFORMULA**    | Returns `TRUE` if `reference` refers to a formula.       | =ISFORMULA(reference)|
| **ISLOGICAL**    | Returns `TRUE` if `value` refers to a logical value.     | =ISLOGICAL(value)    |

- Function: **ISERROR**, **ISERR**, **ISNA**.

| Function         | Description                            | Syntax                            |
|------------------|----------------------------------------|-----------------------------------|
| **ISERROR**      | Returns `TRUE` if `value` refers to any error value (#N/A, #VALUE!,<br /> #REF!, #DIV/0!, #NUM!, #NAME?, or #NULL).      | =ISERROR(value)      |
| **ISERR**        | Returns `TRUE` if `value` refers to any error value except #N/A.    | =ISERR(value)        |
| **ISNA**         | Returns `TRUE` if `value` refers to the #N/A (value not available)<br /> error value.   | =ISNA(value)        |

- Function: **TYPE**, **INFO**, **N**, **CELL**.

| Function         | Description                            | Syntax                            |
|------------------|----------------------------------------|-----------------------------------|
| **TYPE**         | Returns the type of value.             |  TYPE(value)                      |
| **INFO**         | Returns information about the current operating environment.   | =INFO(type_text)    |
| **N**            | Returns a value converted to a number   | =N(value)                        |
| **CELL**         | Returns information about the formatting, location, or contents of<br /> a cell.   | =CELL(info_type, [reference])    | 


Find more detailed explanation and examples, please visit the following link: <br />
[Top 12 Information Functions in Excel You Should Know](/posts/top-12-information-functions-in-excel-you-should-know/)


## **4. Logical** Functions

Logical functions in Excel are essential tools that allow you to perform operations based on specific conditions. These functions enable you to create complex decision-making processes within your spreadsheets by evaluating whether certain conditions are `TRUE` or `FALSE`. These following functions can be combined in various ways to create powerful logical tests that can help automate decision-making and data analysis in Excel.

- Function: **IF**, **IFS**, **IFERROR**.

| Function         | Description                                              | Syntax              |
|------------------|----------------------------------------------------------|---------------------|
| **IF**           | Returns one value if a condition is true and another value <br />if it's false. | =IF(logical_test, value_if_true, <br />[value_if_false])      |
| **IFS**          | Checks whether one or more conditions are met, and returns <br />a value that corresponds to the first TRUE condition. | =IFS(test1,value1,[test2, <br />value2], ...)|
| **IFERROR**      | Returns a value you specify if a formula evaluates to an error; <br />otherwise, returns the result of the formula. | =IFERROR(value, value_if_error)|


- Function: **AND**, **OR**, **NOT**.

| Function         | Description                                              | Syntax              |
|------------------|----------------------------------------------------------|---------------------|
| **AND**          | Determine if all conditions in a test are TRUE.          | =AND(logical1, [logical2], ...) |
| **OR**           | Determine if at lease one condition is TRUE from multiple <br />criteria. | =OR(logical1, [logical2], ...)|
| **NOT**          | Returns a reversed logical value.                        | =NOT(logical)                   |

Find more detailed explanation and examples, please visit the following link: <br />
[Top 6 Logical Functions in Excel You Need to Know About](/posts/top-6-important-logical-functions-in-excel-you-need-to-know-about/)


## **5. Lookup** Functions

Lookup functions in Excel are powerful tools that allow you to search for specific data within a range or a table and return corresponding values. They are essential for tasks that involve finding information based on a specific criterion. The most popular lookup functions are essential for data analysis and manipulation in Excel, making them a fundamental part of any Excel user's toolkit.

- Function: **VLOOKUP**, **HLOOKUP**, **XLOOKUP**.

| Function         | Description                                              | Syntax              |
|------------------|----------------------------------------------------------|---------------------|
| **VLOOKUP**      | Searches for a lookup value in the first column of a range; <br />if a match is found, VLOOKUP returns the value of a cell in <br />the same row, but offset a specified number of columns to <br />the right.                  | =VLOOKUP(lookup_value, table_array, <br />col_index_num, [range_lookup]) |
| **HLOOKUP**      | Searches for a lookup value in the top row of a range; if a <br />match is found, HLOOKUP returns the value of a cell in the <br />same column, but offset a specified number of rows down.                                   | =HLOOKUP(lookup_value, table_array, <br />row_index_num, [range_lookup]) |
| **XLOOKUP**      | Searches a range or an array, and then returns the item <br />corresponding to the first match it finds. If no math exists, <br />then XLOOKUP can return the closest (approximate) match.                                       | =XLOOKUP(lookup_value, lookup_array, <br />return_array, [if_not_found], <br />[match_mode], [search_mode])  |


- Function: **INDEX**, **MATCH**, **FILTER**.

| Function         | Description                                              | Syntax                            |
|------------------|----------------------------------------------------------|-----------------------------------|
| **INDEX**        | Returns the value of an element in a table or an array, <br />selected by the row and column number indexes.     | =INDEX(array, row_num, <br />[column_num]) |
| **MATCH**        | Searches for a specified item in a range of cells, and <br />then returns the relative position of that item in the range. | =MATCH(lookup_value, lookup_array, <br />[match_type]) |
| **FILTER**       | Filters a range of data based on criteria you define.    | =FILTER(array, include, [if_empty]) |

Find more detailed explanation and examples, please visit the following link: <br />
[Top 6 Best Lookup Functions in Excel](/posts/top-6-best-lookup-functions-in-excel)


## **6. Mathematical** Functions

Mathematics functions in Excel are fundamental tools that allow users to perform a wide range of calculations, from basic arithmetic to complex statistical analysis. These functions are crucial for tasks like summing data, finding averages, rounding numbers, and even performing trigonometric calculations. They are highly versatile and can be used in various contexts, such as financial modeling, data analysis, budgeting, and more.

The general idea behind mathematics functions in Excel is to simplify and automate numerical calculations. Instead of manually computing results, users can rely on these built-in functions to quickly and accurately process data, ensuring consistency and reducing the likelihood of errors. These functions can be combined with other Excel functions, such as cell references and arrays, to create powerful formulas that can handle large datasets with ease.

Overall, the following mathematics functions from the backbone of Excel's computation capabilities, making it an indispensable tool for anyone working with numbers.

- Function: **SUM**, **SUMIF**, **SUMIFS**, **SUMPRODUCT**.

| Function         | Description                                              | Syntax              |
|------------------|----------------------------------------------------------|---------------------|
| **SUM**      | Returns `TRUE` if `value` refers to an empty cell.       | =ISBLANK(value)      |
| **SUMIF**     | Returns `TRUE` if `value` refers to a number.            | =ISNUMBER(value)     |
| **SUMIFS**       | Returns `TRUE` if `value` refers to text.                | =ISTEXT(value)       |
| **SUMPRODUCT**    | Returns `TRUE` if `reference` refers to a formula.       | =ISFORMULA(reference)|


- Function: **ROUND**, **ROUNDDOWN**, **ROUNDUP**.

| Function         | Description                                              | Syntax              |
|------------------|----------------------------------------------------------|---------------------|
| **ROUND**        | Returns `TRUE` if `value` refers to an empty cell.       | =ISBLANK(value)      |
| **ROUNDDOWN**    | Returns `TRUE` if `value` refers to a number.            | =ISNUMBER(value)     |
| **ROUNDUP**      | Returns `TRUE` if `value` refers to text.                | =ISTEXT(value)       |

- Function: **ABS**, **MOD**, **RAND**, **RANDBETWEEN**.

| Function         | Description                                              | Syntax              |
|------------------|----------------------------------------------------------|---------------------|
| **ABS**      | Returns `TRUE` if `value` refers to an empty cell.       | =ISBLANK(value)      |
| **MOD**     | Returns `TRUE` if `value` refers to a number.            | =ISNUMBER(value)     |
| **RAND**       | Returns `TRUE` if `value` refers to text.                | =ISTEXT(value)       |
| **RANDBETWEEN**    | Returns `TRUE` if `reference` refers to a formula.       | =ISFORMULA(reference)|

Find more detailed explanation and examples, please visit the following link: <br />
[Top 6 Best Lookup Functions in Excel](/posts/top-6-best-lookup-functions-in-excel)

## **7. Statistical** Functions

TBA


- Function: **COUNT**, **COUNTA**, **COUNTBLANK**, **COUNTIF**, **COUNTIFS**.

| Function         | Description                                              | Syntax              |
|------------------|----------------------------------------------------------|---------------------|
| **COUNT**      | Returns `TRUE` if `value` refers to an empty cell.       | =ISBLANK(value)      |
| **COUNTA**     | Returns `TRUE` if `value` refers to a number.            | =ISNUMBER(value)     |
| **COUNTBLANK**      | Returns `TRUE` if `value` refers to an empty cell.       | =ISBLANK(value)      |
| **COUNTIF**     | Returns `TRUE` if `value` refers to a number.            | =ISNUMBER(value)     |
| **COUNTIFS**      | Returns `TRUE` if `value` refers to an empty cell.       | =ISBLANK(value)      |

- Function: **MIN**, **MEDIAN**, **MAX**, **STDEV**.

| Function         | Description                                              | Syntax              |
|------------------|----------------------------------------------------------|---------------------|
| **MIN**      | Returns `TRUE` if `value` refers to an empty cell.       | =ISBLANK(value)      |
| **MEDIAN**      | Returns `TRUE` if `value` refers to an empty cell.       | =ISBLANK(value)      |
| **MAX**     | Returns `TRUE` if `value` refers to a number.            | =ISNUMBER(value)     |
| **STDEV**     | Returns `TRUE` if `value` refers to a number.            | =ISNUMBER(value)     |

- Function: **AVERAGE**, **AVERAGEIF**, **AVERAGEIFS**.

| Function         | Description                                              | Syntax              |
|------------------|----------------------------------------------------------|---------------------|
| **AVERAGE**      | Returns `TRUE` if `value` refers to an empty cell.       | =ISBLANK(value)      |
| **AVERAGEIF**     | Returns `TRUE` if `value` refers to a number.            | =ISNUMBER(value)     |
| **AVERAGEIFS**     | Returns `TRUE` if `value` refers to a number.            | =ISNUMBER(value)     |


## **8. Text** Functions


- Function: **LEN**, **FIND**, **LEFT**, **RIGHT**, **MID**.

| Function         | Description                                              | Syntax              |
|------------------|----------------------------------------------------------|---------------------|
| **LEN**      | Returns `TRUE` if `value` refers to an empty cell.       | =ISBLANK(value)      |
| **FIND**     | Returns `TRUE` if `value` refers to a number.            | =ISNUMBER(value)     |
| **LEFT**     | Returns `TRUE` if `value` refers to a number.            | =ISNUMBER(value)     |
| **RIGHT**     | Returns `TRUE` if `value` refers to a number.            | =ISNUMBER(value)     |
| **MID**     | Returns `TRUE` if `value` refers to a number.            | =ISNUMBER(value)     |


- Function: **LOWER**, **UPPER**, **PROPER**.

| Function         | Description                                              | Syntax              |
|------------------|----------------------------------------------------------|---------------------|
| **LOWER**      | Returns `TRUE` if `value` refers to an empty cell.       | =ISBLANK(value)      |
| **UPPER**     | Returns `TRUE` if `value` refers to a number.            | =ISNUMBER(value)     |
| **PROPER**     | Returns `TRUE` if `value` refers to a number.            | =ISNUMBER(value)     |


- Function: **TEXT**, **SUBSTITUTE**, **TRIM**, **CONCATENATE**.

| Function         | Description                                              | Syntax              |
|------------------|----------------------------------------------------------|---------------------|
| **TEXT**      | Returns `TRUE` if `value` refers to an empty cell.       | =ISBLANK(value)      |
| **SUBSTITUTE**     | Returns `TRUE` if `value` refers to a number.            | =ISNUMBER(value)     |
| **TRIM**     | Returns `TRUE` if `value` refers to a number.            | =ISNUMBER(value)     |
| **CONCATENATE**     | Returns `TRUE` if `value` refers to a number.            | =ISNUMBER(value)     |


## **Summary**

