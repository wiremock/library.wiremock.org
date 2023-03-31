---
slug: "adyen-com-HopService"
title: "Hosted onboarding API"
provider: "adyen.com"
description: "This API is used for the classic integration. If you are just starting\
  \ your implementation, refer to our [new integration guide](https://docs.adyen.com/marketplaces-and-platforms)\
  \ instead.\n\nThe Hosted onboarding API provides endpoints that you can use to generate\
  \ links to Adyen-hosted pages, such as an [onboarding page](https://docs.adyen.com/marketplaces-and-platforms/classic/hosted-onboarding-page)\
  \ or a [PCI compliance questionnaire](https://docs.adyen.com/marketplaces-and-platforms/classic/platforms-for-partners).\
  \ You can provide these links to your account holders so that they can complete\
  \ their onboarding.\n\n## Authentication\nYour Adyen contact will provide your API\
  \ credential and an API key. To connect to the API, add an `X-API-Key` header with\
  \ the API key as the value, for example:\n\n ```\ncurl\n-H \"Content-Type: application/json\"\
  \ \\\n-H \"X-API-Key: YOUR_API_KEY\" \\\n...\n```\n\nAlternatively, you can use\
  \ the username and password to connect to the API using basic authentication. For\
  \ example:\n\n```\ncurl\n-U \"ws@MarketPlace.YOUR_PLATFORM_ACCOUNT\":\"YOUR_WS_PASSWORD\"\
  \ \\\n-H \"Content-Type: application/json\" \\\n...\n```\nWhen going live, you need\
  \ to generate new web service user credentials to access the [live endpoints](https://docs.adyen.com/development-resources/live-endpoints).\n\
  \n## Versioning\nThe Hosted onboarding API supports [versioning](https://docs.adyen.com/development-resources/versioning)\
  \ using a version suffix in the endpoint URL. This suffix has the following format:\
  \ \"vXX\", where XX is the version number.\n\nFor example:\n```\nhttps://cal-test.adyen.com/cal/services/Hop/v6/getOnboardingUrl\n\
  ```"
logo: "adyen.com-HopService-logo.svg"
logoMediaType: "image/svg+xml"
tags:
- "payment"
stubs: "adyen.com-HopService-stubs.json"
swagger: "adyen.com-HopService-swagger.json"
---
