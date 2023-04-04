---
slug: "openfintech-io"
title: "OpenFinTech.io"
provider: "openfintech.io"
description: "# Introduction\n[OpenFinTech.io](https://openfintech.io) is an open\
  \ database that comprises of standardized primary data for FinTech industry.<br>\n\
  It contains such information as geolocation data (countries, cities, regions), organizations,\
  \ currencies (national, digital, virtual, crypto), banks, digital exchangers, payment\
  \ providers (PSP), payment methods, etc.<br>\nIt is created for communication of\
  \ cross-integrated micro-services on \"one language\". This is achieved through\
  \ standardization of entity identifiers that are used to exchange information among\
  \ different services.<br>\n\n### UML\nUML Domain Model diagram you can find [here](https://api.openfintech.io/public_domain_model.png).<br>\n\
  \n### Persistence\nEntities are updated not more than 1 time per day.<br>\n\n###\
  \ Terms and Conditions\nThis *OpenFinTech.io* is made available under the [Open\
  \ Database License](http://opendatacommons.org/licenses/odbl/1.0/).<br>\nAny rights\
  \ in individual contents of the database are licensed under the [Database Contents\
  \ License](http://opendatacommons.org/licenses/dbcl/1.0/).<br>\n\n### Contacts\n\
  For any questions, please email - info@openfintech.io<br>\nOr you can contact us\
  \ at <a href=\"https://gitter.im/paymaxicom/openfintech.io\">Gitter</a><br>\n\n\
  Powered by [Paymaxi](https://www.paymaxi.com)\n\n# Get Started\n\nIf you use [POSTMAN](https://www.getpostman.com)\
  \ or similar program which can operate with swagger`s files - just [download](https://docs.openfintech.io)\
  \ our spec and [import it](https://www.getpostman.com/docs/importing_swagger). Also\
  \ you can try live [API demo](https://api.openfintech.io).\n\n## Overview\n\nThe\
  \ OpenFinTech API is organized around [REST](https://en.wikipedia.org/wiki/Representational_state_transfer).\
  \ Our API has predictable, resource-oriented URLs, and uses HTTP response codes\
  \ to indicate API errors.<br>\nAPI is based on [JSON API](http://jsonapi.org) standard.\
  \ JSON is returned by all API responses, including errors, although our API libraries\
  \ convert responses to appropriate language-specific objects.<br>\nJSON API requires\
  \ use of the JSON API media type (`application/vnd.api+json`) for exchanging data.<br>\n\
  ### Additional Request Headers\n#### ACCEPT HEADER\nYour requests should always\
  \ include the header:\n```curl\nAccept: application/vnd.api+json\n```\n\n## Authentication\n\
  \nTo use OpenFinTech API no needed authorization.\n\n## Versioning\n\nWhen we make\
  \ changes to the API, we release new, dated versions. The current version is **2017-08-24**.\
  \ Read our [API upgrades guide]() to see our API changelog and to learn more about\
  \ backwards compatibility.\n\n## Pagination\n\nOpenFinTech APIs to retrieve lists\
  \ of banks, currencies and other resources - paginated to **100** items by default.\
  \ The pagination information will be included in the list API response under the\
  \ node name `meta` - contains information about listed objects [`total` - contains\
  \ information about total count of listed objects, `pages` - count of pages], `links`\
  \ - contain links to navigate between pages [`first` - link to first page, `prev`\
  \ - link to previous page, `next` - link to next page, `last` - link to last page].<br>\n\
  By default first page will be listed. For navigating through pages, use the page\
  \ parameter (e.g. `page[number]`, `page[size]`).<br>\nThe `page[size]` parameter\
  \ can be used to set the number of records that you want to receive in the response.<br>\n\
  The `page[number]` parameter can be used to set needed page number.<br>\nExample\
  \ of response:\n```json\n{\n  \"meta\": {\n    \"total\": 419,\n    \"pages\": 42\n\
  \  },\n  \"links\": {\n    \"first\": \"/v1/{path}?page[number]=1&page[size]=10\"\
  ,\n    \"prev\": \"/v1/{path}?page[number]=39&page[size]=10\",\n    \"next\": \"\
  /v1/{path}?page[number]=41&page[size]=10\",\n    \"last\": \"/v1/{path}?page[number]=42&page[size]=10\"\
  \n  }\n```\n\n### Sorting\n\nOpenFinTech\\`s API supported query parameter to sort\
  \ result collection [e.g. `?sort=code`]. Information about available parameters\
  \ may be found in the endpoint description. Positive parameter [e.g. `?sort=code`]\
  \ points to ascending sorting, negative  [e.g. `?sort=-code`] - to descending sorting.\
  \ Also, supported multiple sorting parameters [e.g. `?sort=code, -name, id`, etc.]\n\
  ```curl\nhttps://api.openfintech.io/v1/countries?sort=name,-area\n```\n\n### Filtering\n\
  \nFiltering provided by unique query key `filter[*filtering_condition*]`. Information\
  \ about available parameters may be found in the endpoint description.\n```curl\n\
  https://api.openfintech.io/v1/countries?filter[region]=europe\n```\n\n## Images\n\
  \nOpenFinTech provides two types of images: icons and logos. To get one of those\
  \ types you should to use next url pattern:\n``` curl\nhttps://api.openfintech.io/v1/{path}/{id}/{icon/logo}\n\
  ```\nAlso, images can be resized by adding next parameters: `h={height}&w={width}`.\
  \ For example, you want to get organization icon with width equals to 20 pixels:\n\
  ``` curl\nhttps://api.openfintech.io/v1/organizations/{id}/icon?w=20&h=20\n```\n\
  If argument height or width is missing API returns original image with real sizes.\n\
  \n## Errors\n\nAPI uses conventional HTTP response codes to indicate the success\
  \ or failure of an API request. In general, codes in the `2xx` range indicate success,\
  \ codes in the `4xx` range indicate an error that failed given the information provided\
  \ (e.g., a required parameter was omitted, etc.), and codes in the `5xx` range indicate\
  \ an error with OpenFinTech's servers (these are rare).\n\n| Code | Description\
  \ |\n|------|-------------|\n| 200 - OK\t| Everything worked as expected. |\n| 400\
  \ - Bad Request |\tThe request was unacceptable, often due to missing a required\
  \ parameter. |\n| 401 - Unauthorized |\tNo valid API key provided. |\n| 402 - Request\
  \ Failed\t| The parameters were valid but the request failed. |\n| 404 - Not Found\
  \ |\tThe requested resource doesn't exist. |\n| 409 - Conflict\t| The request conflicts\
  \ with another request (perhaps due to using the same idempotent key). |\n| 429\
  \ - Too Many Requests |\tToo many requests hit the API too quickly. We recommend\
  \ an exponential backoff of your requests. |\n| 500, 502, 503, 504 - Server Errors\
  \ |\tSomething went wrong on OpenFinTech's end. (These are rare.) |\n"
logo: "openfintech.io-logo.jpeg"
logoMediaType: "image/jpeg"
tags:
- "financial"
stubs: "openfintech.io-stubs.json"
swagger: "openfintech.io-swagger.json"
---