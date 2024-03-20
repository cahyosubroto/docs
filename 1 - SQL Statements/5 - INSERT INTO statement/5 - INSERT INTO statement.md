---
title: INSERT INTO statement
slug: yhYE-insert-into
createdAt: 2024-01-08T13:59:14.927Z
updatedAt: 2024-01-10T15:52:00.334Z
---

## **Overview**

The `INSERT INTO` statement adds new rows to an existing table using a `SELECT` statement or explicitly stating input values.

## **Syntax**

The basic syntax for `INSERT INTO` is as follows:

```pgsql
INSERT INTO table_name[(columns_order)] VALUES (value 1), (value 2), ... (value n);
```

or

```pgsql
INSERT INTO table_name[(columns_order)] select_statement; 
```

Where:

*   `table_name`: The table name.

*   `(columns_order)`: Optional column order in the table.

*   `select_statement`: A `SELECT` statement that provides the data to insert. For example, `SELECT (value 1), (value 2), ... (value n);`.

## **Examples**

### **Case #1: Basic Usage**

Let's create a distance table.&#x20;

```pgsql
CREATE TABLE distance_table (distance INT, unit TEXT);
```

We'll then insert values representing different distance measurements.

```pgsql
INSERT INTO distance_table (distance, unit) VALUES
    (2000, 'kilometers'),
    (1000, 'meters'),
    (5, 'miles');
```

Display the table using the query below.

```pgsql
SELECT * FROM distance_table;
```

You’ll get the following output.

```pgsql
 distance |    unit    
----------+------------
     2000 | kilometers
     1000 | meters
        5 | miles
```

### **Case #2: Switching Column Orders**

In this example, we create a `weight` table with columns `kilo` and `gram`. Then, we add data using the default column order (`kilo`, `gram`).

```pgsql
CREATE TABLE weight(kilo INT, gram INT);
INSERT INTO weight SELECT 45, 52;
```

Next, we insert data with a switched column order (`gram`, `kilo`).

```pgsql
INSERT INTO weight(gram, kilo) SELECT 45, 52;
```

Let’s see what’s on the table.

```pgsql
SELECT * FROM weight;
```

The output displays the first row with data from the default column order and the second row with reversed data from the switched column order.

```pgsql
 kilo | gram 
------+------
   45 |   52
   52 |   45
```

### **Case #3: Inserting with a NULL Column**

In this case, we only insert data into a `gram` column while leaving the `kilo` column as NULL.

```pgsql
CREATE TABLE weight(kilo INT, gram INT);
INSERT INTO weight(gram) SELECT 45;
```

Display the table.

```pgsql
SELECT * FROM weight;
```

The output shows the first column (`kilo`) as NULL.

```pgsql
kilo  | gram 
------+------
      |  45 
```

### **Case #4: Error Handling - Too Many Values**

In this case, an error occurs when attempting to insert more values than the specified columns in the table.

```pgsql
CREATE TABLE weight(kilo INT, gram INT);
INSERT INTO weight SELECT 45, 52, 30;
```

The error result indicates that the table `weight` has only 2 columns.

```pgsql
ERROR:  INSERT has more expressions than target columns
```

### **Case #5: Error Handling - Inserting NULL into a Not-Nullable Column**

In this example, you insert data into a `gram` column and a NULL value into a `kilo` column.

```pgsql
CREATE TABLE weight(kilo INT, gram INT);
INSERT INTO weight(gram) SELECT 30;
```

You will get an error result as you try to input data only in the `gram` column, leaving the `kilo` column empty, where there is a NOT NULL constraint.

```pgsql
ERROR:  null value in column "kilo" of relation "weight" violates not-null constraint
```

