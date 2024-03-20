---
title: SQL Mutations
slug: ARCo-sql-mutations
createdAt: 2023-12-01T00:51:06.341Z
updatedAt: 2023-12-01T01:50:11.170Z
---

## What are Mutations? 🤔

A mutation refers to a change made to data stored in a database. Several commands are provided for data manipulation, such as `INSERT` (adds new records), `UPDATE` (modifies existing records), and `DELETE` (deletes records).

This support has limitations:

*   Only **one data mutation (DELETE or UPDATE) **at a given moment is possible. Trying to run another one will fail.

*   Data mutations rewrite all files containing the data from the UPDATE/DELETE condition. Running `DELETE from the table` without any condition is possible, but it will be much slower than the `DROP TABLE table`.

*   The syntax is simplified in comparison to Postgres. For example, the `SET column=<value>` operation doesn't support sub-SELECT as the value, and the `WHERE` clause cannot contain sub-SELECT.

***

Currently, Oxla supports the following SQL mutations:

```html
<style>
  .buttons {
    display: flex;
    align-items: center;
    margin-top: -3.5rem;
  }

  .button-7 {
  margin-right: 1rem;
  white-space: normal;
  width: 100px;
  height: 50px;
  align-items: center;
  background-clip: padding-box;
  background-color: #20bdff;
  border: 1px solid transparent;
  border-radius: 0.25rem;
  box-shadow: rgba(0, 0, 0, 0.02) 0 1px 3px 0;
  box-sizing: border-box;
  color: #fff;
  cursor: pointer;
  display: inline-flex;
  font-size: 12px;
  justify-content: center;
  line-height: 1.25;
  padding: calc(0.875rem - 1px) calc(1.5rem - 1px);
  position: relative;
  text-decoration: none;
  transition: all 250ms;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
  vertical-align: baseline;
  z-index: 3;
}

.button-7 a {
  display: none;
}

.button-7:hover,
.button-7:focus {
  background-color: #351ad2;
  box-shadow: rgba(0, 0, 0, 0.1) 0 4px 12px;
}

.button-7:hover {
  transform: translateY(-1px);
}

.button-7:active {
  background-color: #351ad2;
  box-shadow: rgba(0, 0, 0, 0.06) 0 2px 4px;
  transform: translateY(0);
}

@media (max-width: 600px) {
    .buttons {
      flex-direction: column;
  }
  }

</style>
<div class="buttons">
  <a href="https://docs.oxla.com/update">
    <button class="button-7">
      UPDATE
    </button>
  </a>
  <a href="https://docs.oxla.com/delete">
    <button class="button-7">
      DELETE
    </button>
  </a>
</div>
```









