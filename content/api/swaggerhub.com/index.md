---
slug: "swaggerhub-com"
title: "SwaggerHub Registry API"
provider: "swaggerhub.com"
description: "# Overview\nUse SwaggerHub Registry API to access, manage, and update\
  \ the following resources in SwaggerHub, bypassing the web interface:\n  * APIs\n\
  \  * Domains\n  * Integrations\n  * Projects\n  * Templates\n\n\nSwaggerHub also\
  \ provides the [User Management API](https://app.swaggerhub.com/apis-docs/swagger-hub/user-management-api/)\
  \ to get information about organizations and manage organization members.\n\n# Base\
  \ URL\nUse the following base URL for SwaggerHub SaaS:\n    \n    http(s)://api.swaggerhub.com\n\
  \n**Note:** This documentation is for SwaggerHub SaaS. On-Premise customers should\
  \ use the bundled API definition, which can be found at the URLs provided below.\n\
  \nVersion 1.29.0 or later:\n\n    http(s)://SERVER/v1/openapi.yaml - YAML version\n\
  \    http(s)://SERVER/v1/openapi.json - JSON version\n\nEarlier versions:\n\n  \
  \  http(s)://SERVER/v1/swagger.yaml - YAML version\n    http(s)://SERVER/v1/swagger.json\
  \ - JSON version\n\n# Authentication\nOperations that update data or access private\
  \ data require authentication using an API key. You can find your personal API key\
  \ on the [API Keys](https://app.swaggerhub.com/settings/apiKey) page in your account\
  \ settings. Send this key in the `Authorization` header when making requests to\
  \ the Registry API:\n\n    Authorization: YOUR_API_KEY\n\nTo test API calls from\
  \ this documentation page, click the **Authorize** button below and paste your API\
  \ key there.\n\n**Important:** Keep the API key secure and do not store it directly\
  \ in your code.\n# Tools\nIn addition to calling the Registry API directly, you\
  \ can use the following tools to interact with the API from the command line or\
  \ CI/CD pipeline:\n\n * [SwaggerHub CLI](https://www.npmjs.com/package/swaggerhub-cli)\
  \ \n * [Maven plugin](https://github.com/swagger-api/swaggerhub-maven-plugin)\n\
  \ * [Gradle plugin](https://github.com/swagger-api/swaggerhub-gradle-plugin)\n"
logo: "swaggerhub.com-logo.jpeg"
logoMediaType: "image/jpeg"
tags:
- "developer_tools"
stubs: "swaggerhub.com-stubs.json"
swagger: "swaggerhub.com-swagger.json"
---
