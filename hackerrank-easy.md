1.  Query all columns for all American cities in the CITY table with populations larger than 100000. The CountryCode for America is USA.

```sql
SELECT *
FROM CITY   
WHERE POPULATION > 100000 AND CountryCode = 'USA';
```

2. Query the NAME field for all American cities in the CITY table with populations larger than 120000. The CountryCode for America is USA.

```sql
SELECT NAME
FROM CITY
WHERE COUNTRYCODE = 'USA' AND POPULATION > 120000;
```

3. Query all columns (attributes) for every row in the CITY table.
The CITY table is described as follows:
```sql
SELECT * 
FROM CITY
```

4. Query all columns for a city in CITY with the ID 1661.

```sql
SELECT *
FROM CITY WHERE ID = 1661;
```

5.Query all attributes of every Japanese city in the CITY table. The COUNTRYCODE for Japan is JPN.

```sql
SELECT *
FROM CITY
WHERE COUNTRYCODE = 'JPN';
```

6. Query the names of all the Japanese cities in the CITY table. The COUNTRYCODE for Japan is JPN.

```sql
SELECT NAME
FROM CITY
WHERE COUNTRYCODE = 'JPN';
```

7.Query a list of CITY and STATE from the STATION table.

```sql
SELECT CITY, STATE
FROM STATION;
```

8. Query a list of CITY names from STATION for cities that have an even ID number. Print the results in any order, but exclude duplicates from the answer.

```sql
SELECT DISTINCT CITY
FROM STATION
WHERE ID % 2 = 0
```

9.Find the difference between the total number of CITY entries in the table and the number of distinct CITY entries in the table.

```sql
SELECT COUNT(CITY) - COUNT(DISTINCT CITY)
FROM STATION
```

10. Query the two cities in STATION with the shortest and longest CITY names, as well as their respective lengths (i.e.: number of characters in the name). If there is more than one smallest or largest city, choose the one that comes first when ordered alphabetically.

```sql
SELECT CITY, LENGTH(CITY) FROM STATION ORDER BY LENGTH(CITY), CITY LIMIT 1;
SELECT CITY, LENGTH(CITY) FROM STATION ORDER BY LENGTH(CITY) DESC, CITY LIMIT 1;
```

11. Query the list of CITY names starting with vowels (i.e., a, e, i, o, or u) from STATION. Your result cannot contain duplicates.

```sql
SELECT DISTINCT CITY
FROM STATION
WHERE UPPER(CITY) LIKE 'A%' 
      OR UPPER(CITY) LIKE 'E%'
      OR UPPER(CITY) LIKE 'I%'
      OR UPPER(CITY) LIKE 'O%'
      OR UPPER(CITY) LIKE 'U%'
ORDER BY CITY ASC;
```

```sql
SELECT DISTINCT CITY
FROM STATION
WHERE LEFT(UPPER(CITY),1) IN ('A','E','I','O','U')
ORDER BY CITY ASC;
```


12. Query the list of CITY names ending with vowels (a, e, i, o, u) from STATION. Your result cannot contain duplicates.
      
```sql
SELECT DISTINCT CITY
FROM STATION
WHERE UPPER(CITY) LIKE '%A' 
      OR UPPER(CITY) LIKE '%E'
      OR UPPER(CITY) LIKE '%I'
      OR UPPER(CITY) LIKE '%O'
      OR UPPER(CITY) LIKE '%U'
ORDER BY CITY ASC;
```

```sql
SELECT DISTINCT CITY
FROM STATION
WHERE RIGHT(UPPER(CITY),1) IN ('A','E','I','O','U')
ORDER BY CITY ASC;
```

13. Query the list of CITY names from STATION which have vowels (i.e., a, e, i, o, and u) as both their first and last characters. Your result cannot contain duplicates.


```sql
SELECT DISTINCT CITY
FROM STATION
WHERE LEFT(UPPER(CITY),1) IN ('A','E','I','O','U') AND
      RIGHT(UPPER(CITY),1) IN ('A','E','I','O','U')
ORDER BY CITY ASC;
```


14.  Query the list of CITY names from STATION that do not start with vowels. Your result cannot contain duplicates.


```sql
SELECT DISTINCT CITY 
FROM STATION
WHERE UPPER(LEFT(CITY,1)) NOT IN ('A','E','I','O','U')
```

15. Query the list of CITY names from STATION that do not end with vowels. Your result cannot contain duplicates.

```sql
SELECT DISTINCT CITY 
FROM STATION
WHERE UPPER(RIGHT(CITY,1)) NOT IN ('A','E','I','O','U');
```


16. Query the list of CITY names from STATION that either do not start with vowels or do not end with vowels. Your result cannot contain duplicates.

```sql
SELECT DISTINCT CITY 
FROM STATION
WHERE UPPER(RIGHT(CITY,1)) NOT IN ('A','E','I','O','U') 
       OR  UPPER(LEFT(CITY,1)) NOT IN ('A','E','I','O','U');
```


17. Query the list of CITY names from STATION that do not start with vowels and do not end with vowels. Your result cannot contain duplicates.

```sql
SELECT DISTINCT CITY 
FROM STATION
WHERE UPPER(RIGHT(CITY,1)) NOT IN ('A','E','I','O','U') 
      AND  UPPER(LEFT(CITY,1)) NOT IN ('A','E','I','O','U');
```

18.  Query the Name of any student in STUDENTS who scored higher than  Marks. Order your output by the last three characters of each name. If two or more students both have names ending in the same last three characters (i.e.: Bobby, Robby, etc.), secondary sort them by ascending ID.

```sql
SELECT Name
FROM STUDENTS
WHERE Marks > 75
ORDER BY RIGHT(Name,3), ID;
```

19. Write a query that prints a list of employee names (i.e.: the name attribute) from the Employee table in alphabetical order.

```sql
SELECT name
FROM employee
ORDER BY name;
```

20. Write a query that prints a list of employee names (i.e.: the name attribute) for employees in Employee having a salary greater than $2000  per month who have been employees for less than  10 months. Sort your result by ascending employee_id.

```sql
SELECT name
FROM employee
WHERE salary > 2000 AND months < 10
ORDER BY employee_id;
```


21.Write a query identifying the type of each record in the TRIANGLES table using its three side lengths. Output one of the following statements for each record in the table:
- Equilateral: It's a triangle with 3 sides of equal length.
- Isosceles: It's a triangle with 2  sides of equal length.
- Scalene: It's a triangle with 3 sides of differing lengths.
- Not A Triangle: The given values of A, B, and C don't form a triangle.


```sql
SELECT
CASE
    WHEN A+B <= C OR B+C<= A OR C+A <= B THEN 'Not A Triangle'
    WHEN A = B AND B = C THEN 'Equilateral'
    WHEN (A = B AND B!=C) OR (C = B AND C!=A) OR (C=A AND C!=B)  THEN 'Isosceles' 
    ELSE 'Scalene'
END
    FROM TRIANGLES;
```
