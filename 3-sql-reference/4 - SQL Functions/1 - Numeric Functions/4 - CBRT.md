---
title: CBRT
slug: hwij-cbrt
description: The CBRT() function calculates and returns the cube root of a given number. More information can be found in this guide.
createdAt: 2023-08-31T01:25:58.662Z
updatedAt: 2023-10-09T13:02:32.129Z
---

## Overview

The `CBRT()` function calculates and returns the cube root of a given number. In mathematical terms, for a number *x*, its cube root *y* is determined by the equation *y³ = x*.

## Syntax

The syntax for the `CBRT()` function is as follows:

```pgsql
CBRT(number)
```

Where:

*   `number`: This is a required value representing the number for which you want to calculate the cube root. It can be a positive or negative whole number, a decimal, or even an expression that evaluates to a number.

For example, you can use expressions like `SELECT CBRT(some_column) from test_table`, assuming `some_column` contains a numeric value.

:::hint{type="info"}
**Return Value:**
\- It will return `NULL` if the argument is `NULL`.&#x20;
\- It will give an error if you input a parameter that is not a numeric type.
:::

## Examples

Below are several usage examples of the `CBRT()` function:

### Case #1: **Basic Cube Root Calculation**

Consider the following example:

```pgsql
  SELECT CBRT(125);
```

The result of this query will be:

```pgsql
 cbrt 
------
    5
```

### Case #2: **Cube Root of a Negative Value**

To calculate the cube root of a negative number, use the `CBRT()` function as shown:

```pgsql
  SELECT CBRT(-125);
```

The final result is as follows.

```pgsql
 cbrt 
------
   -5
```

### Case #3: **Cube Root of Decimal Result**

For calculations with decimal numbers, use the `CBRT()` function as demonstrated below:

```pgsql
SELECT CBRT(32);
```

The result will be a decimal value, as shown below:

```pgsql
       cbrt        
-------------------
 3.174802103936399
```

### Case #4: **Cube Root of Decimal Input**

In this scenario, fractional seconds are incorporated into the argument:

```pgsql
SELECT CBRT(0.12815);
```

The result will be the cube root of the provided decimal value.

```pgsql
    cbrt    
------------
 0.50416523
```

### Case #5: Handling Incorrect Argument

When a non-numeric argument is provided, the `CBRT()` function works as follows:

```pgsql
SELECT CBRT('abc');
```

An error will be generated, and the result will not be valid.

```pgsql
invalid input syntax for type double precision: "abc"
```

### Case #6: CBRT Operator (`||/(x)`)

Here's an example using the CBRT operator (`||/(x)`) to calculate the cube root of a given number:

```pgsql
SELECT ||/(1728) AS cbrt_operator;
```

In this example, we calculate the cube root of 1728 using the CBRT operator. The result of this query will be:

```pgsql
   cbrt_operator    
--------------------
 12.000000000000002
```

