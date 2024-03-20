---
title: JSON_EXTRACT_PATH_TEXT
slug: OUA_-jsonextractpathtext
description: The JSON_EXTRACT_PATH_TEXT() function extracts JSON nested value from a specified JSON value according to the defined path. Consider these related details.
createdAt: 2023-03-28T08:00:52.000Z
updatedAt: 2023-10-09T13:02:32.129Z
---

## **Overview**

The `JSON_EXTRACT_PATH_TEXT()` function extracts JSON nested value from a specified JSON value according to the defined path.&#x20;

:::hint{type="info"}
This function may be similar to the `JSON_EXTRACT_PATH()`. This function returns a value of type string instead of type JSON.
:::

## **Syntax**

The `JSON_EXTRACT_PATH_TEXT()` syntax is shown below:&#x20;

```pgsql
JSON_EXTRACT_PATH_TEXT(from_json JSON, path TEXT[])
```

The required arguments are explained below.

*   `from_json`: the JSON value to extract.

*   `path`: the path to extract.

### **Another Option**

Besides the syntax above, Oxla provides and supports the use of operators in queries. See the syntax below:

```pgsql
SELECT 'from_json'::JSON ->> 'path';
```

*   `from_json`: the JSON value from which to extract.

*   `::JSON`: a symbol that casts the string literal to a JSON type.

*   `path`: key of the field that we want to extract.

## **Example**

**1)** This example shows how to use the `JSON_EXTRACT_PATH_TEXT()` function to extract values ​​from a JSON object at a specified index.&#x20;

Run the following query:

```pgsql
SELECT JSON_EXTRACT_PATH_TEXT('{"a": "Oxla", "b": {"x": 1.234, "y": 4.321}}', 'a') AS "result a";
```

**or**

```pgsql
SELECT '{"a": "Oxla", "b": {"x": 1.234, "y": 4.321}}'::JSON ->> 'a' AS "result a";
```

**2)** The JSON\_EXTRACT\_PATH\_TEXT() function extracts the values and returns the output below:

```pgsql
+------------+
| result a   |
+------------+
| "Oxla"     |
+------------+
```

