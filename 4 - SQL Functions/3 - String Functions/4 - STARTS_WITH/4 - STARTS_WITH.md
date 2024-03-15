---
title: STARTS_WITH
slug: pOgJ-startswith
description: The STARTS_WITH() function determines whether or not the first argument starts with a specified string in the second argument. Let's look at the basics.
createdAt: 2022-09-12T06:10:29.000Z
updatedAt: 2023-10-09T13:02:32.129Z
---

## Overview

The `STARTS_WITH()` function determines whether the first argument starts with a specified string in the second argument or not.

```pgsql
STARTS_WITH(first_argument, 'second_argument')
```

*   `first_argument`: the specified argument, which will be the search reference. It can be a string or a column name.

*   `second_argument`: the specified argument, which will have the search keywords.

The input type will be `STRING`, and the return type is `BOOL`, shown as `true` or `false`.

💡**Special case:**

*   It will return `NULL` for the `NULL` record.

*   It will return `true` (including the `NULL` record) if the `second_argument` is not specified.

## Examples

### #Case 1: `STARTS_WITH()` function using column

Let’s say we have a table with the title **petsData**, as shown below.

```pgsql
CREATE TABLE petsData (
  petid int,
  petname string,
  species string,
  breed string,
  sex string,
  age int
);
INSERT INTO petsData 
    (petid, petname, species, breed, sex, age) 
VALUES 
    (2021001,'Bartholomeow','cat','persian','m',2),
    (2021004,'Jack','dog','boston terrier','m',1),
    (2022001,'Jesse','hamster','dzungarian','m',1),
    (2022010,'Bella','dog','dobberman','f',3),
    (2022011,'June','cat','american shorthair','f',2);
```

```pgsql
SELECT * FROM petsData;
```

The above query will show the following table:

```pgsql
+----------+--------------+----------+---------------------+------+-----+
| petid    | petname      | species  | breed               | sex  | age |
+----------+--------------+----------+---------------------+------+-----+
| 2021001  | Bartholomeow | cat      | persian             | m    | 2   |
| 2021004  | Jack         | dog      | boston terrier      | m    | 1   |
| 2022001  | Jesse        | hamster  | dzungarian          | m    | 1   |
| 2022010  | Bella        | dog      | dobberman           | f    | 3   |
| 2022011  | June         | cat      | american shorthair  | f    | 2   |
+----------+--------------+----------+---------------------+------+-----+
```

From the table above, we want to retrieve the values of **petname** column that start with “J” by using the following query:

```pgsql
SELECT petname, STARTS_WITH(petname, 'J') FROM petsData;
```

It will return `true` to the pet with a pet starting with the letter J. Otherwise, `false`.

```pgsql
+--------------+---------------+
|   petname     | starts_with  |
+---------------+--------------+
| Bartholomeow  | false        |
| Jack          | true         |
| Jesse         | true         |
| Bella         | false        |
| June          | true         |
+---------------+--------------+
```

### Case 2: `STARTS_WITH()` function with no specified argument

Here we have the **petsData** table with a `NULL` value in the breed column.

```pgsql
CREATE TABLE petsData (
  petid int,
  petname string,
  species string,
  breed string,
  sex string,
  age int
);
INSERT INTO petsData 
    (petid, petname, species, breed, sex, age) 
VALUES 
    (2021001,'Bartholomeow','cat','persian','m',2),
    (2021004,'Jack','dog','boston terrier','m',1),
    (2022001,'Jesse','hamster','dzungarian','m',1),
    (2022010,'Bella','dog','dobberman','f',3),
    (2022011,'June','cat','american shorthair','f',2),
    (2022012,'Phoebe','gold fish','','f',1);
```

```pgsql
SELECT * FROM petsData;
```

```pgsql
+----------+--------------+------------+---------------------+------+------+
| petid    | petname      | species    | breed               | sex  | age  |
+----------+--------------+------------+---------------------+------+------+
| 2021001  | Bartholomeow | cat        | persian             | m    | 2    |
| 2021004  | Jack         | dog        | boston terrier      | m    | 1    |
| 2022001  | Jesse        | hamster    | dzungarian          | m    | 1    |
| 2022010  | Bella        | dog        | dobberman           | f    | 3    |
| 2022011  | June         | cat        | american shorthair  | f    | 2    |
| 2022012  | Phoebe       | gold fish  |                     | f    | 1    |
+----------+--------------+------------+---------------------+------+------+
```

For example, we run the `STARTS_WITH` function but with no specified `second_argument:`

```pgsql
SELECT breed, STARTS_WITH(breed, '') FROM petsData;
```

We will have the following result where the `STARTS_WITH` will return true to all records (even the `null` one):

```pgsql
+---------------------+--------------+
| breed               | starts_with  |
+---------------------+--------------+
| persian             | true         |
| boston terrier      | true         |
| dzungarian          | true         |
| dobberman           | true         |
| american shorthair  | true         |
| null                | true         |
+---------------------+--------------+
```

