---
slug: "getpostman-com"
title: "Postman API"
provider: "getpostman.com"
description: "The Postman API allows you to programmatically access data stored in\
  \ Postman account with ease.\n\nThe easiest way to get started with the API is to\
  \ click the **fork** button to fork this collection to your own workspace and use\
  \ Postman to send requests.\n\n\n# Overview\n\n1. You need a valid <a href=\"#authentication\"\
  >API Key</a> to send requests to the API endpoints. You can get your key from the\
  \ [integrations dashboard](https://go.postman.co/settings/me/api-keys).\n\n1. The\
  \ API has an access <a href=\"#rate-limits\">rate limit</a> applied to it.\n\n1.\
  \ The Postman API will only respond to secured communication done over HTTPS. HTTP\
  \ requests will be sent a `301` redirect to corresponding HTTPS resources.\n\n1.\
  \ Response to every request is sent in [JSON format](https://en.wikipedia.org/wiki/JSON).\
  \ In case the API request results in an error, it is represented by an `\"error\"\
  : {}` key in the JSON response.\n\n1. The request method (verb) determines the nature\
  \ of action you intend to perform. A request made using the `GET` method implies\
  \ that you want to fetch something from Postman, and `POST` implies you want to\
  \ save something new to Postman.\n\n1. The API calls will respond with appropriate\
  \ [HTTP status codes](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes) for\
  \ all requests. Within Postman Client, when a response is received, the status code\
  \ is highlighted and is accompanied by a help text that indicates the possible meaning\
  \ of the response code. A `200 OK` indicates all went well, while `4XX` or `5XX`\
  \ response codes indicate an error from the requesting client or our API servers\
  \ respectively.\n\n1. Individual resources in your Postman Account is accessible\
  \ using its unique id (`uid`). The `uid` is a simple concatenation of the resource\
  \ owner's user-id and the resource-id. For example, a collection's `uid` is `{{owner_id}}-{{collection_id}}`.\n\
  \n# Authentication\n\nAn API Key is required to be sent as part of every request\
  \ to the Postman API, in the form of an `X-Api-Key` request header.\n\n> If you\
  \ do not have an API Key, you can easily generate one by heading over to the [Postman\
  \ Integrations Dashboard](https://go.postman.co/integrations/services/pm_pro_api).\n\
  \nAn API Key tells our API server that the request it received came from you. Everything\
  \ that you have access to in Postman is accessible with an API Key that is generated\
  \ by you.\n\nFor ease of use inside Postman, you could store your API key in an\
  \ [environment variable](https://www.getpostman.com/docs/environments) called `postman_api_key`\
  \ and this [Collection](https://www.getpostman.com/docs/collections) will automatically\
  \ use it to make API calls.\n\n## API Key related error response\n\nIf an API Key\
  \ is missing, malformed, or invalid, you will receive a `401 Unauthorised` response\
  \ code and the following JSON response:\n\n```\n{\n  \"error\": { \n    \"name\"\
  : \"AuthenticationError\",\n    \"message\": \"API Key missing. Every request requires\
  \ an API Key to be sent.\"\n  }\n}\n```\n\n## Using the API Key as a query parameter\n\
  \nEvery request that accepts API Key as `X-Api-Key` request header, also accepts\
  \ the key when sent as `apikey` URL query parameter.\n\nAPI key sent as part of\
  \ the header has a higher priority in case you send the key using both request header\
  \ and query parameter.\n\n\n# Rate Limits\n\nAPI access rate limits are applied\
  \ at a per-key basis in unit time. Access to the API using a key is limited to **60\
  \ requests per minute**. In addition, every API response is accompanied by the following\
  \ set of headers to identify the status of your consumption.\n\n\n| Header     \
  \             | Description |\n|-------------------------|-------------|\n| `X-RateLimit-Limit`\
  \     | The maximum number of requests that the consumer is permitted to make per\
  \ minute. |\n| `X-RateLimit-Remaining` | The number of requests remaining in the\
  \ current rate limit window. |\n| `X-RateLimit-Reset`     | The time at which the\
  \ current rate limit window resets in UTC epoch seconds. |\n\n\nOnce you hit the\
  \ rate limit, you will receive a response similar to the following JSON, with a\
  \ status code of `429 Too Many Requests`.\n\n```json\n{\n  \"error\": {\n    \"\
  name\": \"rateLimitError\",\n    \"message\": \"Rate Limit exceeded. Please retry\
  \ at 1465452702843\"\n  }\n}\n```\n\n\n# Support\n\nFor help regarding accessing\
  \ the Postman API, feel free to discuss it in our [Discourse Community](https://community.getpostman.com).\
  \ You can also drop in a line at [help@getpostman.com](mailto:help@getpostman.com).\n\
  \nIn the event you receive a `503` response from our servers, it implies that we\
  \ have hit an unexpected spike in API access traffic and would usually be operational\
  \ within the next 5 minutes. If the outage persists, or your receive any other form\
  \ of `5XX` error, kindly let us know.\n\n\n# Terms of Use\n\nFor information on\
  \ API terms of use and privacy, refer to our terms at [http://postman.com/legal/terms/](http://postman.com/legal/terms/)\
  \ and our privacy policy at [https://www.postman.com/legal/privacy-policy/](https://www.postman.com/legal/privacy-policy/).\n\
  \n\n# API Reference"
logo: "getpostman.com-logo.svg"
logoMediaType: "image/svg+xml"
tags:
- "developer_tools"
stubs: "getpostman.com-stubs.json"
swagger: "getpostman.com-swagger.json"
---
