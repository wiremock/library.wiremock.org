---
slug: "pims-io"
title: "Pims"
provider: "pims.io"
description: "\nHereafter is the documentation of the private API of [Pims: Pointages\
  \ Intelligents pour le Monde du Spectacle](https://pims.io). This API is designed\
  \ for 3rd-party softwares, editors and partners. Its main purpose is to give access\
  \ the core data of a Pims customer (i.e. events, ticket counts and promotions).\n\
  \n## Authentication\nThe API uses [basic access authentication](https://en.wikipedia.org/wiki/Basic_access_authentication),\
  \ meaning you will need a username and password to get authorized.\n\nAs each customer\
  \ in Pims has its own domain (e.g. caramba.pims.io, gdp.pims.io...), each credentials\
  \ will be valid for one domain/customer only. If you need dedicated credentials\
  \ for one domain, please contact us. (In any case, we will need an explicit agreement\
  \ from the customer before we create these credentials.)\n\n<div class=\"info\"\
  >\nTo make your life easy, you can try all endpoints with the public credentials\
  \ below, pointing to our [demo domain](https://demo.pims.io):\n  <ul>\n    <li>Base\
  \ path: `https://demo.pims.io/api`</li>\n    <li>Username: `demo`</li>\n    <li>Password:\
  \ `q83792db2GCvgYVdKpU3yG3R`</li>\n  </ul>\n</div>\n\n## Response format\nThe API\
  \ returns JSON and matches the [HAL specification](http://stateless.co/hal_specification.html).\
  \ The `Content-Type` of each response will be `application/hal+json`, unless an\
  \ error occurs.\n\nPlease note that this documentation describes all responses “\
  as if” they were plain JSON. The specificities of HAL are ignored on purpose, in\
  \ order to remain compact and avoid repetition.\n<div style=\"-webkit-column-count:\
  \ 2; -moz-column-count: 2; column-count: 2; -webkit-column-rule: 1px dotted #e0e0e0;\
  \ -moz-column-rule: 1px dotted #e0e0e0; column-rule: 1px dotted #e0e0e0;\">\n\t\
  <div style=\"display: inline-block; width:100%;\">\n\t\t<strong>So when you read\
  \ in the doc:</strong>\n<pre><code class=\"lang-json\">{\n\t<span class=\"token\
  \ string\">\"id\"</span>: <span class=\"token number\">123</span>,\n\t<span class=\"\
  token string\">\"property1\"</span>: <span class=\"token string\">\"Lorem ipsum\"\
  </span>,\n\t<span class=\"token string\">\"object\"</span>: {\n\t\t<span class=\"\
  token string\">\"id\"</span>: <span class=\"token number\">456</span>,\n\t\t<span\
  \ class=\"token string\">\"property2\"</span>: <span class=\"token number\">7.89</span>\n\
  \t}\n}</code></pre>\n\t</div>\n\t<div style=\"display: inline-block; width:100%;\"\
  >\n\t\t<strong>... you'll get in the Real World®:</strong>\n<pre><code class=\"\
  lang-json\">{\n\t<span class=\"token string\">\"id\"</span>: <span class=\"token\
  \ number\">123</span>,\n\t<span class=\"token string\">\"property2\"</span>: <span\
  \ class=\"token string\">\"Lorem ipsum\"</span>,\n\t<span class=\"token string\"\
  >\"_embedded\"</span>: {\n\t\t<span class=\"token string\">\"object\"</span>: {\n\
  \t\t\t<span class=\"token string\">\"id\"</span>: <span class=\"token number\">456</span>,\n\
  \t\t\t<span class=\"token string\">\"property2\"</span>: <span class=\"token number\"\
  >7.89</span>,\n\t\t\t<span class=\"token string\">\"_links\"</span>: {\n\t\t\t\t\
  <span class=\"token string\">\"self\"</span>: {\n\t\t\t\t\t<span class=\"token string\"\
  >\"href\"</span>: <span class=\"token string\">\"https://api.mydomain.com/other-item/456\"\
  </span>\n\t\t\t\t}\n\t\t\t}\n\t\t}\n\t}\n\t<span class=\"token string\">\"_links\"\
  </span>: {\n\t\t<span class=\"token string\">\"self\"</span>: {\n\t\t\t<span class=\"\
  token string\">\"href\"</span>: <span class=\"token string\">\"https://api.mydomain.com/item/123\"\
  </span>\n\t\t}\n\t}\n}</code></pre>\n\t</div>\n</div>\n\n### Errors\nErrors return\
  \ JSON too and tries to match the [Problem Details for HTTP APIs specification](https://tools.ietf.org/html/rfc7807).\
  \ If it does not match this spec, that's either a bug or a compatibility issue.\
  \ Please contact us to solve the problem.\n\nThe `Content-Type` of errors will be\
  \ `application/problem+json`. The content will match the following JSON:\n```json\n\
  {\n\t\"type\": \"https://tools.ietf.org/html/rfc2616#section-10\",\n    \"title\"\
  : \"Not Found\",\n\t\"status\": 404,\n    \"detail\": \"Entity not found\"\n}\n\
  ```\n\n## Versioning\nThe API is fully versionned, using an URL-versioning scheme:\
  \ `https://demo.pims.io/api/v1/events`, `https://demo.pims.io/api/v2/events`,...\n\
  \nThe version part of the URL is optional, and will be completed with the last stable\
  \ version if omitted.\n\n## Pagination\nAll responses corresponding to a collection\
  \ of resources (e.g. `/venues` or `/series/:id/events`) are paginated. When so,\
  \ you will only get the first 25 resources you asked for.\n\nIf you need to get\
  \ more resources in one call, you can use the `page_size` query parameter. E.g.\
  \ `/venues?page_size=50` to get the 50 first venues.\n\nAlso note that with HAL,\
  \ the navigation in paginated responses is a piece of cake, as you can see below:\n\
  ```json\n{\n\t\"_links\": {\n\t\t\"self\": {\n\t\t\t\"href\": \"https://demo.pims.io/api/v1/events?page=1\"\
  \n\t\t},\n\t\t\"first\": {\n\t\t\t\"href\": \"https://demo.pims.io/api/v1/events\"\
  \n\t\t},\n\t\t\"last\": {\n\t\t\t\"href\": \"https://demo.pims.io/api/v1/events?page=14\"\
  \n\t\t},\n\t\t\"next\": {\n\t\t\t\"href\": \"https://demo.pims.io/api/v1/events?page=2\"\
  \n\t\t}\n\t},\n\t\"_embedded\": {\n \t\t... // data content goes here\n\t},\n\t\"\
  page_count\": 14,\n\t\"page_size\": 25,\n\t\"total_items\": 331,\n\t\"page\": 1\n\
  }\n```\n\n## Filtering and sorting\nEvery textual filter (e.g. `/events?label=U2`)\
  \ and/or sort (e.g. `/events?sort=label`) performed with the API uses UTF8_UNICODE_CI\
  \ collation, meaning it is:\n- Case insensitive: “Chloé” will be considered the\
  \ same as “CHLOÉ”;\n- Diacritic insensitive: “Chloé” will be considered the same\
  \ as “Chloe”.\n\nWhen performing a sort, it will always be *ascending* by default.\
  \ To make it *descending*, just use a minus sign (`-`) in front of the parameter\
  \ value (e.g. `/events?sort=-label`).\n\n## I18n\nIn responses, some labels can\
  \ be translated (e.g. promotion types, event input types, etc.). These translatable\
  \ labels are clearly indicated in the documentation below.\n\nBy default, they will\
  \ be displayed in English, but you can change this behaviour via the `Accept-Language`\
  \ header. E.g., use `fr` as a value for French.\n\n## PHP SDK\nWe provide a simple\
  \ yet convenient SDK for the PHP language, see [the Github page of the project](https://github.com/pimssas/pims-api-client-php).\n\
  \n## And now?\nGeneraly, you will start by [fetching one or more events](#tag/Events).\
  \ An <span class=\"definition\">event</span> can be anything that occurs in one\
  \ venue at one given date and time: a concert, a play, a match, a conference, etc.\
  \ Additionnally, you can explore the [series](#tag/Series): a <span class=\"definition\"\
  >series</span> is just a group of events (e.g. a tour or a festival).\n\nOnce you\
  \ retrieved the events you were interested in, you can look for the sales (<span\
  \ class=\"definition\">ticket counts</span>):\n- Get a quick overview with [`/events/:id/ticket-counts`](#operation/fetchAllTicketCounts)\n\
  - Or get a full insight by calling these endpoints:\n    1. [`/events/:id/categories`](#operation/fetchAllEventsCategories)\n\
  \    2. [`/events/:id/channels`](#operation/fetchAllEventsChannels)\n    3. [`/events/:id/ticket-counts/detailed`](#operation/fetchAllDetailedTicketCounts)\n\
  \nEventually, you may also want to fetch the [promotions](#tag/Promotions). A <span\
  \ class=\"definition\">promotion</span> can be anything meant to leverage the sales:\
  \ ads, marketing campaigns, buzz or news around the event, etc. A promotion can\
  \ be linked to any combination of events and/or series."
logo: "pims.io-logo.svg"
logoMediaType: "image/svg+xml"
tags:
- "ecommerce"
stubs: "pims.io-stubs.json"
swagger: "pims.io-swagger.json"
---
