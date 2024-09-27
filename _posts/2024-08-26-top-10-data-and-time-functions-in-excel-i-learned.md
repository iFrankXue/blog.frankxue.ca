---
title: Top 10 Date and Time Functions in Excel I Learned
description: Date and time functions are essential when working with dates, times, and durations in Excel, offering a wide range of capabilities for handling temporal data. In this article, I list top 10 most useful functions in "Date and Time".
author: frank
date: 2024-08-26 15:20:00 -0700
categories: [Excel, functions]
tags: [excel, function, date, time]
pin: false
math: false
mermaid: true
image:
  path: /assets/img/2024/08-25-title-time-clock-calendar.png
  lqip: /assets/img/2024/08-25-title-time-clock-calendar.png # or base64 URI
  alt: Top 10 date and time functions in Excel
---

## **Introduction**

Excel is a powerful tool for managing and analyzing data, and one of its most essential features is the ability to handle dates and times with precision and flexibility. Whether you're calculating project timelines, tracking important dates, or managing schedules, Excel's date and time functions are indispensable. In this post, we'll explore some of the most useful **date and time functions** in Excel, including **[`TODAY()`](#1-today)**, **[`NOW()`](#2-now)**, **[`DATE()`](#3-date)**, **[`DATEDIF()`](#4-datedif)**, **[`YEAR()`](#5-year)**, **[`MONTH()`](#6-month)**, **[`DAY()`](#7-day)**, **[`EOMONTH()`](#8-eomonth)**, **[`WEEKDAY()`](#9-weekday)**, and **[`NETWORKDAYS()`](#10-networkdays)**. Each of these functions serves a unique purpose, from simple returning the current date and time to performing more complex calculations like finding the number of working days between two dates. 

I'll walk you through how each function works, provide examples of their practical application, and share tips to help you make the most of these tools in your daily work. Whether you're a beginner looking to get started with Excel or an experienced user aiming to enhance your efficiency, understanding these functions will significantly improve your ability to manage date and time-related tasks.

___

## **Functions**

### 1. TODAY

| Function       | Description                            | Syntax                            |
|----------------|----------------------------------------|-----------------------------------|
| **TODAY**      | Returns the current system date.       | TODAY() - with no arguments.      |

The **TODAY()** function in Excel is a simple but powerful tool that **automatically** gives you the **current date**. You don't have to type in the date manually - just use `TODAY()`, and Excel will display today's date, updating it **every time** you open the spreadsheet. This function is great for **tracking** when you last update a file, creating deadlines, or calculating how many days have passed since a certain date. It is like having **a built-in calendar** that always stays current!

![Excel function: TODAY](/assets/img/2024/08-26-excel-function-today.png){: .w-75 .shadow .rounded-10 w='1212' h='668' }

{: width="500" .w-30 }

It has **no argument**, you just need to enter the function with open and closed parenthesis.

### 2. NOW

| Function       | Description                            | Syntax                            |
|----------------|----------------------------------------|-----------------------------------|
| **NOW**        | Returns the current date and time.     | NOW() - with no arguments.        |

The **NOW()** function in Excel is similar to the `TODAY()` function, but it gives you **both the current date and the exact time**. When you use `NOW()`, Excel displays the current date along with the current time down to the minute, and it updates this information **every time** you open the spreadsheet or make a change. This function is perfect for when you need a timestamp for when data was entered or modified, or when you need to **track time-sensitive information**. It is like having **a live clock and calendar** right in your Excel Sheet!

![Excel function: NOW](/assets/img/2024/08-26-excel-function-now.png){: .w-75 .shadow .rounded-10 w='1212' h='668' }


It has **no argument**, you just need to enter this function with open and closed parenthesis.

### 3. DATE

| Function       | Description                                                  | Syntax                            |
|----------------|--------------------------------------------------------------|-----------------------------------|
| **DATE**       | Returns a date based on the arguments: year, month and day.  | DATE(year,month,day)              |

The **Date()** function in Excel is used to create a date by combining individual **year**, **month**, and **day** value into a single, valid date. Instead of typing the date manually, you can use `DATE(year, month, day)` to construct it. 

For example, if you have the year in one cell, the month in another, and the day in a third, you can use `DATE()` to combine them into on complete date. 

![Excel function: DATE](/assets/img/2024/08-26-excel-function-date.png){: .w-75 .shadow .rounded-10 w='1212' h='668' }

This function is especially useful when dealing with data where dates are split into separate parts, or when you want to ensure that the date is **formatted correctly** according to Excel's date system. It helps you build dates dynamically based on different inputs.

### 4. DATEDIF

| Function       | Description                            | Syntax                            |
|----------------|----------------------------------------|-----------------------------------|
| **DATEDIF**    | Calculates the number of days, months, or years between <br />two dates.  | DATEDIF(start_date,end_date,unit)    |

The **DATEDIF()** function in Excel is a useful tool for calculating the difference between two dates. It tells you how much time has passed between a start date and an end date, an you can specify whether you want the result in days, months, or years. The function is written as `DATEDIF(start_date, end_date, unit)`, where "unit" can be "d" for days, "m" for months, or "y" for years.

For example, if you want to find out how many days are between two dates, you'd use `DATEDIF(start_date, end_date, "d")`. Similarly, if you need to know the number of complete months or years between the two dates, you can use "m" or "y" as the unit.

![Excel function: DATEDIF](/assets/img/2024/08-26-excel-function-datedif.png){: .w-75 .shadow .rounded-10 w='1212' h='668' }

This function is particularly handy for calculating ages, the duration of projects, or any situation where you need to measure the **time span** between two dates. It's a versatile function that helps you manage and analyze time-related data effectively!

### 5. YEAR

| Function      | Description                                             | Syntax                      |
|---------------|---------------------------------------------------------|-----------------------------|
| **YEAR**      | Returns the year of a date.                             | YEAR(serial_number)         |

The **YEAR()** function in Excel is a simple yet powerful tool that **extracts the year** from a given date. When you use `YEAR(date)`, Excel takes the date you provide and returns just the **year portion** of it as a **four-digit** number.

For example, if you have a date like "15-Aug-2024" in a cell, using `YEAR()` on that cell will give you "2024". 

![Excel function: YEAR](/assets/img/2024/08-26-excel-function-year.png){: .w-75 .shadow .rounded-10 w='1212' h='668' }

This function is particularly useful when you need to analyze or group data by year, such as tracking annual trends, organizing records by year, or calculating how many years have passed since a certain event. It helps you work with data information more flexibly by isolating just the year from a full date.

### 6. MONTH

| Function      | Description                                             | Syntax                      |
|---------------|---------------------------------------------------------|-----------------------------|
| **MONTH**     | Returns the month of a date.                            | MONTH(serial_number)        |

The **MONTH()** function in Excel is used to extract the **month** from a specific date, returning it as a number between 1 (for January) and 12 (for December). When you use `MONTH(date)`, Excel takes the date you provide and returns just the month portion of it.

For instance, if you have a date like "15-Aug-2024" in a cell, using `MONTH()` on that cell will give you "8", because August is the 8th month of the year. 

![Excel function: MONTH](/assets/img/2024/08-26-excel-function-month.png){: .w-75 .shadow .rounded-10 w='1212' h='668' }

This function is helpful when you need to focus on or analyze data by month, such as identifying monthly trends, organizing data into monthly periods, or simply pulling out the month from a complete date. It allows you to work with dates in a more detailed and precise way by isolating just the month from a full date.

### 7. DAY

| Function      | Description                                             | Syntax                      |
|---------------|---------------------------------------------------------|-----------------------------|
| **DAY**       | Returns the day of a date.                              | DAY(serial_number)          |

The **DAY()** function in Excel is used to extract the day of the month from a given date, returning it as a number between 1 and 31, depending on the date. When you use `DAY(date)`, Excel takes the date you provide and gives you just the day portion of it.

For example, if you have a date like "15-Aug-2024" in a cell, using `DAY()` on that cell will give you "15", because it's the 15th day of the month. 

![Excel function: DAY](/assets/img/2024/08-26-excel-function-day.png){: .w-75 .shadow .rounded-10 w='1212' h='668' }

This function is especially useful when you need to focus on or analyze data based on specific days of the month, such as identify patterns on particular days, organizing events by day, or simply pulling out the day from a full date. It lets you work with the day component of dates separately, making it easier to manage and analyze data-specific data.


### 8. EOMONTH

| Function      | Description                                             | Syntax                      |
|---------------|---------------------------------------------------------|-----------------------------|
| **EOMONTH**   | Returns the serial number for the last day of the month <br /> that is the indicated number of months before or after <br />start_date. | EOMONTH(start_date, months)  |

The **EOMONTH()** function in Excel is used to find the last day of a month, either in the same month as a given date or in a specified number of months before or after that date. The function is written as `EOMONTH(start_date, months)`, where `start_date` is the date you're starting with, and `months` is the number of months you want to move forward or backward.

For example, if you want to find the last day of the month for "15-Aug-2024", you would use `EOMONTH("15-Aug-2024", 0)`, and Excel would return "31-Aug-2024". If you wanted to find the last day of the month two months after August 2024, you would use `EOMONTH("15-Aug-2024", 2)`, and Excel would give you "30-Oct-2024".

![Excel function: EOMONTH](/assets/img/2024/08-26-excel-function-eomonth.png){: .w-75 .shadow .rounded-10 w='1212' h='668' }

This function is particularly useful for financial analysis, or any situation where you need to determine the end of a month quickly. It helps you manage month-end dates efficiently, especially when working with data that spans multiple months or when you need to calculate due dates, billing cycles, or project timelines.

### 9. WEEKDAY

| Function         | Description                                          | Syntax                      |
|------------------|------------------------------------------------------|-----------------------------|
| **WEEKDAY**      | Returns the day of the week corresponding to a date. <br />The day is given as an integer, ranging from 1 (Sunday) <br />to 7 (Saturday), by default. | WEEKDAY(serial_number,<br />[return_type])     |

The **WEEKDAY()** function in Excel is used to determine the day of the week for a given date, returning a number that represents that day. By default, `WEEKDAY()` returns a number between 1 and 7, where 1 corresponds to Sunday, 2 to Monday, and so on, up to 7 for Saturday. The function is written as `WEEKDAY(date, [return_type])`, where `date` is the date you want to analyze, and `return_type` is an optional argument that lets you choose which day you want to start the week on.

For example, if you use `WEEKDAY("15-Aug-2024")`, Excel will return "5", meaning that August 15, 2024, falls on a Thursday (since the default setting considers Sunday as 1). If you want the week to start on Monday instead, you could use `WEEKDAY("15-Aug_2024", 2), and Excel would return "4", indicating that Thursday is the fourth day of the week when counting from Monday.

![Excel function: WEEKDAY](/assets/img/2024/08-26-excel-function-weekday.png){: .w-75 .shadow .rounded-10 w='1212' h='668' }

This function is particularly useful when you need to categorize or analyze data based on the day of the week, such as finding out how many sales occurred on weekends, scheduling tasks for specific days, or simply determining what day a certain date falls on. It gives you the flexibility to work with dates in a more detailed way by identifying the exact day of the week.

### 10. NETWORKDAYS

| Function         | Description                                          | Syntax                      |
|------------------|------------------------------------------------------|-----------------------------|
| **NETWORKDAYS**  | Returns the number of whole working days between <br />start_date and end_date. | NETWORKDAYS(start_date, <br />end_date, [holidays])   |

The **NETWORKDAYS()** function in Excel is used to calculate the number of working days between two dates, excluding weekends and optionally specified holidays. This function is particularly useful for project management, scheduling, and any situation where you need to account for business days rather than just calendar days.

The function is written as `NETWORKDAYS(start_date, end_date, [holidays])`, where:
- `start_date` is the starting date.
- `end_date` is the ending date.
- `[holidays]` is an optional range of dates that you want to exclude from the count, such as public holidays.

For example, if you want to find out how many working days there are between "01-Aug-2024" and "15-Aug-2024", you would use  `NETWORKDAYS("01-Aug-2024", "15-Aug-2024")`. Excel would exclude the weekends and give you the total number of weekdays in that period. If you have specific holidays within that range, you can list them in a separate range and include that range in the function to exclude those days as well.

![Excel function: NETWORKDAYS](/assets/img/2024/08-26-excel-function-networkdays.png){: .w-75 .shadow .rounded-10 w='1212' h='668' }

This function is particularly useful for calculating deadlines, determining the duration of tasks in business days, or planning schedules that need to consider only working days. It helps ensure that your calculations are accurate by taking into account the non-working days automatically.

___

## **Summary**

All in conclusion, Excel's date and time functions, such as `TODAY()`, `NOW()`, `DATE()`, `DATEDIF()`, `YEAR()`, `MONTH()`, `DAY()`, `EOMONTH()`, `WEEKDAY()`, and `NETWORKDAYS()` are powerful tolls for efficiently managing and analyzing temporal data. From calculating the current date and time to determining the number of working days between two dates, these functions can simplify complex tasks and enhance your productivity. Understanding how to use them effectively will help you better handle time-sensitive data and streamline your work in Excel.

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

