---
title: TIMESTAMP_TRUNC
slug: hWFE-timestamptrunc
description: This function rounds a timestamp to a specific day_time granularity, resulting in a truncated timestamp. This guide helps users understand this function.
createdAt: 2023-03-09T13:25:16.000Z
updatedAt: 2023-10-09T13:02:32.129Z
---

## Overview

The `TIMESTAMP_TRUNC()` function rounds a timestamp to a specific `day_time` granularity, resulting in a truncated timestamp.

### Syntax

```pgsql
SELECT TIMESTAMP_TRUNC(TIMESTAMP 'YYYY-MM-DD hour:min:sec', day_time);
```

`day_time` can be replaced with various time values as follows:

*   `SECOND`

*   `MINUTE`

*   `HOUR`

*   `DAY`

*   `MONTH`

*   `YEAR`

## Examples

### #Case 1: `TIMESTAMP_TRUNC()` - Hour

The following example shows how to round the hour to the closest value:

```pgsql
SELECT TIMESTAMP_TRUNC(TIMESTAMP '2017-09-18 14:43:39.02322', HOUR) ;
```

The final result will display the current date and time in your timezone:

```pgsql
+-----------------------------+
| f                           |
+-----------------------------+
| 2017-09-18 14:00:00.00000   |
+-----------------------------+
```

### #Case 2: `TIMESTAMP_TRUNC()` - Minute

Here we will truncate the specified timestamp into the nearest value:

```pgsql
SELECT TIMESTAMP_TRUNC(TIMESTAMP '2005-03-18 14:13:13', MINUTE) ;
```

The result will return the truncated timestamp as shown below:

```pgsql
+-----------------------------+
| f                           |
+-----------------------------+
| 2005-03-18 14:13:00.00000   |
+-----------------------------+
```

### #Case 3: Basic `TIMESTAMP_TRUNC()` function - Year

Run the following query to round the date to the closest value:

```pgsql
SELECT TIMESTAMP_TRUNC(TIMESTAMP '2023-03-04', YEAR);
```

The function will truncate the year and return the following result:

```pgsql
+-----------------------------+
| f                           |
+-----------------------------+
| 2023-01-01 00:00:00.00000   |
+-----------------------------+
```

