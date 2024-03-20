---
title: TO_CHAR() from Timestamp
slug: PoRh-tochar-from-timestamp
description: The TO_CHAR function formats a timestamp into a string using a given format.
createdAt: 2024-02-29T14:39:55.419Z
updatedAt: 2024-02-29T14:45:06.088Z
---

## **Overview**

The `TO_CHAR` function formats a timestamp into a string using a given format.

## **Syntax**

The syntax for using the `TO_CHAR` function is as follows:

```pgsql
TO_CHAR(timestamp, format_string)
```

Parameters in the syntax include:

*   `timestamp`: The `TIMESTAMP` or `TIMESTAMP WITH TIMEZONE` to be formatted to string.&#x20;

*   `format`: The format of the input string.&#x20;

## **Format**

Format string supports following template patterns (can be lowercase):

| **Pattern**                      | **Description**                    |
| -------------------------------- | ---------------------------------- |
| `YYYY`                           | Year (1-9999)&#x20;                |
| `HH`                             | Hour of day (1–12)&#x20;           |
| `HH12`                           | Hour of day (1–12)&#x20;           |
| `HH24`                           | Hour of day (0–23)&#x20;           |
| `MI`                             | Minute (0–59)                      |
| `SS`                             | Second (0–59)&#x20;                |
| `MS`                             | Millisecond (0–999)&#x20;          |
| `US`                             | Microsecond (0–999999)             |
| `AM`, `am`, `PM` or `pm`         | Meridiem indicator without periods |
| `A.M.`, `a.m.`, `P.M.` or `p.m.` | Meridiem indicator with periods    |

### ❌ Limitations

*   All text inside double quote `"{text}" `will not be considered a pattern.

*   The quote character `""` will not appear in the result string.&#x20;

*   Any text that does not match any pattern will be preserved in the result string.

## **Examples**

### Case 1: Timestamp with Microseconds

The query aims to format a timestamp to display the year, month, day, hour, minute, second, and microseconds (`YYYY-MM-DD HH24:MI:SS.US`).

```pgsql
SELECT TO_CHAR('2012-03-04 05:06:07.080910'::timestamp, 'YYYY-MM-DD HH24:MI:SS.US');
```

The output shows the timestamp '2012-03-04 05:06:07.080910'.

```pgsql
          to_char           
----------------------------
 2012-03-04 05:06:07.080910
```

### Case 2: Time with Milliseconds and Meridiem

This query format a timestamp in a 12-hour clock format with the meridiem indicator (`p.m`).

```pgsql
SELECT TO_CHAR('2012-03-04 05:06:07.080910'::timestamp, 'HH12-MI-SS.MS p.m.');
```

The output shows the time 5:06:07 a.m. with milliseconds.

```pgsql
      to_char      
-------------------
 05-06-07.080 a.m.
```

### Case 3: Time with Meridiem Indicator

This query format a timestamp to display time in a 12-hour clock format along with the meridiem indicator (`AM`).

```pgsql
SELECT TO_CHAR('2012-03-04 17:06:07.080910'::timestamp, 'HH-MI-SS AM');
```

The output presents the time '17:06:07' in the format 'HH-MI-SS AM': 5:06:07 PM.

```pgsql
  to_char   
-------------
 05-06-07 PM
```

### Case 4: Timestamp with Text

This example adds custom text to the timestamp output.

```pgsql
SELECT TO_CHAR('2012-03-04 17:06:07.080910'::timestamp, 'Text "HH24-MI-SS" {HH24-MI-SS}');
```

It will return the output below.

```pgsql
          to_char           
----------------------------
 Text HH24-MI-SS {17-06-07}
```

