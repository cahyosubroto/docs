---
title: String Functions
slug: bUxq-string-functions
description: String functions are used to analyze and manipulate string values. We'll go over the different String functions supported in this comprehensive table.
createdAt: 2022-08-24T04:28:40.000Z
updatedAt: 2023-10-09T13:02:32.129Z
---

String functions are used to analyze and manipulate string values. Oxla supports the following String functions:

| **Functions**                                            | **Description**                                                                                                                                                                                                                   |
| -------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [LENGTH()](https://docs.oxla.com/length)                 | Returns the number of characters in a string.                                                                                                                                                                                     |
| [LOWER()](https://docs.oxla.com/lower)                   | Makes string lowercase.&#x20;                                                                                                                                                                                                     |
| [UPPER()](https://docs.oxla.com/upper)                   | Makes string upper case.&#x20;                                                                                                                                                                                                    |
| [STARTS\_WITH()](https://docs.oxla.com/startswith)       | It returns true if the first argument starts with the second argument.                                                                                                                                                            |
| [ENDS\_WITH()](https://docs.oxla.com/endswith)           | It returns true if the first argument ends with the second argument.                                                                                                                                                              |
| [CONCAT()](https://docs.oxla.com/concat)                 | Concatenates all inputs into a single result.Concatenates all inputs into a single result.Concatenates all inputs into a single result.Concatenates all inputs into a single result.Concatenates all inputs into a single result. |
| [SUBSTR()](https://docs.oxla.com/substr)                 | Retrieves substring.                                                                                                                                                                                                              |
| [STRPOS()](https://docs.oxla.com/strpos)                 | Finds the position at which the substring (defined as a second argument) starts within the string (defined as a first argument).                                                                                                  |
| [REGEXP\_REPLACE()](https://docs.oxla.com/regexpreplace) | Substitutes new text for substrings that match POSIX regular expression patterns.                                                                                                                                                 |
| [REPLACE()](https://docs.oxla.com/replace)               | Finds and replaces a substring with a new one in a string.                                                                                                                                                                        |

String operators:

| **Functions**                                                                                                      | **Description**                                                                                                  |
| ------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------- |
| text \~ text -> boolean                                                                                            | Return true if the first argument matches the pattern of the second argument in case sensitive match.            |
| text \~\* text -> booleanReturn true if first argument matches pattern of second argument in case sensitive match. | Return true if the first argument matches the pattern of the second argument in a case-insensitive match.        |
| text !\~ text -> boolean                                                                                           | Return true if the first argument does not match the pattern of the second argument in case sensitive match.     |
| text !\~\* text -> boolean                                                                                         | Return true if the first argument does not match the pattern of the second argument in a case-insensitive match. |

 





