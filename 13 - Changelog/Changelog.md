---
title: Changelog
slug: ZrsK-change
createdAt: 2023-11-23T13:59:14.087Z
updatedAt: 2024-02-21T16:48:28.763Z
---

## Oxla beta release 1.14.0 - 21/2/24

### ➕ ADDED

*   A sanity check on oxla startup for minimal `memory.max` and `memory.non_query_max` configuration.

*   `information_schema.columns`, which contain information about all columns in user namespaces.

*   `pg_language` table.

*   `to_char function` converting timestamp/timestamptz to string using given format string.

*   Support for int8 and int4 binary parameters in Postgres extended query protocol.



## Oxla beta release 1.13.0 – 16/2/24

### ➕ ADDED

*   Add` information_schema.referential_constraints` table for tools integration purposes.

*   Add `to_char` function to convert the number to string using the given format string.

*   Add `to_timestamp` function to convert the string to timestamp using given format string.

*   Cast from time to `interval date_trunc` function working like Postgres `date_trunc`.

*   DISCARD ALL to reset all session variables.

*   Add support for `pg_catalog.has_database_privilege()` function.

*   Possibility to the hardcode leader of the cluster in config.

*   Postgres-like tables: `pg_enum`, `pg_range`, `information_schema.character_sets`.

*   Enabled optimization, taking advantage of complex expressions in filters.

*   Add `pg_encoding_to_char` and `pg_size_pretty function`function.

*   Add `pg_catalog.obj_description` function although descriptions are not supported by Oxla, always returns null.

*   Add table `tables` in the information\_schema namespace.

*   Add table `pg_catalog.pg_tablespace` , `pg_catalog.pg_database` , `information_schema.key_column_usage`, and `pg_catalog.pg_am` support.

*   Support for operator interval div number.

### ⭐ CHANGED

*   Reduced the amount of s3 requests when performing `COPY FORM (FORMAT CSV)`.

*   Improved the error messages in `INSERT INTO VALUES` queries.

### 🪛 FIXED

*   Increased stability of `COPY FROM` queries with large inputs.

*   Fixed the issue with `INSERT INTO SELECT` queries where data types were not cast to proper types automatically.

## Oxla beta release 1.8.0 - 12/1/24

### ➕ ADDED

*   Optimization of HAVING clause when combined with WHERE clause in the same query.

*   Support for String Constants with C-Style Escapes.

*   Support for `COPY (table|select statement) TO filename.csv (options) `query.

*   Support for operator interval \* float.

### 🪛 FIXED

*   Fixed the instability issue when the whole table's content has been deleted using `DELETE FROM <table_name>`

*   Fixed the instability cluster issue when disconnecting a disconnected node bug in cluster monitoring.

*   Fixed a bug that appeared during conversion intervals when the interval used a date/time format.

*   Fixed the error handling response when the pipeline startup failed.

*   Fixed a bug with duplicated name detection caused the cluster to be inoperable after startup.

*   Fixed a bug on `INSERT INTO table SELECT` statement due to the lifetime issues.

## Oxla beta release 1.4.0 - 14/12/23

### ➕ ADDED

*   Support for date - date operator.

*   Support for time - time operator.

*    Support for date + time operator.

### ⭐ CHANGED



*   Improved performance of query planning.

### 🪛 FIXED

*   Fixed intermittent crashes in the GROUP BY.

*   Fixed a bug that happens when deleting the index table.

*   Fixed the Google Cloud Storage compatibility issue.&#x20;

*   Fixed an issue that could result in a crash when running GROUP BY over columns with very high cardinality.

*   Fixed an issue that could result in deadlock upon cluster startup.

### 🪲 TEMPORARY COMPATIBILITY ISSUES

*   The default AWS S3 endpoint is used when no endpoint is specified in the COPY statement.&#x20;

## Oxla beta release 1.3.0 - 06/12/23

### 🪲 TEMPORARY COMPATIBILITY ISSUES

*   The COPY statement with unsupported FORMAT (tbl / binary / bin) will return error ("... format not supported"). Previously all these formats, despite their names, resulted in importing CSV. COPY without provided FORMAT will still use CSV as default format.

*   The format of internal messages passed between Oxla nodes for COPY CSV changed, so the new node and old node must not be in the same cluster when COPY is being executed.

*   We are working closely with our team to resolve this issue as soon as possible.

### 🪛 FIXED

*   Fixed the degradation error failure when OXLA\_HOME was an empty S3 folder created before Oxla started.&#x20;

*   Fixed a bug where OXLA would not return an error when cast would overflow the integer type.

*   Fixed a bug where OXLA would return an error when casting values from Date type to Timestamp/Timestamptz.

*   Fixed the issue of improper read of storage\_config.s3.http parameter.

*   Fixed a bug in an optimization causing some queries using aggregation functions as WHERE conditions to fail to plan and run on OXLA.

## Oxla beta release 1.2.0 - 27/11/23

### ➕ ADDED

*   Handling columns specified in the INSERT INTO with SELECT. e.g. INSERT INTO tbl1(c2) SELECT col1 FROM tbl2.

### ⭐ CHANGED

*   Extended support for implicit conversions of timestamp-like types in INSERT and COPY queries.

### 🪛 FIXED

*   Fixed the arithmetic operator was used to determine the output type.

*   Fixed the errors with storage communication.

*   Fixed the error handling when downcasting number types with losing data.

*   Fixed the issue that Oxla sometimes left files when dropping tables or deleting data.

## Oxla beta release 1.1.0 - 20/11/23

### ➕ ADDED

*   Support for Basic INSERT INTO \[table] SELECT \[statement].

### ⭐ CHANGED

*   Improved performance of most GROUP BY variants.

*   Slight performance improvement of GROUP BY over numeric columns.

*   Degraded node stays in the cluster.

### 🪛 FIXED

*   Fixed the issue with the node connection to the cluster.

*   Disabled the empty string as a valid internal value.

*   Fixed the failures when reading timestamp values from CSV.

