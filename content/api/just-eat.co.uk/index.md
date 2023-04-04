---
slug: "just-eat-co-uk"
title: "Just Eat UK"
provider: "just-eat.co.uk"
description: "# Just Eat API\nJust Eat offers services for our various business partners\
  \ and our consumer applications.\nHow you interact with the API depends on the services\
  \ you wish to interact with.\n## Security\n### HTTPS\nAll api calls and callbacks\
  \ require HTTPS. Your service will need a valid SSL certificate and be accessible\
  \ via the standard SSL port (port 443).\n## Making an API request\nSome API calls\
  \ require an API key, to authenticate the partner calling the API.\n```\nPUT https://uk-partnerapi.just-eat.io/orders/abcd1234\
  \ HTTP/1.1\nAuthorization: JE-API-KEY abcd123456789\n```\nOther calls require a\
  \ user token in the form of a JWT.\n```\nGET https://uk.api.just-eat.io/consumer/me/orders/uk\
  \ HTTP/1.1\nAuthorization: Bearer abcd123456789\n```\n\n## Date Formats\n### Date\
  \ and time formats\nAll dates and times should use the [ISO 8601 standard for representation\
  \ of dates and times](https://en.wikipedia.org/wiki/ISO_8601).\n\n#### For instance:\n\
  * DueDateWithUtcOffset: `\"2015-05-26T14:52:35.5444292+01:00\"`\n  - Local time:\
  \ `14:52`\n  - UTC time: `13:52`\n  - UTC offset: `+1hr` (due to daylight time saving)\n\
  * DueDateWithUtcOffset: `\"2015-02-03T11:10:00.0000000+00:00\"`\n  - Local time:\
  \ `11:10`\n  - UTC time: `11:10`\n  - UTC offset: `0` (no daylight time saving,\
  \ local time is equivalent to UTC)\n\nNote that the offset may be for a timezone\
  \ different to your own, so you should alway convert to your own local time for\
  \ display purposes (e.g. on receipts and terminals).\n\n### Callback timestamps\n\
  Timestamps sent to Just Eat should be recorded as the current local time (including\
  \ any changes needed to account for daylight saving) with an accompanying offset\
  \ that shows the difference between the recorded local time and the current UTC\
  \ time.\n\nIf it is not possible to record timestamps in local time, timestamps\
  \ may be recorded in UTC time with a 00:00 offset.\n## Async Webhooks\nSome of the\
  \ webhooks on the platform are configured as being 'async' webhooks. These are for\
  \ long-running operations, and work as follows:\n  1. Your webhook is invoked with\
  \ a `?callback={returnUrl}` query string parameter. The `returnUrl` is a unique\
  \ URL that you will need to send the async response to.\n  2. Return an immediate\
  \ `202 Accepted` response from the webhook endpoint, to indicate that you have received\
  \ the request.\n  3. Perform the long-running operation. This can be deemed either\
  \ a _success_; or a _failure_.\n  4. If the result is a _**success**_, return the\
  \ following:\n  ```\n  POST {returnUrl} HTTP/1.1\n\n  {\n        \"status\": \"\
  Success\",\n        \"message\": \"{successMessage}\",\n        \"data\": {}   //\
  \ webhook-specific response object\n  }\n  ```\n  5. Otherwise, if the result is\
  \ a _**failure**_, return the following:\n  ```\n  POST {returnUrl} HTTP/1.1\n\n\
  \  {\n        \"status\": \"Failure\",\n        \"message\": \"{failureMessage}\"\
  ,\n        \"data\": {}   // webhook-specific response object\n  }\n  ```"
logo: "just-eat.co.uk-logo.png"
logoMediaType: "image/png"
tags:
- "ecommerce"
stubs: "just-eat.co.uk-stubs.json"
swagger: "just-eat.co.uk-swagger.json"
---
