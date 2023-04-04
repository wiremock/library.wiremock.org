---
slug: "pdfgeneratorapi-com"
title: "PDF Generator API"
provider: "pdfgeneratorapi.com"
description: "# Introduction\nPDF Generator API allows you easily generate transactional\
  \ PDF documents and reduce the development and support costs by enabling your users\
  \ to create and manage their document templates using a browser-based drag-and-drop\
  \ document editor.\n\nThe PDF Generator API features a web API architecture, allowing\
  \ you to code in the language of your choice. This API supports the JSON media type,\
  \ and uses UTF-8 character encoding.\n\nYou can find our previous API documentation\
  \ page with references to Simple and Signature authentication [here](https://docs.pdfgeneratorapi.com/legacy).\n\
  \n## Base URL\nThe base URL for all the API endpoints is `https://us1.pdfgeneratorapi.com/api/v3`\n\
  \nFor example\n* `https://us1.pdfgeneratorapi.com/api/v3/templates`\n* `https://us1.pdfgeneratorapi.com/api/v3/workspaces`\n\
  * `https://us1.pdfgeneratorapi.com/api/v3/templates/123123`\n\n## Editor\nPDF Generator\
  \ API comes with a powerful drag & drop editor that allows to create any kind of\
  \ document templates, from barcode labels to invoices, quotes and reports. You can\
  \ find tutorials and videos from our [Support Portal](https://support.pdfgeneratorapi.com).\n\
  * [Component specification](https://support.pdfgeneratorapi.com/en/category/components-1ffseaj/)\n\
  * [Expression Language documentation](https://support.pdfgeneratorapi.com/en/category/expression-language-q203pa/)\n\
  * [Frequently asked questions and answers](https://support.pdfgeneratorapi.com/en/category/qanda-1ov519d/)\n\
  \n## Definitions\n\n### Organization\nOrganization is a group of workspaces owned\
  \ by your account.\n\n### Workspace\nWorkspace contains templates. Each workspace\
  \ has access to their own templates and organization default templates.\n\n### Master\
  \ Workspace\nMaster Workspace is the main/default workspace of your Organization.\
  \ The Master Workspace identifier is the email you signed up with.\n\n### Default\
  \ Template\nDefault template is a template that is available for all workspaces\
  \ by default. You can set the template access type under Page Setup. If template\
  \ has \"Organization\" access then your users can use them from the \"New\" menu\
  \ in the Editor.\n\n### Data Field\nData Field is a placeholder for the specific\
  \ data in your JSON data set. In this example JSON you can access the buyer name\
  \ using Data Field `{paymentDetails::buyerName}`. The separator between depth levels\
  \ is :: (two colons). When designing the template you don’t have to know every Data\
  \ Field, our editor automatically extracts all the available fields from your data\
  \ set and provides an easy way to insert them into the template.\n```\n{\n    \"\
  documentNumber\": 1,\n    \"paymentDetails\": {\n        \"method\": \"Credit Card\"\
  ,\n        \"buyerName\": \"John Smith\"\n    },\n    \"items\": [\n        {\n\
  \            \"id\": 1,\n            \"name\": \"Item one\"\n        }\n    ]\n\
  }\n```\n\n*  *  *  *  *\n# Authentication\nThe PDF Generator API uses __JSON Web\
  \ Tokens (JWT)__ to authenticate all API requests. These tokens offer a method to\
  \ establish secure server-to-server authentication by transferring a compact JSON\
  \ object with a signed payload of your account’s API Key and Secret.\nWhen authenticating\
  \ to the PDF Generator API, a JWT should be generated uniquely by a __server-side\
  \ application__ and included as a __Bearer Token__ in the header of each request.\n\
  \n## Legacy Simple and Signature authentication\nYou can find our legacy documentation\
  \ for Simple and Signature authentication [here](https://docs.pdfgeneratorapi.com/legacy).\n\
  \n<SecurityDefinitions />\n\n## Accessing your API Key and Secret\nYou can find\
  \ your __API Key__ and __API Secret__ from the __Account Settings__ page after you\
  \ login to PDF Generator API [here](https://pdfgeneratorapi.com/login).\n\n## Creating\
  \ a JWT\nJSON Web Tokens are composed of three sections: a header, a payload (containing\
  \ a claim set), and a signature. The header and payload are JSON objects, which\
  \ are serialized to UTF-8 bytes, then encoded using base64url encoding.\n\nThe JWT's\
  \ header, payload, and signature are concatenated with periods (.). As a result,\
  \ a JWT typically takes the following form:\n```\n{Base64url encoded header}.{Base64url\
  \ encoded payload}.{Base64url encoded signature}\n```\n\nWe recommend and support\
  \ libraries provided on [jwt.io](https://jwt.io/). While other libraries can create\
  \ JWT, these recommended libraries are the most robust.\n\n### Header\nProperty\
  \ `alg` defines which signing algorithm is being used. PDF Generator API users HS256.\n\
  Property `typ` defines the type of token and it is always JWT.\n```\n{\n  \"alg\"\
  : \"HS256\",\n  \"typ\": \"JWT\"\n}\n```\n\n### Payload\nThe second part of the\
  \ token is the payload, which contains the claims  or the pieces of information\
  \ being passed about the user and any metadata required.\nIt is mandatory to specify\
  \ the following claims:\n* issuer (`iss`): Your API key\n* subject (`sub`): Workspace\
  \ identifier\n* expiration time (`exp`): Timestamp (unix epoch time) until the token\
  \ is valid. It is highly recommended to set the exp timestamp for a short period,\
  \ i.e. a matter of seconds. This way, if a token is intercepted or shared, the token\
  \ will only be valid for a short period of time.\n\n```\n{\n  \"iss\": \"ad54aaff89ffdfeff178bb8a8f359b29fcb20edb56250b9f584aa2cb0162ed4a\"\
  ,\n  \"sub\": \"demo.example@actualreports.com\",\n  \"exp\": 1586112639\n}\n```\n\
  \n### Signature\nTo create the signature part you have to take the encoded header,\
  \ the encoded payload, a secret, the algorithm specified in the header, and sign\
  \ that. The signature is used to verify the message wasn't changed along the way,\
  \ and, in the case of tokens signed with a private key, it can also verify that\
  \ the sender of the JWT is who it says it is.\n```\nHMACSHA256(\n    base64UrlEncode(header)\
  \ + \".\" +\n    base64UrlEncode(payload),\n    API_SECRET)\n```\n\n### Putting\
  \ all together\nThe output is three Base64-URL strings separated by dots. The following\
  \ shows a JWT that has the previous header and payload encoded, and it is signed\
  \ with a secret.\n```\neyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJhZDU0YWFmZjg5ZmZkZmVmZjE3OGJiOGE4ZjM1OWIyOWZjYjIwZWRiNTYyNTBiOWY1ODRhYTJjYjAxNjJlZDRhIiwic3ViIjoiZGVtby5leGFtcGxlQGFjdHVhbHJlcG9ydHMuY29tIn0.SxO-H7UYYYsclS8RGWO1qf0z1cB1m73wF9FLl9RCc1Q\n\
  \n// Base64 encoded header: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9\n// Base64 encoded\
  \ payload: eyJpc3MiOiJhZDU0YWFmZjg5ZmZkZmVmZjE3OGJiOGE4ZjM1OWIyOWZjYjIwZWRiNTYyNTBiOWY1ODRhYTJjYjAxNjJlZDRhIiwic3ViIjoiZGVtby5leGFtcGxlQGFjdHVhbHJlcG9ydHMuY29tIn0\n\
  // Signature: SxO-H7UYYYsclS8RGWO1qf0z1cB1m73wF9FLl9RCc1Q\n```\n\n## Testing with\
  \ JWTs\nYou can create a temporary token in [Account Settings](https://pdfgeneratorapi.com/account/organization)\
  \ page after you login to PDF Generator API. The generated token uses your email\
  \ address as the subject (`sub`) value and is valid for __5 minutes__.\nYou can\
  \ also use [jwt.io](https://jwt.io/) to generate test tokens for your API calls.\
  \ These test tokens should never be used in production applications.\n*  *  *  *\
  \  *\n\n# Libraries and SDKs\n## Postman Collection\nWe have created a [Postman](https://www.postman.com)\
  \ Collection so you can easily test all the API endpoints wihtout developing and\
  \ code. You can download the collection [here](https://app.getpostman.com/run-collection/329f09618ec8a957dbc4)\
  \ or just click the button below.\n\n[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/329f09618ec8a957dbc4)\n\
  \n## Client Libraries\nAll our Client Libraries are auto-generated using [OpenAPI\
  \ Generator](https://openapi-generator.tech/) which uses the OpenAPI v3 specification\
  \ to automatically generate a client library in specific programming language.\n\
  \n* [PHP Client](https://github.com/pdfgeneratorapi/php-client)\n* [Java Client](https://github.com/pdfgeneratorapi/java-client)\n\
  * [Ruby Client](https://github.com/pdfgeneratorapi/ruby-client)\n* [Python Client](https://github.com/pdfgeneratorapi/python-client)\n\
  * [Javascript Client](https://github.com/pdfgeneratorapi/javascript-client)\n\n\
  We have validated the generated libraries, but let us know if you find any anomalies\
  \ in the client code.\n*  *  *  *  *\n\n# Error codes\n\n| Code   | Description\
  \                    |\n|--------|--------------------------------|\n| 401    |\
  \ Unauthorized                   |\n| 403    | Forbidden                      |\n\
  | 404    | Not Found                      |\n| 422    | Unprocessable Entity   \
  \        |\n| 500    | Internal Server Error          |\n\n## 401 - Unauthorized\n\
  | Description                                                             |\n|-------------------------------------------------------------------------|\n\
  | Authentication failed: request expired                                  |\n| Authentication\
  \ failed: workspace missing                                |\n| Authentication failed:\
  \ key missing                                      |\n| Authentication failed: property\
  \ 'iss' (issuer) missing in JWT           |\n| Authentication failed: property 'sub'\
  \ (subject) missing in JWT          |\n| Authentication failed: property 'exp' (expiration\
  \ time) missing in JWT  |\n| Authentication failed: incorrect signature        \
  \                      |\n\n## 403 - Forbidden\n| Description                  \
  \                                           |\n|-------------------------------------------------------------------------|\n\
  | Your account has exceeded the monthly document generation limit.        |\n| Access\
  \ not granted: You cannot delete master workspace via API          |\n| Access not\
  \ granted: Template is not accessible by this organization     |\n| Your session\
  \ has expired, please close and reopen the editor.           |\n\n## 404 Entity\
  \ not found\n| Description                                                     \
  \        |\n|-------------------------------------------------------------------------|\n\
  | Entity not found                                                        |\n| Resource\
  \ not found                                                      |\n| None of the\
  \ templates is available for the workspace.                   |\n\n## 422 Unprocessable\
  \ Entity\n| Description                                                        \
  \     |\n|-------------------------------------------------------------------------|\n\
  | Unable to parse JSON, please check formatting                           |\n| Required\
  \ parameter missing                                              |\n| Required parameter\
  \ missing: template definition not defined             |\n| Required parameter missing:\
  \ template not defined                        |\n"
logo: "pdfgeneratorapi.com-logo.svg"
logoMediaType: "image/svg+xml"
tags:
- "text"
stubs: "pdfgeneratorapi.com-stubs.json"
swagger: "pdfgeneratorapi.com-swagger.json"
---