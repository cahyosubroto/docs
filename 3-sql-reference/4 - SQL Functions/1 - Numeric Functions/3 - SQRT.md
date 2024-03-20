---
title: SQRT
slug: gOdK-sqrt
description: The SQRT function returns the square root of a positive number. This article helps guide you through the overview, syntax, and examples of this function.
createdAt: 2023-01-25T03:07:34.000Z
updatedAt: 2023-10-09T13:02:32.129Z
---

## Overview

The `SQRT()` function returns the square root of a given positive number.

## Syntax

The syntax for the `SQRT()` function in Oxla is:

```pgsql
SQRT(x)
```

The `SQRT()` function requires one argument:

*   `x`: A positive number or an expression that evaluates to a positive number.

## Examples

### Case #1: SQRT() a Positive Value

The following example demonstrates how the `SQRT()` function can be used to find the square root of a positive integer:

```pgsql
SELECT SQRT(81);
```

You will get the following result:

```pgsql
+-----+
| f   |
+-----+
| 9   |
+-----+
```

### Case #2: SQRT() With an Expression

Let’s look at an example of using the `SQRT()` function to find the square root of the result of an expression.

```pgsql
SELECT SQRT(60 + 4);
```

The result of the above statement is the square root of 64:

```pgsql
+-----+
| f   |
+-----+
| 8   |
+-----+
```

### Case #3: SQRT() With Double Precision Result

In addition to integers, Oxla also supports calculating square roots with floating-point numbers as the outcome. For further details, please refer to the statement below:

```pgsql
SELECT SQRT(70);
```

The output of the statement above is 8.3666, which is the square root of 70 with double precision, as demonstrated below:

```pgsql
+----------+
| f        |
+----------+
| 8.3666   |
+----------+
```

### Case #4: SQRT() a Negative Number

The following example demonstrates how attempting to use the `SQRT()` function with a negative value will return an error:

```pgsql
SELECT SQRT(-25);
```

As the `SQRT()` function only accepts positive numbers, you will get a ***NaN (Not a Number)*** result for the square root of -25, as shown below:

```pgsql
+-------+
| f     |
+-------+
| NaN   |
+-------+
```

### Case #5: SQRT Operator (`|/(x)`)

Here's an example using the SQRT operator (`|/(x)`) to calculate the square root of a given number:

```pgsql
SELECT |/(169) AS sqrt_operator;
```

In this example, we calculate the square root of 169 using the SQRT operator. The result of this query will be:

```pgsql
 sqrt_operator 
---------------
            13
```

