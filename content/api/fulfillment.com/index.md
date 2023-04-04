---
slug: "fulfillment-com"
title: "Fulfillment.com APIv2"
provider: "fulfillment.com"
description: "Welcome to our current iteration of our REST API. While we encourage\
  \ you to upgrade to v2.0 we will continue support for our [SOAP API](https://github.com/fulfillment/soap-integration).\n\
  \n# Versioning\n\nThe Fulfillment.com (FDC) REST API is version controlled and backwards\
  \ compatible. We have many future APIs scheduled for publication within our v2.0\
  \ spec so please be prepared for us to add data nodes in our responses, however,\
  \ we will not remove knowledge from previously published APIs.\n\n#### A Current\
  \ Response\n\n```javascript\n{\n  id: 123\n}\n```\n\n#### A Potential Future Response\n\
  \n```javascript\n{\n  id: 123,\n  reason: \"More Knowledge\"\n}\n```\n\n# Getting\
  \ Started\n\nWe use OAuth v2.0 to authenticate clients, you can choose [implicit](https://oauth.net/2/grant-types/implicit/)\
  \ or [password](https://oauth.net/2/grant-types/password/) grant type. To obtain\
  \ an OAuth `client_id` and `client_secret` contact your account executive.\n\n**Tip**:\
  \ Generate an additional login and use those credentials for your integration so\
  \ that changes are accredited to that \"user\".\n\nYou are now ready to make requests\
  \ to our other APIs by filling your `Authorization` header with `Bearer {access_token}`.\n\
  \n## Perpetuating Access\n\nPerpetuating access to FDC without storing your password\
  \ locally can be achieved using the `refresh_token` returned by [POST /oauth/access_token](#operation/generateToken).\n\
  \nA simple concept to achieve this is outlined below.\n\n1. Your application/script\
  \ will ask you for your `username` and `password`, your `client_id` and `client_secret`\
  \ will be accessible via a DB or ENV.\n2. [Request an access_token](#operation/generateToken)\n\
  \  + Your function should be capable of formatting your request for both a `grant_type`\
  \ of \\\"password\\\" (step 1) and \\\"refresh_token\\\" (step 4).\n3. Store the\
  \ `access_token` and `refresh_token` so future requests can skip step 1\n4. When\
  \ the `access_token` expires request anew using your `refresh_token`, replace both\
  \ tokens in local storage.\n\n+ If this fails you will have to revert to step 1.\n\
  \nAlternatively if you choose for your application/script to have access to your\
  \ `username` and `password` you can skip step 4.\n\nIn all scenarios we recommend\
  \ storing all credentials outside your codebase.\n\n## Date Time Definitions\n\n\
  We will report all date-time stamps using the [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)\
  \ standard. When using listing API's where fromDate and toDate are available note\
  \ that both dates are inclusive while requiring the fromDate to be before or at\
  \ the toDate.\n\n### The Fulfillment Process\n\nMany steps are required to fulfill\
  \ your order we report back to you three fundamental milestones inside the orders\
  \ model.\n\n* `recordedOn` When we received your order. This will never change.\n\
  \n* `dispatchDate` When the current iteration of your order was scheduled for fulfillment.\
  \ This may change however it is an indicator that the physical process of fulfillment\
  \ has begun and a tracking number has been **assigned** to your order. The tracking\
  \ number **MAY CHANGE**. You will not be able to cancel an order once it has been\
  \ dispatched. If you need to recall an order that has been dispatched please contact\
  \ your account executive.\n\n* `departDate` When we recorded your order passing\
  \ our final inspection and placed with the carrier. At this point it is **safe to\
  \ inform the consignee** of the tracking number as it will not change.\n\n## Evaluating\
  \ Error Responses\n\nWe currently return two different error models, with and without\
  \ context. All errors will include a `message` node while errors with `context`\
  \ will include additional information designed to save you time when encountering\
  \ highly probable errors. For example, when you send us a request to create a duplicate\
  \ order, we will reject your request and the context will include the FDC order\
  \ `id` so that you may record it for your records.\n\n### Without Context\n\nNew\
  \ order with missing required fields.\n\n| Header | Response |\n| ------ | --------\
  \ |\n| Status | `400 Bad Request` |\n\n```javascript\n{    \n  \"message\": \"Invalid\
  \ request body\"\n}\n```\n\n### With Context\n\nNew order with duplicate `merchantOrderId`.\n\
  \n| Header | Response |\n| ------ | -------- |\n| Status | `409 Conflict` |\n\n\
  ```javascript\n{\n  \"message\": \"Duplicate Order\",\n  \"context\": {\n    \"\
  id\": 123\n  }\n}\n```\n\n## Status Codes\n\nCodes are a concatenation of State,\
  \ Stage, and Detail.\n\n`^([0-9]{2})([0-9]{2})([0-9]{2})$`\n\n| Code | State   \
  \           | Stage    | Detail         |\n| ---- | ------------------ | --------\
  \ | -------------- |\n| 010101 | Processing Order | Recieved | Customer Order |\n\
  | 010102 | Processing Order | Recieved | Recieved |\n| 010201 | Processing Order\
  \ | Approved | |\n| 010301 | Processing Order | Hold | Merchant Stock |\n| 010302\
  \ | Processing Order | Hold | Merchant Funds |\n| 010303 | Processing Order | Hold\
  \ | For Merchant |\n| 010304 | Processing Order | Hold | Oversized Shipment |\n\
  | 010305 | Processing Order | Hold | Invalid Parent Order |\n| 010306 | Processing\
  \ Order | Hold | Invalid Address |\n| 010307 | Processing Order | Hold | By Admin\
  \ |\n| 010401 | Processing Order | Address Problem | Incomplete Address |\n| 010402\
  \ | Processing Order | Address Problem | Invalid Locality |\n| 010403 | Processing\
  \ Order | Address Problem | Invalid Region |\n| 010404 | Processing Order | Address\
  \ Problem | Address Not Found |\n| 010405 | Processing Order | Address Problem |\
  \ Many Addresses Found |\n| 010406 | Processing Order | Address Problem | Invalid\
  \ Postal Code |\n| 010407 | Processing Order | Address Problem | Country Not Mapped\
  \ |\n| 010408 | Processing Order | Address Problem | Invalid Recipient Name |\n\
  | 010409 | Processing Order | Address Problem | Bad UK Address |\n| 010410 | Processing\
  \ Order | Address Problem | Invalid Address Line 1 or 2 |\n| 010501 | Processing\
  \ Order | Sku Problem | Invalid SKU |\n| 010501 | Processing Order | Sku Problem\
  \ | Child Order has Invalid SKUs |\n| 010601 | Processing Order | Facility Problem\
  \ | Facility Not Mapped |\n| 010701 | Processing Order | Ship Method Problem | Unmapped\
  \ Ship Method |\n| 010702 | Processing Order | Ship Method Problem | Unmapped Ship\
  \ Cost |\n| 010703 | Processing Order | Ship Method Problem | Missing Ship Method\
  \ |\n| 010704 | Processing Order | Ship Method Problem | Invalid Ship Method |\n\
  | 010705 | Processing Order | Ship Method Problem | Order Weight Outside of Ship\
  \ Method Weight |\n| 010801 | Processing Order | Inventory Problem | Insufficient\
  \ Inventory In Facility |\n| 010802 | Processing Order | Inventory Problem | Issue\
  \ Encountered During Inventory Adjustment |\n| 010901 | Processing Order | Released\
  \ To WMS | Released |\n| 020101 | Fulfillment In Progress | Postage Problem | Address\
  \ Issue |\n| 020102 | Fulfillment In Progress | Postage Problem | Postage OK, OMS\
  \ Issue Occurred |\n| 020103 | Fulfillment In Progress | Postage Problem | Postage\
  \ Void Failed |\n| 020201 | Fulfillment In Progress | Postage Acquired | |\n| 020301\
  \ | Fulfillment In Progress | Postage Voided | Postage Void Failed Gracefully |\n\
  | 020301 | Fulfillment In Progress | Hold | Departure Hold Requested |\n| 020401\
  \ | Fulfillment In Progress | 4PL Processing | |\n| 020501 | Fulfillment In Progress\
  \ | 4PL Problem | Order is Proccessable, Postage Issue Occurred |\n| 020601 | Fulfillment\
  \ In Progress | Label Printed | |\n| 020701 | Fulfillment In Progress | Shipment\
  \ Cubed | |\n| 020801 | Fulfillment In Progress | Picking Inventory | |\n| 020901\
  \ | Fulfillment In Progress | Label Print Verified | |\n| 021001 | Fulfillment In\
  \ Progress | Passed Final Inspection | |\n| 030101 | Shipped | Fulfilled By 4PL\
  \ | |\n| 030102 | Shipped | Fulfilled By 4PL | Successfully Fulfilled, OMS Encountered\
  \ Issue During Processing |\n| 030201 | Shipped | Fulfilled By FDC | |\n| 040101\
  \ | Returned | Returned | |\n| 050101 | Cancelled | Cancelled | |\n| 060101 | Test\
  \ | Test | Test |\n"
logo: "fulfillment.com-logo.png"
logoMediaType: "image/png"
tags:
- "ecommerce"
stubs: "fulfillment.com-stubs.json"
swagger: "fulfillment.com-swagger.json"
---