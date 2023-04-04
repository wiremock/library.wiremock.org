---
slug: "rudder-example-local"
title: "Rudder API"
provider: "rudder.example.local"
description: "Download OpenAPI specification: [openapi.yml](openapi.yml)\n\n# Introduction\n\
  \nRudder exposes a REST API, enabling the user to interact with Rudder without using\
  \ the webapp, for example in scripts or cronjobs.\n\n## Versioning\n\nEach time\
  \ the API is extended with new features (new functions, new parameters, new responses,\
  \ ...), it will be assigned a new version number. This will allow you\nto keep your\
  \ existing scripts (based on previous behavior). Versions will always be integers\
  \ (no 2.1 or 3.3, just 2, 3, 4, ...) or `latest`.\n\nYou can change the version\
  \ of the API used by setting it either within the url or in a header:\n\n* the URL:\
  \ each URL is prefixed by its version id, like `/api/version/function`.\n\n```bash\n\
  # Version 10\ncurl -X GET -H \"X-API-Token: yourToken\" https://rudder.example.com/rudder/api/10/rules\n\
  # Latest\ncurl -X GET -H \"X-API-Token: yourToken\" https://rudder.example.com/rudder/api/latest/rules\n\
  # Wrong (not an integer) => 404 not found\ncurl -X GET -H \"X-API-Token: yourToken\"\
  \ https://rudder.example.com/rudder/api/3.14/rules\n```\n\n* the HTTP headers. You\
  \ can add the **X-API-Version** header to your request. The value needs to be an\
  \ integer or `latest`.\n\n```bash\n# Version 10\ncurl -X GET -H \"X-API-Token: yourToken\"\
  \ -H \"X-API-Version: 10\" https://rudder.example.com/rudder/api/rules\n# Wrong\
  \ => Error response indicating which versions are available\ncurl -X GET -H \"X-API-Token:\
  \ yourToken\" -H \"X-API-Version: 3.14\" https://rudder.example.com/rudder/api/rules\n\
  ```\n\nIn the future, we may declare some versions as deprecated, in order to remove\
  \ them in a later version of Rudder, but we will never remove any versions without\
  \ warning, or without a safe\nperiod of time to allow migration from previous versions.\n\
  \n\n<h4>Existing versions</h4>\n<table>\n  <thead>\n    <tr>\n      <th style=\"\
  width: 20%\">Version</th>\n      <th style=\"width: 20%\">Rudder versions it appeared\
  \ in</th>\n      <th style=\"width: 70%\">Description</th>\n    </tr>\n  </thead>\n\
  \  <tbody>\n    <tr>\n      <td class=\"code\">1</td>\n      <td class=\"code\"\
  >Never released (for internal use only)</td>\n      <td>Experimental version</td>\n\
  \    </tr>\n    <tr>\n      <td class=\"code\">2 to 10 (deprecated)</td>\n     \
  \ <td class=\"code\">4.3 and before</td>\n      <td>These versions provided the\
  \ core set of API features for rules, directives, nodes global parameters, change\
  \ requests and compliance, rudder settings and system API</td>\n    </tr>\n    <tr>\n\
  \      <td class=\"code\">11</td>\n      <td class=\"code\">5.0</td>\n      <td>New\
  \ system API (replacing old localhost v1 api): status, maintenance operations and\
  \ server behavior</td>\n    </tr>\n    <tr>\n      <td class=\"code\">12</td>\n\
  \      <td class=\"code\">6.0 and 6.1</td>\n      <td>Node key management</td>\n\
  \    </tr>\n    <tr>\n      <td class=\"code\">13</td>\n      <td class=\"code\"\
  >6.2</td>\n      <td><ul>\n        <li>Node status endpoint</li>\n        <li>System\
  \ health check</li>\n        <li>System maintenance job to purge software [that\
  \ endpoint was back-ported in 6.1]</li>\n      </ul></td>\n    </tr>\n    <tr>\n\
  \      <td class=\"code\">14</td>\n      <td class=\"code\">7.0</td>\n      <td><ul>\n\
  \        <li>Secret management</li>\n        <li>Directive tree</li>\n        <li>Improve\
  \ techniques management</li>\n        <li>Demote a relay</li>\n      </ul></td>\n\
  \    </tr>\n    <tr>\n      <td class=\"code\">15</td>\n      <td class=\"code\"\
  >7.1</td>\n      <td><ul>\n        <li>Package updates in nodes</li>\n      </ul></td>\n\
  \    </tr>\n    <tr>\n      <td class=\"code\">16</td>\n      <td class=\"code\"\
  >7.2</td>\n      <td><ul>\n        <li>Create node API included from plugin</li>\n\
  \        <li>Configuration archive import/export</li>\n      </ul></td>\n    </tr>\n\
  \  </tbody>\n</table>\n\n\n## Response format\n\nAll responses from the API are\
  \ in the JSON format.\n\n```json\n{\n  \"action\": \"The name of the called function\"\
  ,\n  \"id\": \"The ID of the element you want, if relevant\",\n  \"result\": \"\
  The result of your action: success or error\",\n  \"data\": \"Only present if this\
  \ is a success and depends on the function, it's usually a JSON object\",\n  \"\
  errorDetails\": \"Only present if this is an error, it contains the error message\"\
  \n}\n```\n\n\n* __Success__ responses are sent with the 200 HTTP (Success) code\n\
  \n* __Error__ responses are sent with a HTTP error code (mostly 5xx...)\n\n\n##\
  \ HTTP method\n\nRudder's REST API is based on the usage of [HTTP methods](http://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html).\
  \ We use them to indicate what action will be done by the request. Currently, we\
  \ use four of them:\n\n\n* **GET**: search or retrieve information (get rule details,\
  \ get a group, ...)\n\n* **PUT**: add new objects (create a directive, clone a Rule,\
  \ ...)\n\n* **DELETE**: remove objects (delete a node, delete a parameter, ...)\n\
  \n* **POST**: update existing objects (update a directive, reload a group, ...)\n\
  \n\n## Parameters\n\n### General parameters\n\nSome parameters are available for\
  \ almost all API functions. They will be described in this section.\nThey must be\
  \ part of the query and can't be submitted in a JSON form.\n\n#### Available for\
  \ all requests\n\n<table>\n  <thead>\n    <tr>\n      <th style=\"width: 30%\">Field</th>\n\
  \      <th style=\"width: 10%\">Type</th>\n      <th style=\"width: 70%\">Description</th>\n\
  \    </tr>\n  </thead>\n  <tbody>\n    <tr>\n      <td class=\"code\">prettify</td>\n\
  \      <td><b>boolean</b><br><i>optional</i></td>\n      <td>\n        Determine\
  \ if the answer should be prettified (human friendly) or not. We recommend using\
  \ this for debugging purposes, but not for general script usage as this does add\
  \ some unnecessary load on the server side.\n        <p class=\"default-value\"\
  >Default value: <code>false</code></p>\n      </td>\n    </tr>\n  </tbody>\n</table>\n\
  \n\n#### Available for modification requests (PUT/POST/DELETE)\n\n<table>\n  <thead>\n\
  \    <tr>\n      <th style=\"width: 25%\">Field</th>\n      <th style=\"width: 12%\"\
  >Type</th>\n      <th style=\"width: 70%\">Description</th>\n    </tr>\n  </thead>\n\
  \  <tbody>\n    <tr>\n      <td class=\"code\">reason</td>\n      <td><b>string</b><br><i>optional</i>\
  \ or <i>required</i></td>\n      <td>\n        Set a message to explain the change.\
  \ If you set the reason messages to be mandatory in the web interface, failing to\
  \ supply this value will lead to an error.\n        <p class=\"default-value\">Default\
  \ value: <code>\"\"</code></p>\n      </td>\n    </tr>\n    <tr>\n      <td class=\"\
  code\">changeRequestName</td>\n      <td><b>string</b><br><i>optional</i></td>\n\
  \      <td>\n        Set the change request name, is used only if workflows are\
  \ enabled. The default value depends on the function called\n        <p class=\"\
  default-value\">Default value: <code>A default string for each function</code></p>\n\
  \      </td>\n    </tr>\n    <tr>\n      <td class=\"code\">changeRequestDescription</td>\n\
  \      <td><b>string</b><br><i>optional</i></td>\n      <td>\n        Set the change\
  \ request description, is used only if workflows are enabled.\n        <p class=\"\
  default-value\">Default value: <code>\"\"</code></p>\n      </td>\n    </tr>\n \
  \ </tbody>\n</table>\n\n\n### Passing parameters\n\nParameters to the API can be\
  \ sent:\n\n* As part of the URL for resource identification\n\n* As data for POST/PUT\
  \ requests\n\n  * Directly in JSON format\n\n  * As request arguments\n\n#### As\
  \ part of the URL for resource identification\n\nParameters in URLs are used to\
  \ indicate which resource you want to interact with. The function will not work\
  \ if this resource is missing.\n\n```bash\n# Get the Rule of ID \"id\"\ncurl -H\
  \ \"X-API-Token: yourToken\" https://rudder.example.com/rudder/api/latest/rules/id\n\
  ```\n\n\n\nCAUTION: To avoid surprising behavior, do not put a '/' at the end of\
  \ an URL: it would be interpreted as '/[empty string parameter]' and redirected\
  \ to '/index', likely not what you wanted to do.\n\n\n#### Sending data for POST/PUT\
  \ requests\n\n##### Directly in JSON format\n\nJSON format is the preferred way\
  \ to interact with Rudder API for creating or updating resources.\nYou'll also have\
  \ to set the *Content-Type* header to **application/json** (without it the JSON\
  \ content would be ignored).\nIn a `curl` `POST` request, that header can be provided\
  \ with the `-H` parameter:\n\n```bash\ncurl -X POST -H \"Content-Type: application/json\"\
  \ ...\n```\n\nThe supplied file must contain a valid JSON: strings need quotes,\
  \ booleans and integers don't, etc.\n\nThe (human readable) format is:\n\n```json\n\
  {\n  \"key1\": \"value1\",\n  \"key2\": false,\n  \"key3\": 42\n}\n```\n\n\nHere\
  \ is an example with inlined data:\n\n```bash\n# Update the Rule 'id' with a new\
  \ name, disabled, and setting it one directive\ncurl -X POST -H \"X-API-Token: yourToken\"\
  \ -H  \"Content-Type: application/json\"\nhttps://rudder.example.com/rudder/api/rules/latest/{id}\n\
  \  -d '{ \"displayName\": \"new name\", \"enabled\": false, \"directives\": \"directiveId\"\
  }'\n```\n\nYou can also pass a supply the JSON in a file:\n\n```bash\n# Update the\
  \ Rule 'id' with a new name, disabled, and setting it one directive\ncurl -X POST\
  \ -H \"X-API-Token: yourToken\" -H \"Content-Type: application/json\" https://rudder.example.com/rudder/api/rules/latest/{id}\
  \ -d @jsonParam\n```\n\nNote that the general parameters view in the previous chapter\
  \ cannot be passed in a JSON, and you will need to pass them a URL parameters if\
  \ you want them to be taken into account (you can't mix JSON and request parameters):\n\
  \n```bash\n# Update the Rule 'id' with a new name, disabled, and setting it one\
  \ directive with reason message \"Reason used\"\ncurl -X POST -H \"X-API-Token:\
  \ yourToken\" -H \"Content-Type: application/json\" \"https://rudder.example.com/rudder/api/rules/latest/{id}?reason=Reason\
  \ used\" -d @jsonParam -d \"reason=Reason ignored\"\n```\n\n##### Request parameters\n\
  \nIn some cases, when you have little, simple data to update, JSON can feel bloated.\
  \ In such cases, you can use\nrequest parameters. You will need to pass one parameter\
  \ for each data you want to change.\n\nParameters follow the following schema:\n\
  \n```\nkey=value\n```\n\nYou can pass parameters by two means:\n\n* As query parameters:\
  \ At the end of your url, put a **?** then your first parameter and then a **&**\
  \ before next parameters. In that case, parameters need to be https://en.wikipedia.org/wiki/Percent-encoding[URL\
  \ encoded]\n\n```bash\n# Update the Rule 'id' with a new name, disabled, and setting\
  \ it one directive\ncurl -X POST -H \"X-API-Token: yourToken\"  https://rudder.example.com/rudder/api/rules/latest/{id}?\"\
  displayName=my new name\"&\"enabled=false\"&\"directives=aDirectiveId\"\n```\n\n\
  * As request data: You can pass those parameters in the request data, they won't\
  \ figure in the URL, making it lighter to read, You can pass a file that contains\
  \ data.\n\n```bash\n# Update the Rule 'id' with a new name, disabled, and setting\
  \ it one directive (in file directive-info.json)\ncurl -X POST -H \"X-API-Token:\
  \ yourToken\"\nhttps://rudder.example.com/rudder/api/rules/latest/{id} -d \"displayName=my\
  \ new name\" -d \"enabled=false\" -d @directive-info.json\n```\n"
logo: "rudder.example.local-logo.png"
logoMediaType: "image/png"
tags:
- "developer_tools"
stubs: "rudder.example.local-stubs.json"
swagger: "rudder.example.local-swagger.json"
---