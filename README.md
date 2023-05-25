# SQL Practice

## Preface
I already know a lot of SQL so this will just be a good place to take notes for things I'd like to remember.

## Beginner Notes
SQL - Structured Query Language

```CREATE TABLE``` - creates a new table

```INSERT INTO``` - adds a new row to a table

```SELECT``` - queries data from a table

```ALTER TABLE``` - changes an existing table

```UPDATE``` - edits a row in a table

```DELETE FROM``` - deletes row from a table

## Queries

You can seperate columns in a query by using a comma like so:
```
SELECT column1, column2
FROM table_name;
```
### Aliasing
You can alias column names by doing this:
```
SELECT name AS 'Titles'
FROM movies;
```
The keyword AS renames the column in the table but not in the database. Although it isn't always necessary , it is best practices to surround your aliases with single quotes.

### Distinct
Used to return unique values in the output. It filters out all duplicate values in the specified columns. EX:
```
SELECT DISTINCT tools
FROM inventory;
```
### Where
Filters the result set to only include the rows where the follwoing condition is true. Comparison operators used with the ```WHERE``` clause are: ```=``` equal to, ```!=``` not equal to, ```>``` greater than, ```<``` less than, ```>=``` greater than or equal to, ```<=``` less than or equal to.

### Like
A special operator used with the ```WHERE``` clause to search for a specific pattern in a column. EX:
```
SELECT *
FROM movies
WHERE name LIKE 'Se_en';
```
The ```_``` means that you can substitue any individual character here without breaking the pattern.

Another useful character to use with ```LIKE``` is the percentage sign ```%```. This character matches zero or more missing letter in the pattern. As an example: ```A%``` matches all movies with names tha begin with the letter "A". Alternatively, ```%a``` matches all names that end with "a". You can also use it before and after the pattern such as ```%man%```.

### Is Null
We must use ```IS NULL``` or ```IS NOT NULL``` to check for NULL values.

### Between
Filters results within a certain range. Accepts two values which can be numbers, text, or dates. The second value is inlcusive but does not go past that value. For example:
```
SELECT * 
FROM movies
WHERE name BETWEEN 'A' AND 'J';
```
The results will include titles that are just "J" but not any movies that have full names that begin with "J".

### And
Used to combine conditions, both conditions must be true for the result to be part of the dataset. EX:
```
SELECT *
FROM movies
WHERE year BETWEEN 1990 AND 1999
  AND genre = 'romance';
```

### Or
Similar to ```AND``` the ```OR``` keyword is used with the ```WHERE``` keyword. It displays rows if any of the conditions are met. Ex:
```
SELECT *
FROM movies
WHERE year > 2014
  OR genre = 'action';
```

### Order By

This allows you to sort the dataset either alphabetically or numerically. Used with ```ASC``` (low to high or A to Z) and ```DESC``` (high to low or Z to A) Ex:
```
SELECT *
FROM movies
WHERE imdb_rating > 8
ORDER BY year DESC;
```

### Limit

Lets you specify the maximum number of rows the result set will have. ```LIMIT``` always goes at the end of the query and isn't supported by all SQL databases. Ex:
```
SELECT * 
FROM movies
LIMIT 10;
```
### Case

A ```CASE``` statement allows us to create different outputs (usually in the ```SELECT``` statement). It is also where we will use SQL's if then logic. EX:
```
SELECT name, 
  CASE 
    WHEN imdb_rating > 8 THEN 'Fantastic'
    WHEN imdb_rating > 6 THEN 'Poorly recieved'
    ELSE 'Avoid at all costs'
  END AS 'Review'
FROM movies;
```
Each ```WHEN``` tests a condtion and the following ```THEN``` gives us the string if the condition is true. The ```ELSE``` gies us the string if all the above donistions are false. The ```CASE``` statement must end with ```END  ```. We alias the column name to shorten it using ```AS```.

## Review of Queries

* ```SELECT``` is the clause we use every time we want to query information from the database.
* ```AS``` renames a column or table.
* ```DISTINCT``` return unique values.
* ```WHERE``` is a populer command that lets you filter the results of the query based on conditions that you specify.
* ```LIKE``` and ```BETWEEN``` are special operators.
* ```AND``` and ```OR``` combine multiple conditions.
* ```ORDER BY``` sorts the result.
* ```LIMIT``` specifies the maximum number of rows that the query will return.
* ```CASE``` creates different outputs.

## Aggregate Functions

