---
title: Text Type
slug: _a9W-string-type
description: String is a data type that stores a sequence of characters (text). This article covers the overview, format, and examples of the String data type.
createdAt: 2022-08-24T04:23:03.000Z
updatedAt: 2023-10-09T13:02:32.129Z
---

## Overview

The text data type is a UTF8-encoded text with Unicode support, which stores a sequence of characters (text).

:::hint{type="warning"}
**STRING** is an alias for the **TEXT** data type. You can create a table using **STRING. **However, it will be stored and processed equivalently to **TEXT**.
:::

## **Examples**

Let’s create an employee table with a text data type in each column:

```pgsql
CREATE TABLE employee (
    employeeName TEXT,
    employeeDept TEXT,
    employeeRole TEXT
);
INSERT INTO employee (employeeName, employeeDept, employeeRole)
VALUES ('John','Finance','Staff'),
       ('Maya','Product','Staff'),
       ('Jane','Finance','Staff'),
       ('Phil','HR','Manager');
```

:::hint{type="success"}
Insert the text value between the single quotes** ' '**.
:::

The created table is shown below:

```pgsql
+---------------+---------------+---------------+
| employeename  | employeedept  | employeerole  |
+---------------+---------------+---------------+
| John          | Finance       | Staff         |
| Maya          | Product       | Staff         |
| Jane          | Finance       | Staff         |
| Phil          | HR            | Manager       |
+---------------+---------------+---------------+
```

## **Text With SUBSTR Function**

The `substr()`** **function extracts a specific number of characters from a text.&#x20;

### **Syntax**

```pgsql
substr( text, start_position, length )
```

Let’s analyze the above syntax:

*   `text`* *is the specified text.

*   `start_position`* *is used as the starting position, specifying the part from which the substring will be returned. It is written as an int value.&#x20;

*   `length` is used to determine the number of characters to be extracted*. *It can be one or more characters.

:::hint{type="info"}
The first position in the `text` is 1.
:::

### **Example**

Insert a value into the text column.

```pgsql
SELECT substr('Watermelon',6,5) AS "Fruit";
```

The updated table is shown below:

```pgsql
+-------------+
| Fruit       |    
+-------------+
| melon       |
+-------------+
```

## **Text With LENGTH Function**

The `length()`** **function returns the number of characters in a text.&#x20;

:::hint{type="info"}
The number of characters might be different from the byte length.
:::

### **Syntax**

The length function will take a text as a parameter.

```pgsql
LENGTH (text);
```

### **Example**

Insert a value into the text column.

```pgsql
SELECT LENGTH ('UNITED STATES');
```

The updated table is shown below.

```pgsql
+---------+
| f       |
+---------+
| 13      | 
+---------+
```

:::hint{type="info"}
The `length()` function will also count spaces.
:::







