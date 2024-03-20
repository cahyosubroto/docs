---
title: MAX
slug: Fcil-max
description: The MAX function returns the maximum values from a set of values. Let's cover the basics and examples with this guide.
createdAt: 2022-08-24T04:27:11.000Z
updatedAt: 2023-10-09T13:02:32.129Z
---

## Overview

`MAX()` function returns the maximum value from a set of records.

The input and return types we support can be seen in the table below.

![max types](../../../assets/max.png)

:::hint{type="success"}
✅ The return will be the same as the data type used as the input values.
:::

💡**Special cases:**

- Returns `NULL` if there are no input rows or `NULL` values.

- Returns `NaN` if the input contains a `NaN`.

## Examples

:::hint{type="info"}
For the `MAX()` examples, we will use the same sample table as in the MIN() section.
:::

We have a movies table that stores the movie details, such as the movie’s title, category, and IMDb rating.

```pgsql
CREATE TABLE movies (
    movieid int,
    moviename string,
    moviecategory string,
    imdbrating real
);
INSERT INTO movies (movieid, moviename, moviecategory, imdbrating)
VALUES
(8557411, 'The Shawshank Redemption', 'Drama', 9.4),
(8557421, 'Life Is Beautiful', 'Romance', 8.4),
(8557451, 'The Godfather', 'Crime', 9.3),
(8557311, 'Prisoners', 'Thriller', 8.5),
(8557321, 'Inception', 'Science Fiction', 9),
(8557351, 'The Dark Knight', 'Action', 9.2),
(8557221, 'Coco', 'Drama', 8.2),
(8557251, 'The Sixth Sense', 'Horror', 8.1),
(8557231, 'Kill Bill: Vol. 1', 'Action', 8.1),
(8557281, 'The Notebook', 'Romance', 7.8),
(8557291, 'Forrest Gump', 'Drama', 8);
```

```pgsql
SELECT * FROM movies;
```

The above query will show the following table:

```pgsql
+---------+--------------------------+-----------------+-------------+
| movieid | moviename                | moviecategory   | imdbrating  |
+---------+--------------------------+-----------------+-------------+
| 8557411 | The Shawshank Redemption | Drama           | 9.4         |
| 8557421 | Life Is Beautiful        | Romance         | 8.4         |
| 8557451 | The Godfather            | Crime           | 9.3         |
| 8557311 | Prisoners                | Thriller        | 8.5         |
| 8557321 | Inception                | Science Fiction | 9           |
| 8557351 | The Dark Knight          | Action          | 9.2         |
| 8557221 | Coco                     | Drama           | 8.2         |
| 8557251 | The Sixth Sense          | Horror          | 8.1         |
| 8557231 | Kill Bill: Vol. 1        | Action          | 8.1         |
| 8557281 | The Notebook             | Romance         | 7.8         |
| 8557291 | Forrest Gump             | Drama           | 8           |
+---------+--------------------------+-----------------+-------------+
```

### #Case 1: `MAX()` with a single expression

For example, you might want to know what is the highest rating among all stored movies:

```pgsql
SELECT MAX(imdbRating) AS "Highest Rating"
FROM movies;
```

It will return the following output:

```pgsql
+-----------------+
| Highest Rating  |
+-----------------+
| 9.4             |
+-----------------+
```

### #Case 2: `MAX()` with GROUP BY clause

We use a `MAX()` for this example to get the highest rating in each movie category.

```pgsql
SELECT movieCategory AS "Movie Category", MAX(imdbRating) AS "Highest Rating"
FROM movies
GROUP BY movieCategory;
```

It will display the highest rating from a group of `movieCategory` as shown below:

```pgsql
+------------------+-----------------+
| Movie Category   | Highest Rating  |
+------------------+-----------------+
| Thriller         | 8.5             |
| Romance          | 8.4             |
| Crime            | 9.3             |
| Horror           | 8.1             |
| Drama            | 9.4             |
| Action           | 9.2             |
| Science Fiction  | 9               |
+------------------+-----------------+
```

### #Case 3: `MAX()` in a subquery

In this example, we want to get a movie that has the highest rating by using a subquery:

```pgsql
SELECT movieName, IMDbRating
FROM movies
WHERE IMDbRating = (
SELECT MAX(IMDbRating)
FROM movies
);
```

It will return the following result:

```pgsql
+---------------------------+-------------+
| moviename                 | imdbrating  |
+---------------------------+-------------+
| The Shawshank Redemption  | 9.4         |
+---------------------------+-------------+
```
