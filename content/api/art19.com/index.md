---
slug: "art19-com"
title: "ART19 Content API Documentation"
provider: "art19.com"
description: "The ART19 Content API conforms to the [JSON:API specification](http://jsonapi.org).\n\
  \nAPI requests **MUST** use the HTTP Accept header:\n\n`Accept: application/vnd.api+json`\n\
  \nAPI requests **MUST** be authenticated using the HTTP Authorization header:\n\n\
  `Authorization: Token token=\"your-token\", credential=\"your-credential\"`\n\n\
  ## General Notes\n\nSome query parameters use unencoded [ and ] characters simply\
  \ for readability. Defaults, examples, and\npossible values are additionally rendered\
  \ in double quotes for readability. In practice, query parameters should\nnot have\
  \ quotes around the values (e.g., `foo=bar` is valid, not `foo=\"bar\"`), and both\
  \ query parameter keys\nand values must be percent-encoded, per the requirements\
  \ in [RFC 3986 § 3.4](https://tools.ietf.org/html/rfc3986#section-3.4).\n\n## Rate\
  \ Limiting\n\nIn order to provide a fair distribution of available resources, all\
  \ API calls are subject to rate limits.\nIf you exceed the number of API calls per\
  \ minute granted to your credential, a `429 Too Many Requests`\nerror response will\
  \ be returned.\n\nIn that case, a `Retry-After` header MAY be included in the response,\
  \ describing the number of seconds\nafter which a request can be retried.\n\nIf\
  \ you run into a high number of 429 errors, please reach out to ART19 Support to\
  \ adjust your rate limit.\n\n### Example\n\nIn the following example the request\
  \ can be retried after waiting for 21 seconds:\n\n    HTTP/1.1 429 Too Many Requests\n\
  \    Content-Type: text/html\n    Retry-After: 21\n\n## Pagination\n\nRequests to\
  \ collection endpoints **SHOULD** provide pagination parameters.\nSome endpoints\
  \ **REQUIRE** pagination parameters to be provided.\nWhenever pagination is provided,\
  \ it **MUST** be valid.\nFailing to provide pagination when it is required or providing\
  \ wrong or incomplete pagination\nalways results in a `400 Bad Request` error response.\n\
  \nThe page numbering starts with `1` and the maximum page size (if not otherwise\
  \ documented\non an endpoint) is `100`. Pagination **MUST NOT** be specified if\
  \ requesting a list of IDs (using an `ids[]` parameter).\n\nProviding invalid values\
  \ for page number or page size, as well as providing only a page number or only\
  \ a page size,\nis considered an error. Pagination is provided like this:\n\n`page[number]=1&page[size]=25`\n\
  \nResponses conform to the [JSON:API specification's pagination section](https://jsonapi.org/format/#fetching-pagination)\n\
  by including pagination links. Your requested page size will be carried into the\
  \ pagination links.\n\n## Sorting\n\nRequests to collection endpoints usually accept\
  \ a `sort` parameter. Please refer to the\n[JSON:API Specification's sorting section](https://jsonapi.org/format/#fetching-sorting)\
  \ for further details.\n\n## Relationship Linking\n\nCurrently, resources return\
  \ all of their relationships, in no particular order, pursuant to how relationships\n\
  should be returned [according to the JSON:API specification](https://jsonapi.org/format/#document-resource-object-relationships).\
  \ Consumers of this API\n**MUST NOT** make assumptions about the order of these\
  \ collections. Even though this data is not currently paginated, consumers **MUST**\
  \ support\npaginating relationships per the JSON:API specification if this data\
  \ is important for their application.\n"
logo: "art19.com-logo.jpeg"
logoMediaType: "image/jpeg"
tags:
- "media"
stubs: "art19.com-stubs.json"
swagger: "art19.com-swagger.json"
---
