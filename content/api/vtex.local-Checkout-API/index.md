---
slug: "vtex-local-Checkout-API"
title: "Checkout API"
provider: "vtex.local"
description: ">ℹ️ Check the new [Checkout onboarding guide](https://developers.vtex.com/vtex-rest-api/docs/checkout-overview).\
  \ We created this guide to improve the onboarding experience for developers at VTEX.\
  \ It assembles all documentation on our Developer Portal about the Checkout and\
  \ is organized by focusing on the developer's journey.\r\n\r\nThe Checkout API allows\
  \ you to obtain and configure information about the shopping cart and its attachments,\
  \ personalization of custom fields, orderForm structure, fulfillment data, order\
  \ management, and identification of the sellers delivery region.\r\n\r\n>ℹ️ Data\
  \ modification operations (`POST`, `PATCH`, `PUT` or `DELETE` endpoints) shall not\
  \ be performed in parallel in the Checkout APIs. They need to be enqueued by the\
  \ client/requester. Otherwise, old values ​​can be overwritten incorrectly or competition\
  \ errors may occur.\r\n\r\n>⚠️ All endpoints that consult or edit the orderForm\
  \ can change the authentication depending on the customer context. If you are handling\
  \ information from a customer with a complete profile on the store, authentication\
  \ will be required. You can only access or modify the customer data for these profiles\
  \ with an authenticated request.\r\n\r\n## Shopping cart\r\n\r\nAllows merchants\
  \ to simulate, configure and customize shopping cart information.\r\n\r\n- [POST\
  \ - Cart Simulation](https://developers.vtex.com/vtex-rest-api/reference/cartsimulation)\r\
  \n- [GET - Get current or create a new cart](https://developers.vtex.com/vtex-rest-api/reference/createanewcart)\r\
  \n- [GET - Get cart information by ID](https://developers.vtex.com/vtex-rest-api/reference/getcartinformationbyid)\r\
  \n- [POST - Remove all items](https://developers.vtex.com/vtex-rest-api/reference/removeallitems)\r\
  \n- [GET - Remove all personal data](https://developers.vtex.com/vtex-rest-api/reference/removeallpersonaldata)\r\
  \n- [POST - Update cart items](https://developers.vtex.com/vtex-rest-api/reference/itemsupdate)\r\
  \n- [POST - Add cart items](https://developers.vtex.com/vtex-rest-api/reference/items)\r\
  \n- [PUT - Change price](https://developers.vtex.com/vtex-rest-api/reference/pricechange)\r\
  \n- [PATCH - Ignore profile data](https://developers.vtex.com/vtex-rest-api/reference/ignoreprofiledata)\r\
  \n- [GET - Cart installments](https://developers.vtex.com/vtex-rest-api/reference/getcartinstallments)\r\
  \n- [POST - Add coupons to the cart](https://developers.vtex.com/vtex-rest-api/reference/addcoupons)\r\
  \n\r\n\r\n## Cart attachments\r\n\r\nAllows merchants to obtain client profiles\
  \ and add information to a given shopping cart.\r\n\r\n- [GET - Get client profile\
  \ by email](https://developers.vtex.com/vtex-rest-api/reference/getclientprofilebyemail)\r\
  \n- [POST - Add client profile](https://developers.vtex.com/vtex-rest-api/reference/addclientprofile)\r\
  \n- [POST - Add shipping address and select delivery option](https://developers.vtex.com/vtex-rest-api/reference/addshippingaddress)\r\
  \n- [POST - Add client preferences](https://developers.vtex.com/vtex-rest-api/reference/addclientpreferences)\r\
  \n- [POST - Add marketing data](https://developers.vtex.com/vtex-rest-api/reference/addmarketingdata)\r\
  \n- [POST - Add payment data](https://developers.vtex.com/vtex-rest-api/reference/addpaymentdata)\r\
  \n- [POST - Add merchant context data](https://developers.vtex.com/vtex-rest-api/reference/addmerchantcontextdata)\r\
  \n\r\n\r\n## Custom data\r\n\r\nAllows merchants to manage custom fields that were\
  \ created by an app in their account.\r\n\r\n- [PUT - Set multiple custom field\
  \ values](https://developers.vtex.com/vtex-rest-api/reference/setmultiplecustomfieldvalues)\r\
  \n- [PUT - Set single custom field value](https://developers.vtex.com/vtex-rest-api/reference/setsinglecustomfieldvalue)\r\
  \n- [DELETE - Remove single custom field value](https://developers.vtex.com/vtex-rest-api/reference/removesinglecustomfieldvalue)\r\
  \n\r\n\r\n## Configuration\r\n\r\nAllows merchants to configure orderForm in the\
  \ account and seller exchange on a given order.\r\n\r\n- [GET - Get orderForm configuration](https://developers.vtex.com/vtex-rest-api/reference/getorderformconfiguration)\r\
  \n- [POST - Update orderForm configuration](https://developers.vtex.com/vtex-rest-api/reference/updateorderformconfiguration)\r\
  \n- [GET - Get window to change seller](https://developers.vtex.com/vtex-rest-api/reference/getwindowtochangeseller)\r\
  \n- [POST - Update window to change seller](https://developers.vtex.com/vtex-rest-api/reference/updatewindowtochangeseller)\r\
  \n- [POST - Clear orderForm messages](https://developers.vtex.com/vtex-rest-api/reference/clearorderformmessages)\r\
  \n\r\n\r\n## Fulfillment\r\n\r\nAllows merchants to obtain pickup points and address\
  \ information.\r\n\r\n- [GET - List pickup points by location](https://developers.vtex.com/vtex-rest-api/reference/listpickupppointsbylocation)\r\
  \n- [GET - Get address by postal code](https://developers.vtex.com/vtex-rest-api/reference/getaddressbypostalcode)\r\
  \n\r\n\r\n## Order placement\r\n\r\nAllows merchants to place and process orders\
  \ by creating a new cart or using an existing cart.\r\n\r\n- [POST - Place order\
  \ from an existing cart](https://developers.vtex.com/vtex-rest-api/reference/placeorderfromexistingorderform)\r\
  \n- [PUT - Place order](https://developers.vtex.com/vtex-rest-api/reference/placeorder)\r\
  \n- [POST - Process order](https://developers.vtex.com/vtex-rest-api/reference/processorder)\r\
  \n\r\n\r\n## Region\r\n\r\nAllows merchants to obtain a list of sellers serving\
  \ a specific delivery region.\r\n\r\n- [GET - Get sellers by region or address](https://developers.vtex.com/vtex-rest-api/reference/getsellersbyregion)"
logo: "vtex.local-Checkout-API-logo.svg"
logoMediaType: "image/svg+xml"
tags: []
stubs: "vtex.local-Checkout-API-stubs.json"
swagger: "vtex.local-Checkout-API-swagger.json"
---
