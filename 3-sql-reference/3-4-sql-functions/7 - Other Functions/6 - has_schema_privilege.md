---
title: has_schema_privilege
slug: LrLg-hasschemaprivilege
description: A function that checks whether the current user has specific privileges on a schema. More information here.
createdAt: 2023-09-13T06:56:01.691Z
updatedAt: 2023-10-31T05:32:57.172Z
---

## **Overview**

The `has_schema_privilege` function checks whether the current user has specific privileges on a schema.&#x20;

## **Syntax**

There are two versions of the `has_schema_privilege` function:

**Version 1**

```pgsql
SELECT has_schema_privilege('user', 'schema', 'privilege');
```

**Version 2**

```pgsql
SELECT has_schema_privilege('schema', 'privilege');
```

See the breakdown of both versions:

*   `schema`: The name of the schema for which you want to check privileges. It can be any string value or string columns from other tables.

*   `user`: The name of the user who has the privileges. It can be any string value.

*   `privilege`: The privilege parameter specifies the specific privilege you want to check for in the schema. Currently, the function supports `create` and `usage`.&#x20;

The comparison for the `privilege` is case-insensitive, so you can use lowercase or uppercase letters for the privilege name (e.g., `CREATE` or `create` are both valid).

## **Output**

Both versions of the `has_schema_privilege` function will always return a `TRUE (t)` value.

## **Examples**

### Case #1: Check for CREATE Privilege

In this example, we will use the `has_schema_privilege` function to determine if the current user has the `create` privilege on a schema named "public."

```pgsql
SELECT has_schema_privilege('public', 'create');
```

This query will return `TRUE`, which means the current user has a `create` privilege on the "public" schema.

```pgsql
 has_schema_privilege 
----------------------
 t
```

### Case #2: Check for USAGE Privilege

You can also use the `has_schema_privilege` function to check for the `usage` privilege on a schema. For example, to check if the current user can create objects in the "public" schema:

```pgsql
SELECT has_schema_privilege('cahyo', 'public', 'USAGE');
```

This query will return `TRUE`, which means the current user has usage privilege on the "public" schema.

```pgsql
 has_schema_privilege 
----------------------
 t
```

