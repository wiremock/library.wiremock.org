---
slug: "adyen-com-ManagementService"
title: "Management API"
provider: "adyen.com"
description: "Configure and manage your Adyen company and merchant accounts, stores,\
  \ and payment terminals.\n## Authentication\nEach request to the Management API\
  \ must be signed with an API key. [Generate your API key](https://docs.adyen.com/development-resources/api-credentials#generate-api-key)\
  \ in the Customer Area and then set this key to the `X-API-Key` header value.\n\n\
  To access the live endpoints, you need to generate a new API key in your live Customer\
  \ Area.\n## Versioning\n\nManagement API handles versioning as part of the endpoint\
  \ URL. For example, to send a request to version 1 of the `/companies/{companyId}/webhooks`\
  \ endpoint, use:\n\n```text\nhttps://management-test.adyen.com/v1/companies/{companyId}/webhooks\n\
  ```\n\n## Going live\n\nTo access the live endpoints, you need an API key from your\
  \ live Customer Area. Use this API key to make requests to:\n\n```text\nhttps://management-live.adyen.com/v1\n\
  ```"
logo: "adyen.com-ManagementService-logo.svg"
logoMediaType: "image/svg+xml"
tags:
- "payment"
stubs: "adyen.com-ManagementService-stubs.json"
swagger: "adyen.com-ManagementService-swagger.json"
---
