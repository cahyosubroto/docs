---
title: Getting Started
slug: wT5s-getting-started
description: We'll set you up with an Oxla server so you can see how easy it is to access through this guide.
createdAt: 2022-09-12T05:58:58.000Z
updatedAt: 2023-10-09T13:02:32.129Z
---

******Let's play around with Oxla! 🎊******

Over the following steps, we'll set you up with an Oxla server so you can see how easy it is to access. Let's get started!

## Prerequisite

⚠️ Install PostgreSQL on your local machine. Please refer to [this](https://www.postgresql.org/download/) page.

## For Windows

1\) Open the command prompt.

2\) Execute the following command to run the Oxla server: psql.exe -h 44.210.23.203``

```typescript
(c) Microsoft Corporation. All rights reserved.

C:\Users\HP> psql.exe -h 44.210.23.203
```

When you get the following result, you are now in the Oxla server✅

```typescript
psql (14.4, server Oxla 1.0)
WARNING: Console code page (65001) differs from Windows code page (1252)
         8-bit characters might not work correctly. See psql reference
         page "Notes for Windows users" for details.
Type "help" for help.

HP=>
```

## For Mac

1\) Open the terminal.

2\) Execute the following command to run the Oxla server: psql -h 44.210.23.203``

```typescript
Mac:~ mac$ psql -h 44.210.23.203
```

When you get the following result, you are now in the Oxla server✅

```typescript
psql (14.4, server Oxla 1.0)
Type "help" for help.

mac=>
```

:::hint{type="danger"}
🚧 Encountered an error? We got you! Head over [here](https://docs.oxla.com/error-handling) to see your troubleshooting options!
:::

