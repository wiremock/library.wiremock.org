---
slug: "enode-io"
title: "Enode API"
provider: "enode.io"
description: "Download [OpenAPI 3.0 Specification](/OpenAPI-Enode-v1.4.0.json)\n\n\
  Download [Postman Collection](/Postman-Enode-v1.4.0.json)\n\nThe Enode API is designed\
  \ to make smart charging applications easy to develop. We provide an abstraction\
  \ layer that reduces the complexity when extracting vehicle data and sending commands\
  \ to vehicles from a variety of manufacturers.\n\nThe API has a RESTful architecture\
  \ and utilizes OAuth2 authorization.\n\nWe are always available to handle any issues\
  \ or just answer your questions. Feel free to reach out on post@enode.io\n\n\n##\
  \ Registration for API access\nIn order to use the API you will need a `client_id`\
  \ and `client_secret`. Please contact us if you are interested in using our API\
  \ in production, and we will provide these credentials.\n\n# Authorization\nVehicle\
  \ / hardware access via the Enode API is granted to your application by the User\
  \ in a standard OAuth `Authorization Code` flow.\n\n> The authorization scheme documented\
  \ here is the recommended approach for most situations. However, it is also possible\
  \ to user other OAuth flows, non-confidential clients, and temporary users. Please\
  \ feel free to contact us if you have any questions about your use-case or the integration\
  \ of your existing infrastructure.\n\n### Preparation: Configure your OAuth client\n\
  \nBecause Enode API implements the OAuth 2.0 spec completely and without modifications,\
  \ you can avoid rolling your own OAuth client implementation and instead use a well-supported\
  \ and battle-tested implementation. This is strongly recommended. Information on\
  \ available OAuth clients for many languages is available [here](https://oauth.net/code/)\n\
  \nTo configure your chosen OAuth client, you will need these details:\n- Your `client_id`\n\
  - Your `client_secret`\n- Authorization URL: `https://link.test.enode.io/oauth2/auth`\n\
  - Token URL: `https://link.test.enode.io/oauth2/token`\n\n```javascript\n// Node.js\
  \ + openid-client example\nconst enodeIssuer = await Issuer.discover('https://link.test.enode.io');\n\
  const client = new enodeIssuer.Client({\n  client_id: 'xyz',\n  client_secret: 'shhhhh',\n\
  \  redirect_uris: ['http://localhost:5000/callback'],\n  response_types: ['code'],\n\
  });\n```\n\n\n### Preparation: Obtain a client access token via OAuth Client Credentials\
  \ Grant\nYour OAuth client will have a method for using the `OAuth 2.0 Client Credentials\
  \ Grant` to obtain an access token.\n\n```javascript\n// Node.js + openid-client\
  \ example\nconst clientAccessToken = await client.grant({grant_type: \"client_credentials\"\
  });\n```\n\nThis access token belongs to your client and is used for administrative\
  \ actions, such as the next step.\n\nThis token should be cached by your server\
  \ and reused until it expires, at which point your server should request a new one.\n\
  \n\n\n### Step 1. Generate an Enode Link session for your User and launch the OAuth\
  \ flow\n\nWhen your User indicates that they want to connect their hardware to your\
  \ app, your server must call [Link User](#operation/postUsersUseridLink) to generate\
  \ an Enode Link session for your User. The User ID can be any string that uniquely\
  \ identifies the User, but it is recommended that you use the primary key by which\
  \ you identify the User within your application.\n\nExample Request:\n```\nPOST\
  \ /users/{userId}/link HTTP/1.1\nAuthorization: Bearer {access_token}\n{\n  \"forceLanguage\"\
  : \"nb-NO\",\n  \"vendor\": \"Tesla\",\n}\n```\n\nExample Response:\n```\n{\n  \
  \  \"linkState\": \"ZjE2MzMxMGFiYmU4MzcxOTU1ZmRjMTU5NGU2ZmE4YTU3NjViMzIwY2YzNG\"\
  ,\n}\n```\n\nThe returned linkState must be stored by your server, attached to the\
  \ session of the authenticated user for which it was generated.\n\nYour OAuth client\
  \ will provide a method to construct an authorization URL for your user. That method\
  \ will require these details:\n- Redirect URI - The URI to which your user should\
  \ be redirected when the Oauth flow completes\n- Scope - The OAuth scope(s) you\
  \ wish to request access to (see list of valid values [here](#section/Authentication/AccessTokenBearer))\n\
  - State - The value of `linkState` from the request above\n\nTo launch the OAuth\
  \ flow, send your user to the authorization URL constructed by your OAuth client.\
  \ This can be done in an embedded webview within a native iOS/Android app, or in\
  \ the system's default browser.\n\n```javascript\n// Node.js + openid-client + express\
  \ example\n\n// Construct an OAuth authorization URL\nconst authorizationUrl = client.authorizationUrl({\n\
  \  scope: \"offline_access all\",\n  state: linkState\n});\n\n// Redirect user to\
  \ authorization URL\nres.redirect(authorizationUrl);\n```\n\n\n### Step 2. User\
  \ grants consent\nIn the Link UI webapp the user will follow 3 steps:\n\n1. Choose\
  \ their hardware from a list of supported manufacturers (EVs and charging boxes).\
  \ For certain EV makes it will be necessary to also select a charge box.\n2. For\
  \ each selection, the user will be presented with the login screen for that particular\
  \ hardware. The user must successfully log in.\n3. A summary of the requested scopes\
  \ will be presented to the user. The user must choose whether to grant access to\
  \ your application.\n\n\n### Step 3. OAuth flow concludes with a callback\nWhen\
  \ the user has completed their interactions, they will be redirected to the `Redirect\
  \ URI` you provided in Step 1, with various metadata appended as query parameters.\n\
  \nYour OAuth client will have a method to parse and validate that metadata, and\
  \ fetch the granted access and refresh tokens.\n\nAmong that metadata will be a\
  \ `state` value - you must verify that it is equal to the `linkState` value persisted\
  \ in Step 1, as [a countermeasure against CSRF attacks](https://tools.ietf.org/html/rfc6819#section-4.4.1.8).\n\
  \n```javascript\n// Node.js + openid-client + express example\n\n// Fetch linkState\
  \ from user session\nconst linkState = get(req, 'session.linkState');\n\n// Parse\
  \ relevant parameters from request URL\nconst params = client.callbackParams(req);\n\
  \n// Exchange authorization code for access and refresh tokens\n// In this example,\
  \ openid-client does the linkState validation check for us\nconst tokenSet = await\
  \ client.oauthCallback('http://localhost:5000/callback', params, {state: linkState})\n\
  ```\n\nWith the access token in hand, you can now access resources on behalf of\
  \ the user.\n\n\n# Errors And Problems\n## OAuth Authorization Request\n\nWhen the\
  \ User has completed the process of allowing/denying access in Enode Link, they\
  \ will be redirected to your configured redirect URI. If something has gone wrong,\
  \ query parameters `error` and `error_description` will be set as documented in\
  \ [Section 4.1.2.1](https://tools.ietf.org/html/rfc6749#section-4.1.2.1) of the\
  \ OAuth 2.0 spec:\n\n|error                      |error_description|\n|---------------------------|-----------------|\n\
  |invalid_request            |The request is missing a required parameter, includes\
  \ an invalid parameter value, includes a parameter more than once, or is otherwise\
  \ malformed.|\n|unauthorized_client        |The client is not authorized to request\
  \ an authorization code using this method.|\n|access_denied              |The resource\
  \ owner or authorization server denied the request.|\n|unsupported_response_type\
  \  |The authorization server does not support obtaining an authorization code using\
  \ this method.|\n|invalid_scope              |The requested scope is invalid, unknown,\
  \ or malformed.|\n|server_error               |The authorization server encountered\
  \ an unexpected condition that prevented it from fulfilling the request.|\n|temporarily_unavailable\
  \    |The authorization server is currently unable to handle the request due to\
  \ a temporary overloading or maintenance of the server|\n\nExample:\n```\nhttps://website.example/oauth_callback?state=e0a86fe5&error=access_denied&error_description=The+resource+owner+or+authorization+server+denied+the+request.\n\
  ```\n\n\n## Errors when accessing a User's resources\n\nWhen using an `access_token`\
  \ to access a User's resources, the following HTTP Status Codes in the 4XX range\
  \ may be encountered:\n\n|HTTP Status Code           |Explanation      |\n|---------------------------|-----------------|\n\
  |400 Bad Request            |The request payload has failed schema validation /\
  \ parsing\n|401 Unauthorized           |Authentication details are missing or invalid\n\
  |403 Forbidden              |Authentication succeeded, but the authenticated user\
  \ doesn't have access to the resource\n|404 Not Found              |A non-existent\
  \ resource is requested\n|429 Too Many Requests      |Rate limiting by the vendor\
  \ has prevented us from completing the request\n\n\nIn all cases, an [RFC7807 Problem\
  \ Details](https://tools.ietf.org/html/rfc7807) body is returned to aid in debugging.\n\
  \nExample:\n```\nHTTP/1.1 400 Bad Request\nContent-Type: application/problem+json\n\
  {\n  \"type\": \"https://docs.enode.io/problems/payload-validation-error\",\n  \"\
  title\": \"Payload validation failed\",\n  \"detail\": \"\\\"authorizationRequest.scope\\\
  \" is required\",\n}\n```\n\n"
logo: "enode.io-logo.svg"
logoMediaType: "image/svg+xml"
tags:
- "location"
stubs: "enode.io-stubs.json"
swagger: "enode.io-swagger.json"
---
