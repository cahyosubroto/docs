---
title: CURRENT_SCHEMA
slug: PBk4-currentschema
description: A quick and easy guide to the The CURRENT_SCHEMA() function, which returns the name of the first existing schema in Oxla.
createdAt: 2023-03-27T02:05:05.000Z
updatedAt: 2023-10-09T13:02:32.129Z
---

## **Overview**

The `CURRENT_SCHEMA()` function returns the name of the first existing schema.

:::hint{type="info"}
It will return NULL if none of the schemas from `search_path` exist.&#x20;
:::

## **Syntax**

`CURRENT_SCHEMA()` function has the following syntax:

```pgsql
SELECT CURRENT_SCHEMA();
```

Another method is to omit the parenthesis from the above syntax.

```pgsql
SELECT CURRENT_SCHEMA;
```

:::hint{type="info"}
It does not require any argument to operate.
:::

## **Example**

The following example shows how to get the current schema name using `CURRENT_SCHEMA()` function.

```pgsql
SELECT CURRENT_SCHEMA();
```

The final result will display the schema that you currently use:

```pgsql
+------------+
| f          |
+------------+
| public     |
+------------+
```

