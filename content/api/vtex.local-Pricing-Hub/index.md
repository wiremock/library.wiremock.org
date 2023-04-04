---
slug: "vtex-local-Pricing-Hub"
title: "Pricing Hub"
provider: "vtex.local"
description: "> This feature is in closed beta, available only for selected customers.\
  \ If you have any questions, contact our [Support](https://support.vtex.com/hc/en-us/requests).\
  \ \r\n\r\n In the B2B scenario, it is common for stores to have personalized prices\
  \ per customer and complex pricing systems that require external integrations. Pricing\
  \ Hub is a system developed for the B2B context that works as an intermediary between\
  \ VTEX and external pricing systems.\r\n\r\n In VTEX, B2B stores have the option\
  \ to use our internal pricing system or an external one. If the store chooses to\
  \ operate with an external pricing system, Pricing Hub will query an external price\
  \ calculation API. The external API should then respond with the price for all items\
  \ in the shopping cart according to its predefined tax rules.\r\n\r\n![Pricing hub\
  \ protocal diagram](https://user-images.githubusercontent.com/77292838/211634260-e4f7a516-91df-416e-ab43-d9c79d56bc91.png)\r\
  \n\r\n## Implementation\r\n\r\nTo connect with external pricing systems using Pricing\
  \ Hub, it is necessary to build a VTEX IO middleware app. We offer two reference\
  \ implementation templates to simplify this process:\r\n\r\n- [C# template](https://github.com/vtex-apps/external-prices-app)\r\
  \n- [Node template](https://github.com/vtex-apps/external-prices-node)\r\n\r\nRead\
  \ the documentation on each repository to learn more about the required steps to\
  \ use and customize the app.\r\n\r\n> The app used by Pricing Hub to connect must\
  \ be a `major 0`. \r\n\r\n## Specifications\r\n\r\nSee below all the specifications\
  \ of the request and the response expected when communicating with Pricing Hub.\r\
  \n\r\n### Price calculation request\r\n\r\nThe external prices calculation tool\
  \ must provide an endpoint that will receive a `POST` [Get Prices](https://developers.vtex.com/docs/api-reference/pricing-hub#post-/api/pricing-hub/prices)\
  \ request. This route retrieves and applies prices for the items that are passed\
  \ in the request. Pricing Hub will select the pricing method that will be used for\
  \ each item and will fetch their respective price from the selected pricing method.\r\
  \n\r\n>⚠️ Responses from Pricing Hub tend to have a greater delay when compared\
  \ to other VTEX systems. That is expected, however, due to the complexity of its\
  \ nested requests. The timeout for this request is 900 milliseconds.\r\n\r\nIn this\
  \ request, Pricing Hub provides a body in a specific format, exemplified below.\
  \ This means that either the endpoint must be prepared to receive this body format,\
  \ or the app must contain a parser to adapt it to the correct format.\r\n\r\n####\
  \ Request body example\r\n\r\n```json\r\n{\r\n    \"item\": \r\n        {\r\n  \
  \          \"index\": 0,\r\n            \"skuId\": \"880011\",\r\n            \"\
  quantity\": 1\r\n        },\r\n    \"context\":{\r\n        \"email\": \"john@email.com\"\
  \r\n    }\r\n}\r\n```\r\n\r\nThe request body should have the following properties:\r\
  \n\r\n| **Attribute** | **Type** | **Description**                             \
  \                                                                              \
  \                                                                              \
  \ |\r\n|---------------|----------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|\r\
  \n| `item`        | object   | The item whose price is supposed to be fetched by\
  \ Pricing Hub.                                                                 \
  \                                                                          |\r\n\
  | ↪ `index`     | integer  | This is the index of the item at Checkout's cart. It\
  \ has to be unique in the items array.                                         \
  \                                                                       |\r\n| ↪\
  \ `skuId`     | string   | This is the SKU ID of the item that will be priced. \
  \                                                                              \
  \                                                                       |\r\n| ↪\
  \ `quantity`  | integer  | This is the amount of items that will be priced. It is\
  \ possible to have a volume discount for many repeated items. Hence, the price may\
  \ not be the quantity of the item multiplied by the unitary price. |\r\n| `context`\
  \     | object   | The object that contains the context to inform the query.   \
  \                                                                              \
  \                                                               |\r\n| ↪ `email`\
  \     | string   | The customer's email address. If there is no value, use an empty\
  \ string.                                                                      \
  \                                                           |\r\n\r\n### External\
  \ prices provider response\r\n\r\nIn response to the request sent by Pricing Hub,\
  \ we expect an outcome in the following format:\r\n\r\n```json\r\n{\r\n    \"item\"\
  : {\r\n        \"price\": 54035,\r\n        \"priceTables\": \"special\",\r\n  \
  \      \"index\": 0,\r\n        \"skuId\": \"880011\",\r\n        \"listPrice\"\
  : 54035,\r\n        \"costPrice\": 50000,\r\n        \"sellingPrice\": 54035,\r\n\
  \        \"priceValidUntil\": \"2023-01-27T20:29:57Z\",\r\n        \"tradePolicyId\"\
  : \"special\"\r\n    }\r\n}\r\n```\r\n\r\nThe response should have the following\
  \ properties:\r\n\r\n| **Attribute**       | **Type** | **Description**        \
  \                                                                              \
  \                                                  |\r\n|---------------------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|\r\
  \n| `item`              | object   | The object that contains the price data.  \
  \                                                                              \
  \                               |\r\n| ↪ `price`           | integer  | The price\
  \ returned by the pricing API that was used by Pricing-Hub. It is measured in cents,\
  \ so 5000 means 50,00 in local currency.                    |\r\n| ↪ `priceTables`\
  \     | string   | The price table that was used to price the item.            \
  \                                                                              \
  \             |\r\n| ↪ `index`           | integer  | The same index referring to\
  \ Checkout's cart that was passed to the API.                                  \
  \                                              |\r\n| ↪ `skuId`           | string\
  \   | The same SKU ID that was passed to the API.                              \
  \                                                                              |\r\
  \n| ↪ `listPrice`       | integer  | The list price returned by the pricing API\
  \ that was used by Pricing Hub. It is measured in cents, so 5000 means 50,00 in\
  \ local currency.               |\r\n| ↪ `costPrice`       | integer  | The cost\
  \ price returned by the pricing API that was used by Pricing-Hub. It is measured\
  \ in cents, so 5000 means 50,00 in local currency.               |\r\n| ↪ `sellingPrice`\
  \    | integer  | The computed price before applying coupons, taxes or promotions.\
  \                                                                              \
  \         |\r\n| ↪ `priceValidUntil` | string   | The moment up until the price\
  \ is valid. After that moment, it will be necessary to call the pricing API again.\
  \ The format of the string is in RFC3339. |\r\n| ↪ `tradePolicyId`   | string  \
  \ | Trade Policy ID.                                                           \
  \                                                                            |\r\
  \n\r\n## Index - Pricing Hub API\r\n\r\n`POST` [Get Prices](https://developers.vtex.com/docs/api-reference/pricing-hub#post-/api/pricing-hub/prices)\r\
  \n`PUT` [Configure External Price Source](https://developers.vtex.com/docs/api-reference/pricing-hub#put-/config)\r\
  \n"
logo: "vtex.local-Pricing-Hub-logo.svg"
logoMediaType: "image/svg+xml"
tags: []
stubs: "vtex.local-Pricing-Hub-stubs.json"
swagger: "vtex.local-Pricing-Hub-swagger.json"
---