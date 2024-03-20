---
title: CREATE INDEX statement
slug: uLLy-create-index-statement
description: Let's cover the overview, syntax, and use cases of the CREATE INDEX statement in regards to tables.
com/S_lGBDD7H53z1OcF8Kc79/kpGI0RcRUhR00xzL-mUld_img5232.png
createdAt: 2022-11-02T12:15:20.000Z
updatedAt: 2023-10-09T13:02:32.129Z
---

## Overview

Oxla allows creating a single index on an empty table (before any row is added to the table). This index is used to sort data on storage, ordering it using indexed columns. This greatly speeds up the scanning table, reducing the scan just to the relevant portion of data.

## Syntax

While creating an index one should define the index name, the table for which the index is created, list of columns for which the index was created.

```pgsql
CREATE INDEX index_name ON table_name(column_name_1, ...);
```

## Using index

The index is used when a query uses a range of values from a given index. To do that user must compare the index column with the literal.

## Performance impact

### Single column index

Let's consider the given table:

```pgsql
CREATE TABLE lineorder (
    customer_id              INTEGER NOT NULL,
    part_key_id              INTEGER NOT NULL,
    quantity                 INTEGER NOT NULL,
    unit_price               FLOAT NOT NULL,
    commit_date              DATE NOT NULL
);
```

Let's say we want to calculate the value of orders for 5th November 2019:

```pgsql
SELECT SUM(unit_price * quantity) AS revenue FROM lineorder WHERE commit_date = '2019-11-05';
```

This query will scan all data for columns unit\_price, quantity, and commit\_date for table lineorder. To speed this query up we can use the index:

```pgsql
CREATE INDEX lineorder_index ON lineorder(commit_date);
```

If the table was created with this index then the query mentioned above will scan just over rows for which `commit_date` is equal to 2019-11-05.

Unfortunately, expressions like the one shown below will not take advantage of the index.

```pgsql
SELECT SUM(unit_price * quantity) AS revenue
FROM lineorder
WHERE EXTRACT(YEAR FROM commit_date) = 2019;
```

### Multi-column index

The index might contain multiple columns. Let's consider a different index for the table line order mentioned above:

```pgsql
CREATE INDEX lineorder_index ON lineorder(part_key_id, commit_date);
```

Thanks to this index, extracting orders related to a given part or orders for a given part and given time range will be very fast. Example of queries taking advantage of index:

```pgsql
SELECT SUM(unit_price * quantity) AS revenue
FROM lineorder
WHERE part_key_id = 5;

SELECT SUM(unit_price * quantity) AS revenue
FROM lineorder
WHERE part_key_id = 5 OR part_key_id = 7;

SELECT SUM(unit_price * quantity) AS revenue
FROM lineorder
WHERE part_key_id >= 5 AND part_key_id <= 7;

SELECT SUM(unit_price * quantity) AS revenue
FROM lineorder
WHERE
    part_key_id = 5 AND
    commit_date BETWEEN '2019-11-01' AND '2019-11-15';

SELECT SUM(unit_price * quantity) AS revenue
FROM lineorder
WHERE
    part_key_id >= 5 AND part_key_id <= 7 AND
    commit_date BETWEEN '2019-11-01' AND '2019-11-15';
```

A query that will not take advantage of the index:

```pgsql
SELECT SUM(unit_price * quantity) AS revenue
FROM lineorder
WHERE commit_date BETWEEN '2019-11-01' AND '2019-11-15';
```

