# Video Game Sales Analysis

## Dataset

You will be working with the following dataset: [Video Game Sales](https://www.kaggle.com/datasets/gregorut/videogamesales?resource=download)

📦 **Dataset Download Instructions**
1. Download the dataset ZIP file from the above link.
2. After downloading: Unzip the file to access vgsales.csv. Note the full file path to vgsales.csv — you'll need it in the next step.

🔍 **Challenge: Load the Data into DuckDB**
Using DBeaver and your DuckDB connection, how would you load the vgsales.csv file into a table so you can begin querying it?

## Business Question
How can game developers and publishers optimize their strategy to maximize global sales by understanding the performance of different game genres, platforms, and publishers?

*To answer the above question, use the following SQL queries to explore the dataset and address the following questions:*

Which genres contribute the most to global sales?

SQL:
```sql
SELECT Genre, SUM(Global_Sales) AS total_sales
FROM vgsales
GROUP BY Genre
ORDER BY total_sales DESC;

```
Findings: Action - 1751.18

```findings

```
Which platforms generate the highest global sales?

SQL:
```sql
SELECT Platform, ROUND(SUM(Global_Sales),2) AS total_sales
FROM vgsales
GROUP BY Platform
ORDER BY total_sales DESC; 
```
Findings: PS2 - 1255.64
```findings

```
Which publishers are the most successful in terms of global sales?

SQL:
```sql
SELECT Publisher, ROUND(SUM(Global_Sales),2) AS total_sales
FROM vgsales
GROUP BY Publisher
ORDER BY total_sales DESC
LIMIT 10;
```
Findings:Nintendo - 1786.56
```findings

```
How does success vary across regions (North America, Europe, Japan, Others)?

SQL:
```sql
SELECT 
    Genre,
    SUM(NA_Sales) AS NA,
    SUM(EU_Sales) AS EU,
    SUM(JP_Sales) AS JP,
    SUM(Other_Sales) AS Other
FROM vgsales
GROUP BY Genre
ORDER BY NA DESC;

SELECT 
    Genre,
    SUM(NA_Sales) AS NA,
    SUM(EU_Sales) AS EU,
    SUM(JP_Sales) AS JP,
    SUM(Other_Sales) AS Other
FROM vgsales
GROUP BY Genre
ORDER BY EU DESC;


SELECT 
    Genre,
    SUM(NA_Sales) AS NA,
    SUM(EU_Sales) AS EU,
    SUM(JP_Sales) AS JP,
    SUM(Other_Sales) AS Other
FROM vgsales
GROUP BY Genre
ORDER BY JP DESC;


SELECT 
    Genre,
    SUM(NA_Sales) AS NA,
    SUM(EU_Sales) AS EU,
    SUM(JP_Sales) AS JP,
    SUM(Other_Sales) AS Other
FROM vgsales
GROUP BY Genre
ORDER BY Other DESC;


SELECT 
    Genre,
    SUM(NA_Sales) AS NA,
    SUM(EU_Sales) AS EU,
    SUM(JP_Sales) AS JP,
    SUM(Other_Sales) AS Other
FROM vgsales
GROUP BY Genre
ORDER BY EU DESC;
```
Findings: 
NA
Action - 877.83
EU
Action - 525
JP
Role-Playing - 352.31
Other
Action - 187.38


```findings

```
What are the trends over time in game sales by genre and platform?

SQL:
```sql
SELECT Year, Genre, SUM(Global_Sales) AS total_sales
FROM vgsales
WHERE Year IS NOT NULL
GROUP BY Year, Genre
ORDER BY Year, total_sales DESC;
```
Findings: Trend is PS3 between 2010
```findings

```
Which platforms are most successful for specific genres?

SQL:
```sql
SELECT Platform, Genre, SUM(Global_Sales) AS total_sales
FROM vgsales
GROUP BY Platform, Genre
ORDER BY Genre, total_sales DESC;

```
Findings: PS3 Action - 307.88 
          DS Adventure - 47.29
          PS2 Fighting - 92.60
          Wii Misc - 221.06
          NES Platform - 95.78
          DS Puzzle - 84.29
          PS2 Racing 156.28
          
```findings

```
## Deliverables:
- SQL Queries: Provide all the SQL queries you used to answer the business questions.
- Summary of Findings: For each question, summarise your key findings and recommendations based on your analysis.

## Submission

- Submit the GitHub URL of your assignment to NTU black board.
- Should you reference the work of your classmate(s) or online resources, give them credit by adding either the name of your classmate or URL.
