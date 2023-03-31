---
slug: "adyen-com-AccountService"
title: "Account API"
provider: "adyen.com"
description: "This API is used for the classic integration. If you are just starting\
  \ your implementation, refer to our [new integration guide](https://docs.adyen.com/marketplaces-and-platforms)\
  \ instead.\n\nThe Account API provides endpoints for managing account-related entities\
  \ on your platform. These related entities include account holders, accounts, bank\
  \ accounts, shareholders, and verification-related documents. The management operations\
  \ include actions such as creation, retrieval, updating, and deletion of them.\n\
  \nFor more information, refer to our [documentation](https://docs.adyen.com/marketplaces-and-platforms/classic).\n\
  ## Authentication\nYour Adyen contact will provide your API credential and an API\
  \ key. To connect to the API, add an `X-API-Key` header with the API key as the\
  \ value, for example:\n\n ```\ncurl\n-H \"Content-Type: application/json\" \\\n\
  -H \"X-API-Key: YOUR_API_KEY\" \\\n...\n```\n\nAlternatively, you can use the username\
  \ and password to connect to the API using basic authentication. For example:\n\n\
  ```\ncurl\n-U \"ws@MarketPlace.YOUR_PLATFORM_ACCOUNT\":\"YOUR_WS_PASSWORD\" \\\n\
  -H \"Content-Type: application/json\" \\\n...\n```\nWhen going live, you need to\
  \ generate new web service user credentials to access the [live endpoints](https://docs.adyen.com/development-resources/live-endpoints).\n\
  \n## Versioning\nThe Account API supports [versioning](https://docs.adyen.com/development-resources/versioning)\
  \ using a version suffix in the endpoint URL. This suffix has the following format:\
  \ \"vXX\", where XX is the version number.\n\nFor example:\n```\nhttps://cal-test.adyen.com/cal/services/Account/v6/createAccountHolder\n\
  ```"
logo: "adyen.com-AccountService-logo.svg"
logoMediaType: "image/svg+xml"
tags:
- "payment"
stubs: "adyen.com-AccountService-stubs.json"
swagger: "adyen.com-AccountService-swagger.json"
---
