---
slug: "globalwinescore-com"
title: "GlobalWineScore API Documentation"
provider: "globalwinescore.com"
description: "\n\nThe GlobalWineScore API is designed as a RESTful API, providing\
  \ several resources and methods depending on your usage plan.\n\nFor further information\
  \ please refer to <a href=\"https://www.globalwinescore.com/plans\" target=\"_blank\"\
  >our plans</a>.\n\n# Authentication\nThe API uses token-based authentication.\n\
  In order to authenticate your requests, you need to include a specific header in\
  \ each of your requests:\n\n```\nAuthorization: Token {YOUR-API-TOKEN}\n```\nThe\
  \ word <b>Token</b> must be written. Your requests must also use the <b>HTTPS</b>\
  \ protocol.\n\nIf you don't have a token yet, you need to apply for one [here](https://www.globalwinescore.com/api/).\n\
  \nYour personal token can be found under the <a href=\"https://www.globalwinescore.com/account/api/\"\
  \ target=\"_blank\">My account > API</a> section of the GlobalWineScore website\n\
  \n# Format\nThe API provides several rendering formats which you can control using\
  \ the `Accept` header or `format` query parameter.\n\n- JSON (default): no header\
  \ or `Accept: application/json`\n- XML: `Accept: application/xml`\n# Rate limiting\n\
  For API requests, the rate limit allows for up to 10 requests per minute.\n\n# Error\
  \ handling\n\nWhether a request succeeded is indicated by the HTTP status code.\
  \ A 2xx status code indicates success, whereas a 4xx status code indicates failure.\n\
  \nWhen a request fails, the response body is still JSON, but always contains a `detail`\
  \ field with a description of the error, which you can inspect for debugging.\n\n\
  For example, trying to access the API without proper authentication will return\
  \ code 403 along with the message:\n\n`{\"detail\": \"Authentication credentials\
  \ were not provided.\"}`\n\nFound a bug ? send us an email at <a href=\"mailto:api@globalwinescore.com\"\
  >api@globalwinescore.com</a>\n\n# Ordering\n\nAt the moment, GlobalWineScores may\
  \ be sorted by `date` and `score`. Use \"-\"\nto sort in descending order.\n\n#\
  \ Continuous synchronization\n\nIf you need to synchronize your database with our\
  \ API, you can query our API using `?ordering=-date` to get the newest scores first,\
  \ which means you won't have to crawl the whole catalog every time :-)\n\n# Quick\
  \ search interface\nIf you need to search our catalog (e.g. to align it with yours),\
  \ we're providing you with a handy interface accessible here: <a href=\"https://api.globalwinescore.com/search/\"\
  \ target=\"_blank\">https://api.globalwinescore.com/search/</a>\n\nYou need to be\
  \ logged in (email/password) to access this page, but other than that you can share\
  \ it with anyone in your team and start searching right away !\n\n# Resources\n\n\
  The details about available endpoints can be found below.\nYou can click on each\
  \ endpoint to find information about their parameters.\n"
logo: "globalwinescore.com-logo.jpeg"
logoMediaType: "image/jpeg"
tags:
- "open_data"
stubs: "globalwinescore.com-stubs.json"
swagger: "globalwinescore.com-swagger.json"
---
