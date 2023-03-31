---
slug: "adyen-com-PayoutService"
title: "Adyen Payout API"
provider: "adyen.com"
description: "A set of API endpoints that allow you to store payout details, confirm,\
  \ or decline a payout.\n\nFor more information, refer to [Online payouts](https://docs.adyen.com/online-payments/online-payouts).\n\
  ## Authentication\nTo use the Payout API, you need to have [two API credentials](https://docs.adyen.com/online-payments/online-payouts#payouts-to-bank-accounts-and-wallets):\
  \ one for storing payout details and submitting payouts, and another one for confirming\
  \ or declining payouts. If you don't have the required API credentials, contact\
  \ our [Support Team](https://www.adyen.help/hc/en-us/requests/new).\n\nBoth of these\
  \ API credentials must be authenticated with [basic authentication](https://docs.adyen.com/development-resources/api-credentials#basic-authentication).The\
  \ following example shows how to authenticate your request when submitting a payout:\n\
  \n```\ncurl\n-U \"storePayout@Company.YOUR_COMPANY_ACCOUNT\":\"YOUR_BASIC_AUTHENTICATION_PASSWORD\"\
  \ \\\n-H \"Content-Type: application/json\" \\\n...\n```\n\n## Versioning\nPayments\
  \ API supports [versioning](https://docs.adyen.com/development-resources/versioning)\
  \ using a version suffix in the endpoint URL. This suffix has the following format:\
  \ \"vXX\", where XX is the version number.\n\nFor example:\n```\nhttps://pal-test.adyen.com/pal/servlet/Payout/v68/payout\n\
  ```\n\n## Going live\n\nTo authenticate to the live endpoints, you need [API credentials](https://docs.adyen.com/development-resources/api-credentials)\
  \ from your live Customer Area.\n\nThe live endpoint URLs contain a prefix which\
  \ is unique to your company account:\n```\n\nhttps://{PREFIX}-pal-live.adyenpayments.com/pal/servlet/Payout/v68/payout\n\
  ```\n\nGet your `{PREFIX}` from your live Customer Area under **Developers** > **API\
  \ URLs** > **Prefix**."
logo: "adyen.com-PayoutService-logo.svg"
logoMediaType: "image/svg+xml"
tags:
- "payment"
stubs: "adyen.com-PayoutService-stubs.json"
swagger: "adyen.com-PayoutService-swagger.json"
---
