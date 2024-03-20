---
title: Multi-node Deployment
slug: mult-node-deployment
description: Follow this quick tutorial to deploy our multi-node database in minutes! Let us walk you through the basics with steps, illustrations and examples.
createdAt: 2023-07-18T15:01:32.265Z
updatedAt: 2024-02-21T17:07:04.118Z
---

Over the following steps, we'll show you how to set up and deploy Oxla multi-node database. Let’s get started!

:::hint{type="info"}
**Note: **In this tutorial, we will show you how to deploy Oxla with three nodes. If you want to deploy more than that, simply update and adjust the yaml configuration per tutorial below.
:::

## Prerequisite

⚠️ There shall be always a single node per machine.

⚠️ Install Docker. Please refer to [this page](https://docs.docker.com/engine/install/) for further details.

⚠️ x86 64bit CPU (Intel or AMD).

⚠️ Install PostgresSQL-client-14 for psql connection. Please refer to [this page](https://www.postgresql.org/download/).&#x20;

⚠️ Grab N machines with ssh access to them. The N number refers to the number of nodes that you want to deploy.

⚠️ Configure the networking so that all nodes can connect to each other.



## Installation on Each Node

*   Open your terminal command and execute this command to check if you have installed your docker properly.

```dockerfile
docker ps
```

:::hint{type="info"}
**Note: **If it returns “Bad response from Docker engine”, this means there is an issue with your docker engine. Try re-install your docker.
:::

*   Execute the following command to create a file that contains docker compose file:

```dockerfile
vim multi_node.yml
```

*   Input the following code into the docker compose file for **each node**:

```dockerfile
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
    ports:
      - 5432:5432
    environment:
      - FORCED_REVOKE_TIMEOUT_MS=1500
      - BUFFER_TIMEOUT=1
      - HOST_NAME=oxla_node_1
      - OXLA_NODES=192.168.0.1;192.168.0.2;192.168.0.3
      - OXLA_HOME=s3://yourdirectoryname
      - AWS_DEFAULT_REGION=AWS_DEFAULT_REGION
      - AWS_ACCESS_KEY_ID=AWS_ACCESS_KEY_ID
      - AWS_SECRET_ACCESS_KEY=AWS_SECRET_ACCESS_KEY
```

:::hint{type="info"}
**Note: **Don’t forget to replace the following values with appropriate values:&#x20;

*   192.168.0.1; 192.168.0.2; 192.168.0.3

*   s3://yourdirectoryname

*   AWS\_DEFAULT\_REGION

*   AWS\_ACCESS\_KEY\_ID

*   AWS\_SECRET\_ACCESS\_KEY
:::

:::hint{type="warning"}
**Warning: **Please ensure you the three machines that you are using to deploy Oxla is connected in a same network.
:::

:::hint{type="success"}
**Info: **Depending on your computer's RAM capacity, you may need to adjust the environment variable to optimize performance. You can set `OXLA_MAX_NON_QUERY_MEM` to a custom number.&#x20;

For example `OXLA_MAX_NON_QUERY_MEM=4194304`** **
:::



*   Execute the following command to create and start the docker container:

```dockerfile
docker compose -f multi_node.yml up
```

*   Execute the following command to run Oxla:

```dockerfile
psql -h IP_ADDRESS
```

:::hint{type="info"}
**Note: **Please replace IP\_ADDRESS with one of the IP addresses that you setup in your yaml file. If you encounter an error response “bash: psql: command not found“, this means that you have not installed PostgreSQL.&#x20;
:::

:::hint{type="warning"}
**Warning: **Please ensure that you repeat all of the steps above on all of the nodes.
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

