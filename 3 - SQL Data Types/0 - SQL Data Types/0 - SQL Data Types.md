---
title: SQL Data Types
slug: 2JPq-sql-data-types
description: Here is a complete list of the available data types within the SQL supported in Oxla.
createdAt: 2022-08-22T09:11:05.000Z
updatedAt: 2023-10-09T13:02:32.129Z
---

While creating a table, you need to specify a data type for each column to define what kind of data you want to store. This section will look into the various data types supported in Oxla. Now, let’s get an overview of each data type:

| **Data Types**                | **Definition**                                             | **Format**                                     |
| ----------------------------- | ---------------------------------------------------------- | ---------------------------------------------- |
| `BOOL`                        | Boolean value.                                             | `True` or `False`.                             |
| `TEXT`                        | UTF8 encoded string with Unicode support.                  | 'text'                                         |
| `DATE`                        | Date value.                                                | `YYYY-MM-DD`                                   |
| `TIMESTAMP WITHOUT TIME ZONE` | Time and date values without a time zone.                  | `YYYY-MM-DD [HH:MM:SS[.SSSSSS]]`               |
| `TIMESTAMP WITH TIME ZONE`    | Date and time values, including the time zone information. | `YYYY-MM-DD HH:MM:SS.SSSSSS+TZ`                |
| `TIME`                        | Time values without any date information.&#x20;            | `HH:MM:SS[.SSSSSS]`                            |
| `JSON`                        | A value in JSON standard format.                           | `variable_name JSON`                           |
| `INTERVAL`                    | Encodes a span of time                                     | `year-month (YYYY-MM); day-time (DD HH:MM:SS)` |
| `INT`                         | 32-bit signed integer                                      | one or more digits "0" to "9"                  |
| `BIGINT`                      | 64-bit signed integer                                      | large numeric/decimal value                    |
| `REAL`                        | 32-bit floating point number                               | `float(n)`                                     |
| `DOUBLE PRECISION`            | 64-bit floating point number                               | `decimal(p, s)`                                |

