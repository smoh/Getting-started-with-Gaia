
# ADQL cheatsheet

- Use random_index to subsample:

```sql
-- randomly selects one out of every million objects
SELECT *
FROM gaiadr1.gaia_source
WHERE MOD(random_index, 1000000) = 0
```

- When cross-matching by position, do

```sql
1 = CONTAINS(POINT(smaller_catalog), CIRCLE(larger_catalog))
```

## Functions

- SIN(x), COS(x), TAN(x): all in radians
- ASIN(x), ACOS(x), ATAN(x)
- ATAN2(x, y): arctan(y/x) -> [-pi, +pi]
- DEGREES(x): radians to degrees
- RADIANS(x): degrees to radians
- EXP(x)
- LOG(x): natural log
- LOG10(x)
- POWER(x, y): x**y
- SQRT(x)

- ROUND(x, n): round to n decimal places. positive: to the right, negative: to the left of the decimal point.
- FLOOR(x)
- CEILING(x)
- TRUNCATE(x, n)
- ABS(x)
- RAND(n)?
- MOD(x, y): x mod y
- PI()

### Geometric functions

All angle in degrees.

### Data type functions

- POINT(coordsys, lon, lat)
- BOX(coordsys, longitudeCentre, latitudeCentre, longitudeExtent, latitudeExtent)
- CIRCLE(coordsys, longitudeCentre, latitudeCentre, radius)
- POLYGON(coordsys, longitude_1, latitude_1, ..., longitude_N, latitude_N)

### Predicate functions

- CONTAINS(geometry_1, geometry_2) (=1 : true, =0 : false)
- INTERSECTS(geometry_1, geometry_2)

### Utility functions

- AREA(geometry): area in square degrees
- DISTANCE(point1, point2): great circle distance in degrees

## SQL

- Put column names with spaces in double quotes ("").
- Put column values to compare in single quotes ('').
- Arithmetic operations are for columns. For operations between rows, use aggregate functions.
- comments:

```SQL
-- single line
/* multiple
  lines*/
```

### Logical operators

* LIKE: pattern matching
  - `%`: wildcard e.g., `WHERE column LIKE 'abc%'`
  - `_`: any individual character e.g., `WHERE column LIKE 'ab_de'`
  - can be case sensitive or insensitive depending on DB?

* IN: compare to a set of values
  - `WHERE year in (2009, 2010)`
  - `WHERE flag in ('big', 'small')`

* BETWEEN AND: range of values incl. bounds
  - ` WHERE year_rank BETWEEN 5 AND 10` is exactly same as ` WHERE year_rank >= 5 AND year_rank <= 10`

* IS NULL: missing or not
  - `= NULL` does not work since `=` is arithmetic comparison
* NOT
  - year_rank NOT BETWEEN 2 AND 3
  - "group" NOT LIKE '%macklemore%'
  - artist IS NOT NULL


* ORDER BY
  - ascending by default; use ORDER BY column DESC for descending
  - multiple columns: `ORDER BY year DESC, year_rank`


### Aggregate functions

* COUNT
  - `COUNT(*)`: count all rows
  - `COUNT(column)`: count all rows in column that is not NULL
* SUM only on numerical columns
* MIN, MAX works on non-numerical columns (alphabetical)
* AVG on numerical columns, NULL rows are ignored

* GROUP BY
- multiple columns: GROUP BY col1, col2

* HAVING: filter on aggregates
  - order matters: select -> from -> where -> group by -> having -> order by

### JOIN

- JOIN = INNER JOIN: unmatched rows are dropped.
- LEFT/RIGHT JOIN: find match for every row in left, right table. Includes duplicates.
- FULL JOIN = FULL OUTER JOIN: union of two tables
- filter in JOIN by doing: JOIN table ON table.col1 = table2.col2 AND [condition]

### String manipulation

* Casting - supported for adql?
  - CAST(column AS integer) or column::integer
* Cleaning strings
  - LEFT(column, 5): 5 characters from the left
  - RIGHT(column, 5)
  - LENGTH(column)
  - TRIM([leading/trailing/both] 'characters' FROM column)


### Subqueries

```SQL
SELECT *
FROM (
  -- inner query
  SELECT ...
) sub
WHERE ...
```

- Subqueries are required to have names, which are added after parentheses.

When are subqueries useful?
1. aggregate in multiple stages, e.g., average count for col1 grouped by col2
2. with conditional logic
  - treated as single value or multiple values not a table.
  - do not put alias
  - `... WHERE column = (SELECT MIN(col2) FROM ...)`
  - `... WHERE column IN (SELECT col2 FROM ...)`
3. subquery to pre-process columns in the same table, and self-join


## Resources
- https://community.modeanalytics.com/sql
- https://www.gaia.ac.uk/data/gaia-data-release-1/adql-cookbook
