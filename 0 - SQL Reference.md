---
title: SQL Reference
slug: C523-sql-reference
description: SQL reference is a comprehensive guide to the Structured Query Language used to manage and manipulate relational databases, providing detailed information.
createdAt: 2022-08-22T08:43:16.000Z
updatedAt: 2024-02-29T14:01:13.576Z
---

This section provides information about the syntax and semantics of SQL queries, clauses, data types, and functions that Oxla supports. The information in this section is divided into groups according to the kind of operation they perform as follows:

```html
<style>

  #main-column.w-full.max-w-\[760px\] {
    max-width: unset;
  }
  
  .landing-wrapper {
    margin: -5rem 1rem 1rem 1rem;
    white-space: normal;
  }

  .landing-wrapper header > div:last-of-type > h1 {
    font-size: 51px;
    font-weight: 600;
    color: #afafaf;
  }
  .landing-wrapper header > div:last-of-type > p {
    font-size: 24px;
  }
  
  .card-title {
    color: #0c121d;
  }
</style>

<div class="landing-wrapper flex flex-col items-center">
    <style>
        .landing-wrapper > .header > div:first-of-type {
        width: 400px;
        height: 175px;
        margin-right: 3rem;
        background-image: url(https://uploads-ssl.webflow.com/60fe80283b1f1bb3b054edc8/60fe84c1c8933226b00487a0_logo.svg);
        background-size: contain;
        background-repeat: no-repeat;
        background-position: center;
        }
        .landing-wrapper > .header {
        max-width: 1242px;
        }
        .landing-wrapper > .grid {
        grid-template-columns: 1fr 1fr 1fr;
        grid-gap: 1.5rem;
        margin-top: 2.5rem;
        }
        .landing-wrapper > .grid > .category {
        max-width: 400px;
        padding: 1.5rem 1rem 1.5rem 1.5rem;
        border-radius: 7px;
        border: 1px solid #AFAFAF;
        transition-duration: 300ms;
        cursor: pointer;
        }
        .landing-wrapper > .grid > .category:hover {
        border-color: transparent;
        box-shadow: 0px 4px 16px 1px #351ad2;
        }
        .landing-wrapper > .grid > .category > div:first-of-type {
        width: 4.75rem;
        height: 4rem;
        margin-right: 1.5rem;
        background-size: contain;
        background-repeat: no-repeat;
        background-position: center center;
        }
        .landing-wrapper > .grid > .category > div:last-of-type {
        width: 3.5rem;
        height: 100%;
        background-image: url(https://cdn.flipperzero.one/docs-landing-chevron-down.png);
        background-repeat: no-repeat;
        background-size: 20px;
        background-position: bottom 22% right;
        }
        .landing-wrapper > .grid > .category > div:nth-of-type(2) {
        width: 100%;
        }
        .landing-wrapper > .grid > .category:hover > div:last-of-type {
        background-image: url(https://cdn.flipperzero.one/docs-landing-chevron-down-black.png);
        }

        @media (max-width: 920px) {
        .landing-wrapper > .grid {
            grid-template-columns: 1fr 1fr;
        }
        }
        @media (max-width: 780px) {
        .landing-wrapper {
            margin-top: 2rem;
        }
        .header {
            flex-direction: column;
            max-width: 90vw;
        }
        .landing-wrapper > .header > div:first-of-type {
            width: 280px;
            height: 125px;
            margin: 0 0 1.5rem 0;
        }
        .landing-wrapper > .header > div:last-of-type {
            text-align: center;
            max-width: 80vw;
        }
        }
        @media (max-width: 620px) {
        .landing-wrapper {
            margin-top: 1.5rem;
        }
        .landing-wrapper > .header > div:first-of-type {
            width: 235px;
            height: 100px;
        }
        .landing-wrapper > .grid {
            grid-template-columns: 1fr;
        }
        }
        @media (max-width: 375px) {
        .landing-wrapper > .header > div:last-of-type > h1 {
            font-size: 2.5rem;
        }
        .landing-wrapper > .header > div:last-of-type > p {
            font-size: 1.15rem;
        }
        }
    </style>
    <div class="grid">
        <div class="category flex items-center" onclick="window.open('https://docs.oxla.com/sql-statements', 'this')">
            <div style="background-image: url(https://cdn-icons-png.flaticon.com/512/8309/8309203.png);"></div>
            <div>
                <h4 class="text-xl font-bold text-gray-900 card-title">SQL Statements</h4>
                <p>Learn how to create a request for data or information from one or more database tables using our supported statements.</p>
            </div>
            <div></div>
        </div>
        <div class="category flex items-center" onclick="window.open('https://docs.oxla.com/sql-clauses', 'this')">
            <div style="background-image: url(https://cdn-icons-png.flaticon.com/512/2326/2326877.png);"></div>
            <div>
                <h4 class="text-xl font-bold text-gray-900 card-title">SQL Clauses</h4>
                <p>See just how easy it is to filter and get a large amount of data using a query that lets you filter or customize how you want your data to be returned to you.</p>
            </div>
            <div></div>
        </div>
        <div class="category flex items-center" onclick="window.open('https://docs.oxla.com/sql-data-types', 'this')">
            <div style="background-image: url(https://cdn-icons-png.flaticon.com/512/7771/7771738.png);"></div>
            <div>
                <h4 class="text-xl font-bold text-gray-900 card-title">SQL Data Types</h4>
                <p>This sub-section will guide you through implementing our supported data types to run your operations, such as string, timestamp, numeric, and many more…💨</p>
            </div>
            <div></div>
        </div>
        <div class="category flex items-center" onclick="window.open('https://docs.oxla.com/sql-functions', 'this')">
            <div style="background-image: url(https://cdn-icons-png.flaticon.com/512/3891/3891639.png);"></div>
            <div>
                <h4 class="text-xl font-bold text-gray-900 card-title">SQL Functions</h4>
                <p>See how you can combine the statements, data types, and other references into specific functions for particular tasks.</p>
            </div>
            <div></div>
        </div>
        <div class="category flex items-center" onclick="window.open('https://docs.oxla.com/schema', 'this')">
            <div style="background-image: url(https://cdn-icons-png.flaticon.com/512/9118/9118882.png);"></div>
            <div>
                <h4 class="text-xl font-bold text-gray-900 card-title">Schema</h4>
                <p>Learn about a logical container that holds database objects and relationships of data in a database.</p>
            </div>
            <div></div>
        </div>
        <div class="category flex items-center" onclick="window.open('https://docs.oxla.com/sql-functions', 'this')">
            <div style="background-image: url(https://cdn-icons-png.flaticon.com/512/2593/2593463.png);"></div>
            <div>
                <h4 class="text-xl font-bold text-gray-900 card-title">Comment Support</h4>
                <p>Adding comments in your queries for better documentation and collaboration.</p>
            </div>
            <div></div>
        </div>
    </div>
</div>

```


