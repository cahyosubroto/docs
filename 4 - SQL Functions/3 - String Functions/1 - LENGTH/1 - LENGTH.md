---
title: LENGTH
slug: KJuF-length
description: The LENGTH() function is used to find the length of a string (the number of characters in a given string). Here's more you need to know about the function.
createdAt: 2022-09-12T05:41:23.000Z
updatedAt: 2023-10-09T13:02:32.129Z
---

## Overview

The `LENGTH()` function is used to find the length of a string, i.e., the number of characters in a given string. It accepts a string as a parameter. Syntax of the length function is illustrated below:

```pgsql
LENGTH(string)
```

The input type is a string, and the return type is int, as it returns the number of characters.

**💡Special cases:**

*   If a null value is passed in the function, i.e., `LENGTH(NULL)`, it will return `NULL`.

*   If the parameter is an empty string `LENGTH(")`, it will return 0.

*   If the parameter is a space character `LENGTH('')`, not empty or null, it will return 1 as it is not empty anymore.

## Examples

### #Case 1: Basic `LENGTH()` function

The below example uses the `LENGTH()` function to find out the length of a string text:

```pgsql
SELECT LENGTH ('Oxla PostgreSQL Tutorial');
```

The final output will be as follows:

```pgsql
+------------+
| length     |
+------------+
| 24         |
+------------+
```

### #Case 2: `LENGTH()` function using columns

Let's see how the `LENGTH()` function works on the **personal\_details** table containing the employee's **id**, **first\_name**, **last\_name**, and **gender** of a retail store as columns.

```pgsql
CREATE TABLE personal_details (
  id int,
  first_name string,
  last_name string,
  gender string
);
INSERT INTO personal_details 
    (id, first_name, last_name, gender) 
VALUES 
    (1,'Mark','Wheeler','M'),
    (2,'Tom','Hanks','M'),
    (3,'Jane','Hopper','F'),
    (4,'Emily','Byers','F'),
    (5,'Lucas','Sinclair','M');
```

```pgsql
SELECT * FROM personal_details;
```

The above query will show the following table:

```pgsql
+-----+-------------+-------------+----------+
| id  | first_name  | last_name   | gender   |
+-----+-------------+-------------+----------+
| 1   | Mark        | Wheeler     | M        |
| 2   | Tom         | Hanks       | M        |
| 3   | Jane        | Hopper      | F        |
| 4   | Emily       | Byers       | F        |
| 5   | Lucas       | Sinclair    | M        |
+-----+-------------+-------------+----------+
```

The following query returns the last name and the length of the last name from the personal\_details table, where the length of the last\_name is greater than 5.

```pgsql
SELECT last_name,length(last_name)
AS "Length of Last Name"
FROM personal_details
WHERE LENGTH(last_name) > 5;
```

The output displays all those items in the last\_name column with a length of more than 5 characters.

```pgsql
+---------------+-----------------------+
| last_name     | Length of Last Name   |
+---------------+-----------------------+
| Wheeler       | 7                     |
| Hopper        | 6                     |
| Sinclair      | 8                     |
+---------------+-----------------------+
```

