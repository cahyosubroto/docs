---
title: Run Oxla on S3
slug: R72d-run-oxla-on-s
description: We'll help you get set up with an Oxla server so you can see how easy it is to access and run Oxla on S3 today!
createdAt: 2023-08-14T13:17:14.523Z
updatedAt: 2023-11-28T17:00:10.523Z
---

Run Oxla on S3 in minutes! 🎊******

Over the following steps, we'll set you up with an Oxla server so you can see how easy it is to access. Let's get started!

## Prerequisite

⚠️ Install Docker. Please refer to [this page](https://docs.docker.com/engine/install/) for further details.

⚠️ We recommend you use a Linux OS computer to deploy an Oxla server.

⚠️ Install PostgresSQL-client-14 for psql connection. Please refer to [this page](https://www.postgresql.org/download/).&#x20;

## Installation Steps

1\) Open your terminal and execute this command to check if you have installed your docker properly:

```typescript
docker ps
```

:::hint{type="info"}
**Note**: If it returns “Bad response from Docker engine”, this means there is an issue with your docker engine. Try re-install your docker.
:::

2\) Execute the following command to create a file that contains docker compose file:

```typescript
vim one_node.yml
```

3\) Input the following code into the docker compose file:

```typescript
version: '3.5'
volumes:
  oxla_data:
services:
  oxla_node:
    image: public.ecr.aws/oxla/release:latest
    security_opt:
      - seccomp:unconfined
    ulimits:
      nofile:
        soft: 40000
        hard: 40000
    volumes:
      - oxla_data:/data
    ports:
      - 5432:5432
    environment:
      - OXLA_HOME=s3://yourdirectoryname
      - AWS_DEFAULT_REGION=AWS_DEFAULT_REGION
      - AWS_ACCESS_KEY_ID=AWS_ACCESS_KEY_ID
      - AWS_SECRET_ACCESS_KEY=AWS_SECRET_ACCESS_KEY

```

:::hint{type="info"}
**Note**: Don’t forget to replace the s3, AWS\_DEFAULT\_REGION, AWS\_ACCESS\_KEY\_ID, and AWS\_SECRET\_ACCESS\_KEY with appropriate values.&#x20;
:::

:::hint{type="success"}
**Info: **Depending on your computer's RAM capacity, you may need to adjust the environment variable to optimize performance. You can set `OXLA_MAX_NON_QUERY_MEM` to a custom number.&#x20;

For example `OXLA_MAX_NON_QUERY_MEM=4194304`
:::

4\) Execute the following command to create and start the docker container:

```typescript
docker compose -f one_node.yml up
```

5\) Execute the following command to run Oxla:

```typescript
psql -h localhost
```

:::hint{type="info"}
**Note**: If you encounter an error response “bash: psql: command not found“, this means that you have not installed PostgreSQL.&#x20;
:::

When you get the following result, you are now in the Oxla server✅

```typescript
psql (14.4, server Oxla 1.0)

HP=>
```

:::hint{type="danger"}
🚧 Encountered an error? We got you! Head over [here](https://docs.oxla.com/error-handling) to see your troubleshooting resolutions!
:::

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    /* Styling for the pop-up */
    .popup {
      display: flex;
      align-items: center;
      justify-content: center;
      position: fixed;
      bottom: 5%;
      left: 50%;
      transform: translateX(-50%);
      border: 1px solid #2595fe;
      border-radius: 10px;
      background-color: #fff;
      padding: 0 20px 0 20px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
      z-index: 9999;
      text-align: left;
    }
  
    .h3 {
      font-size: 16px;
      margin: 1rem;
      color: #2595fe;
    }
    
    .p {
      margin: 1rem;
      font-size: 16px;
    }

    .button {
      margin: 1rem;
      background-color: #2595fe;
      color: #fff;
      padding: 10px 20px;
      
      border-radius: 10px;
      cursor: pointer;
    }

    .button:hover {
      background-color: #3a37d1;
    }

    /* Styling for the overlay */
    .overlay {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0, 0, 0, 0.5);
      z-index: 9998;
    }
    
    @media (max-width: 1200px) {
      .popup {
        width: 250px;
        flex-direction: column;
        align-items: flex-start;
      }
    }
  </style>
</head>
<body>

<button onclick="togglePopup()"></button>

<div id="popup" class="popup">
  <h3 class='h3'>Terms of Use</h3>
  <p class='p'>I have read and accept the <a href="https://oxla.com/terms-of-use/"style="TEXT-DECORATION: underline">Terms of Use</a> </p>

    <button class='button' onclick="togglePopup()">Accept</button>

</div>


<script>
  function togglePopup() {
    var popup = document.getElementById('popup');
    popup.style.display = popup.style.display === 'none' ? 'block' : 'none';
  }
</script>

</body>
</html>

```

