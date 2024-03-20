---
title: TO_CHAR() from Number
slug: SH4O-tochar-from-number
description: The TO_CHAR function formats a number into a string using a given format.
createdAt: 2024-02-29T14:34:02.136Z
updatedAt: 2024-02-29T14:39:48.771Z
---

## **Overview**

The `TO_CHAR` function formats a number into a string using a given format.

## **Syntax**

The syntax for using the `TO_CHAR` function is as follows:

```pgsql
TO_CHAR(value, format_string)
```

Parameters in the syntax include:

*   `value`: A number that will be formatted to a string.

*   `format`: The format of the input string.

## **Format**&#x20;

Format string supports following template patterns (can be lowercase):

| **Pattern** | **Description**                                            |
| ----------- | ---------------------------------------------------------- |
| `9 `        | Digit position (may be dropped if insignificant)           |
| `0`         | Digit position (never dropped)                             |
| `.`&#x20;   | Decimal point                                              |
| `,`&#x20;   | Group (thousands) separator                                |
| `D`&#x20;   | Decimal point                                              |
| `G`&#x20;   | Group separator                                            |
| `S`         | Plus/minus sign directly before or after a number          |
| `PL`        | Plus sign in the specified position (for negative numbers) |
| `MI`        | Minus sign in specified position (for positive numbers)    |
| `SG`        | Plus/minus sign in the specified position.                 |

### ❌ Limitations

*   All text inside double quote `"{text}"` will not be considered a pattern.

*   The quote character `""` will not appear in the result string.

*   Any text that does not match any pattern will be preserved in the result string.

## **Examples**

### Case 1: **Formatting with Leading Zeros**

The query formats 123.456 with leading zeros using the pattern '00000.00000'.

```pgsql
SELECT TO_CHAR(123.456, '00000.00000');
```

The output displays the formatted number as shown below.

```pgsql
   to_char    
--------------
  00123.45600
```

### Case 2: **Formatting with Variable Length**

The query formats the number 123.456 with a variable-length pattern '99999.99999'.

```pgsql
SELECT TO_CHAR(123.456, '99999.99999');
```

The output displays the formatted number as shown below.

```pgsql
   to_char    
--------------
    123.45600
```

### Case 3: **Formatting with Group**

The query formats the number 123456 with grouping separators using the pattern '9,999,999,999'.

```pgsql
SELECT TO_CHAR(123456, '9,999,999,999');
```

It will return the output below.

```pgsql
    to_char     
----------------
        123,456
```

### Case 4: **Formatting with Negative Number**

The query formats the number -123 with a custom pattern including the sign.

```pgsql
SELECT TO_CHAR(-123, '"Number formatted with pattern:000S":{000S}');
```

The output shows the custom-formatted number.

```pgsql
                  to_char                  
-------------------------------------------
 Number formatted with pattern:000S:{123-}
```

### Case 5: **Formatting with Sign**

The query formats the number -123.456 with a custom pattern including the sign and separated integer.

```pgsql
SELECT TO_CHAR(-123.456, '"Sing is: "SG" integer part is: "999", mantissa part is: ".999');
```

The output shows the customized format as shown below.

```pgsql
                         to_char                         
---------------------------------------------------------
 Sing is: - integer part is: 123, mantissa part is: .456
```

