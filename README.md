# SQL-cheat-sheet
```
SELECT title,release_year
FROM films
LIMIT 10
WHERE release_year=2016


SELECT COUNT(language)
FROM films
WHERE language = 'Hindi'

SELECT * FROM films
Where language = 'Spanish' 
AND release_year >2000
AND release_year <2010

SELECT title,release_year 
FROM films 
WHERE language in ('English', 'Spanish', 'French') 

SELECT AVG(gross)
FROM films
WHERE title like 'A%'

SELECT MAX(gross)
FROM films
WHERE release_year BETWEEN 2000 AND 2012

SELECT country,release_year, MIN(gross)
FROM films
GROUP BY country,release_year
ORDER BY country,release_year

SELECT release_year, AVG(budget) AS avg_budget, AVG(gross) AS avg_gross
FROM films
WHERE release_year > 1990
GROUP BY release_year
HAVING AVG(budget) > 60000000
ORDER BY AVG(gross) DESC;
```
