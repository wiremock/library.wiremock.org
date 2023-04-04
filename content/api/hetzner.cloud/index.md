---
slug: "hetzner-cloud"
title: "Hetzner Cloud API"
provider: "hetzner.cloud"
description: "This is the official API documentation for the Public Hetzner Cloud.\n\
  \n## Introduction\n\nThe Hetzner Cloud API operates over HTTPS and uses JSON as\
  \ its data format. The API is a RESTful API and utilizes HTTP methods and HTTP status\
  \ codes to specify requests and responses.\n\nAs an alternative to working directly\
  \ with our API you may also consider to use:\n* Our CLI program [hcloud](https://github.com/hetznercloud/cli)\n\
  * Our [library for Go](https://github.com/hetznercloud/hcloud-go)\n* Our [library\
  \ for Python](https://github.com/hetznercloud/hcloud-python)\n\nAlso you can find\
  \ a [list of libraries, tools, and integrations on GitHub](https://github.com/hetznercloud/awesome-hcloud).\n\
  \nIf you are developing integrations based on our API and your product is Open Source\
  \ you may be eligible for a free one time €50 (excl. VAT) credit on your account.\
  \ Please contact us via the the support page on your Cloud Console and let us know\
  \ the following:\n* The type of integration you would like to develop\n* Link to\
  \ the GitHub repo you will use for the Project\n* Link to some other Open Source\
  \ work you have already done (if you have done so)\n\n## Getting Started\nTo get\
  \ started using the API you first need an API token. Sign in into the [Hetzner Cloud\
  \ Console](https://console.hetzner.cloud/) choose a Project, go to `Security` →\
  \ `API Tokens`, and generate a new token. Make sure to copy the token because it\
  \ won’t be shown to you again. A token is bound to a Project, to interact with the\
  \ API of another Project you have to create a new token inside the Project. Let’\
  s say your new token is `jEheVytlAoFl7F8MqUQ7jAo2hOXASztX`.\n\nYou’re now ready\
  \ to do your first request against the API. To get a list of all Servers in your\
  \ Project, issue the example request on the right side using [curl](https://curl.haxx.se/).\n\
  \nMake sure to replace the token in the example command with the token you have\
  \ just created. Since your Project probably does not contain any Servers yet, the\
  \ example response will look like the response on the right side. We will almost\
  \ always provide a resource root like `servers` inside the example response. A response\
  \ can also contain a `meta` object with information like [Pagination](https://docs.hetzner.cloud/#overview-pagination).\n\
  \n**Example Request**\n```bash\ncurl -H \"Authorization: Bearer jEheVytlAoFl7F8MqUQ7jAo2hOXASztX\"\
  \ \\\n    https://api.hetzner.cloud/v1/servers\n```\n\n**Example Response**\n```json\n\
  {\n    \"servers\": [],\n    \"meta\": {\n        \"pagination\": {\n          \
  \  \"page\": 1,\n            \"per_page\": 25,\n            \"previous_page\": null,\n\
  \            \"next_page\": null,\n            \"last_page\": 1,\n            \"\
  total_entries\": 0\n        }\n    }\n}\n```\n\n## Authentication\nAll requests\
  \ to the Hetzner Cloud API must be authenticated via a API token. Include your secret\
  \ API token in every request you send to the API with the `Authorization` HTTP header.\n\
  \nTo create a new API token for your Project, switch into the [Hetzner Cloud Console](https://console.hetzner.cloud/)\
  \ choose a Project, go to `Security` → `API Tokens`, and generate a new token.\n\
  \n**Example Authorization header**\n```html\nAuthorization: Bearer LRK9DAWQ1ZAEFSrCNEEzLCUwhYX1U3g7wMg4dTlkkDC96fyDuyJ39nVbVjCKSDfj\n\
  ```\n\n## Errors\nErrors are indicated by HTTP status codes. Further, the response\
  \ of the request which generated the error contains an error code, an error message,\
  \ and, optionally, error details. The schema of the error details object depends\
  \ on the error code.\n\nThe error response contains the following keys:\n\n| Keys\
  \      | Meaning                                                               |\n\
  |-----------|-----------------------------------------------------------------------|\n\
  | `code`    | Short string indicating the type of error (machine-parsable)     \
  \     |\n| `message` | Textual description on what has gone wrong              \
  \              |\n| `details` | An object providing for details on the error (schema\
  \ depends on code) |\n\n**Example response**\n```json\n{\n  \"error\": {\n    \"\
  code\": \"invalid_input\",\n    \"message\": \"invalid input in field 'broken_field':\
  \ is too long\",\n    \"details\": {\n      \"fields\": [\n        {\n         \
  \ \"name\": \"broken_field\",\n          \"messages\": [\"is too long\"]\n     \
  \   }\n      ]\n    }\n  }\n}\n```\n\n### Error Codes\n\n| Code                \
  \      | Description                                                           \
  \           |\n|---------------------------|----------------------------------------------------------------------------------|\n\
  | `forbidden`               | Insufficient permissions for this request        \
  \                                |\n| `invalid_input`           | Error while parsing\
  \ or processing the input                                      |\n| `json_error`\
  \              | Invalid JSON input in your request                            \
  \                   |\n| `locked`                  | The item you are trying to\
  \ access is locked (there is already an Action running) |\n| `not_found`       \
  \        | Entity not found                                                    \
  \             |\n| `rate_limit_exceeded`     | Error when sending too many requests\
  \                                             |\n| `resource_limit_exceeded` | Error\
  \ when exceeding the maximum quantity of a resource for an account           |\n\
  | `resource_unavailable`    | The requested resource is currently unavailable  \
  \                                |\n| `service_error`           | Error within a\
  \ service                                                           |\n| `uniqueness_error`\
  \        | One or more of the objects fields must be unique                    \
  \             |\n| `protected`               | The Action you are trying to start\
  \ is protected for this resource                |\n| `maintenance`             |\
  \ Cannot perform operation due to maintenance                                  \
  \    |\n| `conflict`                | The resource has changed during the request,\
  \ please retry                        |\n| `unsupported_error`       | The corresponding\
  \ resource does not support the Action                           |\n| `token_readonly`\
  \          | The token is only allowed to perform GET requests                 \
  \               |\n| `unavailable`             | A service or product is currently\
  \ not available                                  |\n\n**invalid_input**\n```json\n\
  {\n  \"error\": {\n    \"code\": \"invalid_input\",\n    \"message\": \"invalid\
  \ input in field 'broken_field': is too long\",\n    \"details\": {\n      \"fields\"\
  : [\n        {\n          \"name\": \"broken_field\",\n          \"messages\": [\"\
  is too long\"]\n        }\n      ]\n    }\n  }\n}\n```\n\n**uniqueness_error**\n\
  ```json\n{\n  \"error\": {\n    \"code\": \"uniqueness_error\",\n    \"message\"\
  : \"SSH key with the same fingerprint already exists\",\n    \"details\": {\n  \
  \    \"fields\": [\n        {\n          \"name\": \"public_key\"\n        }\n \
  \     ]\n    }\n  }\n}\n```\n\n**resource_limit_exceeded**\n```json\n{\n  \"error\"\
  : {\n    \"code\": \"resource_limit_exceeded\",\n    \"message\": \"project limit\
  \ exceeded\",\n    \"details\": {\n      \"limits\": [\n        {\n          \"\
  name\": \"project_limit\"\n        }\n      ]\n    }\n  }\n}\n```\n\n## Labels\n\
  Labels are `key/value` pairs that can be attached to all resources.\n\nValid label\
  \ keys have two segments: an optional prefix and name, separated by a slash (`/`).\
  \ The name segment is required and must be a string of 63 characters or less, beginning\
  \ and ending with an alphanumeric character (`[a-z0-9A-Z]`) with dashes (`-`), underscores\
  \ (`_`), dots (`.`), and alphanumerics between. The prefix is optional. If specified,\
  \ the prefix must be a DNS subdomain: a series of DNS labels separated by dots (`.`),\
  \ not longer than 253 characters in total, followed by a slash (`/`).\n\nValid label\
  \ values must be a string of 63 characters or less and must be empty or begin and\
  \ end with an alphanumeric character (`[a-z0-9A-Z]`) with dashes (`-`), underscores\
  \ (`_`), dots (`.`), and alphanumerics between.\n\nThe `hetzner.cloud/` prefix is\
  \ reserved and cannot be used.\n\n**Example Labels**\n```json\n{\n  \"labels\":\
  \ {\n    \"environment\":\"development\",\n    \"service\":\"backend\",\n    \"\
  example.com/my\":\"label\",\n    \"just-a-key\":\"\"\n  }\n}\n```\n\n## Label Selector\n\
  For resources with labels, you can filter resources by their labels using the label\
  \ selector query language.\n\n| Expression           | Meaning                 \
  \                                            |\n|----------------------|---------------------------------------------------------------------|\n\
  | `k==v` / `k=v`       | Value of key `k` does equal value `v`                 \
  \              |\n| `k!=v`               | Value of key `k` does not equal value\
  \ `v`                           |\n| `k`                  | Key `k` is present \
  \                                                 |\n| `!k`                 | Key\
  \ `k` is not present                                              |\n| `k in (v1,v2,v3)`\
  \    | Value of key `k` is `v1`, `v2`, or `v3`                             |\n|\
  \ `k notin (v1,v2,v3)` | Value of key `k` is neither `v1`, nor `v2`, nor `v3`  \
  \              |\n| `k1==v,!k2`          | Value of key `k1` is `v` and key `k2`\
  \ is not present                |\n\n### Examples\n* Returns all resources that\
  \ have a `env=production` label and that don't have a `type=database` label:\n\n\
  \  `env=production,type!=database`\n* Returns all resources that have a `env=testing`\
  \ or `env=staging` label:\n\n    `env in (testing,staging)`\n* Returns all resources\
  \ that don't have a `type` label:\n\n    `!type`\n\n## Pagination\nResponses which\
  \ return multiple items support pagination. If they do support pagination, it can\
  \ be controlled with following query string parameters:\n\n* A `page` parameter\
  \ specifies the page to fetch. The number of the first page is 1.\n* A `per_page`\
  \ parameter specifies the number of items returned per page. The default value is\
  \ 25, the maximum value is 50 except otherwise specified in the documentation.\n\
  \nResponses contain a `Link` header with pagination information.\n\nAdditionally,\
  \ if the response body is JSON and the root object is an object, that object has\
  \ a `pagination` object inside the `meta` object with pagination information:\n\n\
  **Example Pagination**\n```json\n{\n    \"servers\": [...],\n    \"meta\": {\n \
  \       \"pagination\": {\n            \"page\": 2,\n            \"per_page\": 25,\n\
  \            \"previous_page\": 1,\n            \"next_page\": 3,\n            \"\
  last_page\": 4,\n            \"total_entries\": 100\n        }\n    }\n}\n```\n\n\
  The keys `previous_page`, `next_page`, `last_page`, and `total_entries` may be `null`\
  \ when on the first page, last page, or when the total number of entries is unknown.\n\
  \n**Example Pagination Link header**\n```bash\nLink: <https://api.hetzner.cloud/v1/actions?page=2&per_page=5>;\
  \ rel=\"prev\",\n      <https://api.hetzner.cloud/v1/actions?page=4&per_page=5>;\
  \ rel=\"next\",\n      <https://api.hetzner.cloud/v1/actions?page=6&per_page=5>;\
  \ rel=\"last\"\n```\n\nLine breaks have been added for display purposes only and\
  \ responses may only contain some of the above `rel` values.\n\n## Rate Limiting\n\
  All requests, whether they are authenticated or not, are subject to rate limiting.\
  \ If you have reached your limit, your requests will be handled with a `429 Too\
  \ Many Requests` error. Burst requests are allowed. Responses contain serveral headers\
  \ which provide information about your current rate limit status.\n\n* The `RateLimit-Limit`\
  \ header contains the total number of requests you can perform per hour.\n* The\
  \ `RateLimit-Remaining` header contains the number of requests remaining in the\
  \ current rate limit time frame.\n* The `RateLimit-Reset` header contains a UNIX\
  \ timestamp of the point in time when your rate limit will have recovered and you\
  \ will have the full number of requests available again.\n\nThe default limit is\
  \ 3600 requests per hour and per Project. The number of remaining requests increases\
  \ gradually. For example, when your limit is 3600 requests per hour, the number\
  \ of remaining requests will increase by 1 every second.\n\n## Server Metadata\n\
  Your Server can discover metadata about itself by doing a HTTP request to specific\
  \ URLs. The following data is available:\n\n| Data              | Format | Contents\
  \                                                     |\n|-------------------|--------|--------------------------------------------------------------|\n\
  | hostname          | text   | Name of the Server as set in the api            \
  \             |\n| instance-id       | number | ID of the server               \
  \                              |\n| public-ipv4       | text   | Primary public\
  \ IPv4 address                                  |\n| private-networks  | yaml  \
  \ | Details about the private networks the Server is attached to |\n| availability-zone\
  \ | text   | Name of the availability zone that Server runs in            |\n| region\
  \            | text   | Network zone, e.g. eu-central                          \
  \      |\n\n**Example: Summary**\n```bash\n$ curl http://169.254.169.254/hetzner/v1/metadata\n\
  ```\n\n```yaml\navailability-zone: hel1-dc2\nhostname: my-server\ninstance-id: 42\n\
  public-ipv4: 1.2.3.4\nregion: eu-central\n```\n\n**Example: Hostname**\n```bash\n\
  $ curl http://169.254.169.254/hetzner/v1/metadata/hostname\nmy-server\n```\n\n**Example:\
  \ Instance ID**\n```bash\n$ curl http://169.254.169.254/hetzner/v1/metadata/instance-id\n\
  42\n```\n\n**Example: Public IPv4**\n```bash\n$ curl http://169.254.169.254/hetzner/v1/metadata/public-ipv4\n\
  1.2.3.4\n```\n\n**Example: Private Networks**\n```bash\n$ curl http://169.254.169.254/hetzner/v1/metadata/private-networks\n\
  ```\n\n```json\n- ip: 10.0.0.2\n  alias_ips: [10.0.0.3, 10.0.0.4]\n  interface_num:\
  \ 1\n  mac_address: 86:00:00:2a:7d:e0\n  network_id: 1234\n  network_name: nw-test1\n\
  \  network: 10.0.0.0/8\n  subnet: 10.0.0.0/24\n  gateway: 10.0.0.1\n- ip: 192.168.0.2\n\
  \  alias_ips: []\n  interface_num: 2\n  mac_address: 86:00:00:2a:7d:e1\n  network_id:\
  \ 4321\n  network_name: nw-test2\n  network: 192.168.0.0/16\n  subnet: 192.168.0.0/24\n\
  \  gateway: 192.168.0.1\n```\n\n**Example: Availability Zone**\n```bash\n$ curl\
  \ http://169.254.169.254/hetzner/v1/metadata/availability-zone\nhel1-dc2\n```\n\n\
  **Example: Region**\n```bash\n$ curl http://169.254.169.254/hetzner/v1/metadata/region\n\
  eu-central\n```\n\n## Sorting\nSome responses which return multiple items support\
  \ sorting. If they do support sorting the documentation states which fields can\
  \ be used for sorting. You specify sorting with the `sort` query string parameter.\
  \ You can sort by multiple fields. You can set the sort direction by appending `:asc`\
  \ or `:desc` to the field name. By default, ascending sorting is used.\n\n**Example:\
  \ Sorting**\n```bash\nhttps://api.hetzner.cloud/v1/actions?sort=status\nhttps://api.hetzner.cloud/v1/actions?sort=status:asc\n\
  https://api.hetzner.cloud/v1/actions?sort=status:desc\nhttps://api.hetzner.cloud/v1/actions?sort=status:asc&sort=command:desc\n\
  ```\n"
logo: "hetzner.cloud-logo.svg"
logoMediaType: "image/svg+xml"
tags:
- "hosting"
stubs: "hetzner.cloud-stubs.json"
swagger: "hetzner.cloud-swagger.json"
---
