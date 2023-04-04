---
slug: "ato-gov-au"
title: "Business Registries"
provider: "ato.gov.au"
description: "# Introduction\nThe Business Registries API is built on HTTP. The API\
  \ is RESTful. It has predictable resource URIs.\n\n  The API is documented in <a\
  \ target=\"_blank\" href=\"https://github.com/OAI/OpenAPI-Specification\">OpenAPI</a>\
  \ format.\n  In addition to the standard OpenAPI syntax we use a few\n  <a target=\"\
  _blank\" href=\"https://github.com/Rebilly/ReDoc/blob/master/docs/redoc-vendor-extensions.md\"\
  >vendor extensions</a>.\n\n# Overview\nThe following sections describe the resources\
  \ that make up the Business Registries REST API.\n## Current Version\nBy default,\
  \ all requests to https://api.abr.ato.gov.au receive the `v1` version of the REST\
  \ API. We encourage you to explicitly request this version via the `Accept` header.\n\
  \n    Accept: application/vnd.abr-ato.v1+json\n\n## Schema\nAll API access is over\
  \ HTTPS, and accessed from https://api.abr.ato.gov.au. All data is sent and received\
  \ as JSON. Blank fields are included.\n\n  All dates use the [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)\
  \ format:\n\n    YYYY-MM-DD\n\n  For example: `2017-07-01` (the 1st of July 2017)\n\
  \n  All timestamps use the [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format:\n\
  \n    YYYY-MM-DDTHH:MM:SSZ\n\n  For example: `2017-07-01T11:05:06+10:00`\n\n## Timezones\n\
  Some requests allow for specifying timestamps or generate timestamps with time zone\
  \ information. We apply the following rules, in order of priority, to determine\
  \ timezone information for API calls.\n### Explicitly provide an ISO 8601 timestamp\
  \ with timezone information\nFor API calls that allow for a timestamp to be specified,\
  \ we use that exact timestamp.\n\n  For example: `2017-07-01T11:05:06+10:00`\n\n\
  ## Pagination\nInformation about pagination is provided in the [Link](https://tools.ietf.org/html/rfc5988#page-6)\
  \ header.\n\n  For example:\n\n    Link: <https://api.abr.ato.gov.au/individuals?page=2>;\
  \ rel=\"next\",\n          <https://api.abr.ato.gov.au/individuals?page=34>; rel=\"\
  last\"\n\n`rel=\"next\"` states that the next page is `page=2`. This makes sense,\
  \ since by default, all paginated queries start at page `1`. `rel=\"last\"` provides\
  \ some more information, stating that the last page of results is on `page 34`.\
  \ Accordingly, we have 33 more pages of information that we can consume.\n## Parameters\n\
  Many API methods take optional parameters:\n\n    GET /individuals/1234/addresses/?addressType='Mailing'\n\
  \nIn this example, the '1234' value is provided for the `:partyId` parameter in\
  \ the path while `:addressType` is passed in the query string.\nFor POST, PATCH,\
  \ PUT, and DELETE requests, parameters not included in the URL should be encoded\
  \ as JSON with a Content-Type of 'application/json'.\n## Metadata\nThe API provides\
  \ **metadata services** that you can use to discover information about the classifcation\
  \ schemes and values used by the Registry.\n\n  For example:\n\n    GET /classifications/roles\n\
  \n  Sample response:\n\n    [\n      {\n        \"id\": \"123e4567-e89b-12d3-a456-426655440001\"\
  ,\n        \"role\": \"Director\",\n        \"roleDescription\": \"An individual\
  \ responsible for managing a company's ...\",\n        \"relationship\": \"Directorship\"\
  ,\n        \"reciprocalRole\": \"Company\",\n        \"reciprocalRoleDescription\"\
  : \"An incorporated legal entity.\"\n      },\n      {\n        ...\n      }\n \
  \   ]\n\n## Root Endpoint\nYou can issue a GET request to the root endpoint (also\
  \ known as the service root) to get all the endpoint categories that the REST API\
  \ supports:\n\n    curl https://api.abr.ato.gov.au\n\n## Authentication\nThe Business\
  \ Registries API supports API Key authentication.\n\n  When you sign up for an account,\
  \ you are given your first API key. You can generate additional API keys, and delete\n\
  \  API keys (as you may need to rotate your keys in the future). You authenticate\
  \ to the Business Registries API by\n  providing your secret key in the request\
  \ header.\n\n  **Note:** Some requests will return `404 Not Found`, instead of `403\
  \ Permission Denied`. This is to prevent the\n  accidental leakage of information\
  \ to unauthorised users.\n"
logo: "ato.gov.au-logo.png"
logoMediaType: "image/png"
tags:
- "financial"
stubs: "ato.gov.au-stubs.json"
swagger: "ato.gov.au-swagger.json"
---
