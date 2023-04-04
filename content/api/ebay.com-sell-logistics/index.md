---
slug: "ebay-com-sell-logistics"
title: "Logistics API"
provider: "ebay.com"
description: "<span class=\"tablenote\"><b>Note:</b> This is a <a href=\"https://developer.ebay.com/api-docs/static/versioning.html#limited\"\
  \ target=\"_blank\"> <img src=\"/cms/img/docs/partners-api.svg\" class=\"legend-icon\
  \ partners-icon\" title=\"Limited Release\"  alt=\"Limited Release\" />(Limited\
  \ Release)</a> API available only to select developers approved by business units.</span><br\
  \ /><br />The <b>Logistics API</b> resources offer the following capabilities: <ul><li><b>shipping_quote</b>\
  \ &ndash; Consolidates into a list a set of live shipping rates, or quotes, from\
  \ which you can select a rate to ship a package.</li> <li><b>shipment</b> &ndash;\
  \ Creates a \"shipment\" for the selected shipping rate.</li></ul> Call <b>createShippingQuote</b>\
  \ to get a list of live shipping rates. The rates returned are all valid for a specific\
  \ time window and all quoted prices are at eBay-negotiated rates. <br><br>Select\
  \ one of the live rates and using its associated <b>rateId</b>, create a \"shipment\"\
  \ for the package by calling <b>createFromShippingQuote</b>. Creating a shipment\
  \ completes an agreement, and the cost of the base service and any added shipping\
  \ options are summed into the returned <b>totalShippingCost</b> value. This action\
  \ also generates a shipping label that you can use to ship the package.  The total\
  \ cost of the shipment is incurred when the package is shipped using the supplied\
  \ shipping label.  <p class=\"tablenote\"><b>Important!</b> Sellers must set up\
  \ a payment method via their eBay account before they can use the methods in this\
  \ API to create a shipment and the associated shipping label.</p>"
logo: "ebay.com-sell-logistics-logo.jpeg"
logoMediaType: "image/jpeg"
tags:
- "ecommerce"
stubs: "ebay.com-sell-logistics-stubs.json"
swagger: "ebay.com-sell-logistics-swagger.json"
---
