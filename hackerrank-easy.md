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

22. Query a count of the number of cities in CITY having a Population larger than 100000.

```sql
SELECT COUNT(NAME)
FROM CITY
WHERE POPULATION > 100000;
```

23. Query the total population of all cities in CITY where District is California.

```sql
SELECT SUM(POPULATION)
FROM CITY
WHERE DISTRICT = 'California'
```


24.Query the average population of all cities in CITY where District is California.

```sql
SELECT AVG(POPULATION)
FROM CITY
WHERE DISTRICT = 'California';
```


25. Query the average population for all cities in CITY, rounded down to the nearest integer.

```sql
SELECT FLOOR(AVG(POPULATION))
FROM CITY;
```

26. Query the sum of the populations for all Japanese cities in CITY. The COUNTRYCODE for Japan is JPN.

```sql
SELECT SUM(POPULATION)
FROM CITY
WHERE COUNTRYCODE = 'JPN';
```

27. Query the difference between the maximum and minimum populations in CITY.

```sql
SELECT (MAX(POPULATION) - MIN(POPULATION))
FROM CITY;
```

28. We define an employee's total earnings to be their monthly SALARY * MONTHS worked, and the maximum total earnings to be the maximum total earnings for any employee in the Employee table. Write a query to find the maximum total earnings for all employees as well as the total number of employees who have maximum total earnings $2000. Then print these values as  space-separated integers.
```sql
SELECT MAX(SALARY * MONTHS) AS SALARY, COUNT(*)
FROM EMPLOYEE
GROUP BY SALARY
ORDER BY SALARY DESC
LIMIT 1;
```

29. Query the following two values from the STATION table:
The sum of all values in LAT_N rounded to a scale of  decimal places.
The sum of all values in LONG_W rounded to a scale of  decimal places.
```sql
SELECT ROUND(SUM(LAT_N),2), ROUND(SUM(LONG_W),2)
FROM STATION;
```

30. Query the sum of Northern Latitudes (LAT_N) from STATION having values greater than 38.7880 and less than 137.2345 . Truncate your answer to  decimal places.

```sql
SELECT ROUND(SUM(LAT_N),4)
FROM STATION
WHERE LAT_N BETWEEN 38.7880 AND 137.2345
```

31. Query the greatest value of the Northern Latitudes (LAT_N) from STATION that is less than 137.2345. Truncate your answer to 4  decimal places.

```sql
SELECT ROUND(MAX(LAT_N),4)
FROM STATION
WHERE LAT_N < 137.2345
```

32. Query the Western Longitude (LONG_W) for the largest Northern Latitude (LAT_N) in STATION that is less than 137.2345 . Round your answer to 4 decimal places.

```sql
SELECT ROUND(MAX(LAT_N),4)
FROM STATION
WHERE LAT_N < 137.2345
```

33. Query the smallest Northern Latitude (LAT_N) from STATION that is greater than 38.7880 . Round your answer to 4 decimal places.

```sql
SELECT ROUND(MIN(LAT_N),4)
FROM STATION
WHERE LAT_N > 38.7780;
```

34.   Query the Western Longitude (LONG_W)where the smallest Northern Latitude (LAT_N) in STATION is greater than 38.7780 . Round your answer to 4 decimal places.

```sql
SELECT ROUND(LONG_W,4)
FROM STATION
WHERE LAT_N IN(SELECT MIN(LAT_N)
      		FROM STATION 
      		WHERE LAT_N > 38.7780);
```

35.Given the CITY and COUNTRY tables, query the sum of the populations of all cities where the CONTINENT is 'Asia'.

```sql
SELECT SUM(CITY.POPULATION)
FROM CITY
JOIN COUNTRY ON CITY.COUNTRYCODE = COUNTRY.CODE
WHERE CONTINENT = 'Asia'
```

36.Given the CITY and COUNTRY tables, query the names of all cities where the CONTINENT is 'Africa'.

```sql
SELECT CITY.NAME
FROM CITY
JOIN COUNTRY ON CITY.COUNTRYCODE = COUNTRY.CODE
WHERE CONTINENT ='Africa'
```

37. Given the CITY and COUNTRY tables, query the names of all the continents (COUNTRY.Continent) and their respective average city populations (CITY.Population) rounded down to the nearest integer.

```sql
SELECT COUNTRY.CONTINENT, FLOOR(AVG(CITY.POPULATION))
FROM CITY 
JOIN COUNTRY ON CITY.COUNTRYCODE = COUNTRY.CODE
GROUP BY CONTINENT
```

38.Samantha was tasked with calculating the average monthly salaries for all employees in the EMPLOYEES table, but did not realize her keyboard's  key was broken until after completing the calculation. She wants your help finding the difference between her miscalculation (using salaries with any zeros removed), and the actual average salary.
Write a query calculating the amount of error (i.e.:  average monthly salaries), and round it up to the next integer.

```sql
SELECT CEIL(AVG(SALARY) - AVG(REPLACE(SALARY, '0','')))
FROM EMPLOYEES;
```
