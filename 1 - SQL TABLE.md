---
title: SQL TABLE
slug: Fr5E-sql-table
description: A collection of data organized in rows and columns. SQL table commands are used to generate, modify, and manage table data.
com/S_lGBDD7H53z1OcF8Kc79/HxL9M7iMQ16-_bSTHEzk9_img5232.png
createdAt: 2022-08-22T09:10:12.000Z
updatedAt: 2024-01-10T15:49:56.896Z
---

## What is a TABLE?

A table is a collection of data organized in rows and columns.

:::hint{type="info"}
💡 A table has a specified number of columns but can have any number of rows.
:::

## How does a TABLE work?

You may easily create data for real-time analysis and reporting by using the statement TABLE. It can connect datasets, filter datasets, apply SQL functions, batch together datasets (union), and more.

In tables, data is systematically arranged in a row-and-column structure like a spreadsheet. Each column represents a record field, and each row represents a detailed record.&#x20;

Let's see an example of a **library** table:

| **book\_ID** | **book\_Name**         | **book\_Author** |
| ------------ | ---------------------- | ---------------- |
| 00001        | The Catcher in the Rye | J. D. Salinger   |
| 00002        | Anna Karenina          | Leo Tolstoy      |

In the above table:

*   "**library**" is the table's name.

*   "**book\_ID**", "**book\_Name**" and "**book\_Author**" are the names of columns.&#x20;

*   The combination of data from multiple columns creates a row, e.g. (00002, "Anna Karenina,” and “Leo Tolstoy").

## What can we do with the TABLE?

You can perform various operations using a table. We do support some of the table operations, such as:

1.  [Create a new table.](https://docs.oxla.com/create-table-statement)

2.  [Delete an existing table.](https://docs.oxla.com/drop-statement)

3.  [Display a list of data from an existing table.](https://docs.oxla.com/select-statement)

4.  Display a list of data from tables using 'join'.
    And many more…💨

:::hint{type="info"}
By default, the table will be created in the `public` schema. Furthermore, you can also create and specify tables to other specific schemas. Click [here](https://docs.oxla.com/schema) for more info.
:::













