---
title: SQL Statements
slug: uLah-sql-queries
description: SQL queries are commands used to retrieve and manipulate data stored in a relational database and are essential for managing and organizing large datasets.
createdAt: 2022-08-22T09:04:48.000Z
updatedAt: 2024-01-30T15:54:33.582Z
---

## What is a Statement? 🤨

A statement refers to a single SQL operation or a set of operations that are performed together. Statements include queries, but also a broader set of operations, such as: Retrieve, Add, Update, or Delete Data.

## How does a Statement work? 🧐

A statement is like a command or request you give someone, such as "Find all the details about my favorite book." In Oxla, this would be a `SELECT` statement.&#x20;

When you run a statement in Oxla, the command is processed and the requested operation is performed. This statement can affect the data stored in the table or change the database structure.

***

The following articles will explain the statements that we support, with examples:

```html
<style>

  .buttons-sql a{
    display: flex;
    margin: 1rem;
  }

  .buttons-sql {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
  }


  .button-6 {
  padding: 15px;
  white-space: normal;
  background-color: #20bdff;
  border: 1px solid transparent;
  border-radius: 0.25rem;
  box-shadow: rgba(0, 0, 0, 0.02) 0 1px 3px 0;
  box-sizing: border-box;
  color: #fff;
  cursor: pointer;
  font-size: 16px;
  line-height: 1.25;
  height: 70px;
  max-width: 150px;
  text-decoration: none;
  transition: all 250ms;
}

.button-6:hover,
.button-6:focus {
  background-color: #351ad2;
  box-shadow: rgba(0, 0, 0, 0.1) 0 4px 12px;
}

.button-6:hover {
  transform: translateY(-1px);
}

.button-6:active {
  background-color: #351ad2;
  box-shadow: rgba(0, 0, 0, 0.06) 0 2px 4px;
  transform: translateY(0);
}

@media (max-width: 600px) {
    .buttons-sql {
      display: flex;
      flex-direction: column;
      align-items: center;
  }

    .button-6 {
      width: 200px;
      text-align: center;
      margin: 1rem;
    }
  }



</style>
<div class="buttons-sql">
    <a href="https://docs.oxla.com/create-table-statement">
        <button class="button-6">
        CREATE TABLE statement
        </button>
    </a>
    <a href="https://docs.oxla.com/create-index-statement">
        <button class="button-6">
        CREATE INDEX statement
        </button>
    </a>
   <a href="https://docs.oxla.com/drop-statement">
        <button class="button-6">
        DROP statement
        </button>
    </a>
    <a href="https://docs.oxla.com/select-statement">
        <button class="button-6">
        SELECT statement
        </button>
  </a>
  <a href="https://docs.oxla.com/insert-into-statement">
        <button class="button-6">
        INSERT INTO statement
        </button>
  </a>
  <a href="https://docs.oxla.com/show-tables-statement">
        <button class="button-6">
        SHOW TABLES statement
        </button>
    </a>
    <a href="https://docs.oxla.com/describe-statement">
        <button class="button-6">
        DESCRIBE statement
        </button>
    </a>
    <a href="https://docs.oxla.com/show-nodes-statement">
        <button class="button-6">
        SHOW NODES statement
        </button>
    </a>
    <a href="https://docs.oxla.com/setshow-statement">
        <button class="button-6">
        SET/SHOW statement
        </button>
    </a>
    <a href="https://docs.oxla.com/copy-from-statement">
        <button class="button-6">
        COPY FROM statement
        </button>
    </a>
    <a href="https://docs.oxla.com/copy-to-statement">
        <button class="button-6">
        COPY TO statement
        </button>
    </a>
</div>
```




