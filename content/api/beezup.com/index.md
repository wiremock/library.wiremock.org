---
slug: "beezup-com"
title: "BeezUP Merchant API "
provider: "beezup.com"
description: "# The REST API of BeezUP system\n## Overview\nThe REST APIs provide\
  \ programmatic access to read and write BeezUP data. \nBasically, with this API\
  \ you will be able to do everything like you were with your browser on https://go.beezup.com\
  \ !\n\nThe main features are:\n- Register and manage your account\n- Create and\
  \ manage and share your stores with your friends/co-workers.\n- Import your product\
  \ catalog and schedule the auto importation\n- Search the channels your want to\
  \ use\n- Configure your channels for your catalogs to export your product information:\n\
  \    - cost and general settings\n    - category and columns mappings\n    - your\
  \ will be able to create and manage your custom column\n    - put in place exlusion\
  \ filters based on simple conditions on your product data\n    - override product\
  \ values\n    - get product vision for a channel catalog scope\n- Analyze and optimize\
  \ your performance of your catalogs on all yours channels with different type of\
  \ reportings by day, channel, category and by product.\n- Automatize your optimisation\
  \ by using rules!\n- And of course... Manage your orders harvested from all your\
  \ marketplaces:\n    - Synchronize your orders in an uniformized way\n    - Get\
  \ the available actions and update the order status\n- ...and more!\n\n## Authentication\
  \ credentials\nThe public API with the base path **/v2/public** have been put in\
  \ place to give you an entry point to our system for the user registration, login\
  \ and lost password. The public API does not require any credentials.\nWe give you\
  \ the some public list of values and public channels for our public commercial web\
  \ site [www.beezup.com](http://www.beezup.com).\n\nThe user API with the base path\
  \ **/v2/user** requires a token which is available on this page:\nhttps://go.beezup.com/Account/MyAccount\n\
  \n## Things to keep in mind\n### API Rate Limits\n- The BeezUP REST API is limited\
  \ to 100 calls/minute.\n\n### Media type\nThe default media type for requests and\
  \ responses is application/json. Where noted, some operations support other content\
  \ types. If no additional content type is mentioned for a specific operation, then\
  \ the media type is application/json.\n\n### Required content type\nThe required\
  \ and default encoding for the request and responses is UTF8.\n\n### Required date\
  \ time format\nAll our date time are formatted in ISO 8601 format: 2014-06-24T16:25:00Z.\n\
  \n### Base URL\nThe Base URL of the BeezUP API Order Management REST API conforms\
  \ to the following template.\n\nhttps://api.beezup.com\n\nAll URLs returned by the\
  \ BeezUP API are relative to this base URL, and all requests to the REST API must\
  \ use this base URL template.\n\nYou can test our API on https://api-docs.beezup.com/swagger-ui\\\
  \\\nYou can contact us on [gitter, #BeezUP/API](https://gitter.im/BeezUP/API)"
logo: "beezup.com-logo.png"
logoMediaType: "image/png"
tags:
- "ecommerce"
stubs: "beezup.com-stubs.json"
swagger: "beezup.com-swagger.json"
---
