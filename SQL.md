All SQL queries take the following general form

```
SELECT [DISTINCT] <column expression list>
FROM <relation>
[WHERE <predicate>]
[GROUP BY <column list>]
[HAVING <predicate>]
[ORDER BY <column list>]
[LIMIT <number>]
```
### SELECT
Select everything with *

Select unique values with distinct

Use AS to create a new column

```
SELECT price/2 AS half_price
FROM prices
```
### WHERE
Filter columns with WHERE

```
SELECT *
FROM prices
WHERE price < 500
```

AND, OR, NOT can all be used with WHERE to help filter further

```
SELECT *
FROM prices
WHERE retailer = ‘Amazon’
    AND NOT product = ‘Battery pack’
    AND price < 30l
```

### GROUP BY

All columns specified in SELECT must be either listed in the GROUP BY clause or have an aggregate function applied to them

```
SELECT retailer, MAX(price) as max_price
FROM prices 
GROUP BY retailer
```

### HAVING

We can’t use WHERE on aggregated columns, for that we much use HAVING.

```
SELECT retailer, MAX(price) as max_price
FROM prices
GROUP BY retailer
HAVING max_price > 700
```

### ORDER BY
Let’s us order a column either by ascending order (ASC) - by default, or by descending value (DESC).

LIMIT controls how many tuples (rows) are displayed 

```
SELECT *
FROM prices
ORDER BY price ASC
LIMIT 3
```

The order in which SQL commands are executed

1. FROM: one or more source tables
2. WHERE: apply selection criteria
3. GROUP BY: form groups and aggregate
4. HAVING: eliminate groups
5. SELECT: select columns

### Joins

**Inner join** contains only the rows that have matching columns in both tables

**Full/Outer Join** all records from both tables are included in the same joined table. If a row doesn’t match in the other table, the missing values are filled with NULL.

**Left Join** All records from the left table are included in the joined table. If a row doesn’t have a match in the right table, the. missing values are filled with NULL.
