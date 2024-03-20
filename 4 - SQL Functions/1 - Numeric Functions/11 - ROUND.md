---
title: ROUND
slug: fXDc-round
description: Rounds numbers to the nearest integer
createdAt: 2023-10-14T04:32:16.666Z
updatedAt: 2023-10-14T04:52:01.176Z
---

## **Overview**

The `ROUND()` function rounds numbers to the nearest integer or to a specified number of decimal places.

## **Syntax**

The following illustrates the syntax of the `ROUND()` function:

```pgsql
ROUND(number);
```

Where:

*   `number`: The number to round, it can be positive, negative, or zero, and it can be an [Integer](https://docs.oxla.com/numeric-type#_zXh8) or a [Double Precision](https://docs.oxla.com/numeric-type#s_DWu).

## **Examples**

Let's explore some examples to see how the `ROUND()` function works.

### Case #1: **Basic Usage**

In this example, we round decimal numbers to integers:

```pgsql
SELECT
    round(28.11) AS "round(28.11)",
    round(12.51) AS "round(12.51)",
    round(-9.11) AS "round(-9.11)",
    round(-40.51) AS "round(-40.51)";
```

The query will return the nearest integer for all provided values.

```pgsql
 round(28.11) | round(12.51) | round(-9.11) | round(-40.51) 
--------------+--------------+--------------+---------------
           28 |           13 |           -9 |           -41
```

### Case #2: Using `ROUND` with Table

Suppose you have a table named **Product** that stores product prices with multiple decimal places. You want to round the prices to two decimal places for display.&#x20;

```pgsql
CREATE TABLE Product (
    ProductID INT,
    ProductName TEXT,
    Price DOUBLE PRECISION
);

INSERT INTO Product (ProductID, ProductName, Price)
VALUES
    (1, 'Widget A', 12.345),
    (2, 'Widget B', 34.678),
    (3, 'Widget C', 9.99),
    (4, 'Widget D', 45.00),
    (5, 'Widget E', 7.12345),
    (6, 'Widget F', 19.876), 
    (7, 'Widget G', 3.5),
    (8, 'Widget H', 29.999);
```

We use the `ROUND()` function to round the Price column when retrieving the data.&#x20;

```pgsql
SELECT ProductName, ROUND(Price) AS RoundedPrice FROM Product;
```

The result will display the product names along with their prices rounded to two decimal places.

```pgsql
 productname | roundedprice 
-------------+--------------
 Widget A    |           12
 Widget B    |           35
 Widget C    |           10
 Widget D    |           45
 Widget E    |            7
 Widget F    |           20
 Widget G    |            4
 Widget H    |           30
```

