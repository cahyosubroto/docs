---
title: LOG
slug: B8em-log
createdAt: 2023-11-13T17:12:50.830Z
updatedAt: 2023-11-13T17:46:54.193Z
---

# **Overview**

The  `LOG()` function returns the base-10 logarithm or logarithm of the specified base of a given number.

# **Syntax**

The following illustrates the syntax of the `LOG()` function:

```pgsql
-- base-10 logarithm
LOG(number)

-- logarithm of number
LOG(base, number)
```

Where:

*   `base`: The base number. It must be greater than 0 and not equal to 1.

*   `number`: The number whose logarithm you want to obtain. It must be a positive number and greater than 0.

# **Examples**

Let's explore some examples of the `LOG()` function.

## **Case #1: Get base-10 logarithm**

### 1. Basic Usage

In this case, the `LOG()` function calculates the base-10 logarithm of a specified number.

```pgsql
SELECT LOG(2), LOG(2.5);
```

You will get the output below:

```pgsql
        log         |   log   
--------------------+---------
 0.3010299956639812 | 0.39794
```

### 2. Using Negative Value

In this example, the `LOG()` function is applied to negative numbers.

```pgsql
SELECT LOG(-1);
```

Any input of negative values will give you a `NaN` result.

```pgsql
 log 
-----
 NaN
```

### 3. Using Null Value

The `LOG()` function will return `NULL` if the argument is `NULL`.

```pgsql
SELECT LOG(null);
```

You will get a null result when an argument passed is null.

```pgsql
 log 
-----
    
```

### 4. Using Zero Value

In this example, the `LOG()` takes zero as an argument.

```pgsql
SELECT LOG(0);
```

You will get the output below:

```pgsql
    log    
-----------
 -Infinity
```

## **Case #2: Get Logarithm**

### 1. Basic Usage

In this case, the `LOG()` function calculates the logarithm of a specified number.

```pgsql
SELECT LOG(4, 16), 
       LOG(0.7, 0.8), 
       LOG(0.5, 10),
       LOG(1, null);
```

You will get the output below:

```pgsql
 log |    log     |    log    | log 
-----+------------+-----------+-----
   2 | 0.62562156 | -3.321928 |    
```

### 2. Using Table

Consider a database table called ***data*** with the following records:

```pgsql
CREATE TABLE data (
    data_column TEXT,
    x REAL,
    y REAL
);

INSERT INTO data (data_column, x, y) VALUES 
('Data 1', 0.5, 2),
('Data 2', 1, 2),
('Data 3', 5, 2),
('Data 4', 10, 10),
('Data 5', 50, 10);

SELECT * FROM data;
```

```pgsql
 data_column |  x  | y  
-------------+-----+----
 Data 1      | 0.5 |  2
 Data 2      |   1 |  2
 Data 3      |   5 |  2
 Data 4      |  10 | 10
 Data 5      |  50 | 10
```

Use the `LOG()` function to calculate the logarithm of column ***x*** (as a base) and column *y *(as a number):

```pgsql
SELECT *, LOG(y, x) AS LOG_Value FROM data;
```

You will get the result as shown below:

```pgsql
 data_column |  x  | y  | log_value 
-------------+-----+----+-----------
 Data 1      | 0.5 |  2 |        -1
 Data 2      |   1 |  2 |         0
 Data 3      |   5 |  2 |  2.321928
 Data 4      |  10 | 10 |         1
 Data 5      |  50 | 10 |   1.69897
```

