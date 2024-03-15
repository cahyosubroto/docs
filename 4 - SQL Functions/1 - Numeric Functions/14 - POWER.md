---
title: POWER
slug: dGuV-power
createdAt: 2023-11-30T01:16:19.992Z
updatedAt: 2023-11-30T01:19:50.143Z
---

# **Overview**

The `POWER()` function calculates the value of a number raised to the power of another number specified in the arguments.&#x20;

# **Syntax**

The following illustrates the syntax of the `POWER()` function:

```pgsql
POWER(a,b)
```

Where:

*   `a`: The base number.

*   `b`: The exponent to which the base number is raised.

# **Examples**

Let's explore some examples of the `POWER()` function.

## Case #1: **Basic Usage**

In this case, the `POWER()` function calculates the result of raising one number to the power of another.

```pgsql
SELECT POWER(3, 4) AS "Example 1",
       POWER(7, 3) AS "Example 2";
```

You will get the output below:

```pgsql
 Example 1 | Example 2 
-----------+-----------
        81 |       343
```

## Case #2: Using `POWER()` with Negative Values

In this case, the `POWER()` function is applied to negative numbers.

```pgsql
SELECT POWER(-4, -5), POWER(-1, -2), POWER(-6, -7);
```

You will get the output below:

```pgsql
 power | power | power 
-------+-------+-------
 -1024 |     1 |     0
```

## Case #3 Using `POWER()` with Floating-Point Numbers

In this example, the `POWER()` function is used to calculate 2.5 raised to the power of 3.0.&#x20;

```pgsql
SELECT POWER(2.5, 3.0) AS power_result;
```

The result, 15.625, is the value obtained by raising 2.5 to the third power.

```pgsql
 power_result
--------------
       15.625
```

## Case #4 Zero To the Power of Zero

This case shows that 0 expression raised to the power of 0 returns 1.

```pgsql
SELECT POWER(0, 0);
```

You will get the output below:

```pgsql
 power 
-------
     1
```

