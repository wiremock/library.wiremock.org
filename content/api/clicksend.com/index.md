---
slug: "clicksend-com"
title: "ClickSend REST API v3"
provider: "clicksend.com"
description: "This is the official API documentation for ClickSend.com\n\nBelow you\
  \ will find a current list of the available methods for clicksend.\n\n**NOTE**:\
  \ You will need to create a free account to use the API.\n\nYou can\n[**Register\
  \ Here**](https://dashboard.clicksend.com/#/signup/step1/).\n\n# API URL\n\nThe\
  \ API should always be accessed over SSL.\n\nBase URL: `https://rest.clicksend.com/v3/`\n\
  \n# Authentication\n\nBasic HTTP authentication should be used in the header.\n\n\
  **Either:**\n\n`username`: Your API username\n\n`password`: Your API key\n\n```\n\
  You can get your API credentials by clicking 'API Credentials' on the top right\
  \ of the dashboard.\n```\n\n**OR**\n\n`username`: Your account username\n\n`password`:\
  \ Your account password\n\n```\nThese are the same credentials that you use to login\
  \ to the dashboard.\n```\n\n### Authorization Header\n\nThe Authorization header\
  \ is constructed as follows:\n1. Username and password are combined into a string\
  \ `username:password`\n1. The resulting string is then encoded using Base64 encoding\n\
  1. The authorization method and a space i.e. \"Basic \" is then put before the encoded\
  \ string.\n\nFor example, if the user uses `Aladdin` as the username and `open sesame`\
  \ as the password then the header is formed as follows:\n\n`Authorization: Basic\
  \ QWxhZGRpbjpvcGVuIHNlc2FtZQ==`\n\n### PHP Authentication Header Example (using\
  \ cURL)\n\n`curl_setopt($ch, CURLOPT_HTTPHEADER, ['Authorization: Basic ' . base64_encode(\"\
  $username:$password\")]);`\n\n# Verbs\n\nThe API uses restful verbs.\n\n| Verb |\
  \ Description |\n|---|---|\n| `GET` | Select one or more items. Success returns\
  \ `200` status code. |\n| `POST` | Create a new item. Success returns `200` status\
  \ code. |\n| `PUT` | Update an item. Success returns `200` status code. |\n| `DELETE`\
  \ | Delete an item. Success returns `200` status code. |\n\n# Status Codes\n\nThe\
  \ API will respond with one of the following HTTP status codes.\n\n| Code | Response\
  \ | Description |\n|---|---|---|\n| `200` | `SUCCESS` | Request completed successfully.\
  \ |\n| `400` | `BAD_REQUEST` | The request was invalid or cannot be otherwise served.\
  \ An accompanying error message will explain further. |\n| `401` | `UNAUTHORIZED`\
  \ | Authentication credentials were missing or incorrect. |\n| `403` | `FORBIDDEN`\
  \ | The request is understood, but it has been refused or access is not allowed.\
  \ An accompanying error message will explain why. |\n| `404` | `NOT_FOUND` | The\
  \ URI requested is invalid or the resource requested does not exists. |\n| `405`\
  \ | `NOT_FOUND` | Method doesn't exist or is not allowed. |\n| `429` | `TOO_MANY_REQUESTS`\
  \ | Rate Limit Exceeded. Returned when a request cannot be served due to the application’\
  s rate limit having been exhausted for the resource. See Rate Limiting. |\n| `500`\
  \ | `INTERNAL_SERVER_ERROR` | Something is broken |\n\n# Application Status Codes\n\
  \nThe following status codes can be returned in addition to the HTTP status code.\
  \ For example, when using the Send SMS endpoint:\n\n| Response | Description |\n\
  |---|---|\n| `SUCCESS` | Message added to queue OK. Use delivery reports to get\
  \ an update on the delivery status.|\n| `MISSING_CREDENTIALS` | Not enough information\
  \ has been supplied for authentication. Please ensure that your Username and Unique\
  \ Key are supplied in your request.|\n| `ACCOUNT_NOT_ACTIVATED` | Your account has\
  \ not been activated.|\n| `INVALID_RECIPIENT` | The destination mobile number is\
  \ invalid.|\n| `THROTTLED` | Identical message body recently sent to the same recipient.\
  \ Please try again in a few seconds.|\n| `INVALID_SENDER_ID` | Invalid Sender ID.\
  \ Please ensure Sender ID is no longer than 11 characters (if alphanumeric), and\
  \ contains no spaces.|\n| `INSUFFICIENT_CREDIT` | You have reached the end of your\
  \ message credits. You will need to purchase more message credits.|\n| `INVALID_CREDENTIALS`\
  \ | Your Username or Unique Key is incorrect.|\n| `ALREADY_EXISTS` | The resource\
  \ you're trying to add already exists.|\n| `EMPTY_MESSAGE` | Message is empty.|\n\
  | `TOO_MANY_RECIPIENTS` | Too many recipients.|\n| `MISSING_REQUIRED_FIELDS` | Some\
  \ required fields are missing.|\n| `INVALID_SCHEDULE` | The schedule specified is\
  \ invalid. Use a unix timestamp e.g. 1429170372.|\n| `NOT_ENOUGH_PERMISSION_TO_LIST_ID`\
  \ | Don't have enough privilege to access or send to a list_id.|\n| `INTERNAL_ERROR`\
  \ | Internal error.|\n| `INVALID_LANG` | An invalid language option has been provided.|\n\
  | `INVALID_VOICE` | An invalid voice (gender) option has been provided.|\n| `SUBJECT_REQUIRED`\
  \ | Usually happens when MMS Subject is empty.|\n| `INVALID_MEDIA_FILE` | Usually\
  \ MMS media file is invalid file.|\n| `SOMETHING_IS_WRONG` | Generic Error happened.|\n\
  \n# Required Headers\n\nYou'll need to send some headers when making API calls.\n\
  \n| Header | Value |\n|---|---|\n| `Content-type` | `application/json` |\n\n# Pagination\n\
  \nSome methods are paginated. By default, 1 page of 15 items will be returned. You\
  \ can set the pagination parameters by adding `?page={page}&limit={limit}` to the\
  \ URL.\n\n## Request\n\n| Parameter | Type | Default | Value |\n|---|---|---|---|\n\
  | `page` | integer | `1` | The page number to return in the response. |\n| `limit`\
  \ | integer | `15` | The number of results per page. Min 15, Max 100. |\n\n## Response\n\
  \n| Attribute | Type | Value |\n|---|---|---|---|\n| `total` | integer | Total number\
  \ of results available. |\n| `per_page` | integer | Number of results returned per\
  \ page. |\n| `current_page` | integer | Current page number. |\n| `last_page` |\
  \ integer | Last page number. |\n| `next_page_url` | string | A URL of the next\
  \ page. `null` if not available.|\n| `prev_page_url` | string | A URL of the previous\
  \ page. `null` if not available.|\n| `from` | integer | Number of the first result\
  \ in current page. |\n| `to` | integer | Number of the last result in current page.\
  \ |\n\n# Searching and Sorting\n\nMost GET endpoints allow searching and sorting.\
  \ Searches are **not** case-sensitive.\n\n## Search\n\nTo perform a search, add\
  \ `q` as a query parameter. For example:\n\n`/subaccounts?q=field:value,field2:value`\n\
  \n## Order\n\nTo perform a sort, add `order_by` as a query parameter. For example:\n\
  \n`/subaccounts?order_by=field:desc/asc`\n\n## AND / OR\n\nBy default, it will search\
  \ using the `AND` operator. This can be set using `operator` as a query parameter.\
  \ For example:\n\n`/subaccounts?q=field:value&operator=OR`\n\n**Options:**\n\n-\
  \ `AN` - returns results matching **all** query fields specified\n\n- `OR` - returns\
  \ results matching **any** query fields specified\n\n## Example\n\n`/subaccounts?q=first_name:john,last_name:smith&order_by=subaccount_id:asc&operator=AND`\n\
  \n# CORS\n\nWhen creating your API app, specify the JavaScript (CORS) origins you'll\
  \ be using. We use these origins to return the headers needed for CORS.\n\n# Date\
  \ and Time\n\nAll date/timestamps will be returned in Unix time (also known as POSIX\
  \ time or erroneously as Epoch time) with no leap seconds.\n\nFor example: `1435255816`\n\
  \n```\n(ISO 8601: 2015-06-25T18:10:16Z)\n```\n\nMore information: [Wikipedia: Unix\
  \ time](https://en.wikipedia.org/wiki/Unix_time).\n\nThere is ony one Unix time\
  \ and it is created by using the UTC/GMT time zone. This means you might have convert\
  \ time zones to calculate timestamps. Most programming language have libraries to\
  \ help you converting time zones.\n\n**The current Unix time can be found here:**\
  \ [Epoch Converter](http://www.epochconverter.com)\n\n# Testing\n\n## Test Credentials\n\
  \nThese API credentials can be used to test specific scenarios.\n\n**Note:** you\
  \ will need to create a free account to test other scenarios. Refer to introduction.\n\
  \n| API Username | API Key | Description |\n|---|---|---|---|\n| `nocredit` | `D83DED51-9E35-4D42-9BB9-0E34B7CA85AE`\
  \ | This account has no credit. |\n| `notactive` | `D83DED51-9E35-4D42-9BB9-0E34B7CA85AE`\
  \ | This account is not active. |\n| `banned` | `D83DED51-9E35-4D42-9BB9-0E34B7CA85AE`\
  \ | This account is banned. |\n\n## Test SMS/MMS Numbers\n\nThe following numbers\
  \ can be used when testing. No messages will be sent, and your account won't be\
  \ charged. A success response will be returned.\n\n- `+61411111111`\n\n- `+61422222222`\n\
  \n- `+61433333333`\n\n- `+61444444444`\n\n- `+14055555555`\n\n- `+14055555666`\n\
  \n- `+447777777777`\n\n- `+8615555555555`\n\n## Test Voice Numbers\n\nThe following\
  \ numbers can be used when testing. No messages will be sent, and your account won't\
  \ be charged. A success response will be returned.\n\n- `+61411111111`\n\n- `+61422222222`\n\
  \n- `+61433333333`\n\n- `+61444444444`\n\n- `+14055555555`\n\n- `+14055555666`\n\
  \n- `+447777777777`\n\n- `+8615555555555`\n\n## Test Fax Numbers\n\nThe following\
  \ numbers can be used when testing. No messages will be sent, and your account won't\
  \ be charged. A success response will be returned.\n\n- `+61261111111`\n\n- `+61262222222`\n\
  \n- `+61263333333`\n\n## Test Email Addresses\n\nThe following email addresses can\
  \ be used when testing. No messages will be sent, and your account won't be charged.\
  \ A success response will be returned.\n\n- `test1@test.com`\n\n- `test2@test.com`\n\
  \n- `test3@test.com`\n\n## Test Post Letter Addresses\n\nThe following Postal Codes\
  \ (address_postal_code) can be used when testing. No messages will be sent when\
  \ using these post codes, and your account won't be charged. A success response\
  \ will be returned.\n\n- `11111`\n\n- `22222`\n\n- `33333`"
logo: "clicksend.com-logo.png"
logoMediaType: "image/png"
tags:
- "email"
stubs: "clicksend.com-stubs.json"
swagger: "clicksend.com-swagger.json"
---