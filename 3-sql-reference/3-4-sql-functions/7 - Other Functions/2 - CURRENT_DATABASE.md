---
title: CURRENT_DATABASE
slug: YIxM-currentdatabase
description: A quick guide to the CURRENT_DATABASE() function, which returns the current database's name, complete with syntax and an example.
createdAt: 2023-03-30T02:11:38.000Z
updatedAt: 2023-10-09T13:02:32.129Z
---

## **Overview**

The `CURRENT_DATABASE()` returns the current database's name.&#x20;

## **Syntax**

The following syntax describes `CURRENT_DATABASE()` function.

```pgsql
SELECT CURRENT_DATABASE();
```

It does not require any argument to operate.

## **Example**

In the following example, we will obtain the database name to which we are currently connected. 

```pgsql
SELECT CURRENT_DATABASE();
```

The function will return the result with the database name:

```pgsql
+------------+
| f          |
+------------+
| Oxla       |
+------------+
```

