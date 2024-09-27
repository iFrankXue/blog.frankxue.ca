---
title: Top 12 Information Functions in Excel You Should Know
description: Information functions in Excel are a set of functions that return specific details about the data or the cell contents. These functions can help identify the type of data, check for errors, or extract metadata about the cells. Below are some key information functions in Excel.
author: frank
date: 2024-08-29 10:40:00 -0700
categories: [Excel, functions]
tags: [excel, function, information]
pin: false
math: false
mermaid: true
image:
  path: /assets/img/2024/08-29-title-function-information.png
  lqip: /assets/img/2024/08-29-title-function-information.png # or base64 URI
  alt: Top 12 information functions in Excel
---

## **Introduction**


___

## **Functions**

### 1. ISBLANK 

| Function         | Description                                              | Syntax              |
|------------------|----------------------------------------------------------|---------------------|
| **ISBLANK**      | Returns `TRUE` if `value` refers to an empty cell.       | ISBLANK(value)      |

The `ISBLANK()` function in Excel is a simple yet powerful tool for identifying empty cells within your data. This function **checks** whether a specified cell is blank and returns `TRUE` if the cell is empty or `FALSE` if it contains **any data**, including spaces, numbers, text, or formulas. The **syntax** is `=ISBLANK(value)`, and the `value` is the cell reference or value you want to check.

**Example:** suppose you have a data range where you want to identify missing entries. If cell `A1` is empty, the formula `=ISBLANK(A1)` will return `TRUE`. On the other hand, if `A1` contains any data, even a single space, the function will return `FALSE`.

The `ISBLANK()` function is particularly useful in data validation and conditional formatting. For instance, you might want to highlight cells in a report that are blank, indicating missing information. By combining `ISBLANK()` with other functions like [`IF()`](/posts/top-6-important-logical-functions-in-excel-you-need-to-know-about/#1-if), you can create dynamic formulas that respond to empty cells, ensuring your data is complete and ready for analysis.

### 2. ISNUMBER

| Function         | Description                                              | Syntax              |
|------------------|----------------------------------------------------------|---------------------|
| **ISNUMBER**     | Returns `TRUE` if `value` refers to a number.            | ISNUMBER(value)     |

The `ISNUMBER()` function in Excel is a versatile tool that allows you to determine whether a cell contains a numeric value. It returns `TRUE` if the cell's content is a number, and `FALSE` if it contains anything else, such as text, errors, or blanks. The **syntax** is `=ISNUMBER(value)`, and the `value` is the cell reference or value you want to check.

**Example:** imagine you have a dataset where you need to verify if certain cells contain numbers. if cell `B2` contains the number 123, the formula `=ISNUMBER(B2)` will return `TRUE`. However, if `B2` contains text like "abc" or is empty, the function will return `FALSE`.

The `ISNUMBER()` function is particularly useful when working with data that may have mixed types of values, such as importing data from external sources where some entries are numbers and others are text. By using `ISNUMBER()` in conjunction with other functions like [`IF()`](/posts/top-6-important-logical-functions-in-excel-you-need-to-know-about/#1-if) or `SUMIF()`, you can create formulas that perform calculations only on numeric values, ensuring the accuracy of your results. It's also commonly used in data validation to enforce numeric input in specific fields.

### 3. ISTEXT

| Function         | Description                                              | Syntax              |
|------------------|----------------------------------------------------------|---------------------|
| **ISTEXT**       | Returns `TRUE` if `value` refers to text.                | ISTEXT(value)       |

The `ISTEXT()` function in Excel is designed to check whether a cell contains text. This function returns `TRUE` if the content of the specific cell is text, and `FALSE` if the cell contains numbers, errors, or is empty. The **syntax** is `=ISTEXT(value)`, and the `value` is the cell reference or value you want to check.

**Example:** suppose you have a column of mixed data type, and you need to identify which cells contain text. If cell `C3` contains the word "Hello", the formula `=ISTEXT(C3)` will return `TRUE`. Conversely, if `C3` contains a number or is blank, the function will return `FALSE`.

The `ISTEXT()` function is especially useful when you're dealing with datasets that include both text and numbers. For instance, you might want to isolate or perform actions only on text entries in a list, such as highlighting all text cells in a column or combining it with functions like [`IF()`](/posts/top-6-important-logical-functions-in-excel-you-need-to-know-about/#1-if) to apply specific logic based on whether a cell contains text. This function helps ensure that your formulas and analyses behave as expected, depending on the type of data present.

### 4. ISFORMULA

| Function         | Description                                              | Syntax              |
|------------------|----------------------------------------------------------|---------------------|
| **ISFORMULA**    | Returns `TRUE` if `reference` refers to a formula.       | ISFORMULA(reference)|

The `ISFORMULA()` function in Excel is a handy tool for identifying whether a cell contains a formula. This function returns `TRUE` if the specified cell contains a formula and `FALSE` if it dose not. It's particularly useful for auditing and managing complex spreadsheets. The **syntax** is `=ISFORMULA(reference)`, and the `reference` is the cell reference you want to check.

**Example:** consider a scenario where you need to ensure that certain cells in a financial report are based on formulas rather than hardcoded values. If cell `D4` contains a formula like `=SUM(A1:A10)`, the formula `=ISFORMULA(D4)` will return `TRUE`. If `D4` contains a simple number or text, the function will return `FALSE`.

The `ISFORMULA()` function is particularly valuable when auditing or troubleshooting spreadsheets, as it helps you quickly identify which cells are calculated using formulas. This can prevent errors in manual data entry or ensure that calculations are correctly applied. Additionally, you can use `ISFORMULA()` in combination with conditional formatting to highlight all formula cells, making it easier to navigate complex worksheets.

### 5. ISLOGICAL

| Function         | Description                                              | Syntax              |
|------------------|----------------------------------------------------------|---------------------|
| **ISLOGICAL**    | Returns `TRUE` if `value` refers to a logical value.     | ISLOGICAL(value)    |

The `ISLOGICAL()` function in Excel is used to determine whether a cell contains a logical value. Logical values in Excel are `TRUE` and `FALSE`, often the result of comparison operations or logical tests. This function returns `TRUE` if the specific cell contains either `TRUE` or `FALSE`, and `FALSE` if it contains anything else. The **syntax** is `=ISLOGICAL(value)`, and the `value` is the cell reference or value you want to check.

**Example:** suppose you are working with a dataset where logical test are applied, and you want to identify which cells contain logical results. If the cell `E5` contains `TRUE`, the formula `=ISLOGICAL(E5)` will return `TRUE`. If `E5` contains a number, text, or is empty, the function will return `FALSE`.

The `ISLOGICAL()` function is particularly useful in scenario where you need to validate or analyze the results of logical test across a range of cells. For instance, you might want to ensure that specific cells are returning logical outcomes from the formulas such as `AND()`, `OR()`, or `IF()`. By combining `ISLOGICAL()` with other functions, you can create conditional checks or highlight cells that are expected to hold logical values, ensuring the integrity of your logical operations in Excel.

### 6. ISERROR

| Function         | Description                            | Syntax                            |
|------------------|----------------------------------------|-----------------------------------|
| **ISERROR**      | Returns `TRUE` if `value` refers to any error value (#N/A, #VALUE!,<br /> #REF!, #DIV/0!, #NUM!, #NAME?, or #NULL).      | ISERROR(value)      |

The `ISERROR()` function in Excel is a useful tool for detecting errors in a cell. It returns `TRUE` if the cell contains any type of error including `#N/A` and others, such as `#DIV/0!`, `#VALUE!`, `#REF!`, `#NAME?`, `#NUM!`, or `#NULL!`. If the cell contains no error, it returns `FALSE`. The **syntax** is `=ISERROR(value)`, and the `value`is the cell reference or formula you want to check.

**Example**: suppose you have a formula that might produce an error, such as division by zero in cell `F6` (`=A1/B1` where `B1` is 0). Using `=ISERROR(F6)` will return `TRUE` if `F6` contains an error like `#DIV/0!`. If `F6` contains a valid result or no error, it will return `FALSE`.

The `ISERROR()` function is particularly valuable for handling potential errors in large datasets. It is often combined with the `IF()` function to create error-handling formula. For example, `=IF(ISERROR(A1/B1), "Error in calculation", A1/B1)` can be used to replace an error with a custom message. This is a great way to ensure that errors in formula do not disrupt your data analysis or cause confusion in reports.

### 7. ISERR

| Function         | Description                            | Syntax                            |
|------------------|----------------------------------------|-----------------------------------|
| **ISERR**        | Returns `TRUE` if `value` refers to any error value except #N/A.    | ISERR(value)        |

The `ISERR()` function in Excel is used to detect all error types except `#N/A`. It returns `TRUE` if the cell contains errors such as `#DIV/0!`, `#VALUE!`, `#REF!`, `#NAME?`, `#NUM!`, or `#NULL!`, and `FALSE` otherwise. This is useful when you want to handle most errors but exclude cases where a value is simply not available (`#N/A)`. The **syntax** is `=ISERR(value)`, and the `value` is the cell reference or formula you want to check.

**Example**: if cell `G2` contains an invalid formula, like a division by zero (`=A1/B1` where `B1` is 0), and you want to check for all errors except `#N/A`, you can use the formula `=ISERR(G2)`. If `G2` results in an error like `#DIV/0!`, the function will return `TRUE`. However, if `G2` contains `#N/A`, the function will return `FALSE`.

The `ISERR()` function is particularly useful in situations where you want to identify and handle most errors in your dataset but ignore `#N/A` errors. For instance, 

### 8. ISNA

| Function         | Description                            | Syntax                            |
|------------------|----------------------------------------|-----------------------------------|
| **ISNA**         | Returns `TRUE` if `value` refers to the #N/A (value not available)<br /> error value.   | ISNA(value)        |

### 9. TYPE

| Function         | Description                            | Syntax                            |
|------------------|----------------------------------------|-----------------------------------|
| **TYPE**         | Returns the type of value.       |  TYPE(value)    |

### 10. INFO

| Function         | Description                            | Syntax                            |
|------------------|----------------------------------------|-----------------------------------|
| **INFO**         | Returns information about the current operating environment.   |  INFO(type_text)    |

### 11. N

| Function         | Description                            | Syntax                            |
|------------------|----------------------------------------|-----------------------------------|
| **N**            | Returns a value converted to a number   |  N(value)       |

### 12. CELL

| Function         | Description                            | Syntax                            |
|------------------|----------------------------------------|-----------------------------------|
| **CELL**         | Returns information about the formatting, location, or contents of<br /> a cell.   |  CELL(info_type, [reference])    | 


___

## **Summary**




___

For more useful functions in Excel, please refer the following links:

- [Top Useful Functions in EXCEL](/posts/top-useful-functions-in-excel/)

  - [Top 10 Date and Time Functions in Excel I learned](/posts/top-10-data-and-time-functions-in-excel-i-learned)
  - [Top 6 Important Logical Functions in Excel You need to Know About](/posts/top-6-important-logical-functions-in-excel-you-need-to-know-about)
  - [Top 12 Information Functions in Excel You Should Know](/posts/top-12-information-functions-in-excel-you-should-know)
  - [Top 6 Best Lookup Functions in Excel](/posts/top-6-best-lookup-functions-in-excel)
  - [Top 6 Useful Functions for Financial Operations in Excel](/posts/top-6-useful-functions-for-financial-operations-in-excel)
  - [Top 11 Basic Functions for Mathematical Modeling in Excel](/posts/top-11-basic-functions-for-mathematical-modeling-in-excel)
  - [Top 12 Advanced Excel Functions for Statistical Operations](/posts/top-12-advanced-excel-functions-for-statistical-operations)
  - [Top 12 Most Useful Text Functions in Excel You Should Know](/posts/top-12-most-useful-text-functions-in-excel-you-should-know)

