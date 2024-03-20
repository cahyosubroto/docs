---
title: SQL Functions
slug: BXfi-sql-functions
description: Understand how SQL functions work in Oxla, what they are, how to create a function command and its input/return types, and see examples in this guide.
createdAt: 2022-08-22T09:13:54.000Z
updatedAt: 2024-01-08T05:37:20.802Z
---

## What is a Function?

A function *(also known as stored procedures)* is a set of procedural operations stored in the database to carry out processes that usually take several queries; now, it only uses one single function.

***

In this section, we will understand how functions work in Oxla, how to create a function command and its input/return types and see examples of calling the function.

These are the functions that Oxla supports:

```html
<style>
  .buttons {
    display: flex;
    align-items: center;
    margin-top: -3.5rem;
  }

  .button-5 {
  margin-right: 1rem;
  white-space: normal;
  width: 150px;
  align-items: center;
  background-clip: padding-box;
  background-color: #20bdff;
  border: 1px solid transparent;
  border-radius: 0.25rem;
  box-shadow: rgba(0, 0, 0, 0.02) 0 1px 3px 0;
  box-sizing: border-box;
  color: #fff;
  cursor: pointer;
  display: ;
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

.button-5 a {
  display: none;
}

.button-5:hover,
.button-5:focus {
  background-color: #351ad2;
  box-shadow: rgba(0, 0, 0, 0.1) 0 4px 12px;
}

.button-5:hover {
  transform: translateY(-1px);
}

.button-5:active {
  background-color: #351ad2;
  box-shadow: rgba(0, 0, 0, 0.06) 0 2px 4px;
  transform: translateY(0);
}

</style>
<div class="buttons">
  <a href="https://docs.oxla.com/numeric-functions">
    <button class="button-5">
      Numeric Functions
    </button>
  </a>
  <a href="https://docs.oxla.com/aggregation-functions">
    <button class="button-5">
      Aggregate Functions
    </button>
  </a>
  <a href="https://docs.oxla.com/string-functions">
    <button class="button-5">
      String Functions
    </button>
  </a>
  <a href="https://docs.oxla.com/timestamp-functions">
    <button class="button-5">
      Timestamp Functions
    </button>
  </a>
</div>
<div class="buttons">
  <a href="https://docs.oxla.com/boolean-function">
    <button class="button-5">
      Boolean Functions
    </button>
  </a>
  <a href="https://docs.oxla.com/json-functions">
    <button class="button-5">
      JSON Functions
    </button>
  </a>
  <a href="https://docs.oxla.com/other-functions">
    <button class="button-5">
      Other Functions
    </button>
  </a>
  <a href="https://docs.oxla.com/trigonometric-functions">
    <button class="button-5">
      Trigonometric Functions
    </button>
  </a>
</div>
```

