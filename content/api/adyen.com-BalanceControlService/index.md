---
slug: "adyen-com-BalanceControlService"
title: "Adyen Balance Control API"
provider: "adyen.com"
description: "The Balance Control API lets you transfer funds between merchant accounts\
  \ that belong to the same legal entity and are under the same company account.\n\
  \n## Authentication\nTo connect to the Balance Control API, you must authenticate\
  \ your requests with an [API key or basic auth username and password](https://docs.adyen.com/development-resources/api-authentication).\
  \ To learn how you can generate these, see [API credentials](https://docs.adyen.com/development-resources/api-credentials).Here\
  \ is an example of authenticating a request with an API key:\n\n```\ncurl\n-H \"\
  X-API-Key: Your_API_key\" \\\n-H \"Content-Type: application/json\" \\\n...\n```\n\
  Note that when going live, you need to generate API credentials to access the [live\
  \ endpoints](https://docs.adyen.com/development-resources/live-endpoints).\n\n##\
  \ Versioning\nThe Balance Control API supports [versioning](https://docs.adyen.com/development-resources/versioning)\
  \ using a version suffix in the endpoint URL. This suffix has the following format:\
  \ \"vXX\", where XX is the version number.\n\nFor example:\n\n```\nhttps://pal-test.adyen.com/pal/servlet/BalanceControl/v1/balanceTransfer\n\
  ```\n"
logo: "adyen.com-BalanceControlService-logo.svg"
logoMediaType: "image/svg+xml"
tags:
- "payment"
stubs: "adyen.com-BalanceControlService-stubs.json"
swagger: "adyen.com-BalanceControlService-swagger.json"
---
