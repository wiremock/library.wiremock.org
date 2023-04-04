---
slug: "vtex-local-Pricing-API"
title: "Pricing API"
provider: "vtex.local"
description: "\r\n> Check the new [Pricing onboarding guide](https://developers.vtex.com/vtex-rest-api/docs/pricing-overview).\
  \ We created this guide to improve the onboarding experience for developers at VTEX.\
  \ It assembles all documentation on our Developer Portal about Pricing and is organized\
  \ by focusing on the developer's journey.\r\n\r\nPricing is the VTEX module responsible\
  \ for the SKU's price list. At this module we have the base price of each SKU, some\
  \ optional fixed prices by trade policy, and some rules that can be applied to generate\
  \ dynamically different final prices according to the purchase context and the trade\
  \ policy. The variables used in this collection are:\r\n\r\n  * **{{accountName}}**\
  \ = You VTEX account name.\r\n  * **{{tradePolicyId}}** = Current Trade Policy ID.\r\
  \n  * **{{itemId}}** = SKU ID.\r\n  * **{{X-VTEX-API-AppKey}}** and **{{X-VTEX-API-AppToken}}**\
  \ = Credentials.\r\n\r\nYou can get more information about how to use this module\
  \ and its business logic at [VTEX Help](http://help.vtex.com).\r\n\r\n## Rate Limits\r\
  \n\r\n### Limits per route\r\n\r\n- `GET`:  routes are not rate limited at the moment\r\
  \n- `PUT or POST`: `40 requests/second/account` in any **price insert/update route**\
  \ with 1000 *Burst Credits*\r\n- `DELETE`: `16 requests/second/account` in any **price\
  \ deletion route**, with 300 *Burst Credits*.\r\n\r\n### What are Burst Credits?\r\
  \n\r\nIn case the account exceeds the limit frequency for a  `Rate Limiter` (for\
  \ instance, when one account makes `41 requests/second` in any `price insert/update\
  \ route`), we decrease from the *Burst Credit* count the exceeding (in this example,\
  \ *1 Credit*).\r\n\r\nIn the event of the *Burst Credits* reaching **0 (zero)**,\
  \ the request is blocked with a `Status 429` response.\r\n\r\nThe credits fill up\
  \ over time when the route is not being used, in the same rate as the route's `Rate\
  \ Limiter`. In our example, for each second not sending a **PUT or POST request**,\
  \ we increase *40 Burst Credits* to this `Rate Limiter`\r\n\r\n### New Response\
  \ Headers\r\n\r\nIn the response headers of any request to Pricing v2 there are\
  \ some new headers indicating the current status of the Rate Limiting.\r\nThis information\
  \ may be useful to evaluate the ideal frequency to send requests to a route, and\
  \ when to send a new request in the event of reaching a Rate Limit.\r\n\r\n- `Ratelimit-Limit`\
  \ - Total *Burst Credits* offered to a route\r\n- `Ratelimit-Remaining` - How many\
  \ *Burst Credits* are still available to use\r\n- `Ratelimit-Reset` - How long (in\
  \ seconds) it will take to the *Burst Credits* to fill up completely (It will fill\
  \ up to the `Ratelimit-Limit`)\r\n- `Retry-After` - Indicates how many seconds you\
  \ will need to wait until the `Rate Limiter` accepts a new request to this route\
  \ again. If this header response exists, this means your current request has been\
  \ rate limited and has not been processed.\r\n\r\n### How to integrate with Pricing\
  \ v2 considering our Rate Limits\r\n\r\nIntegrate considering the limits of **requests/route/account**\
  \ specified in the [*Limits per route*](#rate-limits) section, avoiding to surpass\
  \ this frequency.\r\n\r\nIf you happen to be Rate Limited, wait the time in seconds\
  \ specified in `Retry-After` before making another request to the service, and reduce\
  \ the rate of requests per second that your integration is making."
logo: "vtex.local-Pricing-API-logo.svg"
logoMediaType: "image/svg+xml"
tags: []
stubs: "vtex.local-Pricing-API-stubs.json"
swagger: "vtex.local-Pricing-API-swagger.json"
---
