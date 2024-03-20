---
title: REPLACE
slug: -Ed0-replace
description: This function looks for and replaces a substring with a new one in a string, and is often used to update the outdated or spelling mistakes in data.
createdAt: 2023-03-27T01:54:44.000Z
updatedAt: 2023-10-09T13:02:32.129Z
---

## **Overview**

The `REPLACE()` function looks for and replaces a substring with a new one in a string. This function is often used to update the outdated or spelling mistakes in data that require an amendment.

:::hint{type="info"}
Oxla also has the `REGEXP_REPLACE()` function. It enables you to search and replace a substring(s) that matches with a POSIX regular expression. See [here](https://docs.oxla.com/regexpreplace) for more info.
:::

## **Syntax**

The `REPLACE()` function syntax is described as follows.

```pgsql
REPLACE(string, old_substring, new_substring)
```

The syntax requires three arguments, explained below:

*   `string`: the string that you want to replace.

*   `old_substring`: the substring that you want to replace. All parts will be replaced if it appears multiple times in the string.

*   `new_substring`: the new substring that will replace the old one**.**

:::hint{type="warning"}
The `REPLACE()` function performs a case-sensitive replacement.
:::

## **Examples**

### Case #1: Basic `REPLACE()` function

We will replace the substring of the “**OxlaDatabase”** string from “**New” **to “**Oxla”**, as shown below:

```pgsql
SELECT REPLACE ('NewDatabase', 'New', 'Oxla');
```

The `REPLACE()` function will find and replace all occurrences in the string and return the following:

```pgsql
+---------------------+
| f                   |
+---------------------+
| OxlaDatabase        |
+---------------------+
```

### Case #2: Replacing the specified values in a table

This example shows how to replace the values of a specific column in a table.

**1)** Create a new table named **extracurriculars** with **club** and **category** columns and insert the values into the respective columns.

```pgsql
CREATE TABLE hobby (
  club string,
  category string 
);
INSERT INTO hobby 
    (club, category) 
VALUES 
    ('Bridge','group'),
    ('Painting','individual'),
    ('Basketball','group'),
    ('Volleyball','group');
```

**2)** Retrieve all values from the table using the following query.

```pgsql
SELECT * FROM hobby;
```

```pgsql
+------------+---------------+
| club       | category      |
+------------+---------------+
| Bridge     | group         |
| Painting   | individual    |
| Basketball | group         |
| Volleyball | group         |
+--------------+-------------+
```

**3)** Replace the **“group”** value in the **category** column with** “sports”.**

```pgsql
SELECT REPLACE(category, 'group', 'sports') from hobby;
```

**4)** The final result will look like the following. 

```pgsql
+--------------+
| f            |
+--------------+
| sports       |
| individual   |
| sports       |
| sports       |
+--------------+
```

### Case #3:  Remove a word with `REPLACE()` function

In the following example, we will remove **“Friends” **in a string with a `REPLACE()` function.&#x20;

```pgsql
SELECT REPLACE('Hello Friends','Friends','');
```

The final output will leave the remaining word, **“Hello”.**

```pgsql
+-----------+
| f         |
+-----------+
| Hello     |
+-----------+
```

### Case #4:  Replace multiple patterns with `REPLACE()` function

The following example uses the `REPLACE()` function to replace multiple patterns of the given string.&#x20;

```pgsql
SELECT REPLACE(REPLACE(REPLACE(REPLACE('2*[9-5]/{4+8}', '[', '('), ']', ')'), '{', '('), '}', ')');
```

We can see that the REPLACE function is called multiple times to replace the corresponding string as specified:

*   the** “\[]” **into** “()”**

*   the** “{}” **into** “()”**

```pgsql
+------------------+
| f                |
+------------------+
| 2*(9-5)/(4-8)    |
+------------------+
```

