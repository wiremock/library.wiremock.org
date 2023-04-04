---
slug: "portfoliooptimizer-io"
title: "Portfolio Optimizer"
provider: "portfoliooptimizer.io"
description: "Portfolio Optimizer is a [Web API](https://en.wikipedia.org/wiki/Web_API)\
  \ to analyze and optimize investment portfolios (collection of financial assets\
  \ such as stocks, bonds, ETFs, crypto-currencies) using modern portfolio theory\
  \ algorithms (mean-variance, VaR, etc.).\n\n# API General Information\n\n  Portfolio\
  \ Optimizer is based on [REST](https://en.wikipedia.org/wiki/Representational_state_transfer)\
  \ for easy integration, uses [JSON](https://en.wikipedia.org/wiki/JSON) for the\
  \ exchange of data and uses a standard [HTTP verb](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Request_methods)\
  \ (`POST`) to represent the action(s).\n\nPortfolio Optimizer is also as secured\
  \ as a Web API could be: \n* [256-bit HTTPS Encryption](https://en.wikipedia.org/wiki/HTTPS)\n\
  * No usage of cookies\n* No usage of personal data  \n\n## API Headers \nThe following\
  \ HTTP header(s) are required when calling Portfolio Optimizer endpoints:\n* `Content-type:\
  \ application/json`  \n  This header specifies that the data provided in input to\
  \ the endpoint is in JSON format\n\nThe following HTTP header(s) are optional when\
  \ calling Portfolio Optimizer endpoints:\n* `Content-Encoding: gzip`  \n  This header\
  \ indicates that the data provided in input to the endpoint is compressed with gzip.\n\
  * `X-API-Key: <private API key>`  \n  This header enables [authenticated users](#auth)\
  \ to provide their private [API key](#overview--api-key) in order to [benefit from\
  \ higher API limits](#overview--api-limits)\n\n## API Key\nPortfolio Optimizer is\
  \ free to use, but not free to run.\n\nIn order to obtain an API key and benefit\
  \ from [higher API limits](#overview--api-limits), a *small* participation to Portfolio\
  \ Optimizer running costs is required.\n\nThis participation takes the form of coffee(s),\
  \ with one coffee = one month of usage.\n\n<p><a href=\"https://www.buymeacoffee.com/portfolioopt\"\
  ><img alt='Buy a Coffee at buymeacoffee.com' src=\"https://img.buymeacoffee.com/button-api/?text=Buymeacoffee.com&emoji=&slug=portfolioopt&button_colour=000000&font_colour=ffffff&font_family=Cookie&outline_colour=ffffff&coffee_colour=FFDD00\"\
  ></a></p>\n\n\n> **Notes:** \n> * Please make sure not to expose your API key publicly!\n\
  \n## API Limits \n\nPortfolio Optimizer comes with *fairly reasonable* API limits.\n\
  \nFor anonymous users:  \n* The API requests are restricted to a subset of all the\
  \ available endpoints and/or endpoints features  \n* The API requests are limited\
  \ to 1 request per second for all the anonymous users combined, with concurrent\
  \ requests rejected \n* The API requests are limited to 1 second of execution time\n\
  * The API requests are limited to 20 assets, 250 portfolios, 500 series data points\
  \ and 5 factors\n\nFor authenticated users with an [API key](#overview--api-key):\
  \  \n* The API requests have access to all the available endpoints and endpoints\
  \ features\n* The API requests are limited to 10000 requests per 24 hour per API\
  \ key, with concurrent requests queued\n* The API requests are limited to 2.5 seconds\
  \ of execution time\n* The API requests are limited to 100 assets, 1250 portfolios,\
  \ 2500 series data points and 25 factors\n\n> **Notes:** \n> * It is possible to\
  \ further relax the API limits, or to disable the API limits alltogether; please\
  \ [contact the support](https://portfoliooptimizer.io/contact/) for more details.\n\
  > * Information on the API rate limits are provided in response messages HTTP headers\
  \ `x-ratelimit-*`:  \n>   * `x-ratelimit-limit-second`, the limit on the number\
  \ of API requests per second\n>   * `x-ratelimit-remaining-second`, the number of\
  \ remaining API requests in the current second    \n>   * `x-ratelimit-limit-minute`,\
  \ the limit on the number of API requests per minute\n>   * ...\n\n## API Regions\n\
  Portfolio Optimizer servers are located in Western Europe.\n\n> **Notes:** \n> *\
  \ It is possible to deploy Portfolio Optimizer in other geographical regions, for\
  \ example to improve the API latency; please [contact the support](https://portfoliooptimizer.io/contact/)\
  \ for more details. \n\n## API Response Codes       \n\nStandard [HTTP response\
  \ codes](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes) are used by Portfolio\
  \ Optimizer to provide details on the status of API requests.\n\n| HTTP Code | Description\
  \ | Notes |\n| --------- | ----------- | ----- |\n| 200 | Request successfully processed\
  \ | - |\n| 400 | Request failed to be processed because of incorrect content | The\
  \ response message body contains information on the incorrect content |\n| 401 |\
  \ Request failed to be processed because of invalid API key | - |\n| 404 | Request\
  \ failed to be processed because of non existing endpoint | The requested endpoint\
  \ might exist, but needs to be accessed with another HTTP method (e.g., `POST` instead\
  \ of `GET`) |\n| 429 | Request failed to be processed because of API limits violated\
  \ | The response message HTTP headers `x-ratelimit-*` contain information on the\
  \ [API limits](#overview--api-limits) |\n| 500 | Request failed to be processed\
  \ because of an internal error | Something went wrong on Portfolio Optimizer side,\
  \ do not hesitate to [report the issue](#overview--support) |\n| 502 | Request failed\
  \ to be processed because of a temporary connectivity error | Something went wrong\
  \ on Portfolio Optimizer side, please check the [API status](#overview--api-status)\
  \ and do not hesitate to [report the issue](#overview--support) |\n\n## API Status\
  \  \n\nPortfolio Optimizer is monitored 24/7 by [UptimeRobot](https://stats.uptimerobot.com/wgW71SL1AW).\n\
  \n# Support\n\nFor any issue or question about Portfolio Optimizer, please do not\
  \ hesitate to [contact the support](https://portfoliooptimizer.io/contact/).\n"
logo: "portfoliooptimizer.io-logo.png"
logoMediaType: "image/png"
tags:
- "financial"
stubs: "portfoliooptimizer.io-stubs.json"
swagger: "portfoliooptimizer.io-swagger.json"
---