---
slug: "vtex-local-Marketplace-APIs-"
title: "Suggestions"
provider: "vtex.local"
description: "\r\nThe **Marketplace API** enables marketplaces and sellers hosted\
  \ on VTEX to perform their collaborative operations.  \r\n\r\n>⚠️ The marketplace\
  \ must [create an appKey and appToken](https://developers.vtex.com/docs/guides/getting-started-authentication)\
  \ for each non-VTEX seller that will use this API.\r\n\r\n## Index\r\n\r\n### Notification\r\
  \n\r\nEndpoints used by sellers to notify marketplaces that the price or inventory\
  \ language has changed for one of their SKUs.\r\n\r\n`POST` [Notify marketplace\
  \ of price update](https://developers.vtex.com/docs/api-reference/marketplace-apis#post-/notificator/-sellerId-/changenotification/-skuId-/price)\r\
  \n\r\n`POST` [Notify marketplace of inventory update](https://developers.vtex.com/docs/api-reference/marketplace-apis#post-/notificator/-sellerId-/changenotification/-skuId-/inventory)\r\
  \n\r\n\r\n### Suggestions\r\n\r\n#### Get Suggestions\r\n\r\nSearch and filter all\
  \ suggestions using specific criteria.\r\n\r\n`GET` [Get all SKU Suggestions](https://developers.vtex.com/docs/api-reference/marketplace-apis-suggestions#get-/suggestions)\r\
  \n\r\n`GET` [Get SKU Suggestion by ID](https://developers.vtex.com/docs/api-reference/marketplace-apis-suggestions#get-/suggestions/-sellerId-/-sellerSkuId-)\r\
  \n\r\n\r\n#### Manage Suggestions\r\n\r\nSend or delete SKU suggestions from the\
  \ seller to marketplace.\r\n\r\n`PUT` [Send SKU Suggestion](https://developers.vtex.com/docs/api-reference/marketplace-apis-suggestions#put-/suggestions/-sellerId-/-sellerSkuId-)\r\
  \n\r\n`DELETE` [Delete SKU Suggestion](https://developers.vtex.com/docs/api-reference/marketplace-apis-suggestions#delete-/suggestions/-sellerId-/-sellerSkuId-)\r\
  \n\r\n\r\n#### Get Versions\r\n\r\nSearch and filter all versions of suggestions,\
  \ using specific criteria.\r\n\r\n`GET` [Get all versions](https://developers.vtex.com/docs/api-reference/marketplace-apis-suggestions#get-/suggestions/-sellerId-/-sellerskuid-/versions)\r\
  \n\r\n`GET` [Get version by ID](https://developers.vtex.com/docs/api-reference/marketplace-apis-suggestions#get-/suggestions/-sellerId-/-sellerskuid-/versions/-version-)\r\
  \n\r\n\r\n#### Match Received SKUs\r\n\r\nMatch SKU suggestions received in the\
  \ marketplace.\r\n\r\n`PUT` [Match Received SKUs individually](https://developers.vtex.com/docs/api-reference/marketplace-apis-suggestions#put-/suggestions/-sellerId-/-sellerskuid-/versions/-version-/matches/-matchid-)\r\
  \n\r\n`PUT` [Match Multiple Received SKUs](https://developers.vtex.com/docs/api-reference/marketplace-apis-suggestions#put-/suggestions/matches/action/-actionName-)\r\
  \n\r\n\r\n#### SKU Approval Settings\r\n\r\nAllows marketplaces to configure rules\
  \ for automatically and manually approving SKUs received from sellers.\r\n\r\n`GET`[Get\
  \ autoApprove Status in Account Settings](https://developers.vtex.com/docs/api-reference/marketplace-apis-suggestions#get-/suggestions/configuration/autoapproval/toggle)\
  \  \r\n\r\n`PUT`[Activate autoApprove in Marketplace's Account](https://developers.vtex.com/docs/api-reference/marketplace-apis-suggestions#put-/suggestions/configuration/autoapproval/toggle)\
  \  \r\n\r\n`GET`[Get Account's Approval Settings](https://developers.vtex.com/docs/api-reference/marketplace-apis-suggestions#get-/suggestions/configuration)\r\
  \n\r\n`PUT`[Save Account's Approval Settings](https://developers.vtex.com/docs/api-reference/marketplace-apis-suggestions#put-/suggestions/configuration)\r\
  \n\r\n`GET`[Get Seller's Approval Settings](https://developers.vtex.com/docs/api-reference/marketplace-apis-suggestions#get-/suggestions/configuration/seller/-sellerId-)\r\
  \n\r\n`PUT`[Save Seller's Approval Settings](https://developers.vtex.com/docs/api-reference/marketplace-apis-suggestions#put-/suggestions/configuration/seller/-sellerId-)\r\
  \n\r\n`PUT`[Activate autoApprove Setting for a Seller](https://developers.vtex.com/docs/api-reference/marketplace-apis-suggestions#put-/suggestions/configuration/autoapproval/toggle/seller/-sellerId-)\
  \   \r\n\r\n\r\n### Matched Offers\r\n\r\nOffers are seller products and SKUs that\
  \ were sent to the marketplace, and already have their price and inventory level\
  \ configured.\r\n\r\n`GET`[Get Matched Offers List](https://developers.vtex.com/docs/api-reference/marketplace-apis#get-/offer-manager/pvt/offers)\r\
  \n\r\n`GET`[Get Matched Offer's Data by SKU ID](https://developers.vtex.com/docs/api-reference/marketplace-apis#get-/offer-manager/pvt/product/-productId-/sku/-skuId-)\
  \  \r\n\r\n`GET`[Get Matched Offer's Data by Product ID](https://developers.vtex.com/docs/api-reference/marketplace-apis#get-/offer-manager/pvt/product/-productId-)\r\
  \n"
logo: "vtex.local-Marketplace-APIs--logo.svg"
logoMediaType: "image/svg+xml"
tags: []
stubs: "vtex.local-Marketplace-APIs--stubs.json"
swagger: "vtex.local-Marketplace-APIs--swagger.json"
---
