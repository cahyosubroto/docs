---
title: ENDS_WITH
slug: x804-endswith
description: The ENDS_WITH() function determines whether the first argument ends with a specified string in the second argument or not. This guide explains more.
createdAt: 2022-09-12T06:10:29.000Z
updatedAt: 2023-10-09T13:02:32.129Z
---

## Overview

The `ENDS_WITH()` function determines whether the first argument ends with a specified string in the second argument or not.

```pgsql
ENDS_WITH(first_argument, 'second_argument')
```

*   `first_argument`:** **the specified argument, which will be the search reference. It can be a string or a column name.

*   `second_argument`: the specified argument, which will have the search keywords.

The input type will be `STRING`, and the return type is `BOOL`, shown as `true` or `false`.

💡**Special case:**

*   It will return `NULL` for the `NULL` record.

*   It will return `true` (including the `NULL` record) if the `second_argument` is not specified.

## Examples

### #Case 1: `ENDS_WITH()` function using column

Let’s say we have a table named **courses**:

```pgsql
CREATE TABLE courses (
  course_id int,
  course_name string,
  credits string
);
INSERT INTO courses 
    (course_id, course_name, credits) 
VALUES 
    (2111,'Basics of Plant Biotechnology',2),
    (2102,'Biochemistry',3),
    (1241,'Statistics',3),
    (4142,'Microbial Biodiversity',2),
    (3262,'Introduction to Plant Pathology',3),
    (3233,'Enzyme Technology',2),
    (1201,'Rural Sociology',2);
```

```pgsql
SELECT * FROM courses;
```

The above query will display the following table:

```pgsql
+------------+----------------------------------+-----------+ 
| course_id  | course_name                      | credits   |
+------------+----------------------------------+-----------+
| 2111       | Basics of Plant Biotechnology    | 2         |
| 2102       | Biochemistry                     | 3         |
| 1241       | Statistics                       | 3         |
| 4142       | Microbial Biodiversity           | 2         |
| 3262       | Introduction to Plant Pathology  | 3         |
| 3233       | Enzyme Technology                | 2         |
| 1201       | Rural Sociology                  | 2         |
+------------+----------------------------------+-----------+
```

Using the following query, we want to confirm the values of the **course\_name** column that end with "ology" in the table above:

```pgsql
SELECT course_name, ENDS_WITH(course_name, 'ology') FROM courses;
```

It will return true to all the courses with the name ending with **ology. **Otherwise**,** `false`.

```pgsql
+----------------------------------+-------------+
| course_name                      | ends_with   |
+----------------------------------+-------------+
| Basics of Plant Biotechnology    | true        |
| Biochemistry                     | false       |
| Statistics                       | false       |
| Microbial Biodiversity           | false       |
| Introduction to Plant Pathology  | true        |
| Enzyme Technology                | true        |
| Rural Sociology                  | true        |
+----------------------------------+-------------+
```

### Case 2: `ENDS_WITH()` function with no specified argument

Here we have the **patients\_data **table with a `NULL` value in the **allergies** column.

```pgsql
CREATE TABLE patients_data (
  record_number int,
  patient_name string,
  height_in_cm int,
  weight_in_kg int,
  allergies string
);
INSERT INTO patients_data 
    (record_number, patient_name, height_in_cm, weight_in_kg, allergies) 
VALUES 
    (2009000908,'Vivienne Desjardin',168,49,''),
    (2012000876,'Elizabeth Reinhard',163,55,''),
    (2015000965,'James McCarthy',188,70,'penicillin'),
    (2020000109,'Jose Ramirez',170,70,'sulfonamide'),
    (2020000222,'Stefani Ricci',170,70,'peniccilin');
```

```pgsql
SELECT * FROM patients_data;
```

```pgsql
+----------------+---------------------+---------------+--------------+-------------+
| record_number  | patient_name        | height_in_cm  | weight_in_kg | allergies   |
+----------------+---------------------+---------------+--------------+-------------+
| 2009000908     | Vivienne Desjardin  | 168           | 49           | null        |
| 2012000876     | Elizabeth Reinhard  | 163           | 55           | null        |
| 2015000965     | James McCarthy      | 188           | 70           | penicillin  |
| 2020000109     | Jose Ramirez        | 170           | 70           | sulfonamide |
| 2020000222     | Stefani Ricci       | 170           | 70           | peniccilin  |
+----------------+---------------------+---------------+--------------+-------------+
```

For example, we run the `ENDS_WITH` function but with no specified `second_argument`.

```pgsql
SELECT allergies, ENDS_WITH(allergies, '') FROM patients_data;
```

We will have the result where the `ENDS_WITH` will return true to all records (even the `null` one).

```pgsql
+--------------+--------------+
| allergies    | starts_with  |
+--------------+--------------+
| null         | true         |
| null         | true         |
| penicillin   | true         |
| sulfonamide  | true         |
| peniccilin   | true         |
+--------------+--------------+
```

