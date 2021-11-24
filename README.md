# SQL-cheat-sheet
```
SQL order of excecution: from>where>groupby>having>select>order by>limit
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


-- Select name fields (with alias) and region 
SELECT cities.name AS city ,countries.name AS country,countries.region AS region
FROM cities
  INNER JOIN countries
    ON cities.country_code = countries.code;
    
-- Select fields
SELECT c.code, name, region, e.year, fertility_rate, unemployment_rate
  -- From countries (alias as c)
  FROM countries AS c
  -- Join to populations (as p)
  INNER JOIN populations AS p
    -- Match on country code
    ON c.code = p.country_code
  -- Join to economies (as e)
  INNER JOIN economies AS e
    -- Match on country code and year
    ON e.code = p.country_code AND e.year = p.year
    
-- Select fields
SELECT c.name AS country,c.continent, l.name AS language, l.official
  FROM countries AS c
    INNER JOIN languages AS l
      USING (code)

-- Select fields with aliases
SELECT p1.country_code,
       p1.size AS size2010,
       p2.size AS size2015
-- From populations (alias as p1)
FROM populations as p1
  -- Join to itself (alias as p2)
  INNER JOIN populations as p2
    -- Match on country code
    ON p1.country_code = p2.country_code
        -- and year (with calculation)
        AND p1.year = p2.year-5
```
