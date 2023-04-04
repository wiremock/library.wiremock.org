---
slug: "jumpseller-com"
title: "Jumpseller API"
provider: "jumpseller.com"
description: "# Endpoint Structure\n\nAll URLs are in the format: \n\n```text\nhttps://api.jumpseller.com/v1/path.json?login=XXXXXX&authtoken=storetoken\
  \  \n```\n\nThe path is prefixed by the API version and the URL takes as parameters\
  \ the login (your store specific API login) and your authentication token.\n<br/><br/>\n\
  ***\n\n# Version\n\nThe current version of the API is **v1**.  \nIf we change the\
  \ API in backward-incompatible ways, we'll increase the version number and maintain\
  \ stable support for the old urls.\n<br/><br/>\n***\n\n# Authentication\n\nThe API\
  \ uses a token-based authentication with a combination of a login key and an auth\
  \ token. **Both parameters can be found on the left sidebar of the Account section,\
  \ accessed from the main menu of your Admin Panel**. The auth token of the user\
  \ can be reset on the same page.\n\n![Store Login](/images/support/api/apilogin.png)\n\
  \nThe auth token is a **32 characters** string.\n\nIf you are developing a Jumpseller\
  \ App, the authentication should be done using [OAuth-2](/support/oauth-2). Please\
  \ read the article [Build an App](/support/apps) for more information.\n<br/><br/>\n\
  ***\n\n# Curl Examples\n\nTo request all the products at your store, you would append\
  \ the products index path to the base url to create an URL with the format:  \n\n\
  ```text\nhttps://api.jumpseller.com/v1/products.json?login=XXXXXX&authtoken=XXXXX\n\
  ```\n\nIn curl, you can invoque that URL with:  \n\n```text\ncurl -X GET \"https://api.jumpseller.com/v1/products.json?login=XXXXXX&authtoken=XXXXX\"\
  \n```\n\nTo create a product, you will include the JSON data and specify the MIME\
  \ Type:  \n\n```text\ncurl -X POST -d '{ \"product\" : {\"name\": \"My new Product!\"\
  , \"price\": 100} }' \"https://api.jumpseller.com/v1/products.json?login=XXXXXX&authtoken=XXXXX\"\
  \ -H \"Content-Type:application/json\"\n```\n\nand to update the product identified\
  \ with 123:  \n\n```text\ncurl -X PUT -d '{ \"product\" : {\"name\": \"My updated\
  \ Product!\", \"price\": 99} }' \"https://api.jumpseller.com/v1/products/123.json?login=XXXXXX&authtoken=XXXXX\"\
  \ -H \"Content-Type:application/json\"\n```\n\nor delete it:  \n\n```text\ncurl\
  \ -X DELETE \"https://api.jumpseller.com/v1/products/123.json?login=XXXXXX&authtoken=XXXXX\"\
  \ -H \"Content-Type:application/json\"\n```\n<br/><br/>\n***\n\n# PHP Examples\n\
  \nCreate a new Product (POST method)\n\n```php\n$url = 'https://api.jumpseller.com/v1/products.json?login=XXXXX&authtoken=XXXXX;\n\
  $ch = curl_init($url);\ncurl_setopt($ch, CURLOPT_RETURNTRANSFER, true);\ncurl_setopt($ch,\
  \ CURLOPT_HTTPHEADER, array('Content-Type: application/json'));\n\ncurl_setopt($ch,\
  \ CURLOPT_CUSTOMREQUEST, \"POST\"); //post method\ncurl_setopt($ch, CURLOPT_POSTFIELDS,\
  \ '{ \"product\" : {\"name\": \"My updated Product!\", \"price\": 99} }');\n\n$result\
  \ = curl_exec($ch);\nprint_r($result);\ncurl_close($ch);\n```\n<br/><br/>\n***\n\
  \n# Plain JSON only. No XML.\n\n* We only support JSON for data serialization.\n\
  * Our node format has no root element.  \n* We use snake_case to describe attribute\
  \ keys (like \"created_at\").  \n* All empty value are replaced with **null** strings.\n\
  * All API URLs end in .json to indicate that they accept and return JSON.\n* POST\
  \ and PUT methods require you to explicitly state the MIME type of your request's\
  \ body content as **\"application/json\"**.\n<br/><br/>\n***\n\n# Rate Limit\nYou\
  \ can perform a maximum of:\n\n+ 240 (two hundred forty) requests per minute and\n\
  + 8 (eight) requests per second \n\nIf you exceed this limit, you'll get a 403 Forbidden\
  \ (Rate Limit Exceeded) response for subsequent requests.  \n\nThe rate limits apply\
  \ by IP address and by store. This means that multiple requests on different stores\
  \ are not counted towards the same rate limit.\n\nThis limits are necessary to ensure\
  \ resources are correctly used. Your application should be aware of this limits\
  \ and retry any unsuccessful request, check the following Ruby stub:\n\n```ruby\n\
  tries = 0; max_tries = 3;\nbegin\n  HTTParty.send(method, uri) # perform an API\
  \ call.\n  sleep 0.5\n  tries += 1\nrescue\n  unless tries >= max_tries\n    sleep\
  \ 1.0 # wait the necessary time before retrying the call again.\n    retry\n  end\n\
  end\n```\n\nFinally, you can review the Response Headers of each request:\n\n```text\n\
  Jumpseller-PerMinuteRateLimit-Limit: 60  \nJumpseller-PerMinuteRateLimit-Remaining:\
  \ 59 # requests available on the per-second interval  \nJumpseller-PerSecondRateLimit-Limit:\
  \ 2  \nJumpseller-PerSecondRateLimit-Remaining: 1 # requests available on the per-second\
  \ interval\n``` \n\nto better model your application requests intervals.\n\nIn the\
  \ event of getting your IP banned, the Response Header `Jumpseller-BannedByRateLimit-Reset`\
  \ informs you the time when will your ban be reseted.\n<br/><br/>\n***\n\n# Pagination\n\
  \nBy default we will return 50 objects (products, orders, etc) per page. There is\
  \ a maximum of 100, using a query string `&limit=100`.\nIf the result set gets paginated\
  \ it is your responsibility to check the next page for more objects -- you do this\
  \ by using query strings `&page=2`, `&page=3` and so on.\n\n```text\nhttps://api.jumpseller.com/v1/products.json?login=XXXXXX&authtoken=XXXXX&page=3&limit=100\n\
  ```\n<br/><br/>\n***\n\n# More\n* [Jumpseller API wrapper](https://gitlab.com/jumpseller-api/ruby)\
  \ provides a public Ruby abstraction over our API;\n* [Apps Page](/apps) showcases\
  \ external integrations with Jumpseller done by technical experts;\n* [Imgbb API](https://api.imgbb.com/)\
  \ provides an easy way to upload and temporaly host for images and files.\n<br/><br/>\n\
  ***\n<br/><br/>\n"
logo: "jumpseller.com-logo.png"
logoMediaType: "image/png"
tags:
- "ecommerce"
stubs: "jumpseller.com-stubs.json"
swagger: "jumpseller.com-swagger.json"
---
