---
title: Timestamp Functions
slug: JPyM-timestamp-functions
description: Timestamp functions return a date-time value based on a specified timestamp/interval. It can also be used to manipulate dates and times in various ways.
createdAt: 2022-08-24T04:28:51.000Z
updatedAt: 2024-02-29T14:50:33.080Z
---

Timestamp functions return a date-time value based on a specified timestamp/interval. Oxla supports the following Timestamp functions:

| **Functions**                                                            | **Description**                                                                                                           |
| :----------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------ |
| [CURRENT\_TIMESTAMP()](https://docs.oxla.com/currenttimestamp)           | Returns the current date and time as a timestamp data type.                                                               |
| [FORMAT\_TIMESTAMP()](https://docs.oxla.com/formattimestamp)             | Modifies the current timestamp into a different format.                                                                   |
| [UNIX\_SECONDS()](https://docs.oxla.com/unixseconds)                     | Converts a given timestamp to a UNIX timestamp in seconds.                                                                |
| [UNIX\_MILLIS()](https://docs.oxla.com/unixmillis)                       | Converts a given timestamp to a UNIX timestamp in milliseconds.                                                           |
| [UNIX\_MICROS()](https://docs.oxla.com/unixmicros)                       | Converts a given timestamp to a UNIX timestamp in microseconds.                                                           |
| [TIMESTAMP\_SECONDS()](https://docs.oxla.com/timestampseconds)           | Converts a UNIX timestamp in seconds to a timestamp.                                                                      |
| [TIMESTAMP\_MILLIS()](https://docs.oxla.com/timestampmillis)             | Converts a UNIX timestamp in milliseconds to a timestamp.                                                                 |
| [TIMESTAMP\_MICROS()](https://docs.oxla.com/timestampmicros)             | Converts a UNIX timestamp in microseconds to a timestamp.                                                                 |
| [TIMESTAMP\_TRUNC()](https://docs.oxla.com/timestamptrunc)               | Truncates a given timestamp to the nearest time part. Supported time parts are YEAR, MONTH, DAY, HOUR, MINUTE, and SECOND |
| [EXTRACT()](https://docs.oxla.com/extract)                               | Extracts some part of a specified timestamp or interval.                                                                  |
| [TO\_TIMESTAMP()](https://docs.oxla.com/totimestamp)                     | Converts a string into a timestamp based on the provided format.                                                          |
| [DATE\_TRUNC()](https://docs.oxla.com/datetrunc)                         | Truncates intervals or timestamps/time zones to a specified field.&#x20;                                                  |
| [TO\_CHAR() from Timestamp](https://docs.oxla.com/tochar-from-timestamp) | Formats a timestamp into a string using a given format.                                                                   |

