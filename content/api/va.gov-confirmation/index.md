---
slug: "va-gov-confirmation"
title: "Veteran Confirmation"
provider: "va.gov"
description: "The Veteran Confirmation API allows you to confirm Veteran status for\
  \ a given person. This can be useful for offering Veterans discounts or other benefits.\n\
  \nThe API will only return “Confirmed” or “Not Confirmed”.\n\n## Quickstart Guide\n\
  ### 1. Get Access Credentials\nGet started by filling out the form on the [Apply\
  \ for VA Lighthouse Developer Access](https://developer.va.gov/apply) page.\n\n\
  After submitting a request, you will receive your credentials for using the API\
  \ in the Development environment, which allows you to try it out with mock data\
  \ before moving to the Production environment.\n\n### 2. Test the API\nIn the endpoint\
  \ documentation below, we've provided a curl command builder for trying out the\
  \ API before implementation with your app.\nUse [Test User](https://github.com/department-of-veterans-affairs/vets-api-clients/blob/master/test_accounts/confirmation_test_accounts.md)\
  \ attributes to populate the request body.\n\n### 3. Build your app\nThe base URI\
  \ for the Veteran Confirmation API in the Sandbox environment is:\n\nhttps://sandbox-api.va.gov/services/veteran_confirmation/v0\n\
  \nIn this environment, use attributes from the list of [Test Users](https://github.com/department-of-veterans-affairs/vets-api-clients/blob/master/test_accounts/confirmation_test_accounts.md).\
  \ Only Test Users can return a `\"confirmed\"` response.\n\nCheck out some of our\
  \ [sample apps](https://github.com/department-of-veterans-affairs/vets-api-clients).\
  \ Please visit our VA Lighthouse [Support portal](https://developer.va.gov/support)\
  \ should you need further assistance.\n\n### 4. Show us a demo and get access to\
  \ the Production environment\nAfter building your app, we ask that you give us a\
  \ demo before we set you up with production credentials. Please see the [Path to\
  \ Production](https://developer.va.gov/go-live) page for more details.\n\n## Authorization\n\
  This API requires an API key in combination with identifiable information for the\
  \ person being confirmed listed below. API requests are authorized through a symmetric\
  \ API token provided in an HTTP header with name `apikey`. Including more information\
  \ has a better chance of making a match and returning a Confirmed status.\n### Required\
  \ information:\n* First Name\n* Last Name\n* Date of Birth\n* Social Security Number\n\
  \n### Optional information:\n* Middle Name\n* Gender\n\n## Reference\n### Sandbox\
  \ vs. Production Data\nAPIs accessed via the Sandbox environment are using the same\
  \ underlying logic as VA’s production APIs; only the underlying data store is different.\n\
  \n### Master Veteran Index (MVI)\nThe Master Veteran Index confirms a user's identity.\
  \ In Production, several factors are considered to confirm identity. These include:\
  \ a user’s first name, last name, date of birth and Social Security number. The\
  \ MVI is mocked in the Sandbox environment. In this environment, the only factor\
  \ used to confirm identity is the Social Security number.\n\n### Rate Limiting\n\
  We implemented basic rate limiting of 60 requests per minute. If you exceed this\
  \ quota, your request will return a 429 status code. You may petition for increased\
  \ rate limits by emailing and requests will be decided on a case by case basis.\n\
  \n### Raw Open API Spec\nhttps://api.va.gov/services/veteran_confirmation/docs/v0/api\n"
logo: "va.gov-confirmation-logo.png"
logoMediaType: "image/png"
tags:
- "open_data"
stubs: "va.gov-confirmation-stubs.json"
swagger: "va.gov-confirmation-swagger.json"
---
