---
slug: "combell-com"
title: "Public Api"
provider: "combell.com"
description: "# Introduction\n\nThis API allows resellers to manage their resources\
  \ in a simple, programmatic way using HTTP requests.\n\n# Conventions\n\n## Requests\n\
  \nThe API supports different methods depending on the required action.\n\n| Method\t\
  | Description\n| ---\t\t| ---\n| GET\t\t| Retrieve resources in a collection or\
  \ get a single resource.<br/>Getters will never have any effect on the queried resources.\n\
  | POST\t\t| Create a new resource in a collection.\n| PUT\t\t| Update an existing\
  \ resource with its new representation.\n| DELETE\t| Delete an existing resource.\n\
  \n## HTTP status codes\n\nThe API will reply with different HTTP statuscodes:\n\n\
  | StatusCode\t\t\t\t| Description\n| ---\t\t\t\t\t\t| ---\n| 200 OK\t\t\t\t\t| The\
  \ requests was processed and you receive data as a result.\n| 201 CREATED\t\t\t\t\
  | The resource has been created. Either the Location header contains a link to the\
  \ created resource, or links are being returned in the response body. The applied\
  \ method will be indicated in the documentation.\n| 202 ACCEPTED\t\t\t\t| The request\
  \ has been validated and accepted. Because we need to do some background processing\
  \ prior to returning the result, we cannot send back a useful representation.\n\
  | 204 NOCONTENT\t\t\t\t| The request has been processed, but no details can be returned.\n\
  | 400 BADREQUEST\t\t\t| Your request is malformed.\n| 401 UNAUTHORIZED\t\t\t| You\
  \ are not authorized. Follow the instructions in the Authorization documentation.\n\
  | 403 FORBIDDEN\t\t\t\t| Access to the resource or operation is not allowed.\n|\
  \ 404 NOTFOUND\t\t\t\t| The resource cannot be found.\n| 410 GONE              \
  \    | The resource is permanently no longer available.\n| 429 TOOMANYREQUESTS\t\
  \t| The ratelimit has been exceeded. Please refer to the documentation on rate limiting\
  \ for more details.\n| 500 INTERNALSERVERERROR\t| An error occurred during the processing\
  \ of the request. The error is unexpected and most likely due to a bug in the api.\n\
  \nIn the event of a problem, the body of the response will usually contain an errorcode\
  \ and errormessage.\nIn rare cases additional details about the error are reported.\n\
  \nErrorcodes 400-499 are considered to be client errors and indicate that there\
  \ was an issue with the request.\nWe will not take any action besides monitoring.\
  \ \n\nErrorcodes 500-599 are considered to be server errors. The errors are monitored\
  \ AND action will be taken to resolve the error.\n\n## Formatting\n\nSnake casing\
  \ is applied on resources and query parameters.\nThe API is strictly returning JSON.\
  \ No other formats are supported.\n\nDatetimes are returned in ISO-8601 format.\n\
  \n## Pagination\n\nPagination is on by default on collections and is controlled\
  \ by specifying *skip* and *take* parameters.  \n**Skip** indicates the number of\
  \ results to skip and where to start the new take.  \n**Take** indicates the number\
  \ of records to return. The returned number of items can be smaller than the requested\
  \ take.\n\nPaged results will have headers with useful information regarding the\
  \ paging.\n\n| Header\t\t\t\t| Description\n| ---\t\t\t\t\t| ---\n| X-Paging-Skipped\t\
  \t| The number of results that have been skipped.\n| X-Paging-Take\t\t\t| The number\
  \ of items in the current take. The number might differ from the requested take.\
  \ It represents the actual number of items returned in the response.\n| X-Paging-TotalResults\
  \ | The total number of results regardless of paging.\n\n## Rate limiting\n\nThe\
  \ number of requests per interval is limited. Detailed information on the rate limiting\
  \ can be found in specific headers which will be sent on each request.\n\n| Header\t\
  \t\t\t| Description\n| ---\t\t\t\t\t| ---\n| X-RateLimit-Limit\t\t| The number of\
  \ requests that can be made in a specific time interval.\n| X-RateLimit-Usage\t\t\
  | The number of requests already made in the current time interval.\n| X-RateLimit-Remaining\t\
  | The number of requests remaining until the reset.\n| X-RateLimit-Reset\t\t| The\
  \ number of seconds until the reset.<br />After the reset you are allowed to make\
  \ as many requests as specified by the X-RateLimit-Limit header.\n| Retry-After\t\
  \t\t| The number of seconds you have to wait until you can make new requests.<br\
  \ />This header is only present when the rate limit has been reached. It is identical\
  \ to X-RateLimit-Reset.\n\nWhen the ratelimit has been reached, all requests will\
  \ return with a HTTP statuscode 429 and ReasonPhrase '*Too many requests, retry\
  \ later.*'.\n\n# Authentication\n\nThe Api uses HMAC authentication.  \nHash-based\
  \ message authentication code (HMAC) is a mechanism for calculating a message authentication\
  \ code involving a hash function in combination with a secret key.  \nBoth the integrity\
  \ and the authenticity of the message are verified this way.\n\n## Steps to generate\
  \ the HMAC\n\n1. Get your api key and secret from your controlpanel.  \nIt is absolutely\
  \ vital that the secret is never exposed. Once the secret is out, anyone would be\
  \ able to generate hmacs to impersonate you.  \nIn case your secret is compromised,\
  \ you can generate a new api key and secret on your controlpanel.\n2. Construct\
  \ the input value for generating the hmac.  \nConcatenate:apikey, request method,\
  \ path and querystring information, unix timestamp, nonce and content.\n\n|\t\t\t\
  \t\t\t\t\t\t\t| Description\n| ---\t\t\t\t\t\t\t\t\t| ---\n| apikey\t\t\t\t\t\t\t\
  \t| The key that is linked to your user.\n| request method\t\t\t\t\t\t| lowercased\
  \ (eg: get, post, delete,...)\n| path and querystring information\t\t| urlencoding\
  \ of the lowercased relative path and querystring.<br />The path **MUST start with\
  \ the api version (/v2)**.<br />The hexadecimal codes (percent encoding) MUST be\
  \ uppercased.\n| unix timestamp\t\t\t\t\t\t| the unix timestamp in **seconds**.\n\
  | nonce\t\t\t\t\t\t\t\t\t| a\tunique string for each request. It should be a random\
  \ string, not related to the request. The nonce (in combination with the unix timestamp)\
  \ protects you from replay attacks in case anyone was able to intercept a request.\n\
  | content\t\t\t\t\t\t\t\t| When the request body is not empty, this should be the\
  \ Base64 encoded Md5 hash of the request body.<br />An empty body should not be\
  \ encoded.\n\n3. Hash the concatenated string using your api secret and the SHA-256\
  \ algorithm.\n4. Base64 encode the result of the hash function. This is the hmac\
  \ signature you will need to send an authorized request.\n\n## Sending an authorized\
  \ request\n\nAn authorized request can be made by sending the generated HMAC in\
  \ the authorization header.  \nA correct authorizationheader uses the hmac authorization\
  \ scheme and a correctly formatted authorization parameter.\n\nCreate the authorization\
  \ parameter by concatenating:\n  * apikey\n  * colon ':'\n  * generated HMAC signature\
  \ (see above)\n  * colon ':'\n  * nonce (the one used to generate the signature)\n\
  \  * colon ':'\n  * unix timestamp (the one used to generate the signature)\n\n\
  A sample (illustrated):\n\n* The first line is the string you create to feed to\
  \ the hashing algorithm.\n* The second line is the authorization header that should\
  \ be sent in the request.\n\n![hmac authorization header illustrated](/v2/images/authentication_illustration.jpg\
  \ \"authorization header illustrated\")\n\n## IP whitelisting\n\nAccess is by default\
  \ restricted for all IP addresses. You need to explicitly whitelist an IP or an\
  \ IP range in your controlpanel.\n\n# Versioning\n\nBecause of breaking contract\
  \ changes compared to v1, we released v2 of the API.  \nV1 will still be available,\
  \ but you are strongly encouraged to migrate to the latest version.  \nNew features\
  \ will only be available on v2.\n\n# Policy\n\n### Fair use policy\n\nPlease respect\
  \ the rate limits and do not use the api for any purposes of abuse.  \nAll requests\
  \ are being monitored and logged.  \nIntentional abuse might result in api key revocation.\n\
  \n# Errors\n\nThe API attempts to return appropriate HTTP status codes for every\
  \ request.  \nWhen the status code indicates failure, the API will also provide\
  \ an error message in most cases.\n\nAn error message contains a machine-parseable\
  \ error code accompanied by a descriptive error text.  \nThe text for an error message\
  \ might change over time, but codes will stay the same.\n\n[An overview of error\
  \ codes can be found here](/v2/documentation/errorcodes).\n\n# Change log\n\n[An\
  \ overview of new changes can be found here](/v2/documentation/changelog).\n\n#\
  \ Provisioning information\n\n## Terminology\n\n| Term\t\t\t| Definition\t\t\t\t\
  \t\t\t\t\t\t\t\t\t\t\t\t|\n| ---\t\t\t| ---\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\t\
  |\n| Servicepack\t| Defines a set of assets that belong together. An example is\
  \ a hosting package which offers Linux hosting, a domain name, a couple of mailboxes\
  \ and databases.<br/>It also limits the size of individual assets within the same\
  \ account. |\n| Account\t\t| Represents an instance of the servicepack. It contains\
  \ one or more assets. The number and size of assets is defined by the servicepack.\
  \ |\n| Asset\t\t\t| A manageable service. For example: a mysql database, a linux\
  \ hosting, a mailbox,...<br/>Some assets are created at the moment when the account\
  \ is created. Other assets can be created afterwards.\n\t\n## Common provisioning\
  \ scenario\n\n**Provisioning of an account with Linux hosting with one MySql database**\n\
  \n*Without a pre-existing account:*\n\n1. Create a new account.<br/>Perform a POST\
  \ on the accounts route and provide the desired servicepack id and identifier (domain\
  \ name).\n2. Read the Location header from the response and perform a GET of the\
  \ provided resource (a provisioning job).\n3. When the response returns 200(OK),\
  \ you should repeat the GET operation after a certain interval (Repeat this step).<br/>\n\
  When the response returns 201(Created), you should read the response body. This\
  \ will contain links to the created resources.<br/>\nThis will usually hold only\
  \ one link, but to be futureproof, this has been designed to return a collection.\n\
  4. The created resource will point to an account. You now know the account's Id\
  \ and can continue with the provisioning of a MySql database on this account.\n\
  5. Perform a POST on the mysqldatabases route and provide the account id along with\
  \ other requested information.\n6. Read the Location header from the response and\
  \ perform a GET of the provided resource (a provisioning job).\n7. When the response\
  \ returns 200(OK), you should repeat the GET operation after a certain interval\
  \ (Repeat this step).<br/>\nWhen the response returns 201(Created), you should read\
  \ the response body. This will contain links to the created resources.<br/>\nThis\
  \ will usually hold only one link, but to be futureproof, this has been designed\
  \ to return a collection.\n8. The created resource will point to a MySql database\
  \ resource.\n\n## SSL certificate requests\n\n**Requesting an SSL certificate causes\
  \ the purchase of a paying product.**\n\n1. A certificate is created by adding an\
  \ ssl certificate request.\n2. Upon statuscode 201 you should query for certificate\
  \ completion on the resource provided in the location response header.\n3. The resource\
  \ request can respond with different statuscodes:\n<ul>\n    <li>200: the certificate\
  \ request is ongoing.<br/>\nCheck the validations collection for validation values\
  \ that are not auto_validated. Those should be set by you system.<br/>\nCall verify\
  \ domain validations once all validation values are in place. It might take some\
  \ time for verification to take place. It is not necessary to call this method more\
  \ than once.</li>\n    <li>303: the certificate request is complete; there is no\
  \ more certificate request resource available. Check the location header value to\
  \ retrieve the representation of the resulting ssl certificate.</li>\n    <li>410:\
  \ the certificate request does not exist anymore, there is no certificate created\
  \ as a result of the request.</li>\n</ul>"
logo: "combell.com-logo.png"
logoMediaType: "image/png"
tags:
- "hosting"
stubs: "combell.com-stubs.json"
swagger: "combell.com-swagger.json"
---