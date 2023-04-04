---
slug: "braze-com"
title: "Braze Endpoints"
provider: "braze.com"
description: "# Braze API Overview\n\nBraze provides a high performance REST API to\
  \ allow you to track users, send messages, export data, and more.\n\nA REST API\
  \ is a way to programmatically transfer information over the web using a predefined\
  \ schema. Braze has created many different endpoints with specific requirements\
  \ that will perform various actions and/or return various data. API access is done\
  \ using HTTPS web requests to your company's REST API endpoint (this will correspond\
  \ to your Dashboard URL as shown in the table below).\n\nCustomers using Braze's\
  \ EU database should use `https://rest.fra-01.braze.eu/`. For more information on\
  \ REST API endpoints for customers using Braze's EU database see our [EU/US Implementation\
  \ Differences documentation](https://www.braze.com/docs/developer_guide/eu01_us3_sdk_implementation_differences/overview/).\n\
  \n## Braze Instances\n\nInstance    | Dashboard URL   | REST Endpoint\n-----------\
  \ |---------------- | --------------------\nUS-01 | `https://dashboard.braze.com`\
  \ or<br> `https://dashboard-01.braze.com` | `https://rest.iad-01.braze.com`\nUS-02\
  \ | `https://dashboard-02.braze.com` | `https://rest.iad-02.braze.com`\nUS-03 |\
  \ `https://dashboard-03.braze.com` | `https://rest.iad-03.braze.com`\nUS-04 | `https://dashboard-04.braze.com`\
  \ | `https://rest.iad-04.braze.com`\nUS-06 | `https://dashboard-06.braze.com` |\
  \ `https://rest.iad-06.braze.com`\nEU-01 | `https://dashboard.braze.eu` or<br> `https://dashboard-01.braze.eu`\
  \ | `https://rest.fra-01.braze.eu`\n\n\n# Using Braze's Postman Collection \n\n\
  If you have a Postman account (MacOS, Windows, and Linux versions can be downloaded\
  \ from their website located [here](https://www.getpostman.com)), you can go to\
  \ our Postman documentation and click the orange `Run in Postman` button in the\
  \ top, right corner. This will allow you to [create an environment](#setting-up-your-postman-environment),\
  \ as well as edit the available `POST` and `GET` requests to suit your own needs.\n\
  \n## Setting Up Your Postman Environment\n\nThe Braze Postman Collection uses a\
  \ templating variable, `{{instance_url}}`, to substitute the REST API URL of your\
  \ Braze instance into the pre-built requests. Rather than having to manually edit\
  \ all requests in the Collection, you can set up this variable in your Postman environment.\
  \ To do so, please follow the steps below:\n\n1. Click on the gear icon in the top\
  \ right corner of the Postman app. \n2. Select \"Manage Environments\" to open a\
  \ modal window which displays your active environments.\n3. In the bottom right\
  \ corner of the modal window, click \"Add\" to create a new environment.\n4. Give\
  \ this environment a name (e.g. \"Braze API Requests\") and add keys for `instance_url`\
  \ and `api_key` with values corresponding to [your Braze instance](https://www.braze.com/docs/api/basics/#endpoints)\
  \ and [Braze REST API Key](https://www.braze.com/docs/api/basics/#app-group-rest-api-keys),\
  \ as pictured below. \n\nAs of April, 2020 Braze has changed how we read App Group\
  \ API keys. Instead of passing them in the request body or through url parameters,\
  \ we now read the App Group Rest`api_key` through the HTTP Authorization header.\
  \ API keys not passed through the HTTP Authorization Header will coninue to work\
  \ until they have been sunset. \n\n## Using the Pre-Built Requests from the Collection\n\
  \nOnce you have configured your environment. You can use any of the pre-built requests\
  \ in the collection as a template for building new API requests. To start using\
  \ one of the pre-built requests, simply click on it within the 'Collections' menu\
  \ on the left side of Postman. This will open the request as a new tab in the main\
  \ window of the Postman app.\n\nIn general, there are two types of requests that\
  \ Braze's API endpoints accept - `GET` and `POST`. Depending on which `HTTP` method\
  \ the endpoint uses, you'll need to edit the pre-built request differently.\n\n\
  ### Edit a POST Request\n\nWhen editing a `POST` request, you'll need to open the\
  \ request and navigate to the `Body` section in the request editor. For readability,\
  \ select the `raw` radio button to format the `JSON` request body.\n\n### Edit a\
  \ GET Request\n\nWhen editing a `GET` request, you will need to edit the parameters\
  \ passed in the request URL. To edit these easily, select the `Params` button next\
  \ to the URL bar and edit the key-value pairs in the fields that will appear below\
  \ the URL bar.\n\n## Send Your Request\n\nOnce your API request is ready to send,\
  \ click on the 'Send' button next to the URL bar. The request will be sent and the\
  \ response data will be populated in a section underneath the request editor. From\
  \ here, you can view the raw data returned from Braze's API, see the HTTP response\
  \ code, see how long the request took to process, and view header information."
logo: "braze.com-logo.png"
logoMediaType: "image/png"
tags:
- "marketing"
stubs: "braze.com-stubs.json"
swagger: "braze.com-swagger.json"
---