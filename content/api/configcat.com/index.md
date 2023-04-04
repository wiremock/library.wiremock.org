---
slug: "configcat-com"
title: "ConfigCat Public Management API"
provider: "configcat.com"
description: "**Base API URL**: https://api.configcat.com\n\nIf you prefer the swagger\
  \ documentation, you can find it here: [Swagger UI](https://api.configcat.com/swagger).\n\
  \nThe purpose of this API is to access the ConfigCat platform programmatically.\
  \ \nYou can **Create**, **Read**, **Update** and **Delete** any entities like **Feature\
  \ Flags, Configs, Environments** or **Products** within ConfigCat. \n\nThe API is\
  \ based on HTTP REST, uses resource-oriented URLs, status codes and supports JSON\
  \ \nand JSON+HAL format. Do not use this API for accessing and evaluating feature\
  \ flag values. Use the [SDKs instead](https://configcat.com/docs/sdk-reference/overview).\n\
  \n\n# OpenAPI Specification\n\nThe complete specification is publicly available\
  \ here: [swagger.json](v1/swagger.json). \nYou can use it to generate client libraries\
  \ in various languages with [OpenAPI Generator](https://github.com/OpenAPITools/openapi-generator)\
  \ or\n[Swagger Codegen](https://swagger.io/tools/swagger-codegen/) to interact with\
  \ this API.\n\n# Authentication\nThis API uses the [Basic HTTP Authentication Scheme](https://en.wikipedia.org/wiki/Basic_access_authentication).\
  \ \n\n<!-- ReDoc-Inject: <security-definitions> -->\n\n# Throttling and rate limits\n\
  All the rate limited API calls are returning information about the current rate\
  \ limit period in the following HTTP headers:\n\n| Header | Description |\n| :-\
  \ | :- |\n| X-Rate-Limit-Remaining | The maximum number of requests remaining in\
  \ the current rate limit period. |\n| X-Rate-Limit-Reset     | The time\twhen the\
  \ current rate limit period resets.\t\t\t\t\t\t  |\n\nWhen the rate limit is exceeded\
  \ by a request, the API returns with a `HTTP 429 - Too many requests` status along\
  \ with a `Retry-After` HTTP header.\n"
logo: "configcat.com-logo.svg"
logoMediaType: "image/svg+xml"
tags:
- "developer_tools"
stubs: "configcat.com-stubs.json"
swagger: "configcat.com-swagger.json"
---
