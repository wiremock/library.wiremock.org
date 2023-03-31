---
slug: "airbyte-local-config"
title: "Airbyte Configuration API"
provider: "airbyte.local"
description: "Airbyte Configuration API\n[https://airbyte.io](https://airbyte.io).\n\
  \nThis API is a collection of HTTP RPC-style methods. While it is not a REST API,\
  \ those familiar with REST should find the conventions of this API recognizable.\n\
  \nHere are some conventions that this API follows:\n* All endpoints are http POST\
  \ methods.\n* All endpoints accept data via `application/json` request bodies. The\
  \ API does not accept any data via query params.\n* The naming convention for endpoints\
  \ is: localhost:8000/{VERSION}/{METHOD_FAMILY}/{METHOD_NAME} e.g. `localhost:8000/v1/connections/create`.\n\
  * For all `update` methods, the whole object must be passed in, even the fields\
  \ that did not change.\n\nAuthentication (OSS):\n* When authenticating to the Configuration\
  \ API, you must use Basic Authentication by setting the Authentication Header to\
  \ Basic and base64 encoding the username and password (which are `airbyte` and `password`\
  \ by default - so base64 encoding `airbyte:password` results in `YWlyYnl0ZTpwYXNzd29yZA==`).\
  \ So the full header reads `'Authorization': \"Basic YWlyYnl0ZTpwYXNzd29yZA==\"\
  `\n"
logo: "airbyte.local-config-logo.svg"
logoMediaType: "image/svg+xml"
tags:
- "developer_tools"
stubs: "airbyte.local-config-stubs.json"
swagger: "airbyte.local-config-swagger.json"
---
