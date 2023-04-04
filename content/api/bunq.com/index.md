---
slug: "bunq-com"
title: "bunq API"
provider: "bunq.com"
description: "***UPDATE:*** *We have released a [beta version of the new bunq API\
  \ documentation.](https://beta.doc.bunq.com)*\n\n***NOTICE:***  *We have updated\
  \ the sandbox base url to `https://public-api.sandbox.bunq.com/v1/`. Please update\
  \ your applications accordingly. Check here: <https://github.com/bunq/sdk_php/issues/149>\
  \ for more info.*\n\n***PSD2 NOTICE:*** *The second Payment Services Directive (PSD2)\
  \ may affect your current or planned usage of our public API, as some of the API\
  \ services are now subject to a permit. Please be aware that using our public API\
  \ without the required PSD2 permit is at your own risk and take notice of our updated\
  \ API Terms and Conditions on <https://www.bunq.com> for more information.*\n\n\
  # <span id=\"topic-introduction\">Introduction</span>\n\nWelcome to bunq!\n\n- The\
  \ bunq API is organised around REST. JSON will be returned in almost all responses\
  \ from the API, including errors but excluding binary (image) files.\n- Please configure\
  \ your implementation to send its API requests to `https://public-api.sandbox.bunq.com/v1/`\n\
  - There is a version of the [Android app](https://appstore.bunq.com/api/android/builds/bunq-android-sandbox-master.apk)\
  \ that connects to the bunq Sandbox environment. To create accounts for the Sandbox\
  \ app, please follow the steps in the [Android Emulator](#android-emulator) section.\n\
  \n## <span id=\"topic-introduction-get-started\">Getting started</span>\n\nBefore\
  \ you start sending API requests, you need to get an API key and activate it. API\
  \ activation happens when you install the API key and link your IP address and device\
  \ to it *(create an API context)*. The steps below will guide you through what you\
  \ need to do to start sending custom API requests.\n\nHere is an overview of what\
  \ you can use to get started with the bunq API: \n1. **Create an API key.** You\
  \ can do it either in our [developer portal](https://developer.bunq.com) or in the\
  \ bunq app *(Profile → Security & Settings → Developers → API keys)*. If you want\
  \ to test our sandbox first, our [bunq Developer ](https://developer.bunq.com)is\
  \ the best place to start.\n2. **Register a device.** A device can be a phone (private),\
  \ computer or a server (public). You can register a new device by using the `POST\
  \ /installation` and `POST /device-server` calls. This will activate your API key.\
  \ You only need to do this once.\n3. **Open a session.** Sessions are temporary\
  \ and expire after the auto-logout time set for the user account. It can be changed\
  \ by the account owner in the bunq app.\n4. **Make your first call!**\n\n![bunq_API_context](https://www.bunq.com/assets/media/developer/API-context.jpg)\n\
  \n## <span id=\"topic-introduction-versioning\">Versioning</span>\n\nDevelopments\
  \ in the financial sector, changing regulatory regimes and new feature requests\
  \ require us to be flexible. This means we can iterate quickly to improve the API\
  \ and related tooling. Therefore, we have chosen not to attach any version numbers\
  \ to the changes just yet. \n\nWe will inform you in a timely manner of any important\
  \ changes we make before they are deployed on together.bunq.com. You can also [subscribe\
  \ to our API newsletter](https://bunq.us8.list-manage.com/subscribe?u=c00d0d6daea4e1cf7c863d52e&id=b08680cdc7)\
  \ to make sure you don't miss any important updates. \n\n# <span id=\"topic-oauth\"\
  >OAuth</span>\n\n## <span id=\"topic-oauth-what-is-oauth\">What is OAuth?</span>\n\
  \n[OAuth 2.0](https://www.oauth.com/oauth2-servers/getting-ready/) is a protocol\
  \ that will let your app connect to bunq users in a safe and easy way. Please be\
  \ aware that if you will gain access to the account information of other bunq users\
  \ or initiate a payment for them, [you may require a PSD2 permit](https://beta.doc.bunq.com/other/faq#can-we-use-the-bunq-api-to-offer-services-to-third-parties).\n\
  \n## <span id=\"topic-oauth-get-started-with-oauth-for-bunq\">Get started with OAuth\
  \ for bunq</span>\n\nTo initiate authorization into the bunq user accounts, you\
  \ need to create an OAuth Client and register at least 1 redirect URL for it. \n\
  \nYou can have 1 OAuth Client at a time. Reuse your OAuth credentials for every\
  \ authorization request. \n\nThe list of steps below will help you to get started:\n\
  \n1. Register an OAuth Client by creating an app in [bunq Developer](https://developer.bunq.com/portal)_._\n\
  2. Add one or more Redirect URLs.\n3. Get your `client_id` and `secret` from your\
  \ app information tab in [bunq Developer](https://developer.bunq.com/portal).\n\
  4. Redirect your users to the [OAuth authorization request URL](#oauth-authorization-request).\n\
  5. If the user accepts the authorization request, they will be redirected to the\
  \ previously specified `redirect_uri` with an authorization `code` parameter.\n\
  6. Use the [token endpoint](#oauth-token-exchange) to exchange the authorization\
  \ `code` for an `access_token`.\n7. Use the `access_token` as a normal API Key.\
  \ Open a session or use [our SDKs](https://github.com/bunq) to get started.\n\n\
  You can set up an OAuth Client and add redirect URLs to it using the dedicated endpoints\
  \ too. Follow the flow below to do it programmatically.\n\nℹ️ As a PSD2 user, you\
  \ cannot log in to the bunq app. You need to follow the flow below to register an\
  \ OAuth Client for your application.\n\n![bunq_OAuth_credentials](https://www.bunq.com/assets/media/developer/create-oauth-credentials.jpg)\n\
  \n## <span id=\"topic-oauth-what-can-my-apps-do-with-oauth\">What can my apps do\
  \ with OAuth?</span>\n\nWe decided to launch OAuth with a default permission that\
  \ allows you to perform the following actions:\n- read and create Monetary Accounts;\n\
  - read Payments & Transactions;\n- create Payments between Monetary Accounts of\
  \ the same user;\n- create Draft-Payments (the user will need to approve the payment\
  \ using the bunq app);\n- assign a Monetary account to a Card;\n- read, create and\
  \ manage Cards;\n- read and create Request-Inquiries\n- read Request-Responses.\n\
  \nAs a PSD2-licensed developer, you are limited to the permission scopes of your\
  \ role.\n\n## <span id=\"topic-oauth-authorization-request\">Authorization request</span>\n\
  \nYour web or mobile app should redirect users to the following URL:\n\n`https://oauth.bunq.com/auth`\n\
  \nThe following parameters should be passed:\n\n- `response_type` - bunq supports\
  \ the authorization code grant, provide `code` as parameter (required)\n- `client_id`\
  \ - your Client ID, get it from the bunq app (required)\n- `redirect_uri` - the\
  \ URL you wish the user to be redirected after the authorization, make sure you\
  \ register the Redirect URL in the bunq app (required)\n- `state` - a unique string\
  \ to be passed back upon completion (optional)\n\nUse `https://oauth.sandbox.bunq.com/auth`\
  \ in the sandbox environment.\n\n**Authorization request example:**\n\n```\nhttps://oauth.bunq.com/auth?response_type=code\n\
  &client_id=1cc540b6e7a4fa3a862620d0751771500ed453b0bef89cd60e36b7db6260f813\n&redirect_uri=https://www.bunq.com\n\
  &state=594f5548-6dfb-4b02-8620-08e03a9469e6\n```\n\n**Authorization request response:**\n\
  \n```\nhttps://www.bunq.com/?code=7d272be434a75933f40c13d56aef6c31496005b653074f7d6ac57029d9995d30\n\
  &state=594f5548-6dfb-4b02-8620-08e03a9469e6\n\n```\n\n![bunq_OAuth_authorization_token_exchange.jpg](https://www.bunq.com/assets/media/developer/Authorization-token-exchange.jpg)\n\
  \n## <span id=\"topic-oauth-token-exchange\">Token exchange</span>\n\nIf the authorization\
  \ request is accepted by the user, you get the authorization `code`_._ Exchange\
  \ it for an `access_token`.\n\nMake a `POST` call to `https://api.oauth.bunq.com/v1/token`\
  \ . Pass the following parameters as `GET` variables:\n\n- `grant_type` - the grant\
  \ type used, `authorization_code` for now (required)\n- `code` -  the authorization\
  \ code received from bunq (required)\n- `redirect_uri` - the same Redirect URL used\
  \ in the authorisation request (required)\n- `client_id` - your Client ID (required)\n\
  - `client_secret` - your Client Secret (required)\n\nUse `https://api-oauth.sandbox.bunq.com/v1/token`\
  \ in the sandbox environment.\n\n**Token request example:**\n\n```\nhttps://api.oauth.bunq.com/v1/token?grant_type=authorization_code\n\
  &code=7d272be434a75933f40c13d56aef6c31496005b653074f7d6ac57029d9995d30\n&redirect_uri=https://www.bunq.com/\n\
  &client_id=1cc540b6e7a4fa3a862620d0751771500ed453b0bef89cd60e36b7db6260f813\n&client_secret=184f969765f6f74f53bf563ae3e9f891aec9179157601d25221d57f2f1151fd5\n\
  ```\n\nNote: The request should only contain URL parameters. No body is expected.\n\
  \n**Example successful response:**\n\n```json\n{\n    \"access_token\": \"8baec0ac1aafca3345d5b811042feecfe0272514c5d09a69b5fbc84cb1c06029\"\
  ,\n    \"token_type\": \"bearer\",\n    \"state\": \"594f5548-6dfb-4b02-8620-08e03a9469e6\"\
  \n}\n```\n\n**Example error response:**\n\n```json\n{\n    \"error\": \"invalid_grant\"\
  ,\n    \"error_description\": \"The authorization code is invalid or expired.\"\n\
  }\n```\n\n## <span id=\"topic-oauth-whats-next\">What's next?</span>\n\nTo start\
  \ sending calls to the account of the user who has accepted your authorization request,\
  \ create an API context for the `access_token` you have received as the result of\
  \ the token exchange. The `access_token` can be used as a normal API key. Please\
  \ continue with [Authentication](#authentication).\n\n**NOTE:** When connecting\
  \ to a bunq user's account using OAuth, you create a new user \\(`userApiKey`\\\
  ) that has its own `id` and `access_token` . When sending a request on behalf of\
  \ a user connected to your app via OAuth,  use the `id` of `userApiKey`  as `userId`\
  \ and the item `id`s of the bunq user \\(`grantedByUser`\\).\n\n**Example of a successful\
  \ request URL:**\n\n```text\nhttps://api.bunq.com/user/{userApiKey's userId}/monetary-account/{grantedByUser's\
  \ monetary-accountId}/payment\n```\n\nWhen calling `GET /user/{userID}`, you might\
  \ expect to get `UserPerson` or `UserCompany`. Instead, you will get the `UserApiKey`\
  \ object, which contains references to both the user that requested access *(you)*\
  \ and the user that granted access *(the bunq user account that you connected to)*.\
  \ \n\n![bunq_OAuth UserApiKey](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LbhJLuxCAKl5yUuS74T%2F-LuhS4YOAX9bwW1eGYF8%2F-LuhnlwEcVXtLVk6846Z%2FUserApiKey%20creation%20(3).jpg?alt=media&token=d1f212a2-3105-4f0e-a980-34b04a12998a)\n\
  \n## <span id=\"topic-oauth-using-the-connect-button\">Using the Connect button</span>\n\
  \nAll good? Ready to connect to your bunq users? Refer to our style guide and use\
  \ the following assets when implementing the **Connect to bunq** button.\n\n- [Style\
  \ guide](https://bunq.com/info/oauth-styleguide)\n- [Connect button assets](https://bunq.com/info/oauth-connect-buttons)\n\
  \nVisit us on together.bunq.com, share your creations, ask question and build your\
  \ very own bunq app!\n\n# <span id=\"topic-authentication\">Authentication</span>\n\
  \n- All requests must use HTTPS. HTTP calls will fail. \n- You should use SSL Certificate\
  \ Pinning and Hostname Verification to ensure your connection with bunq is secure.\n\
  - The auto logout time that you set in the app applies to all your sessions including\
  \ the API ones. If a request is made 30 minutes before a session expires, the session\
  \ will automatically be extended.\n- We use extra signing on top of HTTPS encryption\
  \ that you must implement yourself if you are not using the SDKs.\n\nℹ️ *We use\
  \ asymmetric cryptography for signing requests and encryption.*\n- The client (you)\
  \ and the server (bunq) must have a pair of keys: a private key and a public key.\
  \ You need to pre-generate your own pair of 2048-bit RSA keys in the PEM format\
  \ aligned with the PKCS #8 standard.\n- The parties (you and bunq) exchange their\
  \ public keys in the first step of the API context creation flow. All the following\
  \ requests must be signed by both your application and the server. Pass your signature\
  \ in the `X-Bunq-Client-Signature` header, and the server will return its signature\
  \ in the `X-Bunq-Server-Signature` header.\n\n## <span id=\"topic-authentication-device-registration\"\
  >Device registration</span>\n\nBefore you can start calling the bunq API, you must\
  \ activate your API key, which covers the following steps:\n* register your API\
  \ key, device, and IP address\\(es\\) _\\(only once to activate your API key\\);_\n\
  * create a session via `POST /session-server`. \n\nWe call this sequence of steps\
  \ \"creating an API context.\" \n\nIf you are using OAuth to access a user account,\
  \ you need to create an API context for the `access_token` you receive upon [authorization\
  \ token exchange](https://doc.bunq.com/#/oauth) too. \n\n### <span id=\"topic-authentication-device-registration-using-our-sdks\"\
  >Using our SDKs</span>\n\n1. Go to our [GitHub](https://github.com/bunq) page.\n\
  2. Choose the SDK in your language of choice.\n3. Find and use the part dedicated\
  \ to creating an API context.\n\n[Run Tinker](https://developer.bunq.com/tinker-command-line-banking)\
  \ to see a sample project using bunq SDKs in action.\n\n\n### <span id=\"topic-authentication-device-registration-using-our-api\"\
  >Using our API directly</span>\n\n1. Create an _Installation_ by calling `POST v1/installation`\
  \ and passing your pre-generated public key. You will receive an installation _Token._\
  \ Use it when making the two following API calls.\n2. Create a _DeviceServer_ via\
  \ `POST v1/device-server`. Provide a description and a secret \\(API key in this\
  \ case\\).\n3. Create a _SessionServer_ by executing `POST v1/session-server`. You\
  \ will receive an authentication _Token._ Use it in the API requests in this active\
  \ session.​\n\n[Import our Postman collection](https://github.com/bunq/postman)\
  \ to see our pre-setup API context creation calls. It will automatically generate\
  \ and pre-fill everything in the API calls that create context so you can inspect\
  \ the process.\n\n### <span id=\"topic-authentication-device-registration-ip-addresses\"\
  >IP addresses</span>\n\nWhen using a standard API Key the DeviceServer and Installation\
  \ that are created in this process are bound to the IP address they are created\
  \ from. Afterwards it is only possible to add IP addresses via the Permitted IP\
  \ endpoint.\n\nUsing a Wildcard API Key gives you the freedom to make API calls\
  \ from any IP address after the POST device-server. You can switch to a Wildcard\
  \ API Key by tapping on “Allow All IP Addresses” in your API Key menu inside the\
  \ bunq app. You can also programatically switch to a Wildcard API Key by passing\
  \ your current ip and a `*` (asterisk) in the `permitted_ips` field of the device-server\
  \ POST call. E.g: `[\"1.2.3.4\", \"*\"]`.\n\n# <span id=\"topic-psd2\">Connect as\
  \ a PSD2 service provider</span>\n\nAs a service provider, either an Account Information\
  \ Service Provider (AISP), Payment Initiation Service Provider (PISP), or Card Based\
  \ Payment Instrument Issuer (CBPII), you have obtained or are planning to obtain\
  \ a license from your local supervisor. You will need your unique eIDAS certificate\
  \ number to start using the PSD2-compliant bunq API on production.\n\nWe accept\
  \ pseudo certificates in the sandbox environment so you could test the flow. You\
  \ can generate a test certificate using the command below.\n\n⚠️ Make sure to include\
  \ AISP and/or PISP in the name to generate a certificate with the roles.\n\n```\n\
  openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -days 365 -nodes\
  \ -subj '/CN=My App PISP AISP/C=NL'\n```\n\n## <span id=\"topic-psd2-register-as-a-service-provider\"\
  >Register as a service provider</span>\n\nBefore you can read the information on\
  \ bunq users or initiate payments, you need to register a PSD2 account and receive\
  \ credentials that will enable you to access the bunq user accounts.\n\n1. Execute\
  \ `POST v1/installation` and get your installation *Token* with a unique random\
  \ key pair.\n1. Use the installation *Token* and your unique PSD2 certificate to\
  \ call `POST v1/payment-service-provider-credential`. This will register your software.\
  \ \n1. Receive your API key in return. It will identify you as a PSD2 bunq API user.\
  \ You will use it to start an OAuth flow. The session will last 90 days. After it\
  \ closes, start a new session using the same API key.\n1. Register a device by using\
  \ `POST v1/device-server` using the API key for the secret and passing the installation\
  \ *Token* in the `X-Bunq-Client-Authentication` header. \n1. Create your first session\
  \ by executing `POST v1/session-server`. Provide the installation *Token* in the\
  \ `X-Bunq-Client-Authentication` header. You will receive a session *Token*. Use\
  \ it in any following request in the `X-Bunq-Client-Authentication` header.\n\n\
  **NOTE.** The first session will last 1 hour. Start a new session within 60 minutes.\n\
  \n![bunq_PSD2_API_context](https://www.bunq.com/assets/media/developer/Creating-API-context-as-a-PSD2-user-REVISED.jpg)\n\
  \n## <span id=\"topic-psd2-register-your-applicaton\">Register your OAuth application</span>\n\
  \nBefore you can start authenticating on behalf of a bunq user, you need to get\
  \ *Client ID* and *Client Secret*, which will identify you in authorization requests\
  \ to the user accounts.\n\n1. Call `POST /v1/user/{userID}/oauth-client` to create\
  \ an OAuth Client.\n2. Add a redirect URL to the OAuth Client via `POST /user/{userID}/oauth-client/{oauth-clientID}/callback-url`.\n\
  3. Call `GET /v1/user/{userID}/oauth-client/{oauth-clientID}`. We will return your\
  \ _Client ID_ and _Client Secret_.\n4. You are ready to [initiate authorization\
  \ requests](#oauth-authorization-request).\n\nThe flow below will guide you through\
  \ the full OAuth connection process. Note that you only need to create OAuth credentials\
  \ once.\n\n![bunq_full_OAuth_flow](https://www.bunq.com/assets/media/developer/AuthorizationOAuth-Flow.jpg)\n\
  \n## <span id=\"topic-psd2-access-user-accounts-as-an-aisp\">Access user accounts\
  \ as an AISP</span>\n\nAs an AISP, you are allowed to authenticate in a user’s account\
  \ and access \\(read\\) the following account information:\n\n1. legal name\n2.\
  \ IBAN\n3. nationality\n4. card validity data\n5. transaction history\n6. account\
  \ balance\n\nTo read the user's information, you need to establish a connection\
  \ with their bunq account. You can do it using an [authorization request](#oauth-authorization-request).\
  \ Once a bunq user has confirmed the authorization request and you have done the\
  \ [token exchange](#oauth-token-exchange), you can activate the Access Token \\\
  (use it as an API key\\).\n\nToken activation happens when you create an API context\
  \ \\(install it and link your IP adrress and device to it\\). See the [OAuth](https://beta.doc.bunq.com/basics/oauth)\
  \ page for the full flow illustration.\n\nAn active Access Token allows you to communicate\
  \ with the bunq user’s account. You can use it to start a session to interact with\
  \ the monetary accounts the user allows you to access.\n\n![bunq_AISP](https://www.bunq.com/assets/media/developer/AISP.jpg)\n\
  \n## <span id=\"topic-psd2-initiate-payments-as-a-pisp\">Make payments as a PISP</span>\n\
  \nAs a PISP, you are allowed to authenticate in a user’s account with the following\
  \ permissions:\nread account information \\(via`GET /user`\\):\n   * legal name;\n\
  \   * IBAN;\n2. initiate payments \\(create draft payments via either  `POST /user/{userID}/monetary-account/{monetary-accountID}/draft-payment`\
  \ or `POST /user/{userID}/payment-service-provider-draft-payment`\\) and read their\
  \ statuses;\n3. confirm that the account balance is sufficient for covering the\
  \ payment \\(via`POST /user/{userID}/confirmation-of-funds`\\).\n\nThe bunq API\
  \ provides endpoints for different scenarios of the implementation of the payment\
  \ initiation functionality. In particular, as a PISP user, you can build applications\
  \ that initiate and authorize one-off or multiple incoming payments. Depending on\
  \ the use case you are intending to deploy, you might need to initiate the OAuth\
  \ authorization either before or after the payment initiation.  \n\n### <span id=\"\
  topic-psd2-initiate-multiple-payments-as-a-pisp\">Authorization of multiple (scheduled)\
  \ payments</span>\n\nIt is possible to initiate payments from a bunq user's account\
  \ having previously established an OAuth connection between your application and\
  \ the bunq user's account. The bunq user will receive push notifications for each\
  \ initiated payment.\n\nOnce a bunq user has [confirmed they want to make payments\
  \ via your application](https://beta.doc.bunq.com/psd2/connect-as-a-psd2-service-provider#register-your-application),\
  \ you can initiate the payment confirmation flow.\n\n1. Create a draft payment via\
  \ `POST /user/{userID}/monetary-account/{monetary-accountID}/draft-payment`passing\
  \ the following parameters:\n   * `monetary-accountId and userId` (`userApiKey`'s\
  \ `id`; see [OAuth](https://beta.doc.bunq.com/basics/oauth#user-id-vs-item-ids)\
  \ for more information) in the endpoint URL;\n   * the customer’s email address,\
  \ phone number, or IBAN in the `counterparty_alias` field of the request body.\n\
  2. If the user confirms their intent to make the payment, bunq carries out the transaction.\n\
  3. Check the status of the payment via `GET /user/{userID}/monetary-account/{monetary-accountID}/draft-payment`\
  \ using the draft payment `id` parameter returned in the previous step. \n\n![bunq_PISP](https://www.bunq.com/assets/media/developer/Payment-initiation-1.1-universal.jpg)\n\
  \n### <span id=\"topic-psd2-initiate-single-payments-as-a-pisp\">Single payment\
  \ authorization</span>\n\nIt is possible to initiate payments having only the IBAN\
  \ of the payer using `POST /user/{userID}/payment-service-provider-draft-payment`.\
  \  In this case, the bunq user will accept the payment along with the authorization\
  \ request. No additional push notifications are sent to the user. \n\n1. Collect\
  \ the bunq user's IBAN (and name) in the UI of your application.\n2. Create a draft\
  \ payment via `POST /user/{userID}/payment-service-provider-draft-payment`. \n3.\
  \ Initiate an [authorization request.](https://beta.doc.bunq.com/basics/oauth#authorization-request)\
  \ Upon the QR-code scan, the bunq user will see and be able to either accept or\
  \ reject the payment authorization request.\n4. Check the status of the payment.\n\
  \n![bunq_PISP_single_payment](https://www.bunq.com/assets/media/developer/Payment-initiation-1.0.jpg)\n\
  \n## <span id=\"topic-psd2-confirm-available-funds-as-a-cbpii\">Confirm available\
  \ funds as a CBPII</span>\n\nAs a CBPII, you are allowed to authenticate in a user’\
  s account to validate the availability of funds for the payment in question. \n\n\
  1. Collect an alias for the bunq user's account (their name and IBAN, email address,\
  \ or phone number).\n2. Check the availability of funds via `POST /user/{userID}/confirmation-of-funds`\
  \ passing the following information:\n   * your `userId`;\n   * the amount of money\
  \ needed for the payment;\n   * the name of the bunq user and the IBAN of the account\
  \ (email address or phone number pointing at the user are also possible).\n\n# <span\
  \ id=\"topic-signing\">Signing</span>\n⚠️ **NOTE:**  We deprecated the signing of\
  \ the entire API request (the URL, headers and body). You only need to sign the\
  \ request body. Requests with full request signatures are no longer validated.\n\
  \nWe are legally required to protect our users and their data from malicious attacks\
  \ and intrusions. That is why we beyond having a secure https connection, we use\
  \ [asymmetric cryptography](https://en.wikipedia.org/wiki/Public-key_cryptography)\
  \ for signing requests that create a session or payment. The use of signatures ensures\
  \ the data is coming from the trusted party and was not modified after sending and\
  \ before receiving.\n\nRequest body signing is only mandatory for the following\
  \ operations: \n- open a session;\n- create a payment;\n- create a scheduled payment;\n\
  - any other operation that executes a payment such as the following:\n\t- accept\
  \ a draft payment;\n\t- accept a scheduled payment;\n\t- accept a draft scheduled\
  \ payment;\n\t- accept a payment request.\n\nYou will know that the API call must\
  \ be encrypted if you get the 466 error code. \n\nThe signing mechanism is implemented\
  \ in our [SDKs](https://github.com/bunq) so if you are using them you don't have\
  \ to worry about the details described below.\n\nThe signatures are created using\
  \ the SHA256 cryptographic hash function and included (encoded in base 64) in the\
  \ `X-Bunq-Client-Signature` request header and `X-Bunq-Server-Signature` response\
  \ header. The data to sign is the following:\n\n- For requests: the body only.\n\
  - For responses: the body only.\n\nFor signing requests, the client must use the\
  \ private key corresponding to the public key that was sent to the server in the\
  \ installation API call. That public key is what the server will use to verify the\
  \ signature when it receives the request. In that same call the server will respond\
  \ with a server side public key, which the client must use to verify the server's\
  \ signatures. The generated RSA key pair must have key lengths of 2048 bits and\
  \ adhere to the PKCS #8 standard.\n\n## <span id=\"topic-signing-request-signing-example\"\
  >Request signing example</span>\n\nConsider the following request, a `POST` to `/v1/user/126/monetary-account/222/payment`\
  \ (the JSON is formatted with newlines and indentations to make it more readable):\n\
  \n<table>\n    <thead>\n        <tr>\n            <th>Header</th>\n            <th>Value</th>\n\
  \        </tr>\n    </thead>\n    <tbody>\n        <tr>\n            <td>Cache-Control:</td>\n\
  \            <td>no-cache</td>\n        </tr>\n        <tr>\n            <td>User-Agent:</td>\n\
  \            <td>bunq-TestServer/1.00 sandbox/0.17b3</td>\n        </tr>\n     \
  \   <tr>\n            <td>X-Bunq-Client-Authentication:</td>\n\n<td>f15f1bbe1feba25efb00802fa127042b54101c8ec0a524c36464f5bb143d3b8b</td>\n\
  \        </tr>\n    </tbody>\n</table>\n\n```json\n{\n\t\"amount\": {\n\t\t\"value\"\
  : \"12.50\",\n\t\t\"currency\": \"EUR\"\n\t},\n\t\"counterparty_alias\": {\n\t\t\
  \"type\": \"EMAIL\",\n\t\t\"value\": \"bravo@bunq.com\"\n\t},\n\t\"description\"\
  : \"Payment for drinks.\"\n}\n```\n\nLet's sign that request. First create a variable\
  \ `$dataToSign` containing the body of the request:\n\n```json\n{\n    \"amount\"\
  : {\n        \"value\": \"12.50\",\n        \"currency\": \"EUR\"\n    },\n    \"\
  counterparty_alias\": {\n        \"type\": \"EMAIL\",\n        \"value\": \"bravo@bunq.com\"\
  \n    },\n    \"description\": \"Payment for drinks.\"\n}\n```\nNext, create the\
  \ signature of `$dataToSign` using the SHA256 algorithm and the private key `$privateKey`\
  \ of the Installation's key pair. In PHP, use the following to create a signature.\
  \ The signature will be passed by reference into `$signature`.\n\n`openssl_sign($dataToSign,\
  \ $signature, $privateKey, OPENSSL_ALGO_SHA256);`\n\nEncode the resulting `$signature`\
  \ using base64, and add the resulting value to the request under the `X-Bunq-Client-Signature`\
  \ header. You have just signed your request, and can send it!\n\n## <span id=\"\
  topic-signing-response-verifying-example\">Response verifying example</span>\n\n\
  The response to the previous request is as follows (the JSON is formatted with newlines\
  \ and indentations to make it more readable):\n\n<table>\n    <thead>\n        <tr>\n\
  \            <th>Header</th>\n            <th>Value</th>\n        </tr>\n    </thead>\n\
  \    <tbody>\n        <tr>\n            <td>Access-Control-Allow-Origin:</td>\n\
  \            <td>*</td>\n        </tr>\n        <tr>\n            <td>Content-Type:</td>\n\
  \            <td>application/json</td>\n        </tr>\n        <tr>\n          \
  \  <td>Date:</td>\n            <td>Thu, 07 Apr 2016 08:32:04 GMT</td>\n        </tr>\n\
  \        <tr>\n            <td>Server:</td>\n            <td>APACHE</td>\n     \
  \   </tr>\n        <tr>\n            <td>Strict-Transport-Security:</td>\n     \
  \       <td>max-age=31536000</td>\n        </tr>\n        <tr>\n            <td>Transfer-Encoding:</td>\n\
  \            <td>chunked</td>\n        </tr>\n        <tr>\n            <td>X-Bunq-Client-Response-Id:</td>\n\
  \            <td>89dcaa5c-fa55-4068-9822-3f87985d2268</td>\n        </tr>\n    \
  \    <tr>\n            <td>X-Bunq-Client-Request-Id:</td>\n            <td>57061b04b67ef</td>\n\
  \        </tr>\n        <tr>\n            <td>X-Bunq-Server-Signature:</td>\n  \
  \          <td>ee9sDfzEhQ2L6Rquyh2XmJyNWdSBOBo6Z2eUYuM4bAOBCn9N5vjs6k6RROpagxXFXdGI9sT15tYCaLe5FS9aciIuJmrVW/SZCDWq/nOvSThi7+BwD9JFdG7zfR4afC8qfVABmjuMrtjaUFSrthyHS/5wEuDuax9qUZn6sVXcgZEq49hy4yHrV8257I4sSQIHRmgds4BXcGhPp266Z6pxjzAJbfyzt5JgJ8/suxgKvm/nYhnOfsgIIYCgcyh4DRrQltohiSon6x1ZsRIfQnCDlDDghaIxbryLfinT5Y4eU1eiCkFB4D69S4HbFXYyAxlqtX2W6Tvax6rIM2MMPNOh4Q==</td>\n\
  \        </tr>\n        <tr>\n            <td>X-Frame-Options:</td>\n          \
  \  <td>SAMEORIGIN</td>\n        </tr>\n    </tbody>\n</table>\n\n```json\n{\n\t\"\
  Response\": [\n\t\t{\n\t\t\t\"Id\": {\n\t\t\t\t\"id\": 1561\n\t\t\t}\n\t\t}\n\t\
  ]\n}\n```\nWe need to verify that this response was sent by the bunq server and\
  \ not from a man-in-the-middle:\n- Create a `$dataToSign` variable containing the\
  \ body of the request.\n\n**NOTE:** We started to only sign the response body on\
  \ April 28, 2020. Please make sure you validate our new response signature.\n\n\
  So for our example above the response to sign will look like this:\n\n```\n{\"Response\"\
  :[{\"Id\":{\"id\":1561}}]}\n```\nNow, verify the signature of `$dataToVerify` using\
  \ the SHA256 algorithm and the public key `$publicKey` of the server. In PHP, use\
  \ the following to verify the signature.\n\n`openssl_sign($dataToVerify, $signature,\
  \ $publicKey, OPENSSL_ALGO_SHA256);`\n\n## <span id=\"topic-signing-troubleshooting\"\
  >Troubleshooting</span>\n\nIf you get an error telling you \"The request signature\
  \ is invalid\", please check the following:\n\n- There are no redundant characters\
  \ (extra spaces, trailing line breaks, etc.) in the data to sign.\n- Make sure the\
  \ body is appended to the data to sign exactly as you're adding it to the request.\n\
  - You have added the full body to the data to sign.\n- You use the data to sign\
  \ to create a SHA256 hash signature.\n- You have base64 encoded the SHA256 hash\
  \ signature before adding it to the request under `X-Bunq-Client-Signature`.\n\n\
  # <span id=\"topic-headers\">Headers</span>\n\nHTTP headers allow your client and\
  \ bunq to pass on additional information along with the request or response.\n\n\
  While this is already implemented in our [SDKs](https://github.com/bunq), please\
  \ follow these instructions to make sure you set appropriate headers for calls if\
  \ using bunq API directly.\n\n## <span id=\"topic-headers-request-headers\">Request\
  \ headers</span>\n\n### <span id=\"topic-headers-request-headers-mandatory-request-headers\"\
  >Mandatory request headers</span>\n\n#### Cache-Control\n\n`Cache-Control: no-cache`\n\
  \nThe standard HTTP Cache-Control header is required for all requests.\n\n#### User-Agent\n\
  \n`User-Agent: bunq-TestServer/1.00 sandbox/0.17b3`\n\nThe User-Agent header field\
  \ should contain information about the user agent originating the request. There\
  \ are no restrictions on the value of this header.\n\n#### X-Bunq-Client-Signature\n\
  \n**⚠️ UPCOMING CHANGE:** Header and URL signature will stop being validated on\
  \ April 28, 2020. Please [sign the request body](https://doc.bunq.com/#/signing)\
  \ only.\n\n`X-Bunq-Client-Signature: XLOwEdyjF1d+tT2w7a7Epv4Yj7w74KncvVfq9mDJVvFRlsUaMLR2q4ISgT+5mkwQsSygRRbooxBqydw7IkqpuJay9g8eOngsFyIxSgf2vXGAQatLm47tLoUFGSQsRiYoKiTKkgBwA+/3dIpbDWd+Z7LEYVbHaHRKkEY9TJ22PpDlVgLLVaf2KGRiZ+9/+0OUsiiF1Fkd9aukv0iWT6N2n1P0qxpjW0aw8mC1nBSJuuk5yKtDCyQpqNyDQSOpQ8V56LNWM4Px5l6SQMzT8r6zk5DvrMAB9DlcRdUDcp/U9cg9kACXIgfquef3s7R8uyOWfKLSNBQpdVIpzljwNKI1Q`\n\
  \n\n#### X-Bunq-Client-Authentication\n\n`X-Bunq-Client-Authentication: 622749ac8b00c81719ad0c7d822d3552e8ff153e3447eabed1a6713993749440`\n\
  \nThe authentication *token* is used to authenticate the source of the API call.\
  \ It is required by all API calls except for `POST /v1/installation`. \n\nIt is\
  \ important to note that the device and session calls are using the token from the\
  \ response of the installation call, while all the other calls use the token from\
  \ the response of the session-server call:\n- Pass the **installation *Token***\
  \ you get in the response to the `POST /installation` call in the `/device-server`\
  \ and `/session-server` calls.\n- Pass the **session *Token*** you get in the response\
  \ to the `POST /session-server` call in all the other calls.\n\n### <span id=\"\
  topic-headers-request-headers-otpional-request-headers\">Optional request headers</span>\n\
  \n#### X-Bunq-Language\n\n`X-Bunq-Language: en_US`\n\n`en_US` is the default language\
  \ setting for responses and error descriptions.\n\nThe X-Bunq-Language header must\
  \ contain a preferred language indication. The value of this header is formatted\
  \ as a ISO 639-1 language code plus a ISO 3166-1 alpha-2 country code, separated\
  \ by an underscore.\n\nCurrently only the languages en_US and nl_NL are supported.\
  \ Anything else will default to en_US.\n\n#### X-Bunq-Region\n\n`X-Bunq-Region:\
  \ en_US`\n\n`en_US` is the default region for localization formatting.\n\nThe X-Bunq-Region\
  \ header must contain the region (country) of the client device. The value of this\
  \ header is formatted as a ISO 639-1 language code plus a ISO 3166-1 alpha-2 country\
  \ code, separated by an underscore.\n\n#### X-Bunq-Client-Request-Id\n\n`X-Bunq-Client-Request-Id:\
  \ a4f0de`\n\nThis header has to specify an ID with each request that is unique for\
  \ the logged in user. There are no restrictions for the format of this ID. However,\
  \ the server will respond with an error when the same ID is used again on the same\
  \ DeviceServer.\n\n#### X-Bunq-Geolocation\n\n`X-Bunq-Geolocation: 4.89 53.2 12\
  \ 100 NL`\n\n`X-Bunq-Geolocation: 0 0 0 0 000` *(if no geolocation is available\
  \ or known)*\n\nThis header has to specify the geolocation of the device. It makes\
  \ it possible for bunq to map the geolocation with the payment.\n‌\nThe format of\
  \ this value is longitude latitude altitude radius country. The country is expected\
  \ to be formatted of an ISO 3166-1 alpha-2 country code. When no geolocation is\
  \ available or known the header must still be included but can be zero valued.\n\
  \n### <span id=\"topic-headers-request-headers-attachment-headers\">Attachment headers</span>\n\
  \n#### Content-Type\n\n`Content-Type: image/jpeg`\n\nThis header should be used\
  \ when uploading an attachment to pass its MIME type. Supported types are: image/png,\
  \ image/jpeg and image/gif.\n\n#### X-Bunq-Attachment-Description\nX-Bunq-Attachment-Description:\
  \ Check out these cookies.\nThis header should be used when uploading an Attachment's\
  \ content to give it a description.\n\n## <span id=\"topic-response-headers\">Response\
  \ headers</span>\n\n### <span id=\"topic-response-headers-all-responses\">All Responses</span>\n\
  \n####  X-Bunq-Client-Request-Id\n\n`X-Bunq-Client-Request-Id: a4f0de`\n\nThe same\
  \ ID that was provided in the request's X-Bunq-Client-Request-Id header. Is included\
  \ in the response (and request) signature, so can be used to ensure this is the\
  \ response for the sent request.\n\n#### X-Bunq-Client-Response-Id\n\n`X-Bunq-Client-Response-Id:\
  \ 76cc7772-4b23-420a-9586-8721dcdde174`\n\nA unique ID for the response formatted\
  \ as a UUID. Clients can use it to add extra protection against replay attacks.\n\
  \n#### X-Bunq-Server-Signature\n\n`X-Bunq-Server-Signature: XBBwfDaOZJapvcBpAIBT1UOmczKqJXLSpX9ZWHsqXwrf1p+H+eON+TktYksAbmkSkI4gQghw1AUQSJh5i2c4+CTuKdZ4YuFT0suYG4sltiKnmtwODOFtu1IBGuE5XcfGEDDSFC+zqxypMi9gmTqjl1KI3WP2gnySRD6PBJCXfDxJnXwjRkk4kpG8Ng9nyxJiFG9vcHNrtRBj9ZXNdUAjxXZZFmtdhmJGDahGn2bIBWsCEudW3rBefycL1DlpJZw6yRLoDltxeBo7MjgROBpIeElh5qAz9vxUFLqIQC7EDONBGbSBjaXS0wWrq9s2MGuOi9kJxL2LQm/Olj2g==`\n\
  \nThe server's signature for this response. See the signing page for details on\
  \ how to verify this signature.\n\n### <span id=\"topic-response-headers-warning-header\"\
  >Warning header</span>\n\n#### X-Bunq-Warning\n\n`X-Bunq-Warning: \"You have a negative\
  \ balance. Please check the app for more details.\"`\n\nUsed to inform you on situations\
  \ that might impact your bunq account and API access.\n\n# <span id=\"topic-errors\"\
  >Errors</span>\n\nFamiliar HTTP response codes are used to indicate the success\
  \ or failure of an API request.\n\nGenerally speaking, codes in the 2xx range indicate\
  \ success, while codes in the 4xx range indicate an error having to do with provided\
  \ information (e.g. a required parameter was missing, insufficient funds, etc.).\n\
  \nFinally, codes in the 5xx range indicate an error with bunq servers. If this is\
  \ the case, please stop by the support chat and report it to us.\n\n## <span id=\"\
  topic-errors-response-codes\">Response codes</span>\n\n<table>\n    <thead>\n  \
  \      <tr>\n            <th>Code</th>\n            <th>Error</th>\n           \
  \ <th>Description</th>\n        </tr>\n    </thead>\n    <tbody>\n        <tr>\n\
  \            <td>200</td>\n            <td>OK</td>\n            <td>Successful HTTP\
  \ request</td>\n        </tr>\n        <tr>\n            <td>399</td>\n        \
  \    <td>NOT MODIFIED</td>\n            <td>Same as a 304, it implies you have a\
  \ local cached copy of the data</td>\n        </tr>\n        <tr>\n            <td>400</td>\n\
  \            <td>BAD REQUEST</td>\n            <td>Most likely a parameter is missing\
  \ or invalid</td>\n        </tr>\n        <tr>\n            <td>401</td>\n     \
  \       <td>UNAUTHORISED</td>\n            <td>Token or signature provided is not\
  \ valid</td>\n        </tr>\n        <tr>\n            <td>403</td>\n          \
  \  <td>FORBIDDEN</td>\n            <td>You're not allowed to make this call</td>\n\
  \        </tr>\n        <tr>\n            <td>404</td>\n            <td>NOT FOUND</td>\n\
  \            <td>The object you're looking for cannot be found</td>\n        </tr>\n\
  \        <tr>\n            <td>405</td>\n            <td>METHOD NOT ALLOWED</td>\n\
  \            <td>The method you are using is not allowed for this endpoint</td>\n\
  \        </tr>\n        <tr>\n            <td>429</td>\n            <td>RATE LIMIT</td>\n\
  \            <td>Too many API calls have been made in a too short period</td>\n\
  \        </tr>\n        <tr>\n            <td>466</td>\n            <td>REQUEST\
  \ SIGNATURE REQUIRED</td>\n            <td>Request signature is required for this\
  \ operation.</td>\n        </tr>\n        <tr>\n            <td>490</td>\n     \
  \       <td>USER ERROR</td>\n            <td>Most likely a parameter is missing\
  \ or invalid</td>\n        </tr>\n        <tr>\n            <td>491</td>\n     \
  \       <td>MAINTENANCE ERROR</td>\n            <td>bunq is in maintenance mode</td>\n\
  \        </tr>\n        <tr>\n            <td>500</td>\n            <td>INTERNAL\
  \ SERVER ERROR</td>\n            <td>Something went wrong on bunq's end</td>\n \
  \       </tr>\n    </tbody>\n</table>\n\nAll errors 4xx code errors will include\
  \ a JSON body explaining what went wrong.\n\n## <span id=\"topic-errors-rate-limits\"\
  >Rate limits</span>\n\nIf you are receiving the error 429, please make sure you\
  \ are sending requests at rates that are below our rate limits.\n\nOur rate limits\
  \ per IP address per endpoint:\n\n- GET requests: 3 within any 3 consecutive seconds\n\
  - POST requests: 5 within any 3 consecutive seconds\n- PUT requests: 2 within any\
  \ 3 consecutive seconds\n- Callbacks: 2 callback URLs per notification category\n\
  \nWe have a lower rate limit for `/session-server`: 1 request within 30 consecutive\
  \ seconds.\n\n# <span id=\"topic-api-conventions\">API conventions</span>\n\nMake\
  \ sure to follow these indications when using the bunq API or get started with our\
  \ SDKs.\n\n## <span id=\"topic-api-conventions-responses\">Responses</span>\n\n\
  All JSON responses have one top level object. In this object will be a Response\
  \ field of which the value is always an array, even for responses that only contain\
  \ one object.\n\nExample response body\n\n```json\n{\n\t\"Response\": [\n\t\t{\n\
  \t\t\t\"DataObject\": {}\n\t\t}\n\t]\n}\n```\n\n## <span id=\"topic-api-conventions-errors\"\
  >Errors</span>\n\n- Error responses also have one top level Error object.\n- The\
  \ contents of the array will be a JSON object with an error_description and error_description_translated\
  \ field.\n- The error_description is an English text indicating the error and the\
  \ error_description_translated field can be shown to end users and is translated\
  \ into the language from the X-Bunq-Language header, defaulting to en_US.\n- When\
  \ using bunq SDKs, error responses will be always raised in form of an exception.\n\
  \nExample response body\n```json\n{\n\t\"Error\": [\n\t\t{\n\t\t\t\"error_description\"\
  : \"Error description\",\n\t\t\t\"error_description_translated\": \"User facing\
  \ error description\"\n\t\t}\n\t]\n}\n```\n\n## <span id=\"topic-api-conventionsobject-type-indications\"\
  >Object Type indications</span>\n\nWhen the API returns different types of objects\
  \ for the same field, they will be nested in another JSON object that includes a\
  \ specific field for each one of them. Within bunq SDKs a BunqResponse object will\
  \ be returned as the top level object.\n\nIn this example there is a field content,\
  \ which can have multiple types of objects as value such as — in this case — ChatMessageContentText.\
  \ Be sure to follow this convention or use bunq SDKs instead.\n\n```json\n{\n\t\"\
  content\": {\n\t\t\"ChatMessageContentText\": {\n\t\t\t\"text\": \"Hi! This is an\
  \ automated security message. We saw you just logged in on an My Device Description.\
  \ If you believe someone else logged in with your account, please get in touch with\
  \ Support.\"\n\t\t}\n\t}\n}\n```\n\n## <span id=\"topic-api-conventions-time-formats\"\
  >Time formats</span>\n\nTimes and dates being sent to and from the API are in UTC.\
  \ The format that should be used is `YYYY-MM-DD hh:mm:ss.ssssss`, where the letters\
  \ have the meaning as specified in ISO 8601. For example: `2017-01-13 13:19:16.215235`.\n\
  \n# <span id=\"topic-callbacks\">Callbacks</span>\n\nCallbacks are used to send\
  \ information about events on your bunq account to a URL of your choice, so that\
  \ you can receive real-time updates.\n\n## <span id=\"topic-callbacks-notification-filters\"\
  >Notification Filters</span>\n\nTo receive notifications for certain activities\
  \ on a bunq account, you have to create notification filters. It is possible to\
  \ send the notifications to a provided URL and/or the user’s phone as push notifications.\n\
  \nUse the `notification-filter-push` resource to create and manage push notification\
  \ filters. Provide the type of events you want to receive notifications about in\
  \ the `category` field. \n\n```json    \n{\n   \"notification_filters\":[\n    \
  \  {\n         \"category\":\"SCHEDULE_RESULT\"\n      }\n   ]\n}\n```\n\nUse the\
  \ `notification-filter-url` resource to create and manage URL notification filters.\
  \ The callback URL you provide in the `notification_target` field must use HTTPS.\
  \ \n\n```json\n{\n   \"notification_filters\":[\n      {\n         \"category\"\
  :\"PAYMENT\",\n         \"notification_target\":\"{YOUR_CALLBACK_URL}\"\n      }\n\
  \   ]\n}\n```\n\n### <span id=\"topic-callbacks-notification-filters-callback-categories\"\
  >Callback categories</span>\n\n<table>\n    <thead>\n        <tr>\n            <th>Category</th>\n\
  \            <th>Description</th>\n        </tr>\n    </thead>\n    <tbody>\n  \
  \      <tr>\n            <td>BILLING</td>\n            <td>notifications for all\
  \ bunq invoices</td>\n        </tr>\n        <tr>\n            <td>CARD_TRANSACTION_SUCCESSFUL</td>\n\
  \            <td>notifications for successful card transactions</td>\n        </tr>\n\
  \        <tr>\n            <td>CARD_TRANSACTION_FAILED</td>\n            <td>notifications\
  \ for failed card transaction</td>\n        </tr>\n        <tr>\n            <td>CHAT</td>\n\
  \            <td>notifications for received chat messages</td>\n        </tr>\n\
  \        <tr>\n            <td>DRAFT_PAYMENT</td>\n            <td>notifications\
  \ for creation and updates of draft payments</td>\n        </tr>\n        <tr>\n\
  \            <td>IDEAL</td>\n            <td>notifications for iDEAL-deposits towards\
  \ a bunq account</td>\n        </tr>\n        <tr>\n            <td>SOFORT</td>\n\
  \            <td>notifications for SOFORT-deposits towards a bunq account</td>\n\
  \        </tr>\n        <tr>\n            <td>MUTATION</td>\n            <td>notifications\
  \ for any action that affects a monetary account’s balance</td>\n        </tr>\n\
  \t<tr>\n            <td>OAUTH</td>\n            <td>notifications for revoked OAuth\
  \ connections</td>\n        </tr>\n        <tr>\n            <td>PAYMENT</td>\n\
  \            <td>notifications for payments created from, or received on a bunq\
  \ account (doesn’t include payments that result out of paying a Request, iDEAL,\
  \ Sofort or Invoice). Outgoing payments have a negative value while incoming payments\
  \ have a positive value</td>\n        </tr>\n        <tr>\n            <td>REQUEST</td>\n\
  \            <td>notifications for incoming requests and updates on outgoing requests</td>\n\
  \        </tr>\n        <tr>\n            <td>SCHEDULE_RESULT</td>\n           \
  \ <td>notifications for when a scheduled payment is executed</td>\n        </tr>\n\
  \        <tr>\n            <td>SCHEDULE_STATUS</td>\n            <td>notifications\
  \ about the status of a scheduled payment, e.g. when the scheduled payment is updated\
  \ or cancelled</td>\n        </tr>\n        <tr>\n            <td>SHARE</td>\n \
  \           <td>notifications for any updates or creation of Connects (ShareInviteBankInquiry)</td>\n\
  \        </tr>\n        <tr>\n            <td>TAB_RESULT</td>\n            <td>notifications\
  \ for updates on Tab payments</td>\n        </tr>\n        <tr>\n            <td>BUNQME_TAB</td>\n\
  \            <td>notifications for updates on bunq.me Tab (open request) payments</td>\n\
  \        </tr>\n        <tr>\n            <td>SUPPORT</td>\n            <td>notifications\
  \ for messages received from us through support chat</td>\n        </tr>\n    </tbody>\n\
  </table>\n\n### <span id=\"topic-callbacks-notification-filters-mutation-category\"\
  >Mutation category</span>\n\nA Mutation is a change in the balance of a monetary\
  \ account. So, for each payment-like object, such as a request, iDEAL-payment or\
  \ a regular payment, a Mutation is created. Therefore, the `MUTATION` category can\
  \ be used to keep track of a monetary account's balance.\n\n### <span id=\"topic-callbacks-notification-filters-receiving-callbacks\"\
  >Receiving callbacks</span>\n\nCallbacks for the sandbox environment will be made\
  \ from different IP's at AWS.  \nCallbacks for the production environment will be\
  \ made from `185.40.108.0/22`.\n\n*The IP addresses might change*. We will notify\
  \ you in a timely fashion if such a change would take place.\n\n### <span id=\"\
  topic-callbacks-notification-filters-retry-mechanism\">Retry mechanism</span>\n\n\
  When the execution of a callback fails (e.g. if the callback server is down or the\
  \ response contains an error) it is tried again for a maximum of 5 times, with an\
  \ interval of one minute between each try. If your server is not reachable by the\
  \ callback after the 6th total try, the callback is not sent anymore.\n\n### <span\
  \ id=\"topic-callbacks-notification-filters-removing-callbacks\">Removing callbacks</span>\n\
  \nTo remove callbacks for an object, send a PUT request to the *user-person*, *user-company*,\
  \ *monetary-account* or *cash-register* resource with the `notification_filters`\
  \ field of the JSON request body unset.\n```\n{\n    \"notification_filters\": []\n\
  }\n```\n\n## <span id=\"topic-callbacks-certificate-pinning\">Certificate pinning</span>\n\
  \nWe recommend you use certificate pinning as an extra security measure. With certificate\
  \ pinning, we check the certificate of the server on which you want to receive callbacks\
  \ against the pinned certificate that has been provided by you and cancel the callback\
  \ if that check fails.\n\n### <span id=\"topic-callbacks-certificate-pinning-how-to-set-up-certificate-pinning\"\
  >How to set up certificate pinning</span>\n\nRetrieve the SSL certificate of your\
  \ server using the following command:\n\n1. `openssl s_client -servername www.example.com\
  \ -connect www.example.com:443 < /dev/null | sed -n \"/-----BEGIN/,/-----END/p\"\
  \ > www.example.com.pem`\n2. `POST` the certificate to the certificate-pinned endpoint.\n\
  \nNow every callback that is made will be checked against the pinned certificate\
  \ that you provided. Note that if the SSL certificate on your server expires or\
  \ is changed, our callbacks will fail.\n\n# <span id=\"topic-pagination\">Pagination</span>\n\
  \nIn order to control the size of the response of a `LIST` request, items can be\
  \ paginated. A `LIST` request is a request for every one of a certain resources,\
  \ for instance all payments of a certain monetary account `GET /v1/user/1/monetary-account/1/payment`).\
  \ You can decide on the maximum amount of items of a response by adding a `count`\
  \ query parameter with the number of items you want per page to the URL. For instance:\n\
  \n`GET /v1/user/1/monetary-account/1/payment?count=25`\n\nWhen no `count` is given,\
  \ the default count is set to 10. The maximum `count` you can set is 200.\n\nWith\
  \ every listing, a `Pagination` object will be added to the response, containing\
  \ the URLs to be used to get the next or previous set of items. The URLs in the\
  \ Pagination object can be used to navigate through the listed resources. The Pagination\
  \ object looks like this given a count of 25:\n\n```json\n{\n    \"Pagination\"\
  : {\n        \"future_url\": null,\n        \"newer_url\": \"/v1/user/1/monetary-account/1/payment?count=25&newer_id=249\"\
  ,\n        \"older_url\": \"/v1/user/1/monetary-account/1/payment?count=25&older_id=224\"\
  \n    }\n}\n```\n\nThe `newer_url` value can be used to get the next page. The `newer_id`\
  \ is always the ID of the last item in the current page. If `newer_url` is `null`,\
  \ there are no more recent items before the current page.\n\nThe `older_url` value\
  \ can be used to get the previous page. The `older_id` is always the ID of the first\
  \ item in the current page. If `older_url` is `null`, there are no older items after\
  \ the current page.\n\nThe `future_url` can be used to refresh and check for newer\
  \ items that didn't exist when the listing was requested. The `newer_id` will always\
  \ be the ID of the last item in the current page. `future_url` will be `null` if\
  \ `newer_id` is not also the ID of the latest item.\n\n# <span id=\"topic-sandbox\"\
  >Sandbox</span>\n*The sandbox base URL is https://public-api.sandbox.bunq.com/v1/*\n\
  \nWe do not use real money and do not allow external transactions in the sandbox\
  \ environment. \n\n## Sandbox user accounts\nYou need to create a sandbox user to\
  \ test the bunq API. The easiest way to do it is by using [our developer portal](https://developer.bunq.com/):\n\
  1. Log in using your bunq account or [create a free developer account](https://developer.bunq.com/portal/signup)\
  \ with sandbox-only access.\n1. Go to Sandbox Users.\n1. Generate up to 5 users.\n\
  1. Use the sandbox API key to create an API context and/or use the user credentials\
  \ to log in to the [sandbox bunq app](https://doc.bunq.com/#/android-emulator).\n\
  \n### Alternative ways to generate sandbox API keys\nThere are 3 other ways you\
  \ can generate a bunq sandbox API key:\n* connect to [Tinker](https://lexy.gitbook.io/bunq/quickstart/tinker)\
  \ *(it will also return login credentials for the sandbox app)*;\n* create it in\
  \ the [sandbox app](https://doc.bunq.com/#/android-emulator) *(you need to be logged\
  \ in as a sandbox user)*;\n* call the sandbox user endpoints directly, using [our\
  \ Postman collection](https://github.com/bunq/postman), or by running a cURL command\
  \ (change `sandbox-user-person` to `sandbox-user-company` to generate a business\
  \ user):\n\n```\ncurl https://public-api.sandbox.bunq.com/v1/sandbox-user-person\
  \ -X POST --header \"Content-Type: application/json\" --header \"Cache-Control:\
  \ none\" --header \"User-Agent: curl-request\" --header \"X-Bunq-Client-Request-Id:\
  \ $(date)randomId\" --header \"X-Bunq-Language: nl_NL\" --header \"X-Bunq-Region:\
  \ nl_NL\" --header \"X-Bunq-Geolocation: 0 0 0 0 000\"\n```\n\n⚠️ **NOTE:** An API\
  \ key can only be assigned to an IP within 1 hour after its creation. After the\
  \ 1 hour, it will become invalid if not assigned. API keys that are created via\
  \ the sandbox app are wiped with each sandbox reset.\n\nOnce you have a sandbox\
  \ API key, create more sandbox users to use as test customer accounts, and start\
  \ playing with the API. \n\nThe sandbox base URL is https://public-api.sandbox.bunq.com/v1/.\n\
  \n## Sandbox money\nWithout money, it's not always sunny in the sandbox world. Fortunately,\
  \ getting money on the bunq sandbox is easy. All you need to do is ask Sugar Daddy\
  \ for it.\n\nSend a `POST v1/request-inquiry` request passing sugardaddy@bunq.com\
  \  in the counterparty_alias field. Specify the type for the alias and set the `allow_bunqme`\
  \ field. Request up to €500 at a time.\n```\n{\n    \"amount_inquired\": {\n   \
  \     \"value\": \"100\",\n        \"currency\": \"EUR\"\n    },\n    \"counterparty_alias\"\
  : {\n        \"type\": \"EMAIL\",\n        \"value\": \"sugardaddy@bunq.com\",\n\
  \        \"name\": \"Sugar Daddy\"\n    },\n    \"description\": \"You're the best!\"\
  ,\n    \"allow_bunqme\": false\n}\n```\n\n# <span id=\"topic-android-emulator\"\
  >Android Emulator</span>\n\nIn case you do not own an Android device on which you\
  \ can run our Sandbox app for end-to-end testing, you can set up an emulator to\
  \ run the bunq Sandbox app for Android.\n\n## Things you will need\n\n- The [bunq\
  \ Sandbox App APK](https://appstore.bunq.com/api/android/builds/bunq-android-sandbox-master.apk)\
  \ that's optimised for emulating;\n- [Android Studio](https://developer.android.com/studio/index.html).\n\
  \n## Starting the Android Virtual Device (AVD) Manager\n\n1. Open Android Studio.\n\
  2. From the top menu, select “Tools” > \"Android\" > \"AVD Manager\".\n\n## Setting\
  \ up a new virtual device\n\n1. Start the wizard by clicking on \"+ Create Virtual\
  \ Device\".\n2. Select a device (recommendation: \"Pixel 5.0\" or \"Nexus 6\") and\
  \ press \"Next\".\n3. Select an x86 system image (recommendation: Nougat, API Level\
  \ 25, Android 7.1.1 with Google APIs) and press \"Next\". The image needs to have\
  \ Google Play Services 10.0.1 or higher.\n4. In the bottom left corner, select \"\
  Show Advanced Settings\".\n5. Scroll to \"Memory and Storage\".\n6. Change \"Internal\
  \ Storage\" to \"2048 MB\".\n7. Change \"SD card\" to \"200 MB\".\n8. Press \"Finish\"\
  .\n\n## Starting the virtual device\n\n1. On the right side under \"Actions\", select\
  \ the green \"Play\" button.\n2. Wait for the device to boot, this may take a few\
  \ minutes.\n\n## Installing the bunq Sandbox App APK\n\n1. Open the command line.\n\
  2. Navigate to your Android SDK platform tools directory (e.g. `cd ~/Library/Android/sdk/platform-tools`\
  \ on macOS).\n3. Make sure that the virtual device is started and has fully booted.\n\
  4. Run `./adb install ~/Downloads/bunq-android-sandboxEmulator-public-api.apk`,\
  \ this may take a few minutes, and should finish with \"Success\".\n\n## Creating\
  \ an account or logging in\n\n1. Create a sandbox account in the [developer portal](https://developer.bunq.com/).\n\
  1. Log in to the sandbox app using the sandbox user credentials.\n\nℹ️ *You will\
  \ be asked to verify your phone number when you open the app for the first time.\
  \ Sandbox does not send actual SMS messages. Enter any valid phone number and use\
  \ the default verification code `992266`*. \n\nIf you couldn't generate a sandbox\
  \ account in the developer portal, use Tinker:\n1. Install [Tinker](https://beta.doc.bunq.com/quickstart/tinker).\n\
  1. Run `tinker/user-overview` to create a sandbox account. The output of the command\
  \ will include the login credentials for the sandbox account.\n\n⚠️ **NOTE:** It\
  \ is **not** possible to create accounts using the regular signup in the app, bunq\
  \ is not reviewing Sandbox applications.\n\n# <span id=\"topic-moving-to-production\"\
  >Moving to Production</span>\n\nHave you tested your bunq integration to the fullest\
  \ and are you now ready to introduce it to the world? Then the time has come to\
  \ move it to a production environment!\n\nTo get started you'll need some fresh\
  \ API keys for the production environment, which you can create via your bunq app.\
  \ You can create these under \"Profile\" by tapping the \"Security\" menu. We do,\
  \ however, highly recommend using a standard API Key instead of a Wildcard API Key.\
  \ The former is significantly safer and it protects you from intrusions and possible\
  \ attacks.\n\nThere's only a few things to do before your beautiful bunq creation\
  \ can be moved to production. You're going to have to change your API Key and redo\
  \ the sequence of calls to open a session.\n\nThe bunq Public API production environment\
  \ is hosted at `https://api.bunq.com`.\n\nDo you have any questions or remarks about\
  \ the process, or do you simply want to show off with your awesome creations? Don't\
  \ hesitate to drop us a line on [together.bunq.com](https://together.bunq.com).\n\
  \nPlease be aware that if you will gain access to account information of other bunq\
  \ users or initiate a payment for them, you  maybrequire a PSD2 permit.\n\n# <span\
  \ id=\"topic-quickstart-opening-a-session\">Quickstart: Opening a Session</span>\n\
  \n## <span id=\"topic-quickstart-opening-a-session-goal\">Goal</span>\n\nSo, you\
  \ want to start using the bunq API, awesome! To do this, you have to open a session\
  \ in which you will be making those calls.\n\n## <span id=\"topic-quickstart-opening-a-session-getting-an-api-key\"\
  >Getting an API key</span>\n\nTo connect to the API, you have to make sure you have\
  \ received an API key. \n\n**For production:**\n1. create an app in the [developer\
  \ portal](http://developer.bunq.com/), or\n1. generate it in the bunq app *(Profile\
  \ → Security & Settings → Developers → API keys)*.\n\n**For sandbox**\nYou can use\
  \ one of the following ways:\n- create a sandbox user in the [developer portal](http://developer.bunq.com/);\n\
  - generate an API key in the [sandbox app](#android-emulator) *(Profile → Security\
  \ & Settings → Developers → API keys)*;\n- get an API key from [Tinker](https://beta.doc.bunq.com/quickstart/tinker);\n\
  - run a cURL request: `curl https://public-api.sandbox.bunq.com/v1/sandbox-user-person\
  \ -X POST --header \"Content-Type: application/json\" --header \"Cache-Control:\
  \ none\" --header \"User-Agent: curl-request\" --header \"X-Bunq-Client-Request-Id:\
  \ $(date)randomId\" --header \"X-Bunq-Language: nl_NL\" --header \"X-Bunq-Region:\
  \ nl_NL\" --header \"X-Bunq-Geolocation: 0 0 0 0 000\"`. Use `sandbox-user-company`\
  \ to generate a business user.\n\nNote that production API key is only usable on\
  \ production and sandbox key is only usable on sandbox. Sandbox key has a `sandbox_`\
  \ prefix while production key does not have any noticeable prefixes.\n\n## <span\
  \ id=\"topic-quickstart-opening-a-session-call-sequence\">Call sequence</span>\n\
  \nThe calls you need to perform to set up a session from scratch are the following:\n\
  \n### <span id=\"topic-quickstart-opening-a-session-call-sequence-post-installation\"\
  >1. POST installation</span>\n\nEach call needs to be signed with your own private\
  \ key. An Installation is used to tell the server about the public key of your key\
  \ pair. The server uses this key to verify your subsequent calls.\n\nStart by generating\
  \ a 2048-bit RSA key pair. You can find examples by looking at the source code of\
  \ the sdk's located at github.\n\n#### Headers\n\nOn the headers page you can find\
  \ out about the mandatory headers. Take care that if you are in the sandbox environment,\
  \ you set an `Authorization` header. Specific to the `POST /installation` call,\
  \ you shouldn't use the `X-Bunq-Client-Authentication` or the `X-Bunq-Client-Signature`\
  \ headers.\n\n#### Body\n\nPost your public key to the Installation endpoint (use\
  \ `\\n` for newlines in your public key).\n\n#### Response\n\nSave the Installation\
  \ token and the bunq API's public key from the response. This token is used in the\
  \ `Authentication` header to register a `DeviceServer` and to start a `SessionServer`.\
  \ The bunq API's public key should be used to verify future responses received from\
  \ the bunq API.\n\n### <span id=\"topic-quickstart-opening-a-session-call-sequence-post-device-server\"\
  >2. POST device-server</span>\n\nFurther calls made to the server need to come from\
  \ a registered device. `POST /device-server` registers your current device and the\
  \ IP address(es) it uses to connect to the bunq API.\n\n#### Headers\n\nUse the\
  \ token you received from `POST /installation` in the `X-Bunq-Client-Authentication`\
  \ header. Make sure you sign your call, passing the call signature in `X-Bunq-Client-Signature`\
  \ header.\n\n#### Body\n\nFor the secret, use the API key you received. If you want\
  \ to create another API key, you can do so in the bunq sandbox app (or production\
  \ app for the production environment). Login, go to Profile > Security and tap 'API\
  \ keys'. The freshly created API key can be assigned to one or multiple IP addresses\
  \ using `POST device-server` within 4 hours before becoming invalid. As soon as\
  \ you start using your API key, it will remain valid until the next sandbox reset.\L\
  \L For the secret, use the API key you received.\n\n### <span id=\"topic-quickstart-opening-a-session-call-sequence-post-session-server\"\
  >3. POST session-server</span>\n\nTo make any calls besides `installation` and `device-server`,\
  \ you need to open a session.\n\n#### Headers\n\nUse the token you received from\
  \ `POST /installation` in the `X-Bunq-Client-Authentication` header. Make sure you\
  \ sign your call, passing the call signature in `X-Bunq-Client-Signature` header.\n\
  \n#### Body\n\nFor the secret, use the API key you received.\n\n#### Response\n\n\
  The token received in the response to `POST /session-server` should be used to authenticate\
  \ your calls in this session. Pass this session's token in the `X-Bunq-Client-Authentication`\
  \ header on every call you make in this session.\n\n# <span id=\"topic-quickstart-payment-request\"\
  >Quickstart: Payment Request</span>\n\n## <span id=\"topic-quickstart-payment-request-goal\"\
  >Goal</span>\n\nYou want to offer bunq payments on a website or in an application.\n\
  \n## <span id=\"topic-quickstart-payment-request-scenario\">Scenario</span>\n\n\
  In this use case the consumer and the merchant both have a bunq account. The consumer\
  \ wants to pay with bunq and enters their alias in the bunq payment field at checkout.\
  \ The merchant sends the request for payment to the consumer when the consumer presses\
  \ enter. The consumer agrees to the request in the bunq mobile app and the merchant\
  \ has immediate confirmation of the payment. Please be aware that if you will gain\
  \ access to account information of other bunq users or initiate a payment for them,\
  \ you require a PSD2 permit.\n\n## <span id=\"topic-quickstart-payment-request-before-you-start\"\
  >Before you start</span>\n\nMake sure that you have opened a session and that for\
  \ any call you make after that, you pass the session’s token in the X-Bunq-Client-Authentication\
  \ header.\n\n## <span id=\"topic-quickstart-payment-request-call-sequence\">Call\
  \ Sequence</span>\n\nThe consumer is at checkout and selects the bunq payment method.\
  \ This would be a logical time to open a session on the bunq server.\n\n### <span\
  \ id=\"topic-quickstart-payment-request-call-sequence-list-monetary-account\">1.\
  \ LIST monetary-account</span>\n\nWhen a request for payment is accepted, the money\
  \ will be deposited on the bank account the request for payment is connected to.\
  \ Let’s start by finding all your available bank accounts. Pick one of them to make\
  \ the request for payment with and save its `id`.\n\n### <span id=\"topic-quickstart-payment-request-call-sequence-post-monetary-account-attachment\"\
  >2. POST monetary-account attachment (optional)</span>\n\nOptionally, you can attach\
  \ an image to the request for payment.\n\n#### Headers\nMake sure you set the `Content-Type`\
  \ header to match the MIME type of the image. It’s also required you pass a description\
  \ of the image via the `X-Bunq-Attachment-Description` header.\n\n#### Body\nThe\
  \ payload of this request is the binary representation of the image file. Do not\
  \ use any JSON formatting.\n\n#### Response\nSave the `id` of the posted attachment.\
  \ You’ll need it to attach it to the request for payment.\n\n### <span id=\"topic-quickstart-payment-request-call-sequence-post-request-inquiry\"\
  >3. POST request-inquiry</span>\n\nNext, create a request inquiry. A request inquiry\
  \ is the request for payment that your customer can respond to by accepting or rejecting\
  \ it.\n\n#### Body\n\nPass the customer’s email address, phone number or IBAN in\
  \ the `counterparty_alias`. Make sure you set the correct `type` for the alias,\
  \ depending on what you pass. When providing an IBAN, a name of the `counterparty_alias`\
  \ is required. You can provide the `id` of the created attachment.\n\n#### Response\n\
  \nYou will receive the `id` of the created request inquiry in the response. Save\
  \ this `id`. You will need it to check if the customer has responded to the request\
  \ yet.\n\n### <span id=\"topic-quickstart-payment-request-call-sequence-get-request-inquiry\"\
  >4. GET request-inquiry</span>\n\nAfter you’ve sent the request for payment, its\
  \ status can be checked.\n\n#### Response\n\nWhen the `status` is `ACCEPTED`, the\
  \ customer has accepted and paid the request, and you will have received the money\
  \ on the connected monetary account. If the `status` is `REJECTED`, the customer\
  \ did not accept the request.\n\n# <span id=\"topic-quickstart-create-a-tab-payment\"\
  >Quickstart: Create a Tab payment</span>\n\n## <span id=\"topic-quickstart-create-a-tab-payment-goal\"\
  >Goal</span>\n\nYou will create a tab that can be paid once by a single user, a\
  \ so called TagUsageSingle, and explore three different ways to make the Tab visible\
  \ to your customers:\n\n- QR code from the CashRegister\n- QR code from the Tab.\n\
  \n## <span id=\"topic-quickstart-create-a-tab-payment-before-you-start\">Before\
  \ you start</span>\n\nMake sure that you have opened a session and that for any\
  \ call you make after that, you pass the session’s token in the `X-Bunq-Client-Authentication`\
  \ header.\n\n## <span id=\"topic-quickstart-create-a-tab-payment-call-sequence\"\
  >Call sequence</span>\n\n### <span id=\"topic-quickstart-create-a-tab-payment-call-sequence-post-attachment-public\"\
  >1. POST attachment-public</span>\n\nStart by creating an attachment that will be\
  \ used for the avatar for the cash register.\n\n#### Header\n\nMake sure you set\
  \ the `Content-Type` header to match the MIME type of the image. It is also required\
  \ you pass a description of the image via the `X-Bunq-Attachment-Description` header.\n\
  \n#### Body\n\nThe payload of this request is the binary representation of the image\
  \ file. Do not use any JSON formatting.\n\n#### Response\n\nSave the `uuid` of the\
  \ posted attachment. You'll need it to create the avatar in the next step.\n\n###\
  \ <span id=\"topic-quickstart-create-a-tab-payment-call-sequence-post-avatar\">2.\
  \ POST avatar</span>\n\nMake an avatar using the public attachment you've just created.\n\
  \n#### Body\n\nThe payload of this request is the `uuid` of the attachment public.\n\
  \n#### Response\n\nIn response, you’ll receive the UUID of the avatar created using\
  \ the attachment. Save this UUID. You’ll use it as the avatar for the cash register\
  \ you're about to create.\n\n### <span id=\"topic-quickstart-create-a-tab-payment-call-sequence-list-monetary-account\"\
  >3. LIST monetary-account</span>\n\nGet a listing of all available monetary accounts.\
  \ Choose one, and save the id of the monetary account you want your cash register\
  \ to be connected to. Each paid tab for the cash register will transfer the money\
  \ to this account.\n\n### <span id=\"topic-quickstart-create-a-tab-payment-call-sequence-post-cash-register\"\
  >4a. POST cash-register</span>\n\nCreate a cash register. Use the `id` of the monetary\
  \ account you want to connect the cash register to in the URL of the request.\n\n\
  #### Body\n\nIn the body provide the `uuid` of the avatar you created for this cash\
  \ register. Also make sure to provide a unique name for your cash register. Set\
  \ the status to `PENDING_APPROVAL`.\n\n#### Response\n\nThe response contains the\
  \ `id` of the cash register you created. Save this `id`. You will need it to create\
  \ subsequent tabs and tab items.\n\n### <span id=\"topic-quickstart-create-a-tab-payment-call-sequence-wait-for-approval\"\
  >4b. Wait for approval</span>\n\nOn the production environment, a bunq admin will\
  \ review and approve your cash register. In the sandbox environment, your cash register\
  \ will be automatically approved.\n\n### <span id=\"topic-quickstart-create-a-tab-payment-call-sequence-post-tab-usage-single\"\
  >5. POST tab-usage-single</span>\n\nCreate a new tab that is connected to your cash\
  \ register. Use the id of the cash register you want to connect this tab to in the\
  \ URL of your request.\n\n#### Body\n\nGive the tab a name in `merchant_reference`.\
  \ Create the tab with status `OPEN`, and give the tab a starting amount. You can\
  \ update this amount later.\n\n#### Response\n\nThe response contains the uuid of\
  \ the tab you created.\n\n### <span id=\"topic-quickstart-create-a-tab-payment-call-sequence-post-tab-item\"\
  >6. POST tab-item (optional)</span>\n\nYou can add items to a tab. For instance,\
  \ if a customer will be paying for multiple products via this tab, you can decide\
  \ to add an item for each of these. Adding items to a tab is optional, and adding\
  \ them will not change the total amount of the tab itself. However, if you've added\
  \ any tab items the sum of the amounts of these items must be equal to the `total_amount`\
  \ of the tab when you change its status to `WAITING_FOR_PAYMENT`.\n\n### <span id=\"\
  topic-quickstart-create-a-tab-payment-call-sequence-put-tab-usage-single\">7. PUT\
  \ tab-usage-single</span>\n\nUpdate the status of the tab to `WAITING_FOR_PAYMENT`\
  \ if you want the costumer to pay the tab, and you're done adding any tab items.\
  \ You can use this request to make the tab visible for your costumers.\n\n#### Visibility\n\
  \nTo decide how you are going to make your tab visible, pass a visibility object\
  \ in the payload.\n\nSetting `cash_register_qr_code` to true will connect this tab\
  \ to the QR code from the cash register. If this cash register does not have a QR\
  \ code yet, one will be created. Only one Tab can be connected to the cash register’\
  s QR code at any given time.\n\nSetting `tab_qr_code` to true will create a QR code\
  \ specifically for this tab. This QR code can not be linked to anything else.\n\n\
  # <span id=\"topic-quickstart-transwerwise-payment\">Quickstart: Create a TransferWise\
  \ payment</span>\n\n## Goal\n\nYou want to send a payment in currency other than\
  \ euro outside the SEPA zone.\n\n## Before you start\n\nMake sure that you have\
  \ opened a session and that for any call you make after that, you pass the session’\
  s token in the `X-Bunq-Client-Authentication` header.\n\nℹ️ *bunq relies on TransferWise\
  \ for international, so you need to create a TransferWise account linked to a bunq\
  \ account to be able to create international transfers. You can do it either from\
  \ the bunq app or using our API as described below.*\n\n## Get the up-to-date exchange\
  \ rate (optional)\n\nYou might want to check the latest currency exchange rate before\
  \ making a transfer. Here’s how you can do it using the bunq API:\n1. Check the\
  \ list of supported currencies via `GET /user/{userID}/transferwise-currency`. Copy\
  \ the needed currency code.\n2. Create a temporary quote for the currency of your\
  \ choice via `POST /user/{userID}/transferwise-quote-temporary`.\n\nℹ️ *A quote\
  \ is the exchange rate at the exact timestamp. Temporary quotes carry solely informative\
  \ value and cannot be used for creating a transfer.*\n\n3. Read the temporary quote\
  \ via `GET /user/{userID}/transferwise-quote-temporary/{transferwise-quote-temporaryID}`.\n\
  \n## Create a TransferWise account\n\nYou need a TransferWise account linked to\
  \ your bunq account to make TransferWise payments via the bunq API. Create one via\
  \ `POST /user/{userID}/transferwise-user`, and save its ID. \n\nℹ️ *You cannot use\
  \ an existing TransferWise account.*\n\n## Create a quote\n\n1. Create a quote via\
  \ POST /user/{userID}/transferwise-quote and save its ID. \n\nℹ️ *Use amount_target\
  \ to indicate the sum the recipient must get. Amount_source, on the other hand,\
  \ will indicate the sum you want to send, but it will not necessarily be the final\
  \ sum the recipient gets.*\n\nℹ️ *Quotes are valid for 30 minutes so if you do not\
  \ manage to create a transfer within this time, you will need to create another\
  \ quote.*\n\n2. Get the exchange rate by reading the quote via GET /user/{userID}/transferwise-quote/(transferwise-quoteID).\n\
  \n## Create a recipient\n\nIf you have sent money via the TransferWise account linked\
  \ to your bunq account, you can reuse the recipients. You can list their IDs via\
  \ `GET /user/{userID}/transferwise-quote/{transferwise-quoteID}/transferwise-recipient`.\n\
  \nTo create a new, previously unused recipient, follow these steps:\n1. Retrieve\
  \ the fields required for creating the recipient as the requirements vary for the\
  \ type of recipient in each country. Iterate sending the following request pair\
  \ till there are no more required fields:\n- `GET /user/{userID}/transferwise-quote/{transferwise-quoteID}/transferwise-recipient-requirement`\n\
  - `POST /user/{userID}/transferwise-quote/{transferwise-quoteID}/transferwise-recipient-requirement`\n\
  2. Create a recipient account using the final request body from the previous step\
  \ with `POST /user/{userID}/transferwise-quote/{transferwise-quoteID}/transferwise-recipient-requirement`\n\
  \n## Create a transfer\n\nFinally, having both the quote ID and the recipient ID,\
  \ you can create a transfer. 🎉\n\n1. Check if there are any additional transfer\
  \ requirements via `POST /user/{userID}/transferwise-quote/{transferwise-quoteID}/transferwise-transfer-requirement`.\n\
  2. Create a transfer via `POST /user/{userID}/transferwise-quote/{transferwise-quoteID}/transferwise-transfer`.\
  \ You need to specify the ID of the monetary account from which you want the payment\
  \ to be made.\n\n# <span id=\"topic-quickstart-attachments\">Quickstart: Downloading\
  \ attachments</span>\n\n## Goal\nExport receipts and invoices attached to payments\
  \ to your application.\n\n## The scenario you want to achieve\n0. The bunq user\
  \ has accepted the authorization request and your application can read the bunq\
  \ user’s account information.\n1. Your application imports all the transactions\
  \ and attachments.\n2. The bunq user sees the transactions matched with the receipts\
  \ and invoices in your application.\n\n## Before you start\n* Make sure that you\
  \ have opened a session\n* Make sure you pass the session Token in the X-Bunq-Client-Authentication\
  \ header in all the following requests of the session.\n\n## Call sequence\n1. List\
  \ the payments of the user via GET /user/{userID}/monetary-account/{monetary-accountID}/payment.\n\
  2. Check if the payments have attachments via GET /user/{userID}/monetary-account/{monetary-accountID}/payment/{paymentID}/note-attachment.\
  \ Save the attachment IDs.\n3. Export the raw content of the attachments via GET\
  \ /user/{userID}/attachment/{attachmentID}/content.\n\n***HINT:** You can use [callbacks](https://doc.bunq.com/#/callbacks)\
  \ to make sure you don’t miss anything happening on the bunq account.*\n"
logo: "bunq.com-logo.jpeg"
logoMediaType: "image/jpeg"
tags:
- "financial"
stubs: "bunq.com-stubs.json"
swagger: "bunq.com-swagger.json"
---