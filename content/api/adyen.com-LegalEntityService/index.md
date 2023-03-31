---
slug: "adyen-com-LegalEntityService"
title: "Legal Entity Management API"
provider: "adyen.com"
description: "The Legal Entity Management API enables you to manage legal entities\
  \ that contain information required for verification. \n## Authentication\nTo connect\
  \ to the Legal Entity Management API, you must use the basic authentication credentials\
  \ of your web service user. If you don't have one, contact the [Adyen Support Team](https://www.adyen.help/hc/en-us/requests/new).\
  \ Use the web service user credentials to authenticate your request, for example:\n\
  \n```\ncurl\n-U \"ws_123456@Scope.BalancePlatform_YourBalancePlatform\":\"YourWsPassword\"\
  \ \\\n-H \"Content-Type: application/json\" \\\n...\n```\nNote that when going live,\
  \ you need to generate new web service user credentials to access the [live endpoints](https://docs.adyen.com/development-resources/live-endpoints).\n\
  \n## Versioning\nThe Legal Entity Management API supports versioning of its endpoints\
  \ through a version suffix in the endpoint URL. This suffix has the following format:\
  \ \"vXX\", where XX is the version number.\n\nFor example:\n```\nhttps://kyc-test.adyen.com/lem/v3/legalEntities\n\
  ```\n## Going live\nWhen going live, your Adyen contact will provide your API credential\
  \ for the live environment. You can then use the username and password to send requests\
  \ to `https://kyc-live.adyen.com/lem/v3`.\n\n"
logo: "adyen.com-LegalEntityService-logo.svg"
logoMediaType: "image/svg+xml"
tags:
- "payment"
stubs: "adyen.com-LegalEntityService-stubs.json"
swagger: "adyen.com-LegalEntityService-swagger.json"
---
