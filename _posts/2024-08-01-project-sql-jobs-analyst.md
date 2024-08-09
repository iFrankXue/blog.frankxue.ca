---
title: Project SQL Jobs Analyst
description: Examples of text, typography, math equations, diagrams, flowcharts, pictures, videos, and more.
author: Frank
date: 2024-08-01 11:10:00 -0700
categories: [Projects, SQL]
tags: [sql, postgreSQL, github]
pin: true
math: true
mermaid: true
---

# Introduction

This is my first 📊 data analysis project with sql, following the steps of the tutorial video "[SQL for Data Analytics - Learn SQL in 4 Hours](https://www.youtube.com/watch?v=7mz73uXD9DA)" uploaded by 👨[Luke Barousse](https://github.com/lukebarousse). 👍 Thanks to this fantastic tutorial video, I steped into the whole process of a project. Meanwhile, I also engaged with SQLite 📊 and PostgreSQL 🐘 with the first time.

This project mainly focus on the datasets of job market. Keeping eye on data analyst roles, this project explores 💰 top-paying jobs, 🔥 in-demand skills, and where 📈 high demand meets highsalary in data analytics.

For detail sql files, please visit 🔍 here: [Project sql folder](/project_sql/).

# Background

This project analyzes job market data📊, focusing on data analyst positions. It aims to identify top-paying jobs, valuable skills, and high-demand qualifications to aid job seekers, employers, and educators.

The dataset of this project comes from [Stackoverflow](https://stackoverflow.com)'s [2023 Developer Survey](https://survey.stackoverflow.co/2023/). The CSV files📃 are available at my [Google Drive](https://drive.google.com/drive/folders/1XGe4dxWJeZyD6lN8oWD-rC6VJ9Pyb2OT?usp=share_link)

# Tools I Used

Following this tutorial, I enhanced some skills and get some new skills for the first time. For detial, the following tools are engaged in this project:

- **SQL**: The backbone of this project, I used sql as the mian method to fullfill the whole analysis steps. It covers the basic sql knowledges to advanced skills.
- **PostgreSQL**: As it showed in "[2023 Developer Survey](https://survey.stackoverflow.co/2023/)", PostgreSQL is the most popular Database Management Tool. I used PostgreSQL to handle the job posting data.
- **Visual Studio Code**: This is the most used coding software in recent years, and with the help of the SQLTools extension, VS Code can make the query experience much more easy and handy.
- **Git & GitHub**: It is important to make version control during programming procedures. Git and GitHub are essential to meet this requirement.

# The Analysis

Each query for this project aimed to investigating specific aspects of the data analyst job market.
Here's how I approached each question:

### 1. Top Paying Data Analyst Jobs

This step identify the highest-paying roles. I filtered data analyst positions by average yeraly salary and location, focusing on remote jobs. This query highlights the high paying opportunities in the field.

```sql
SELECT
    job_id,
    job_title,
    job_location,
    job_schedule_type,
    salary_year_avg,
    job_posted_date::DATE,
    name AS company_name
FROM
    job_postings_fact
LEFT JOIN company_dim ON job_postings_fact.company_id = company_dim.company_id
WHERE
    job_title_short = 'Data Analyst' AND
    job_location = 'Anywhere' AND
    salary_year_avg IS NOT NULL
ORDER BY
    salary_year_avg DESC
LIMIT 10
```

Here's the breakdown of the top data analyst jobs in 2023:

- **High Compensation for Leadership Roles**: **Director of Analytics, Associate Director - Data Insights**: Leadership positions command higher salaries, reflecting the value placed on strategic oversight and decision-making in analytics.
- **Remote and Flexible Work Arrangements**: Many high-paying roles are listed as "Anywhere" or offer hybrid/remote options, indicating a growing trend towards flexibility in work locations, especially in the tech and data fields.
- **Diverse Industry Applications**: Companies like **Meta, AT&T, Pinterest, and SmartAsset** highlight that data analysis is a critical function across various industries, from social media and telecommunications to financial services and marketing.

![Top Paying Roles](assets/1_top_paying_jobs.png)
_Bar graph visualizing the salary for the top 10 salaries for data analysts; ChartGPT generated this graph from my SQL query results._

### 2. Top Paying Job Skills

The purpose of this query is to find what skills are required fo the top-pyaing Data Analyst jobs. In order to find out this result, I used the result of query 1 as a CTE(Common Table Expression), and then `INNER JOIN` with `skills_job_dim` and `skill_dim`. Finnaly, I can find the top paying jobs related to specific skill name.

```sql
WITH top_paying_jobs AS (
    SELECT
        job_id,
        job_title,
        salary_year_avg,
        name AS company_name
    FROM
        job_postings_fact
    LEFT JOIN company_dim ON job_postings_fact.company_id = company_dim.company_id
    WHERE
        job_title_short = 'Data Analyst' AND
        job_location = 'Anywhere' AND
        salary_year_avg IS NOT NULL
    ORDER BY
        salary_year_avg DESC
    LIMIT 10
)

SELECT
    top_paying_jobs.*,
    skills
FROM
    top_paying_jobs
INNER JOIN skills_job_dim ON top_paying_jobs.job_id = skills_job_dim.job_id
INNER JOIN skills_dim ON skills_job_dim.skill_id = skills_dim.skill_id
ORDER BY
    salary_year_avg DESC
```

Here's the breakdown of the most demanded skills for data analysts in 2023, based on job postings:
**_SQL_**: Essential across all top-paying jobs with count of 14.
**_Python_**: Highly valued for data analysis and scripting with abold count of 11.
**_Tableau_**: Important for data visualization and highly recommended for data analyst with a bold count of 8. Other skills like **_R_**, **_Snowflake_**, **_Pandas_**, and **_Excel_** show varying degrees of demand.

![Top 10 Paying Job Skills](/assets/2_top_paying_jobs_skills.png)
_Bar graph visualizing the count of skills for the top 10 paying jobs for data analysts; ChartGPT generated this graph from my SQL query results._

### 3. In-Demand Skills for Data Analysts

This query helped identify the skills most frequently requested in job postings, directing focus to areas with high demand.

```sql
SELECT
    skills,
    COUNT(skills_job_dim.job_id) AS demand_count

FROM job_postings_fact
INNER JOIN skills_job_dim ON job_postings_fact.job_id = skills_job_dim.job_id
INNER JOIN skills_dim ON skills_job_dim.skill_id = skills_dim.skill_id
WHERE
    job_title_short = 'Data Analyst' AND
--    job_location = 'Anywhere'
    job_work_from_home = TRUE
GROUP BY
    skills
ORDER BY
    demand_count DESC
lIMIT 5
```

Here's the breakdown of the most demanded skills for data analysts in 2023

- **SQL** and **Excel** remain fundamental, emphasizing the need for strong foundational skills in data processing and spreadsheet manipulation.
- Programming and Visualization Tools like **Python**, **Tableau**, and **Power BI** are essential, pointing towards the increasing importance of technical skills in data storytelling and decision support.

| Skills   | Demand Count |
| -------- | ------------ |
| SQL      | 7291         |
| Excel    | 4611         |
| Python   | 4330         |
| Tableau  | 3745         |
| Power BI | 2609         |

_Table of the demand for the top 5 skills in data analyst job postings._

### 4. Skills Based on Salary

Exploring the average salaries associated with different skills revealed wich skills are the highest paying.

```sql
SELECT
    skills,
    ROUND(AVG(salary_year_avg), 2) AS avg_salary
FROM job_postings_fact
INNER JOIN skills_job_dim ON job_postings_fact.job_id = skills_job_dim.job_id
INNER JOIN skills_dim ON skills_job_dim.skill_id = skills_dim.skill_id
WHERE
    job_title_short = 'Data Analyst'
    AND salary_year_avg IS NOT NULL
    AND job_work_from_home = TRUE
GROUP BY
    skills
ORDER BY
    avg_salary DESC
lIMIT 25
```

Here's the breakdown of the top paying jobs with different skills for data analysts in 2023.

- **Big Data and AI Tools Dominate**: High-paying skills include big data technologies (PySpark, Databricks) and AI platforms (Watson, DataRobot), highlighting a demand for expertise in managing large datasets and AI-driven solutions.
- **DevOps and Cloud Proficiency**: Tools like Bitbucket, GitLab, Jenkins, and Kubernetes are crucial, indicating a need for strong DevOps practices and cloud infrastructure knowledge.
- **Programming and Data Science Skills**: Python libraries (Pandas, Numpy, Scikit-learn) and languages like Swift and Golang are highly valued, reflecting the importance of coding and data manipulation in the field.

| Skills        | Average Salary ($) |
| ------------- | ------------------ |
| pyspark       | 208,172.25         |
| bitbucket     | 189,154.50         |
| couchbase     | 160,515.00         |
| watson        | 160,515.00         |
| datarobot     | 155,485.50         |
| gitlab        | 154,500.00         |
| swift         | 153,750.00         |
| jupyter       | 152,776.50         |
| pandas        | 151,821.33         |
| elasticsearch | 145,000.00         |

_Table of the top 10 skills based on average salary in data analyst job postings._

### 5. Most Optimal Skills to Learn

In this section, I will find out what are the optimal skills to learn for higher demands and top-paying opportunities, and offer a strategic focus for skill development.

```sql

SELECT
    skills_dim.skill_id,
    skills_dim.skills,
    COUNT(skills_job_dim.job_id) AS demand_count,
    ROUND(AVG(job_postings_fact.salary_year_avg), 2) AS avg_salary
FROM job_postings_fact
INNER JOIN skills_job_dim ON job_postings_fact.job_id = skills_job_dim.job_id
INNER JOIN skills_dim ON skills_job_dim.skill_id = skills_dim.skill_id
WHERE
    job_title_short = 'Data Analyst'
    AND job_work_from_home = TRUE
    AND salarY_year_avg IS NOT NULL
GROUP BY
    skills_dim.skill_id
HAVING
    COUNT(skills_job_dim.job_id) > 10
ORDER BY
    avg_salary DESC,
    demand_count DESC
LIMIT 25;
```

Here are some quick insights into the trends from the list of optimal skills for data analysts based on demand and average salary:

- **Cloud Platforms and Data Warehousing**: **Snowflake, Azure, AWS, BigQuery, Redshift**: High demand for cloud-based data warehousing and cloud platforms indicates a trend towards cloud computing and data storage solutions.
- **Data Visualization and BI Tools**: **Tableau, Looker, Qlik**: The prevalence of these tools reflects the importance of data visualization and business intelligence in translating data insights into actionable business strategies.
- **Core Programming and Data Technologies**: **Python, R, SQL Server, Java**: Core programming languages and data management technologies are in high demand, emphasizing the need for foundational skills in data manipulation, analysis, and database management.

| Skill ID | Skills     | Demand Count | Average Salary ($) |
| -------- | ---------- | ------------ | ------------------ |
| 8        | go         | 27           | 115,319.89         |
| 234      | confluence | 11           | 114,209.91         |
| 97       | hadoop     | 22           | 113,192.57         |
| 80       | snowflake  | 37           | 112,947.97         |
| 74       | azure      | 34           | 111,225.10         |
| 77       | bigquery   | 13           | 109,653.85         |
| 76       | aws        | 32           | 108,317.30         |
| 4        | java       | 17           | 106,906.44         |
| 194      | ssis       | 12           | 106,683.33         |
| 233      | jira       | 20           | 104,917.90         |

_Table of the top 10 optimal skills for data analyst based on demand and average salary in data analyst job postings._

# What I Learned

During the over 20 hours learning journey on job market data analysis, I have significantly enhanced my skills in dataset thinking and analysis and enpowered my skills in sql, VSCode,GitHub, etc.

✅ Firstly,I learned how to approach complex datasets methodically, undersatanding the importance of data quality, cleaning, and prepocessing.I gained insights into various analytical techniques and tools to derive meaningful insights from data.

✅ Secondly, I developed a comprehensive understanding of data collection processes. This experience has equipped my with the ability to manage data projects from inception to conclusion, ensuring data-driven decision-making and actionable outcomes.

✅ Thirdly, I acquired a range of technical skills, including SQL, PostgreSQL, VSCode, and GitHub, which have equipped me to tackle more challenging projects in the future.

# Conclusions

### Insights

From this data ananlysis process, several general insights emerged:

- **_Top-Paying Data Analyst Jobs_**: The top-paying jobs for data analysts that allow remote work offer a wide range of salaries, the highest at $650,000.00！
- **_Skills for Top-Paying Jobs_**: According to the query result of this step, high-paying jobs in Data Analyst field require advanced proficiency in SQL, suggesting it's a critical skill for earning a top salary.
- **_Most In-Demand Skills_**: SQL is also the most demanded skill in data analyst job market, thus making it essential for job seekers.
- **_Skills with Higher Salaries_**: Specialized skills, such as PySpark and Databricks in data technologies, Watson and DataRobot in AI platforms, are assocated with the highest average salaries, indicating a premium on niche expetise.
- **_Optimal Skills for Job Market Value_**: SQL leads the demand and offers for a high average salary, positioning it as one of the most optimal skills for data analysts to learn to maximize their maket value.

### Closing Thoughts

To be honest, I have learned a lot during this project step by step and be more confident to tackle problems with more challenging.

Thanks Luke again, for his dedicated job of offering numerous hours of tutorial videos for free.
