---
title: EXTRACT
slug: 2guJ-extract
description: The EXTRACT() function takes out a specific component (such as year, month, day, hour, minute, or second) from a timestamp value. Here are more details.
createdAt: 2022-09-15T06:15:51.000Z
updatedAt: 2023-10-09T13:02:32.129Z
---

## Overview

The `EXTRACT()` function extracts a given part from a specified source. The source must be a value expression of timestamp, time, or interval.

### Syntax

```pgsql
EXTRACT(field from source)
```

Let’s analyze the above syntax:

- `field`: used to specify the time parts that are to be extracted.

- `source`: used to identify a date/time value. The value type is `TIMESTAMP` (YYYY-MM-DD HH\:MM\:SS) or `INTERVAL` (year - month - day hour - minute - second).

### Input and Return Type

The table below shows the supported input types of `field` and the return type of the `EXTRACT()` function:

![](../../../assets/extract.png)

## Examples&#x20;

### #Case 1: `EXTRACT()` with Timestamp - Year

The below example uses the `EXTRACT()` function to extract a given timestamp’s **YEAR**:

```pgsql
SELECT EXTRACT(YEAR FROM TIMESTAMP '2020-12-31 13:30:15');
```

The final output will be as follows:

```pgsql
+----------+
| extract  |
+----------+
| 2020     |
+----------+
```

### #Case 2: `EXTRACT()` with Timestamp - Month

Here we will use the `EXTRACT()` function to extract a given timestamp’s **MONTH:**

```pgsql
SELECT EXTRACT(MONTH FROM TIMESTAMP '2016-10-31 13:30:15');
```

The final output will take the month’s part of a given timestamp:

```pgsql
+----------+
| extract  |
+----------+
| 10       |
+----------+
```

### #Case 3: `EXTRACT()` with Interval - Day

In this example, we will extract the **DAY **part of a given interval:

```pgsql
SELECT EXTRACT(DAY FROM INTERVAL '6 years 8 months 20 days 4 hours 47 minutes 22 second' );
```

The final output will be as follows:

```pgsql
+----------+
| extract  |
+----------+
| 20       |
+----------+
```

### #Case 4: `EXTRACT()` with Interval - Second

The below example uses the `EXTRACT()` function to extract seconds from the given interval.

```pgsql
SELECT EXTRACT(SECOND FROM INTERVAL '6 years 2 months 13 days 8 hours 30 minutes 43 second' );
```

The final output will be as follows:

```pgsql
+------------+
| extract    |
+------------+
| 43.000000  |
+------------+
```
