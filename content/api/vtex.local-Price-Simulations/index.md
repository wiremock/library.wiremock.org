---
slug: "vtex-local-Price-Simulations"
title: "Price Simulations API"
provider: "vtex.local"
description: "\r\n> Check the new [Pricing onboarding guide](https://developers.vtex.com/docs/guides/pricing-overview).\
  \ We created this guide to improve the onboarding experience for developers at VTEX.\
  \ It assembles all documentation on our Developer Portal about Pricing and is organized\
  \ by focusing on the developer's journey\r\n\r\nThe Price Simulations API allows\
  \ you to configure custom price selectors for B2B stores, based on the context set\
  \ by the [Orders Configuration app](https://developers.vtex.com/docs/guides/vtex-order-configuration).\r\
  \n\r\n## Custom Prices\r\n\r\nIn this section, you can create a specific shopping\
  \ scenario with the criteria you want. For explaining purpose, we used the `orderType`\
  \ and `state` as default values, but it can be others too.\r\n\r\n`GET` [Get custom\
  \ prices schema](https://developers.vtex.com/docs/api-reference/price-simulations#get-/_v/custom-prices/session/schema)\r\
  \n`POST` [Create or Update custom prices schema](https://developers.vtex.com/docs/api-reference/price-simulations#post-/_v/custom-prices/session/schema)\r\
  \n\r\n## Session Management\r\n\r\nEvery time you edit a configuration value set\
  \ on the Custom Prices session, you must use this endpoint to update the Order Configuration.\r\
  \n\r\n`POST` [Update Order Configuration](https://developers.vtex.com/docs/api-reference/price-simulations#post-/sessions/)\r\
  \n\r\n\r\n## Price Association\r\n\r\nUse these routes to associate a shopping scenario,\
  \ created at the Custom Price session, to a specific price table.\r\n\r\n`GET` [Get\
  \ price association by ID](https://developers.vtex.com/docs/api-reference/price-simulations#get-/_v/custom-prices/rules/-priceAssociationId-)\r\
  \n`POST` [Create price association](https://developers.vtex.com/docs/api-reference/price-simulations#post-/_v/custom-prices/rules)\r\
  \n`PUT` [Update price association by ID](https://developers.vtex.com/docs/api-reference/price-simulations#put-/_v/custom-prices/rules/-priceAssociationId-)\r\
  \n`DELETE` [Disassociate price association by ID](https://developers.vtex.com/docs/api-reference/price-simulations#delete-/_v/custom-prices/rules/-priceAssociationId-)"
logo: "vtex.local-Price-Simulations-logo.svg"
logoMediaType: "image/svg+xml"
tags: []
stubs: "vtex.local-Price-Simulations-stubs.json"
swagger: "vtex.local-Price-Simulations-swagger.json"
---
