---
slug: "bigoven-com"
title: "1,000,000+ Recipe and Grocery List API (v2)"
provider: "bigoven.com"
description: "#Documentation\r\n\r\nThis is the documentation for the partner endpoint\
  \ of the BigOven Recipe and Grocery List API.\r\n\r\nThe update brings with it Swagger-based\
  \ documentation. [Swagger](http://swagger.io) is an emerging standard for describing\
  \ REST-based APIs, and with this Swagger-compliant endpoint (above), you can make\
  \ ready-to-go interface libraries for your code via [swagger-codegen](https://github.com/swagger-api/swagger-codegen).\
  \ For instance, it's easy to generate libraries for Node.js, Java, Ruby, ASP.NET\
  \ MVC, jQuery, php and more!\r\n\r\nYou can also try out the endpoint calls with\
  \ your own api_key right here on this page. Be sure to enter your api_key above\
  \ to use the \"Try it out!\" buttons on this page.\r\n\r\n##Start Here\r\n\r\nDevelopers\
  \ new to the BigOven API should start with this version, not with the legacy API.\
  \ We'll be making improvements to this API over time, and doing only bug fixes on\
  \ the v1 API.\r\n\r\n\r\n\r\nTo pretend you're a BigOven user (for instance, to\
  \ get your recently viewed recipes or your grocery list), you need to pass in Basic\
  \ Authentication information in the header, just as with the v1 API. We do now require\
  \ that you make all calls via https. You need to pass your api_key in with every\
  \ call, though this can now be done on the header (send a request header \"X-BigOven-API-Key\"\
  \ set to your api_key value, e.g., Request[\"X-BigOven-API-Key\"]=\"your-key-here\"\
  .)\r\n\r\n##Migration Notes\r\n\r\nFor existing partners, we encourage you to [migrate](https://api2.bigoven.com),\
  \ and while at this writing we have no hard-and-fast termination date for the v1\
  \ API, we strongly prefer that you migrate by January 1, 2017. While the changes\
  \ aren't overly complex, there are several breaking changes, including refactoring\
  \ of recipe search and results and removal of support for XML. This is not a simply\
  \ plug-and-play replacement to the v1 API. With respect to an exclusive focus on\
  \ JSON, the world has spoken, and it prefers JSON for REST-based API's. We've taken\
  \ numerous steps to refactor the API to make it more REST-compliant. Note that this\
  \ v2 API will be the preferred API from this point onward, so we encourage developers\
  \ to migrate to this new format. We have put together some [migration notes](/web/documentation/migration-to-v2)\
  \ that we encourage you to read carefully.\r\n\r\n##Photos\r\n\r\nSee our [photos\
  \ documentation](https://api2.bigoven.com/web/documentation/recipe-images). \r\n\
  \r\nFor more information on usage of this API, including features, pricing, rate\
  \ limits, terms and conditions, please visit the [BigOven API website](https://api2.bigoven.com)."
logo: "bigoven.com-logo.jpeg"
logoMediaType: "image/jpeg"
tags: []
stubs: "bigoven.com-stubs.json"
swagger: "bigoven.com-swagger.json"
---
