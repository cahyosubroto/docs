---
title: GREATEST
slug: 3NBOaVTLnVu06RLjqFXvl
description: Extracts the greatest or largest value from a set of values. More information can be found here.
createdAt: 2023-08-21T16:08:41.340Z
updatedAt: 2023-10-09T13:02:32.129Z
---

## **Overview**

The `GREATEST()` function extracts the greatest or largest value from a set of values. It needs at least one argument to work with, and if you mix different types, like a text and a number, it will return an error.&#x20;

For example, comparing the greatest value among 4, "two", and 9 would result in an error.

## **Syntax**

The syntax for the `GREATEST()` function is as follows:

```pgsql
GREATEST(value_1, [value_n])
```

Where:

*   `value_1`: Represents the first value.

*   `value_n`: Represents one or more additional values, separated by commas.

:::hint{type="info"}
**Info:**

*   `NULL` values within the expressions are ignored.

*   The result will be `NULL` if all expressions evaluate to `NULL`.
:::

## **Examples**

Here are examples that illustrate the usage of the `GREATEST()` function:

### Case #1: **Basic Usage**

Consider the following example:

```pgsql
SELECT GREATEST(3,5,8,9,10);
```

The query will return `3`, the smallest value among the provided values.

```pgsql
greatest 
---------
     10
```

### Case #2: **String Comparison**

String comparison is also supported, as shown below:

```pgsql
SELECT GREATEST('apple', 'banana', 'cherry');
```

In this case, the result will be `'cherry'`, the greatest string according to the order.

```pgsql
greatest 
----------
 cherry
```

### Case #3: **Handling NULL Values**

`NULL` values are ignored when determining the greatest value:

```pgsql
SELECT GREATEST (5,null,9);
```

The result will be the greatest non-NULL value, which is `9`.

```pgsql
least 
-------
     9
```

### Case #4: **Positive and Negative Numbers**

Negative numbers can also be compared:

```pgsql
SELECT GREATEST (4,-4,-8,8);
```

This query will return `8`, the greatest value among the provided numbers.

```pgsql
least 
-------
    8
```

### Case #5: **Using Table Data**

The `GREATEST` function can also be used to find the Greatest value between column data. For example, let’s create a table named **Student** that stores students' names and scores.

```pgsql
CREATE TABLE Student(
    Student_name TEXT,
    Student_Class TEXT,
    Subject1 INT,
    Subject2 INT,
    Subject3 INT,
    Subject4 INT
);

INSERT INTO  
    Student(Student_name, Student_Class, Subject1, Subject2, Subject3, Subject4)
VALUES
    ('Sayan', 'Junior', 81, 90, 86, 92 ),
    ('Nitin', 'Junior', 90, 84, 88, 91 ),
    ('Aniket', 'Senior', 81, 80, 87, 95 ),
    ('Abdur', 'Junior', 85, 90, 80, 90  ),
    ('Sanjoy', 'Senio', 88, 82, 84, 90 );
```

Use the `SELECT` statement to view all the records:

```pgsql
SELECT * FROM Student;
```

```pgsql
student_name | student_class | subject1 | subject2 | subject3 | subject4 
--------------+---------------+----------+----------+----------+----------
 Sayan        | Junior        |       81 |       90 |       86 |       92
 Nitin        | Junior        |       90 |       84 |       88 |       91
 Aniket       | Senior        |       81 |       80 |       87 |       95
 Abdur        | Junior        |       85 |       90 |       80 |       90
 Sanjoy       | Senio         |       88 |       82 |       84 |       90
```

Now, we will find the greatest marks for every student in all subjects.

```pgsql
Select Student_name, GREATEST(Subject1, Subject2, Subject3, Subject4) AS Greatest_Mark
FROM Student;
```

```pgsql
student_name | greatest_mark 
--------------+---------------
 Sayan        |            92
 Nitin        |            91
 Aniket       |            95
 Abdur        |            90
 Sanjoy       |            90
```

