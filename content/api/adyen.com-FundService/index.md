---
slug: "adyen-com-FundService"
title: "Fund API"
provider: "adyen.com"
description: "This API is used for the classic integration. If you are just starting\
  \ your implementation, refer to our [new integration guide](https://docs.adyen.com/marketplaces-and-platforms)\
  \ instead.\n\nThe Fund API provides endpoints for managing the funds in the accounts\
  \ on your platform. These management operations include, for example, the transfer\
  \ of funds from one account to another, the payout of funds to an account holder,\
  \ and the retrieval of balances in an account.\n\nFor more information, refer to\
  \ our [documentation](https://docs.adyen.com/marketplaces-and-platforms/classic/).\n\
  ## Authentication\nYour Adyen contact will provide your API credential and an API\
  \ key. To connect to the API, add an `X-API-Key` header with the API key as the\
  \ value, for example:\n\n ```\ncurl\n-H \"Content-Type: application/json\" \\\n\
  -H \"X-API-Key: YOUR_API_KEY\" \\\n...\n```\n\nAlternatively, you can use the username\
  \ and password to connect to the API using basic authentication. For example:\n\n\
  ```\ncurl\n-U \"ws@MarketPlace.YOUR_PLATFORM_ACCOUNT\":\"YOUR_WS_PASSWORD\" \\\n\
  -H \"Content-Type: application/json\" \\\n...\n```\nWhen going live, you need to\
  \ generate new web service user credentials to access the [live endpoints](https://docs.adyen.com/development-resources/live-endpoints).\n\
  \n## Versioning\nThe Fund API supports [versioning](https://docs.adyen.com/development-resources/versioning)\
  \ using a version suffix in the endpoint URL. This suffix has the following format:\
  \ \"vXX\", where XX is the version number.\n\nFor example:\n```\nhttps://cal-test.adyen.com/cal/services/Fund/v6/accountHolderBalance\n\
  ```"
logo: "adyen.com-FundService-logo.svg"
logoMediaType: "image/svg+xml"
tags:
- "payment"
stubs: "adyen.com-FundService-stubs.json"
swagger: "adyen.com-FundService-swagger.json"
---
