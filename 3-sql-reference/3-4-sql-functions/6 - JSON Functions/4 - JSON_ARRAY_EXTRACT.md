---
title: JSON_ARRAY_EXTRACT
slug: LUGS-jsonarrayextract
description: A guide on how to use the JSON array extract function to return a JSON array as a set of JSON values.
createdAt: 2023-03-28T08:09:02.000Z
updatedAt: 2023-10-09T13:02:32.129Z
---

## **Overview**

The `JSON_ARRAY_EXTRACT()` function returns the JSON array as a set of JSON values. 

## **Syntax**

The `JSON_ARRAY_EXTRACT()` has the basic syntax as seen below.

```pgsql
JSON_ARRAY_EXTRACT('json_array'::JSON,id);
```

`JSON_ARRAY_EXTRACT()` requires the following parameters:

*   `json_array`: the array to be extracted.

*   `::JSON`: argument indicating that the query is of type JSON.

*   `id`: ID of the element that we want to extract. It is read in an array format that starts with 0.

### **Another Option**

`JSON_ARRAY_EXTRACT` can also be achieved with the `->` operator, as shown in the syntax below:

```pgsql
SELECT 'from_json'::JSON -> path;
```

*   `from_json`: the JSON value from which to extract.

*   `::JSON`: a symbol that casts the string literal to a JSON type.

*   `path`: key of the field that we want to extract.

## **Examples**

### **Case #1: Basic JSON\_ARRAY\_EXTRACT() function**

**1)** In the below example, we will extract a JSON array as a JSON set.

```pgsql
SELECT JSON_ARRAY_EXTRACT('["Bougenvile", 2, 12, "Lily"]'::JSON,3);
```

**or**

```pgsql
SELECT ('["Bougenvile", 2, 12, "Lily"]'::JSON -> 3);
```

**2)** The extracted array will look like the following.

```pgsql
+------------+
| f          |
+------------+
| "Lily"     |
+------------+
```

### Case #2: Extract element of JSON array as text

**1)** In this case, we will extract the element of the JSON array as text with the `->>` operator.

```pgsql
SELECT ('["Bougenvile", 2, 12, "Lily"]'::JSON ->> 1);
```

**2)** You will get the final output as follows:

```pgsql
+------------+
| f          |
+------------+
| 2.000000   |
+------------+
```

