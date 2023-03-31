---
slug: "adyen-com-CheckoutService"
title: "Adyen Checkout API"
provider: "adyen.com"
description: "Adyen Checkout API provides a simple and flexible way to initiate and\
  \ authorise online payments. You can use the same integration for payments made\
  \ with cards (including 3D Secure), mobile wallets, and local payment methods (for\
  \ example, iDEAL and Sofort).\n\nThis API reference provides information on available\
  \ endpoints and how to interact with them. To learn more about the API, visit [online\
  \ payments documentation](https://docs.adyen.com/online-payments).\n\n## Authentication\n\
  Each request to Checkout API must be signed with an API key. For this, [get your\
  \ API key](https://docs.adyen.com/development-resources/api-credentials#generate-api-key)\
  \ from your Customer Area, and set this key to the `X-API-Key` header value, for\
  \ example:\n\n```\ncurl\n-H \"Content-Type: application/json\" \\\n-H \"X-API-Key:\
  \ YOUR_API_KEY\" \\\n...\n```\n## Versioning\nCheckout API supports [versioning](https://docs.adyen.com/development-resources/versioning)\
  \ using a version suffix in the endpoint URL. This suffix has the following format:\
  \ \"vXX\", where XX is the version number.\n\nFor example:\n```\nhttps://checkout-test.adyen.com/v70/payments\n\
  ```\n\n## Going live\n\nTo access the live endpoints, you need an API key from your\
  \ live Customer Area.\n\nThe live endpoint URLs contain a prefix which is unique\
  \ to your company account, for example:\n```\nhttps://{PREFIX}-checkout-live.adyenpayments.com/checkout/v70/payments\n\
  ```\n\nGet your `{PREFIX}` from your live Customer Area under **Developers** > **API\
  \ URLs** > **Prefix**.\n\nWhen preparing to do live transactions with Checkout API,\
  \ follow the [go-live checklist](https://docs.adyen.com/online-payments/go-live-checklist)\
  \ to make sure you've got all the required configuration in place.\n\n## Release\
  \ notes\nHave a look at the [release notes](https://docs.adyen.com/online-payments/release-notes?integration_type=api&version=70)\
  \ to find out what changed in this version!"
logo: "adyen.com-CheckoutService-logo.png"
logoMediaType: "image/png"
tags:
- "payment"
stubs: "adyen.com-CheckoutService-stubs.json"
swagger: "adyen.com-CheckoutService-swagger.json"
---
