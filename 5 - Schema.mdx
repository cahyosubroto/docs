---
title: Schema
slug: cNUn-schema
description: A schema is a logical container for database objects such as tables, views, functions, and procedures. Let's walk through the multiple schemas we support.
createdAt: 2023-04-26T04:43:51.000Z
updatedAt: 2023-10-09T13:02:32.129Z
---

## **What is Schema?**

Have you ever wondered how to work with your fellows in one database without interfering with each other? Is it possible to organize the database objects into logical groups which do not collide with the other objects' names?

We can do those things with **Schema**.&#x20;

A **schema** is a collection of tables. A schema also contains views, indexes, sequences, data types, operators, and functions. We support multiple schemas. For example, you can have a database named `oxla` and have multiple schemas based on your needs, like `auth`, `model`, `business`, etc.

![schema](../assets/schema.png)

## **Default Schema in Oxla**

By default, the `public` schema is used in Oxla.&#x20;

When unqualified `table_name` is used, that `table_name` is equivalent to `public.table_name`. It also applies to `CREATE`, `DROP`, and `SELECT TABLE` statements.

:::hint{type="info"}
💡 Furthermore, you can create multiple schemas per your needs.&#x20;
:::

## **Schema Usage Scenarios**

### **#1 - Create a Schema**

The basic syntax of creating a schema is as follows:

```pgsql
CREATE SCHEMA schema_name;
```

`schema_name` is the name of the schema you are going to create.

### **#2 - Create a Table in Schema**

The syntax to create a table in a specified schema is as follows:

```pgsql
CREATE TABLE schema_name.table_name(
...
);
```

- `schema_name` is the schema that you have created.

- `table_name` is the table name you are going to create.

### **#3 - Select a Table in Schema**

After creating the table and inserting some data, display all rows with the syntax below:&#x20;

```pgsql
SELECT * FROM schema_name.table_name;
```

- `schema_name` is the name of the schema.

- `table_name` is the name of the table you want to display.

### **#4 - Drop the Schema**

To drop an empty schema where no objects remain in it, use the command below:

```pgsql
DROP SCHEMA schema_name;
```

Tables reside in a schema, so it is impossible to drop a schema without also dropping the tables. With the command below, you will also drop the schema with the tables.

```pgsql
DROP SCHEMA schema_name CASCADE;
```

## **Example #1 **

1\) First, connect to Oxla and create a schema as shown below:

```pgsql
CREATE SCHEMA oxlarefs;
```

2\) Next, create a table in the above schema with the following details:

```pgsql
CREATE TABLE oxlarefs.functions(
  id int,
  function_name string,
  active bool
);

INSERT INTO oxlarefs.functions(id, function_name, active)
VALUES
('1111', 'Numeric', 'TRUE'),
('2222', 'String', 'TRUE'),
('3333', 'Timestamp', 'TRUE'),
('4444', 'JSON', 'TRUE'),
('5555', 'Boolean', 'TRUE');
```

3\) You can verify and show the table made with the command below:

```pgsql
SELECT * FROM oxlarefs.functions;
```

4\) You will get the following result:

```pgsql
+------+---------------+---------+
| id   | function_name | active  |
+------+---------------+---------+
| 1111 | Numeric       | t       |
| 2222 | String        | t       |
| 3333 | Timestamp     | t       |
| 4444 | JSON          | t       |
| 5555 | Boolean       | t       |
+------+---------------+---------+
```

## **Example #2**

From Example #1, we created a new schema and a table. Use the command below to delete the schema and also the tables in it:

```pgsql
DROP SCHEMA oxlarefs CASCADE;
```

Another case is if there is no table or object created inside the schema, you can use the following command to drop the schema:

```pgsql
DROP SCHEMA oxlarefs;
```
