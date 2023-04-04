---
slug: "twinehealth-com"
title: "Fitbit Plus API"
provider: "twinehealth.com"
description: "# Overview\nThe Fitbit Plus API is a RESTful API. The requests and responses\
  \ are formated according to the\n[JSON API](http://jsonapi.org/format/1.0/) specification.\n\
  \nIn addition to this documentation, we also provide an\n[OpenAPI](https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md)\
  \ \"yaml\" file describing the API:\n[Fitbit Plus API Specification](swagger.yaml).\n\
  \n# Authentication\nAuthentication for the Fitbit Plus API is based on the\n[OAuth\
  \ 2.0 Authorization Framework](https://tools.ietf.org/html/rfc6749). Fitbit Plus\
  \ currently supports grant\ntypes of **client_credentials** and **refresh_token**.\n\
  \nSee [POST /oauth/token](#operation/createToken) for details on the request and\
  \ response formats.\n<!-- ReDoc-Inject: <security-definitions> -->\n\n## Building\
  \ Integrations\nWe will provide customers with unique client credentials for each\
  \ application/integration they build, allowing us\nto enforce appropriate access\
  \ controls and monitor API usage.\nThe client credentials will be scoped to the\
  \ organization, and allow full access to all patients and related data\nwithin that\
  \ organization.\n\nThese credentials are appropriate for creating an integration\
  \ that does one of the following:\n - background reporting/analysis\n - synchronizing\
  \ data with another system (such as an EMR)\n\nThe API credentials and oauth flows\
  \ we currently support are **not** well suited for creating a user-facing\napplication\
  \ that allows a user (patient, coach, or admin) to login and have access to data\
  \ which is appropriate to\nthat specific user. It is possible to build such an application,\
  \ but it is not possible to use Fitbit Plus as a\nfederated identity provider. You\
  \ would need to have a separate means of verifying a user's identity. We do not\n\
  currently support the required password-based oauth flow to make this possible.\n\
  \n# Paging\nThe Fitbit Plus API supports two different pagination strategies for\
  \ GET collection endpoints.\n\n#### Skip-based paging\n\nSkip-based paging uses\
  \ the query parameters `page[size]` and `page[number]` to specify the max number\
  \ of resources returned and the page number. We default to skip-based paging if\
  \ there are no page parameters. The response will include a `links` object containing\
  \ links to the first, last, prev, and next pages of data.\n\nIf the contents of\
  \ the collection change while you are iterating through the collection, you will\
  \ see duplicate or missing documents. For example, if you are iterating through\
  \ the `calender_event` resource via `GET /pub/calendar_event?sort=start_at&page[size]=50&page[number]=1`,\
  \ and a new `calendar_event` is created that has a `start_at` value before the first\
  \ `calendar_event`, when you fetch the next page at `GET /pub/calendar_event?sort=start_at&page[size]=50&page[number]=2`,\
  \ the first entry in the second response will be a duplicate of the last entry in\
  \ the first response.\n\n#### Cursor-based paging\nCursor-based paging uses the\
  \ query parameters `page[limit]` and `page[after]` to specify the max number of\
  \ entries returned and identify where to begin the next page. Add `page[limit]`\
  \ to the parameters to use cursor-based paging. The response will include a `links`\
  \ object containing a link to the next page of data, if the next page exists.\n\n\
  Cursor-based paging is not subject to duplication if new resources are added to\
  \ the collection. For example, if you are iterating through the `calender_event`\
  \ resource via `GET /pub/calendar_event?sort=start_at&page[limit]=50`, and a new\
  \ `calendar_event` is created that has a `start_at` value before the first `calendar_event`,\
  \ you will not see a duplicate entry when you fetch the next page at `GET /pub/calendar_event?sort=start_at&page[limit]=50&page[after]=<cursor>`.\n\
  \nWe encourage the use of cursor-based paging for performance reasons.\n\nIn either\
  \ form of paging, you can determine whether any resources were missed by comparing\
  \ the number of fetched resources against `meta.count`. Set `page[size]` or `page[limit]`\
  \ to 0 to get only the count.\n\nIt is not valid to mix the two strategies.\n"
logo: "twinehealth.com-logo.png"
logoMediaType: "image/png"
tags:
- "support"
stubs: "twinehealth.com-stubs.json"
swagger: "twinehealth.com-swagger.json"
---
