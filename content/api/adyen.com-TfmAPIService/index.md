---
slug: "adyen-com-TfmAPIService"
title: "POS Terminal Management API"
provider: "adyen.com"
description: "This API provides endpoints for managing your point-of-sale (POS) payment\
  \ terminals. You can use the API to obtain information about a specific terminal,\
  \ retrieve overviews of your terminals and stores, and assign terminals to a merchant\
  \ account or store.\n\nFor more information, refer to [Assign terminals](https://docs.adyen.com/point-of-sale/automating-terminal-management/assign-terminals-api).\n\
  \n## Authentication\nEach request to the Terminal Management API must be signed\
  \ with an API key. For this, obtain an API Key from your Customer Area, as described\
  \ in [How to get the API key](https://docs.adyen.com/development-resources/api-credentials#generate-api-key).\
  \ Then set this key to the `X-API-Key` header value, for example:\n\n```\ncurl\n\
  -H \"Content-Type: application/json\" \\\n-H \"X-API-Key: Your_API_key\" \\\n...\n\
  ```\nNote that when going live, you need to generate new web service user credentials\
  \ to access the [live endpoints](https://docs.adyen.com/development-resources/live-endpoints).\n\
  \n## Versioning\nTerminal Management API supports [versioning](https://docs.adyen.com/development-resources/versioning)\
  \ using a version suffix in the endpoint URL. This suffix has the following format:\
  \ \"vXX\", where XX is the version number.\n\nFor example:\n```\nhttps://postfmapi-test.adyen.com/postfmapi/terminal/v1/getTerminalsUnderAccount\n\
  ```\nWhen using versioned endpoints, Boolean response values are returned in string\
  \ format: `\"true\"` or `\"false\"`.\nIf you omit the version from the endpoint\
  \ URL, Boolean response values are returned like this: `true` or `false`."
logo: "adyen.com-TfmAPIService-logo.svg"
logoMediaType: "image/svg+xml"
tags:
- "payment"
stubs: "adyen.com-TfmAPIService-stubs.json"
swagger: "adyen.com-TfmAPIService-swagger.json"
---
