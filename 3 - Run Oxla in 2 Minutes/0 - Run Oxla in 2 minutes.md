---
title: Run Oxla in 2 minutes
slug: a15Y-run-oxla-in-2-mins
description: Run and Deploy Oxla in 2 minutes!
createdAt: 2023-08-12T03:08:52.930Z
updatedAt: 2024-03-07T04:37:44.232Z
---

## Prerequisite

⚠️ x86 64bit CPU (Intel or AMD).

⚠️ Linux OS.

⚠️ Install Docker. Please refer to [this page](https://docs.docker.com/engine/install/) for further details.

⚠️ Install the PostgreSQL client on your local machine. Please refer to [this page](https://www.postgresql.org/download/linux/ubuntu/).

## Installation

*   Open your terminal command and execute this command to check if you have installed your docker properly.

```dockerfile
docker ps
```

:::hint{type="info"}
**Note**: If it returns “Bad response from Docker engine”, this means there is an issue with your docker engine. Try re-install your docker.
:::

*   Start Oxla docker and expose PostgreSQL port:

```dockerfile
docker run --rm -it -p 5432:5432 public.ecr.aws/oxla/release:latest
```

*   Execute the following command to connect to Oxla:

```dockerfile
psql -h localhost
```

:::hint{type="info"}
**Note**: If you encounter an error response “bash: psql: command not found“, this means that you have not installed PostgreSQL.&#x20;
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

