---
title: COPY FROM with Delimiter
slug: aww2-copy-from-with-delimiter
description: A COPY FROM statement is used to import data to a table with a Delimiter (a character that separates text strings). Let's cover some more details here.
createdAt: 2023-02-17T15:23:42.000Z
updatedAt: 2023-10-09T13:02:32.129Z
---

## **Overview**

A delimiter is a character that separates text strings. Common delimiters are:

*   Commas (,)

*   Semicolon (;)

*   Quotes ( ", ' )

*   Dash (-)

*   Pipes (|)

*   Slashes ( / \ ).

**By default, the COPY FROM function accepts commas (,).** **By default, the COPY FROM function accepts commas **

## **Syntax**

The syntax for** COPY FROM** is as follows:

```pgsql
COPY table_name FROM 'file_path' (DELIMITER 'delimiter');
```

Two parameters need to be specified in the syntax:

*   `table_name`: the table that will receive data from the file.

*   `file_path`: a link to the file location in the server.

*   `DELIMITER 'delimiter'`: the delimiter used in the CSV file.

## **Example**

Let’s have a look at the step-by-step below:

### Step #1: Create a CSV File

First, you should create a CSV file and store it on your local computer. In this case, we use Dash ( - ) character to separate the text.

> create a table - 1.0
> modify a table - 1.2
> drop a table - 2.2
> rename a table - 2.0

### Step #2:  Import FIle from Local to Server

You can use the syntax below for importing the file to the server:

```typescript
aws s3 cp ~/[file location on your local computer] s3://[server location]/[file name]
```

Next, import the file to the server using the above syntax:

```typescript
aws s3 cp ~/Documents/feature2.csv s3://oxla-testdata/cayo/feature2.csv
```

If it’s successfully imported, you will get the following result:

```typescript
upload: Documents/feature2.csv to s3://oxla-testdata/cayo/feature2.csv
```

### Step #3:  Connect to Oxla Server

Connect to the Oxla server using the command below:

```pgsql
psql -h buildfarm.oxla.com -p 6000
```

You are now in the Oxla environment if you get the output below.

```pgsql
psql (15.1 (Ubuntu 15.1-1.pgdg22.10+1), server Oxla 1.0)
WARNING: psql major version 15, server major version 0.0.
         Some psql features might not work.
Type "help" for help.
```

### Step #4:  Create a Table

Before creating a table, check for duplicate tables with the statement below:

```pgsql
DESCRIBE DATABASE
```

In return, you will retrieve a list of existing tables in Oxla.

```pgsql
+----------------------------+
| name                       |
+----------------------------+
| supplier_scale_1_no_index  |
| features                   |
| orders                     |
| features2                  |
| featurestable              |
| featurestable1             |
| featurestable10            |
+----------------------------+
```

:::hint{type="warning"}
Ensure you are not creating duplicate tables.
:::

Create a “**featurelisttable**” table using the command below:

```pgsql
CREATE TABLE featurelisttable (featurename string, version float);
```

### Step #5:  Copy the CSV File Into Table

Because we are using Dash ( - ), we need to add a DELIMITER param with a specified character, as shown below:

```pgsql
COPY featurelisttable FROM 's3://oxla-testdata/cayo/feature2.csv' (DELIMITER '-');
```

You will get the following successful result:

```pgsql
--
(0 rows)
```

Otherwise, you will get the error message below:

```pgsql
ERROR: unexpected data at line: 1 col: 0 position: 108, expected , but got:
```

### Step #6: Retrieve the Table

To verify that the data was imported correctly from the server, retrieve all the data using the SELECT statement:

```pgsql
SELECT * FROM featurelisttable;
```

You will have the same data in the table as in the CSV file.

```pgsql
+-----------------+----------+
| featurename     | version  | 
+-----------------+----------+
| create a table  | 1        |
| modify a table  | 1.2      |
| drop a table    | 2.2      |
| rename a table  | 2        |
+-----------------+----------+
```

