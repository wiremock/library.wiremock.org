---
slug: "voodoomfg-com"
title: "Voodoo Manufacturing 3D Print API"
provider: "voodoomfg.com"
description: "Welcome to the Voodoo Manufacturing API docs!\n\nYour Voodoo Manufacturing\
  \ API key must be included with each request to the API. The API will look for the\
  \ key in the \"api_key\" header of the request. <a href=\"https://voodoomfg.com/3d-print-api#get-access\"\
  \ target=\"_blank\">You can request a key here.</a>\n\nThis API provides a programmatic\
  \ interface for submitting printing orders to Voodoo Manufacturing. The general\
  \ process for creating an order is as follows:\n  - Get a list of the available\
  \ materials with the /materials endpoint\n  - Upload models to the API with the\
  \ /models endpoint\n  - Get quotes for shipping methods with the /order/shipping\
  \ endpoint\n  - Get a quote for an order with the /order/create endpoint\n  - Confirm\
  \ the order with the /order/confirm endpoint\n\nUploaded models and orders can be\
  \ retrieved either in bulk or by id at the /model and /order endpoints, respectively.\n\
  \nIn some cases, you may wish to get a quote for a specific model without the context\
  \ of an order. In this case, you may use the /model/quote (if you've already uploaded\
  \ the model to the API) or the /model/quote_attrs (lets you quote based on calculated\
  \ model attributes) endpoints.\n"
logo: "voodoomfg.com-logo.jpeg"
logoMediaType: "image/jpeg"
tags:
- "tools"
stubs: "voodoomfg.com-stubs.json"
swagger: "voodoomfg.com-swagger.json"
---
