---
slug: "thetvdb-com"
title: "TheTVDB API v3"
provider: "thetvdb.com"
description: "API v3 targets v2 functionality with a few minor additions. The API\
  \ is accessible via https://api.thetvdb.com and provides the following REST endpoints\
  \ in JSON format.\n\n\nHow to use this API documentation\n----------------\n\n\n\
  You may browse the API routes without authentication, but if you wish to send requests\
  \ to the API and see response data, then you must authenticate.\n1. Obtain a JWT\
  \ token by `POST`ing  to the `/login` route in the `Authentication` section with\
  \ your API key and credentials.\n1. Paste the JWT token from the response into the\
  \ \"JWT Token\" field at the top of the page and click the 'Add Token' button.\n\
  \n\nYou will now be able to use the remaining routes to send requests to the API\
  \ and get a response.\n\n\nLanguage Selection\n----------------\n\n\nLanguage selection\
  \ is done via the `Accept-Language` header. At the moment, you may only pass one\
  \ language abbreviation in the header at a time. Valid language abbreviations can\
  \ be found at the `/languages` route..\n\n\nAuthentication\n----------------\n\n\
  \nAuthentication to use the API is similar to the How-to section above. Users must\
  \ `POST` to the `/login` route with their API key and credentials in the following\
  \ format in order to obtain a JWT token.\n\n`{\"apikey\":\"APIKEY\",\"username\"\
  :\"USERNAME\",\"userkey\":\"USERKEY\"}`\n\nNote that the username and key are ONLY\
  \ required for the `/user` routes. The user's key is labled `Account Identifier`\
  \ in the account section of the main site.\nThe token is then used in all subsequent\
  \ requests by providing it in the `Authorization` header. The header will look like:\
  \ `Authorization: Bearer <yourJWTtoken>`. Currently, the token expires after 24\
  \ hours. You can `GET` the `/refresh_token` route to extend that expiration date.\n\
  \n\nVersioning\n----------------\n\n\nYou may request a different version of the\
  \ API by including an `Accept` header in your request with the following format:\
  \ `Accept:application/vnd.thetvdb.v$VERSION`. This documentation automatically uses\
  \ the version seen at the top and bottom of the page."
logo: "thetvdb.com-logo.png"
logoMediaType: "image/png"
tags:
- "media"
- "open_data"
stubs: "thetvdb.com-stubs.json"
swagger: "thetvdb.com-swagger.json"
---
