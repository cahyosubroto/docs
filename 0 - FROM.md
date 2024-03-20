---
title: FROM
slug: fRqy-from
description: The FROM clause is used to specify which table or joins are required for the query/statement (e.g., SELECTquery) to return or obtain data. More info here.
createdAt: 2022-08-22T11:52:03.000Z
updatedAt: 2024-02-29T14:09:28.217Z
---

## Overview

The `FROM` clause is used to specify which table or joins are required for the query/statement (e.g., `SELECT `statement) to return or obtain data.

## Syntax

There must be at least one table listed in the `FROM` clause. See the following syntax:

```pgsql
query FROM table_name;
```

If two or more tables are listed in the `FROM` clause, these tables are joined using [JOIN](https://docs.oxla.com/join), [RIGHT JOIN](https://docs.oxla.com/right-join), [LEFT JOIN](https://docs.oxla.com/left-join), or [OUTER JOIN](https://docs.oxla.com/outer-join), depending on the operations to be queried as seen in the syntax below:

```pgsql
FROM table1_name
[ { JOIN
  | LEFT JOIN
  | RIGHT JOIN
  | OUTER JOIN } table2_name
ON table1_name.column1 = table2_name.column1 ]
```

:::hint{type="info"}
The examples below are executed in the `public` schema, the default schema in Oxla. You can also create, insert, and display a table from other schemas - click [here](https://docs.oxla.com/schema) for more info.
:::

## Example

We'll start by looking at how to use the `FROM` clause with only a single table.

There is a **client** table, and we want to know the client’s name and the city where the company is based.

```pgsql
CREATE TABLE client (
  client_id int,
  client_name string,
  client_origin string
);
INSERT INTO client 
    (client_id, client_name, client_origin) 
VALUES 
    (181891,'Oxla','Poland'),
    (181892,'Google','USA'),
    (181893,'Samsung','South Korea');
```

```pgsql
SELECT * FROM client;
```

It will create a table as shown below:

```pgsql
+------------+--------------+------------------+
| client_id  | client_name  | client_origin    |
+------------+--------------+------------------+
| 181891     | Oxla         | Poland           |
| 181892     | Google       | USA              | 
| 181893     | Samsung      | South Korea      |
+------------+--------------+------------------+
```

1\) Run the following query:

```pgsql
SELECT client_name, client_origin FROM client;
```

2\) You will get a list of the client’s data for a successful result:

```pgsql
+--------------+------------------+
| client_name  | client_origin    |
+--------------+------------------+
| Oxla         | Poland           |
| Google       | USA              | 
| Samsung      | South Korea      |
+--------------+------------------+
```

:::hint{type="success"}
🧐 If two or more tables are listed in the FROM clause, please refer to these sections for more examples related to this: [JOIN](https://docs.oxla.com/join), [RIGHT JOIN](https://docs.oxla.com/right-join), [LEFT JOIN](https://docs.oxla.com/left-join), or [OUTER JOIN](https://docs.oxla.com/outer-join).
:::

***

## FROM - Sub Queries

FROM clause is also used to specify a sub-query expression. The relation created from the sub-query is then used as a new relation on the other query.&#x20;

:::hint{type="info"}
ℹ️ More than one table can be defined by separating it with a comma **(,)**.
:::

### Syntax

Here is an example of the sub-query syntax that uses a FROM clause:

```pgsql
SELECT X.column1, X.column2, X.column3 
FROM table_2 as X, table_1 as Y
WHERE conditions (X.column, Y.column);
```

1.  The sub-query in the first `FROM` clause will select the columns from the specific table using a new temporary relation (`SELECT X.column1, X.column2, X.column3 FROM` ).


2.  Set the tables into a new temporary relation (`table_2 as X, table_1 as Y`).


3.  Next, the query is evaluated, selecting only those rows from the temporary relation that fulfill the conditions stated in the `WHERE` clause.

### Example

We want to find a product whose price exceeds all categories' average budget. 

&#x20;                                                                        product table****

```pgsql
CREATE TABLE product (
  id int,
  product string,
  category string,
  price int
);
INSERT INTO product 
    (id, product, category, price) 
VALUES 
    (445747,'Court vision women’s shoes nike','Shoes', 8000),
    (445641,'Disney kids h&m','Shirt', 6500),
    (477278,'Defacto adidas','Hat', 8500),
    (481427,'Sophie shopping bag','Bag', 6500),
    (411547,'Candy skirt zara','Skirt', 6500),
    (488198,'Slim cut skirt hush puppies','Skirt', 7600);
```

```pgsql
SELECT * FROM product;
```

It will create a table as shown below:

```pgsql
+---------+----------------------------------+-----------+--------+
| id      | product                          | category  | price  |
+---------+----------------------------------+-----------+--------+
| 445747  | Court vision women’s shoes nike  | Shoes     | 8000   |
| 445641  | Disney kids h&m                  | Shirt     | 6500   |
| 477278  | Defacto adidas                   | Hat       | 8500   |
| 481427  | Sophie shopping bag              | Bag       | 6500   |
| 411547  | Candy skirt zara                 | Skirt     | 6500   |
| 488198  | Slim cut skirt hush puppies      | Skirt     | 7600   |
+---------+----------------------------------+-----------+--------+
```

&#x20;                                                                     category table&#x20;

```pgsql
CREATE TABLE category (
  categoryName string,
  budget int
);
INSERT INTO category 
    (categoryName, budget) 
VALUES 
    ('Shoes', 7000),
    ('Shirt', 9000),
    ('Bag', 8000),
    ('Skirt', 7500),
    ('Hat', 7000);
```

```pgsql
SELECT * FROM category;
```

It will create a table as shown below:

```pgsql
+---------------+----------+
| categoryName  | budget   |
+---------------+----------+
| Shoes         | 7000     |
| Shirt         | 9000     |
| Bag           | 8000     |
| Skirt         | 7500     |
| Hat           | 7000     |
+---------------+----------+
```

***

1\) Run the following query to know and ensure the average value of all category’s budgets:

```pgsql
select avg(budget) as avgBudget from category;
```

2\) The average budget of all categories from the **category** table is 7700.&#x20;

```pgsql
+--------------------+
| avgbudget          |
+--------------------+
| 7700.000000000000  |
+--------------------+
```

3\) Now, run the following query:

*   We specify the **product **table as **P** and the budget’s average value from the **category **table as C.

*   We will display the product’s name, category, and price.

*   We set the conditions where the product’s price exceeds the budget’s average value.

```pgsql
select P.product, P.category, P.price from
(select avg(budget) as avgBudget from category) as C, product as P
where P.price > C.avgBudget;
```

➡️ The output will display “court vision women's shoes nike 👟” and Defacto adidas 🧢”* *as the products with a price of more than 7700.

```pgsql
+------------------------------------+-----------+----------+
| product                            | category  | price    |
+------------------------------------+-----------+----------+
| court vision women`s shoes nike    | shoes     | 8000     |
| Defacto adidas                     | hat       | 8500     |
+------------------------------------+-----------+----------+
```

