---
title: Differences Between Oxla vs. PostgreSQL
slug: EWLb-differences-between-oxla-vs-postgresql
description: Learn about the differences Between Oxla vs. PostgreSQL in handling functions, operators, errors, and behaviors. An in-depth comparison of various details.
createdAt: 2023-04-11T04:12:28.000Z
updatedAt: 2024-03-07T09:18:18.997Z
---

## **1. Functions**

### a) Mathematical

A mathematical function operates on input values provided as arguments and returns a numeric value as the operation's output.

| **Mathematical** | **Description**                                                                                          | **Example**           | **Available in Oxla** |
| ---------------- | -------------------------------------------------------------------------------------------------------- | --------------------- | --------------------- |
| ABS              | Returns the absolute value of a number.                                                                  | > SELECT  ABS(-11);   | Available             |
| CEIL             | Returns the value after rounding up any positive or negative value to the nearest largest integer.&#x20; | > SELECT CEIL(53.7);  | Available             |
| FLOOR            | Returns the value after rounding up any positive or negative decimal value as smaller than the argument. | > SELECT FLOOR(53.6); | Available             |
| LN               | Returns the natural logarithm of a given number.                                                         | > SELECT LN(3);       | Available             |
| RANDOM           | Returns the random value between 0 and 1.                                                                | > SELECT RANDOM();    | Available             |
| SQRT             | Returns the square root of a given positive number.                                                      | > SELECT SQRT(225);   | Available             |

### b) Trigonometric

| **Trigonometric** | **Description**                           | **Example**        | **Available in Oxla** |
| ----------------- | ----------------------------------------- | ------------------ | --------------------- |
| SIN               | Returns the sine of the specified radian. | > SELECT sin(0.2); | Available             |

## **2. Operators**

Below is a list of math operators available in PostgreSQL:

| **Operators** | **Description** | **Example**                                                                        | **Result**               | **Available in Oxla** | **Note**                                |
| ------------- | --------------- | ---------------------------------------------------------------------------------- | ------------------------ | --------------------- | --------------------------------------- |
| `+`           | Addition        | *   `SELECT 5+8;`

*   `SELECT 5 + 8;`

*   `SELECT 5+ 8;`

*   `SELECT 5 +8;`     | >  f  &#xA;----&#xA; 13  | Available             |                                         |
| `-`           | Subtraction     | *   `SELECT 2 - 3;`

*   `SELECT 2+-3;`                                            | >  f  &#xA;----&#xA; \-1 | Available             |                                         |
| `-`           | Negation        | `SELECT -4;`                                                                       | >  f  &#xA;----&#xA; \-4 | Available             |                                         |
|               |                 | `SELECT -(-4);`                                                                    | >  f  &#xA;----&#xA; 4   | Available             |                                         |
|               |                 | `SELECT 5+(-2);`                                                                   | >  f  &#xA;----&#xA; 3   | Available             |                                         |
|               |                 | `SELECT 5-(-2);`                                                                   | >  f &#xA;----&#xA; 7    | Available             |                                         |
| `*`           | Multiplication  | *   `SELECT 3*3;`

*   `SELECT 3 + 3;`

*   `SELECT 3+ 3;`

*   `SELECT 3 +3;`     | >  f  &#xA;----&#xA; 9   | Available             |                                         |
| `/`           | Division&#x20;  | *   `SELECT 10/2;`

*   `SELECT 10 / 2;`

*   `SELECT 10/ 2;`

*   `SELECT 10 /2;` | >  f  &#xA;----&#xA; 5   | Available             |                                         |
| `%`           | Modulo          | *   `SELECT 20%3;`

*   `SELECT 20 % 3;`

*   `SELECT 20% 3;`

*   `SELECT 20 %3;` | >  f  &#xA;----&#xA; 2   | Available             |                                         |
| `&`           | Bitwise AND     | `91 & 15`                                                                          | >  f  &#xA;----&#xA; 91  | Available             | the result is different from PostgreSQL |
| `#`           | Bitwise XOR     | `17 # 5`                                                                           | >  f  &#xA;----&#xA; 17  | Available             | the result is different from PostgreSQL |

## **3. Behaviors Difference**

### a) Output Header

Missing function name in output header, PostgreSQL shows the function name, like in this example:

```pgsql
SELECT COS(0),LN(1);
```

```pgsql
cos  | ln 
-----+-----
 1   | 0
```

Oxla does not show the function name, like in this example:

```pgsql
SELECT COS(0),LN(1);
```

```pgsql
 f | f_1 
---+-----
 1 | 0
```

### b) ABS Output

Differences are also found in the ABS function, where there are differences in decimal results.&#x20;

***For example: ***

The example below will return the absolute value of -1.0

```pgsql
SELECT ABS(-1.0);
```

It returns 1 in Oxla, while in PostgreSQL, it produces 1.0

## **4. Errors Difference**

| **Functions** | **Input**                            | **Output - Oxla**                        | **Output - PostgreSQL**                                   |
| ------------- | ------------------------------------ | ---------------------------------------- | --------------------------------------------------------- |
| LN            | `LN(0)`                              | *Infinity*                               | *ERROR: cannot take the logarithm of zero*                |
|               | `LN(0.0)`                            | *Infinity*                               | *ERROR: cannot take the logarithm of zero*                |
| SQRT          | `SQRT(-1)`                           | *NaN*                                    | *ERROR: cannot take the square root of a negative number* |
| RANDOM        | `SELECT floor(random()*(10-1+1))+1;` | *ERROR: syntax error, unexpected INTVAL* | working as expected                                       |
| SIN           | `SELECT sin(pi()/2);`                | *unknown function pi*                    | working as expected                                       |
| /             | `1/0`                                | *error division(s) by zero*              | *error division(s) by zero*                               |
|               | `1/0.0`                              | *Infinity*                               | *error division(s) by zero*                               |
|               | `0/0.0`                              | *NaN*                                    | *error division(s) by zero*                               |



