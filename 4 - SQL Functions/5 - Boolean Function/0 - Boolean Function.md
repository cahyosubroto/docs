---
title: Boolean Function
slug: _jTx-boolean-function
description: Learn how to use the IF() function to return a Boolean value (either true or false) based on a specified condition. The guide also goes over more details.
createdAt: 2022-08-24T04:29:03.000Z
updatedAt: 2023-10-09T13:02:32.129Z
---

## IF Function

You will learn how to use the `IF()` function to return a value if a condition is true or false.

### Overview

This function returns the specified value if the condition is `TRUE` and another value if the condition is `FALSE`.  The syntax of the `IF()`function is shown below:

```pgsql
IF(expression, true_result, else_result)
```

:::hint{type="warning"}
⚠️ The `expression` must be a Boolean expression.
:::

### Examples

### #Case 1: `IF()` with a table

In this example, we have the **test\_result** table. We want to know which participants passed and which failed from the table below:

```pgsql
CREATE TABLE test_result (
  applicant_id int,
  name text,
  score int
);

INSERT INTO test_result VALUES 
(78765,'Mike Aoki',677),
(78786,'Julie Grahams',650),
(78986,'Alexandra Jones',450),
(79742,'Lucas Moore',487),
(79769,'Augustine Harkness',572);
```

```pgsql
SELECT * FROM test_result;
```

The above query will display the following table:

```pgsql
+---------------+--------------------+--------+
| applicant_id  | name               | score  |
+---------------+--------------------+--------+
| 78765         | Mike Aoki          | 677    |
| 78786         | Julie Grahams      | 650    |
| 78986         | Alexandra Jones    | 450    |
| 79742         | Lucas Moore        | 487    |
| 79769         | Augustine Harkness | 572    |
+---------------+--------------------+--------+
```

1\) IF function in the query below states that *IF the score is equal to or greater than 500, then return “PASSED“. Otherwise, if the score is smaller than 500, return “NOT PASSED”*.

```pgsql
SELECT name, IF(score>=500, 'PASSED', 'NOT PASSED') FROM test_result; 
```

2\) It will return the following result:&#x20;

```pgsql
+--------------------+-------------+
| name	             | case        |
+--------------------+-------------+
| Mike Aoki	         | PASSED      |
| Julie Grahams	     | PASSED      |
| Alexandra Jones	 | NOT PASSED  |
| Lucas Moore	     | NOT PASSED  |
| Augustine Harkness | PASSED      |
+--------------------+-------------+
```

### #Case 2: IF() with expressions as return value

In the second example, we have another table named “**deptcost”**. We want to know which department exceeded the budget and which one did not from the following table.

```pgsql
CREATE TABLE deptcost (
  dept text,
  budget int,
  actual int,
  status text
);
INSERT INTO deptcost VALUES
('Finance', 800,677,'within budget'),
('HR', 700,930,'over budget'),
('Marketing', 500,677,'over budget'),
('Project', 720,700,'within budget'),
('Sales', 910,860,'within budget');
```

Run the following query to display the table:

```pgsql
SELECT * FROM deptcost;
```

We have **deptcost** table as seen below:

```pgsql
+-----------+--------+--------+---------------+
| dept      | budget | actual | status        |
+-----------+--------+--------+---------------+
| Finance   | 800	 | 677	  | within budget |
| HR	    | 700    | 930	  | over budget   |
| Marketing | 500    | 677	  | over budget   |
| Project	| 720    | 700	  | within budget |
| Sales	    | 910	 | 860    | within budget |
+-----------+--------+--------+---------------+
```

1\) The following IF function states that *IF the actual is less than the budget, then return the budget difference, otherwise return 0*.

```pgsql
SELECT dept, IF(actual < budget, budget - actual, 0) FROM deptcost;
```

2\) We get the following result using the `IF()` function:

```pgsql
+-----------+-----+
|   dept    |  f  |
+-----------+-----+
| Finance   | 123 |
| HR        |   0 |
| Marketing |   0 |
| Project   |  20 |
| Sales     |  50 |
+-----------+-----+
```

