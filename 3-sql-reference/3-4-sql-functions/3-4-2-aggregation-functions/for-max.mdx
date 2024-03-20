---
title: FOR_MAX
slug: WpTP-formax
description: The FOR_MAX function returns a value corresponding to the maximal metric and in the same row as the value. Let's covers the overview and some examples.
createdAt: 2022-08-24T04:27:07.000Z
updatedAt: 2023-10-09T13:02:32.129Z
---

## Overview

`FOR_MAX()` function takes two arguments: metric and value. Returns a value corresponding to the maximum metric in the same row from a set of values.

The value argument can be one of the following types:

*   `INT`

*   `LONG`

*   `FLOAT`

*   `DOUBLE`

*   `DATE`&#x20;

*   `TIMESTAMP`&#x20;

The value argument can be of any type except `STRING`.

💡**Special cases:**

*   Returns `NULL` if:
    *   there are no input rows&#x20;

    *   the metric column has only `NULL` values

    *   the value corresponding to the maximum metric is `NULL`.

*   Returns `NaN` if the input contains a `NaN`.

## Examples

We have a payments table that stores the records of payments by customers, along with discounts applied during the payment:

```pgsql
CREATE TABLE payments (
    paymentid int,
    customer_name string,
    price real,
    discount real
);
INSERT INTO payments (paymentid, customer_name, price, discount)
VALUES 
(1, 'Alex', 280.12, 0.1),
(2, NULL, 35.75, NULL),
(3, 'Alex', 45.1, 0.05),
(4, 'Alex', NULL, 0.4),
(5, 'John', NULL, 0.1),
(6, 'Bob', 50.45, 0.07),
(7, 'Bob', 120.5, 0.0);
```

```pgsql
SELECT * FROM payments;
```

It will create a table as shown below:

```pgsql
+-----------+---------------+--------+----------+
| paymentid | customer_name | price  | discount |
+-----------+---------------+--------+----------+
|         2 |               |  35.75 |          |
|         4 | Alex          |        |      0.4 |
|         3 | Alex          |   45.1 |     0.05 |
|         1 | Alex          | 280.12 |      0.1 |
|         6 | Bob           |  50.45 |     0.07 |
|         5 | John          |        |      0.1 |
|         7 | Bob           |  120.5 |        0 |
+-----------+---------------+--------+----------+
```

### #Case 1: `FOR_MAX()` on the whole table

For example, let's check the price for the highest discount applied to it:

```pgsql
SELECT FOR_MAX(discount, price) AS for_lowest_discount
FROM payments;
```

It will return the following output (`NULL` in this case):

```pgsql
+---------------------+
| for_lowest_discount |
+---------------------+
|                     |
+---------------------+
```

### #Case 2: `FOR_MAX()` with `GROUP BY` clause

For this example, we use a `GROUP BY` clause to group the customers, then use `FOR_MAX()` to get a discount for the highest price paid by each customer.

```pgsql
SELECT customer_name, FOR_MAX(price, discount) AS discount
FROM payments
GROUP BY customer_name;
```

Which will give the following result:

```pgsql
+---------------+----------+
| customer_name | discount |
+---------------+----------+
|               |          |
| Bob           |        0 |
| Alex          |      0.1 |
| John          |          |
+---------------+----------+
```

