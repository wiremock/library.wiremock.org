---
slug: "opentargets-io"
title: "Open Targets Platform REST API"
provider: "opentargets.io"
description: "### The Open Targets Platform REST API\n\nThe Open Targets Platform\
  \ API ('Application Programming Interface') allows programmatic retrieval of the\
  \ Open Targets Platform data via a set of [REST](https://en.wikipedia.org/wiki/Representational_state_transfer)\
  \ services.\n\nYou can make calls to the latest version of our API using the base\
  \ URL `https://platform-api.opentargets.io/v3/platform`. Please make sure you use\
  \ `https` instead of the unencrypted `http` calls, which we do not accept.\n\nWe\
  \ list below the methods available to query our data directly from the API, followed\
  \ by an interactive interface that you can use to try out the parameters and execute\
  \ the REST-API calls.\n\nFor every request you create, the interactive interface\
  \ will display both a [curl](https://curl.haxx.se/) command and a request URL that\
  \ you can use to ensure you get the expected response before using your application\
  \ or workflow. \n\nCheck our documentation for some [API tutorials](https://docs.targetvalidation.org/tutorials/api-tutorials)\
  \ and [get in touch](mailto:support@targetvalidation.org) if you have any questions.\n\
  \n### Available Methods\n\nThe available methods can be grouped in three types:\n\
  \n* __public__ - Methods that serve the core set of our data. These are stable and\
  \ we fully supported them.\n* __private__ - Methods used by the web app to serve\
  \ additional data not specific to our platform. These methods\nmay change without\
  \ notice and should be used with caution.\n* __utils__ - Methods to get statistics\
  \ and technical data about our API.\n\n### Supported formats\n\nThe methods above\
  \ are all available via a `GET` request, and will serve outputs as `JSON`.\n\nAlternative\
  \ output formats, such `xml`, `csv` and `tab`, are also available for some of the\
  \ methods. However alternative output formats are not supported in interactive interface\
  \ below where the response will be always in `JSON.\n\nIf you have complex queries\
  \ with large number of parameters, you should use a `POST` request instead of  `GET`.\
  \ \n`POST` methods require a body encoded as `json`. When querying for a specific\
  \ disease using the latest version of the API, your call would look like the example\
  \ below:\n\n```sh\ncurl -X POST -d '{\"disease\":[\"EFO_0000253\"]}' --header 'Content-Type:\
  \ application/json' https://platform-api.opentargets.io/v3/platform/public/evidence/filter\n\
  ```\n### How to interpret a response\n\nEach HTTPS response will serve data in headers\
  \ and body. The headers will give you details about your query, such as how long\
  \ it took to run.\n\nIn the body of the response, you will find the data you have\
  \ requested for in `JSON` format. The [jq](https://stedolan.github.io/jq/) program\
  \ is a useful tool to parse the json response while on the command line.\n\n```sh\n\
  curl https://platform-api.opentargets.io/v3/platform/public/association/filter\\\
  ?target\\=ENSG00000157764 | jq\n```\n\nWe do not analyse the nature of any specific\
  \ API queries except for the purposes of improving the performance of our API.\n\
  Read more in our [privacy section](https://www.targetvalidation.org/terms_of_use#privacy).\n\
  \nHow can we make the Open Targets Platform API more useful to you? Would you like\
  \ additional methods to be implemented?\nPlease [get in touch](mailto:support@targetvalidation.org)\
  \ and send your suggestions.\n"
logo: "opentargets.io-logo.svg"
logoMediaType: "image/svg+xml"
tags:
- "open_data"
stubs: "opentargets.io-stubs.json"
swagger: "opentargets.io-swagger.json"
---
