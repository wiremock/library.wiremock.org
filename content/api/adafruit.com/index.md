---
slug: "adafruit-com"
title: "Adafruit IO REST API"
provider: "adafruit.com"
description: "### The Internet of Things for Everyone\n\nThe Adafruit IO HTTP API\
  \ provides access to your Adafruit IO data from any programming language or hardware\
  \ environment that can speak HTTP. The easiest way to get started is with [an Adafruit\
  \ IO learn guide](https://learn.adafruit.com/series/adafruit-io-basics) and [a simple\
  \ Internet of Things capable device like the Feather Huzzah](https://www.adafruit.com/product/2821).\n\
  \nThis API documentation is hosted on GitHub Pages and is available at [https://github.com/adafruit/io-api](https://github.com/adafruit/io-api).\
  \ For questions or comments visit the [Adafruit IO Forums](https://forums.adafruit.com/viewforum.php?f=56)\
  \ or the [adafruit-io channel on the Adafruit Discord server](https://discord.gg/adafruit).\n\
  \n#### Authentication\n\nAuthentication for every API request happens through the\
  \ `X-AIO-Key` header or query parameter and your IO API key. A simple cURL request\
  \ to get all available feeds for a user with the username \"io_username\" and the\
  \ key \"io_key_12345\" could look like this:\n\n    $ curl -H \"X-AIO-Key: io_key_12345\"\
  \ https://io.adafruit.com/api/v2/io_username/feeds\n\nOr like this:\n\n    $ curl\
  \ \"https://io.adafruit.com/api/v2/io_username/feeds?X-AIO-Key=io_key_12345\n\n\
  Using the node.js [request](https://github.com/request/request) library, IO HTTP\
  \ requests are as easy as:\n\n```js\nvar request = require('request');\n\nvar options\
  \ = {\n  url: 'https://io.adafruit.com/api/v2/io_username/feeds',\n  headers: {\n\
  \    'X-AIO-Key': 'io_key_12345',\n    'Content-Type': 'application/json'\n  }\n\
  };\n\nfunction callback(error, response, body) {\n  if (!error && response.statusCode\
  \ == 200) {\n    var feeds = JSON.parse(body);\n    console.log(feeds.length + \"\
  \ FEEDS AVAILABLE\");\n\n    feeds.forEach(function (feed) {\n      console.log(feed.name,\
  \ feed.key);\n    })\n  }\n}\n\nrequest(options, callback);\n```\n\nUsing the ESP8266\
  \ Arduino HTTPClient library, an HTTPS GET request would look like this (replacing\
  \ `---` with your own values in the appropriate locations):\n\n```arduino\n/// based\
  \ on\n/// https://github.com/esp8266/Arduino/blob/master/libraries/ESP8266HTTPClient/examples/Authorization/Authorization.ino\n\
  \n#include <Arduino.h>\n#include <ESP8266WiFi.h>\n#include <ESP8266WiFiMulti.h>\n\
  #include <ESP8266HTTPClient.h>\n\nESP8266WiFiMulti WiFiMulti;\n\nconst char* ssid\
  \ = \"---\";\nconst char* password = \"---\";\n\nconst char* host = \"io.adafruit.com\"\
  ;\n\nconst char* io_key = \"---\";\nconst char* path_with_username = \"/api/v2/---/dashboards\"\
  ;\n\n// Use web browser to view and copy\n// SHA1 fingerprint of the certificate\n\
  const char* fingerprint = \"77 00 54 2D DA E7 D8 03 27 31 23 99 EB 27 DB CB A5 4C\
  \ 57 18\";\n\nvoid setup() {\n  Serial.begin(115200);\n\n  for(uint8_t t = 4; t\
  \ > 0; t--) {\n    Serial.printf(\"[SETUP] WAIT %d...\\n\", t);\n    Serial.flush();\n\
  \    delay(1000);\n  }\n\n  WiFi.mode(WIFI_STA);\n  WiFiMulti.addAP(ssid, password);\n\
  \n  // wait for WiFi connection\n  while(WiFiMulti.run() != WL_CONNECTED) {\n  \
  \  Serial.print('.');\n    delay(1000);\n  }\n\n  Serial.println(\"[WIFI] connected!\"\
  );\n\n  HTTPClient http;\n\n  // start request with URL and TLS cert fingerprint\
  \ for verification\n  http.begin(\"https://\" + String(host) + String(path_with_username),\
  \ fingerprint);\n\n  // IO API authentication\n  http.addHeader(\"X-AIO-Key\", io_key);\n\
  \n  // start connection and send HTTP header\n  int httpCode = http.GET();\n\n \
  \ // httpCode will be negative on error\n  if(httpCode > 0) {\n    // HTTP header\
  \ has been send and Server response header has been handled\n    Serial.printf(\"\
  [HTTP] GET response: %d\\n\", httpCode);\n\n    // HTTP 200 OK\n    if(httpCode\
  \ == HTTP_CODE_OK) {\n      String payload = http.getString();\n      Serial.println(payload);\n\
  \    }\n\n    http.end();\n  }\n}\n\nvoid loop() {}\n```\n\n#### Client Libraries\n\
  \nWe have client libraries to help you get started with your project: [Python](https://github.com/adafruit/io-client-python),\
  \ [Ruby](https://github.com/adafruit/io-client-ruby), [Arduino C++](https://github.com/adafruit/Adafruit_IO_Arduino),\
  \ [Javascript](https://github.com/adafruit/adafruit-io-node), and [Go](https://github.com/adafruit/io-client-go)\
  \ are available. They're all open source, so if they don't already do what you want,\
  \ you can fork and add any feature you'd like.\n\n"
logo: "adafruit.com-logo.jpeg"
logoMediaType: "image/jpeg"
tags:
- "iot"
stubs: "adafruit.com-stubs.json"
swagger: "adafruit.com-swagger.json"
---
