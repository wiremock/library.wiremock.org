---
slug: "link-fish"
title: "link.fish API"
provider: "link.fish"
description: "API to easily extract data from websites.\n\n\n# Base URL\n\n\nAll URLs\
  \ referenced in the documentation have the following base:\n\n\n```\nhttps://api.link.fish\n\
  ```\n\n\nThe REST API is only served over HTTPS. To ensure data privacy, unencrypted\
  \ HTTP is not supported.\n\n\n# Authentication\nHTTP requests to the REST API are\
  \ protected with [HTTP Basic authentication](https://en.wikipedia.org/wiki/Basic_access_authentication).\
  \ You will use the email address of your link.fish account as the username and your\
  \ API access token as the password for HTTP Basic authentication.\n\nIf you do not\
  \ have an account yet, go to [https://link.fish/api](https://link.fish/api) and\
  \ create one first.\n\nYou will receive the API access token automatically via email\
  \ after you signed up. To generate a new token and invalidate the current one log\
  \ into your link.fish  account at [https://app.link.fish](https://app.link.fish)\
  \ and go to: \"Plugins\" -> \"API Dashboard\"\n\nThere you can also see how many\
  \ credits you used already.\n\n\n# Errors\nThe API uses standard HTTP status codes\
  \ to indicate the success or failure of the API call. The body of the response will\
  \ be JSON in the following format:\n```\n{\n\n  \"status\": {HTTP STATUS CODE}\n\
  \  \"message\": \"{ERROR MESSAGE}\"\n}\n```\nLike for example when the authorization\
  \ is not provided or wrong:\n```\n{\n\n  \"status\": 401\n  \"message\": \"Unauthorized\"\
  \n}\n```\n\n# Request IDs\n\nEach API request has an associated request identifier.\
  \ You can find it in the response headers, under X-LF-Request-Id. In case you have\
  \ problems please provide this identifier that we can help you as good and fast\
  \ as possible.\n\n\nExample:\n```\nX-LF-Request-Id: f7f0036f-5277-421a-b143-f7a151571d18\n\
  ```\n\n\n# Item format\n\nThe data is by default deeply nested. So if it should\
  \ be checked if there is an offer with a price, the whole tree has to be checked.\
  \ To make that simpler, it is also possible to return the data \"flat\". If selected\
  \ it will flatten the tree by copying all the data to the main level under a property\
  \ with the name of its type and link the data internally.\n\nInformation: We created\
  \ a node module which allows converting between the two formats. It did not get\
  \ open sourced yet. If you are in need, simply contact us via api@link.fish.\n\n\
  \n# Response Content Type\nBy default, all data gets returned as JSON. If the data\
  \ should be returned as XML add the following header:\n\n```\nAccept: application/xml\n\
  ```\n\n# Credits\n\nDepending on the request made a different amount of credits\
  \ get charged. How many which request costs can be found on the [API pricing page](http://link.fish/api/#pricing).\
  \ Additionally, does a  header named \"X-LF-Credits-Charged\" get added to each\
  \ successful response with information about the credits.\n\nExample:\n```\nX-LF-Credits-Charged:\
  \ 1 # Credits used for current requests\nX-LF-Credits-Subscription-Max: 1000 # Total\
  \ credits available in subscription\nX-LF-Credits-Subscription-Used: 512 # Credits\
  \ still left in current month\n```\nYou can check anytime how many credits you did\
  \ use already by logging into your link.fish  account at [https://app.link.fish](https://app.link.fish)\
  \ and checking under:  \"Plugins\" -> \"API Dashboard\"\n\n\nIf you have problems,\
  \ questions or improvement advice please send us an email to api@link.fish\n"
logo: "link.fish-logo.png"
logoMediaType: "image/png"
tags:
- "developer_tools"
stubs: "link.fish-stubs.json"
swagger: "link.fish-swagger.json"
---
