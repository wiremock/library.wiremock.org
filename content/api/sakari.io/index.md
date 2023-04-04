---
slug: "sakari-io"
title: "Sakari"
provider: "sakari.io"
description: "# Introduction\n\nWelcome to the documentation for the Sakari Messaging\
  \ REST API. \n\nSakari provides an advanced platform to drive large scale customized\
  \ SMS communication\n\nREST is a web-service protocol that lends itself to rapid\
  \ development by using everyday HTTP and JSON technology.\n\nTo find out more about\
  \ our product offering, please visit [https://sakari.io](https://sakari.io).\n\n\
  # Quickstart\n\nFor your convenience we have created a quickstart guide to get you\
  \ up and running in 5 minutes. \n\n[https://sakari.io/blog/sakari-api-quickstart](https://sakari.io/blog/sakari-api-quickstart)\n\
  \n# PostMan Collection\n\nWe've created a simple set of examples using [PostMan](https://www.getpostman.com/)\
  \ Simply click below to import these. You will need to setup three environment variables\
  \ in PostMan - AccountId, ClientId and ClientSecret. Check out our PostMan blog\
  \ post for more information\n\n[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/d616e273edc916a7a6eb)\n\
  \n# Finding your client id, client secret and account id\n\nTo authenticate against\
  \ the API's you will need three key pieces of data\n - client id\n - client secret\n\
  \ - account id\n\nTo retrieve these, simply login into [https://hub.sakari.io](https://hub.sakari.io)\
  \ and click on the \"cog\" in the top right corner. In the popup dialog at the bottom\
  \ you should see your API credentials and account id. If these are not visible you\
  \ will need to click on \"Request Credentials\"\n\n# Versioning\n\nWith any breaking\
  \ changes we will introduce a new version of the API. The latest version is v1.\n\
  \nThe API uses an open schema model, which means server may add extra properties\
  \ to responses. Likewise, the server will ignore any extra query parameters and\
  \ request body properties. When you write clients, you need to ignore additional\
  \ properties in responses to ensure they do not break.\n\n# Testing\n\nThere are\
  \ numerous tools available for testing the API's. We will include examples using\
  \ curl and the client SDKs that we have created. If you would like to see an SDK\
  \ in a language not currently available, please let us know.\n\n# Throttling / Limits\n\
  \nOur API's have been specifically designed to support bulk messaging in a single\
  \ API call. We therefore impose limits on the frequency of calling the APIs to prevent\
  \ abuse or runaway processes. If you feel you need a higher limit, please contact\
  \ us. If you hit the limit you will get a 429 error code returned from our servers\n\
  \n# Errors\n\nThe API uses standard HTTP status codes to indicate the success or\
  \ failure of the API call. The body of the response will be JSON in the following\
  \ format:\n\n```\n{\n  \"success\": false,\n  \"error\": {\n    \"code\": \"CONT-001\"\
  ,\n    \"message\": \"Invalid mobile number\"\n  }\n}\n```\n\n# Pagination\n\nFor\
  \ performance, most GET calls return a subset of data. This data is paginated for\
  \ easy access. Most APIs which return collections of data will return a pagination\
  \ object as such:\n\n```\n{\n  \"pagination\": {\n    \"offset\": 0,\n    \"limit\"\
  : 10\n    \"totalCount\": 21\n  }  \n}\n```\n\nWhen making calls to the API, you\
  \ can adjust the slice of data returned using query parameters such as:\n\n`` https://api.sakari.io/v1/accounts/123/contacts?offset=20&limit=25\
  \ ``\n\nThis will return 25 contacts with an offset of 20.\n"
logo: "sakari.io-logo.png"
logoMediaType: "image/png"
tags:
- "messaging"
stubs: "sakari.io-stubs.json"
swagger: "sakari.io-swagger.json"
---
