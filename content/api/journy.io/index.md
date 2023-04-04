---
slug: "journy-io"
title: "Developer documentation"
provider: "journy.io"
description: "# Welcome\n\nImplementing a new tool can be daunting, but it doesn't\
  \ have to. You can implement journy.io in a few different ways to ensure it fits\
  \ with the rest of your tech stack seamlessly.\n\nWe welcome your feedback, ideas\
  \ and suggestions. We really want to make your life easier, so if we’re falling\
  \ short or should be doing something different, we want to hear about it. Send us\
  \ an email at [hi@journy.io](mailto:hi@journy.io) or reach out via the chat on our\
  \ website or on our platform.\n\nThere are multiple ways you can send us data about\
  \ users and accounts. We have both frontend and backend APIs, which can be used\
  \ together at the same time.\n\nIf you already use [Segment](https://segment.com/),\
  \ you can [get up and running with journy.io in seconds](https://help.journy.io/en/articles/6488307-the-segment-connector).\n\
  \n# Concepts\n\n## Users\n\nThe most basic entity is a user, a specific individual\
  \ that completed an interaction with your product.\n\nWe support multiple types\
  \ of users, often differentiated by it's external ID prefix. E.g. In the case you\
  \ are building an ordering app, there could easily be an administrator (who updates\
  \ products and checks for orders) and the end-customers who place orders. One could\
  \ have a typical ADM-XXXXXXXX ID, while the other would be referenced by USR-XXXXXXXXX.\n\
  \n## Accounts\n\nIn B2B SaaS, users can be part of multiple accounts. E.g. Imagine\
  \ you're building a content scheduling app where an agency can manage the social\
  \ media posts of their clients. Each client of the agency has its own account in\
  \ the product.\n\nIf your app doesn't have the concept of a team or group of users,\
  \ you can ignore accounts.\n\n## Events\n\nAn event is a data point that represents\
  \ an interaction between a user and/or an account; and your product. Events can\
  \ represents any range of interactions. E.g. Every time a customer creates an invoice\
  \ in an invoicing app. Actions like creating an invoice can be tracked as an event\
  \ in journy.io.\n\nIt's critical to track events properly. You'll need to provide\
  \ either an account ID, or a user ID, or both; when tracking an event. E.g. If a\
  \ user updates his personal settings, you can omit the account ID as the event would\
  \ not be related to any account. In a same logic, an account could get a 'suspend\
  \ account' event (with account ID) from an internal process, whereas no user would\
  \ be associated. In most cases, events will be associated to both 1 user and 1 account.\n\
  \nYou can optionally pass extra details as metadata (e.g. amount of the invoice).\
  \ This gets particarly powerfull when creating computed properties on those event\
  \ metadata. E.g. Our above ordering app could send journy.io 'Place Order' events\
  \ with metadata 'price', on which journy.io very easily would compute a total order\
  \ value (for each account) for the last 30 days.\n\n💡 Metadata does not update\
  \ the properties of a user or account.\n\n# Frontend vs backend\n\nThe best implementations\
  \ we see employ a hybrid approach to maximize data quality while maintaining the\
  \ flexibility to easily collect the data they need.\n\nWe recommend using our JavaScript\
  \ snippet to track screen views and our backend API to sync users, sync accounts\
  \ and track events.\n\nWhen evaluating how to track a particular event, we suggest\
  \ starting with server-side and only use frontend if it's not possible to collect\
  \ purely server-side. This can be the case if you need to track interactions with\
  \ your product that don't result in any natural server requests (such as a button\
  \ click that opens a modal).\n\n# Frontend\n\n## Setup\n\n💡 You can find the JavaScript\
  \ snippet in the website settings in the connections view.\n\nCopy the JavaScript\
  \ snippet and place it in the head or body of your application.\n\nThe snippet automatically\
  \ calls `journy(\"init\", { ... })` and `journy(\"pageview\")`.\n\n## Identify user\n\
  \n💡 A user ID should be a robust, static, unique identifier that you recognize\
  \ a user by in your own systems. Because these IDs are consistent across a customer’\
  s lifetime, you should include a user ID in identify calls as often as you can.\
  \ Ideally, the user ID should be a database ID.\n\n💡 journy.io does not recommend\
  \ using simple email addresses or usernames as user ID, as these can change over\
  \ time. journy.io recommends that you use static IDs instead, so the IDs never change.\
  \ When you use a static ID, you can still recognize the user in your analytics tools,\
  \ even if the user changes their email address.\n\n💡 The properties `full_name`,\
  \ `first_name`, `last_name`, `phone` and `registered_at` will be used for creating\
  \ contacts in destinations like Intercom, HubSpot, Salesforce, ...\n\n`journy(\"\
  identify\")` allows you to identify the user that is currently using your product.\n\
  \n```ts\njourny(\"identify\", {\n  // Email or user ID is required\n  email: \"\
  john.doe@acme.com\",\n  // Unique identifier for the user in your database\n  userId:\
  \ \"20\",\n\n  // Optional\n  // Hash of the user ID using a backend secret\n  //\
  \ You can find the secret in the website settings\n  // Recommended to prevent spoofing\n\
  \  verification: \"hash\",\n\n  // Optional\n  properties: {\n    full_name: \"\
  John Doe\",\n    // or\n    first_name: \"John\",\n    last_name: \"Doe\",\n\n \
  \   phone: \"123\",\n    registered_at: new Date(/* ... */),\n    is_admin: true,\n\
  \    key_with_empty_value: \"\",\n    this_property_will_be_deleted: null,\n  },\n\
  });\n```\n\n## Identify account\n\n💡 An account ID should be a robust, static,\
  \ unique identifier that you recognize an account by in your own systems. Ideally,\
  \ the account ID should be a database ID.\n\n💡 The properties `name`, `mrr`, `plan`\
  \ and `registered_at` will be used to create companies in destinations like Intercom,\
  \ HubSpot, Salesforce, ...\n\n`journy(\"account\")` allows you to identify the business\
  \ account (i.e. organization) using your product.\n\n```ts\njourny(\"account\",\
  \ {\n  // Required\n  // Unique identifier for the account in your database\n  accountId:\
  \ \"30\",\n\n  // Optional\n  // Hash of the account ID using a backend secret\n\
  \  // You can find the secret in the website settings\n  // Recommended to prevent\
  \ spoofing\n  verification: \"hash\",\n\n  // Optional\n  properties: {\n    name:\
  \ \"ACME, Inc\",\n    mrr: 399,\n    plan: \"Pro\",\n    registered_at: new Date(/*\
  \ ... */),\n    is_paying: true,\n    key_with_empty_value: \"\",\n    this_property_will_be_deleted:\
  \ null,\n  },\n});\n```\n\n## Send page view\n\n💡 In applications, we advise you\
  \ to use screen views instead of page views.\n\nThe JavaScript snippet in the site\
  \ settings includes a `pageview` by default.\n\n```ts\njourny(\"pageview\");\n```\n\
  \nIf you have a B2B application, we recommend to set account ID for every page view\
  \ that happens within the context of an account.\n\n💡 An account ID should be a\
  \ robust, static, unique identifier that you recognize an account by in your own\
  \ systems. Ideally, the account ID should be a database ID.\n\n```ts\njourny(\"\
  pageview\", {\n  accountId: \"30\",\n\n  // Optional\n  // Hash of the account ID\
  \ using a backend secret\n  // You can find the secret in the website settings\n\
  \  // Recommended to prevent spoofing\n  verification: \"hash\",\n});\n```\n\n##\
  \ Send screen view\n\nIn applications, we strongly advise you to use screen views\
  \ instead of page views.\n\nPage URLs in applications often include the account\
  \ ID (e.g. https://app.acme.com/accountId/settings).\n\nThis makes it difficult\
  \ to create signals, segments, ... based on those URLs.\n\nThat's what screen views\
  \ solve. It allows you to set a name for the screen being viewed (e.g. Account settings).\n\
  \n```ts\njourny(\"screen\", { name: \"Personal settings\" });\n```\n\nIf you have\
  \ a B2B application, we recommend to set account ID for every screen view that happens\
  \ within the context of an account.\n\nExample: \"Personal settings\" would be without\
  \ account ID, \"Team settings\" would be with account ID.\n\n💡 An account ID should\
  \ be a robust, static, unique identifier that you recognize an account by in your\
  \ own systems. Ideally, the account ID should be a database ID.\n\n```ts\njourny(\"\
  screen\", {\n  name: \"Account settings\",\n  accountId: \"30\",\n\n  // Optional\n\
  \  // Hash of the account ID using a backend secret\n  // You can find the secret\
  \ in the website settings\n  // Recommended to prevent spoofing\n  verification:\
  \ \"hash\",\n});\n```\n\n## Trigger an event\n\n💡 Use past tense for event names.\n\
  \nUser events:\n\n```js\njourny(\"event\", {\n  // required\n  name: \"signed_in\"\
  ,\n\n  // optional\n  metadata: {\n    key: \"value\",\n  },\n});\n```\n\nAccount\
  \ events:\n\n💡 An account ID should be a robust, static, unique identifier that\
  \ you recognize an account by in your own systems. Ideally, the account ID should\
  \ be a database ID.\n\n```js\njourny(\"event\", {\n  // required\n  name: \"created_invoice\"\
  ,\n  accountId: \"30\",\n\n  // Optional\n  // Hash of the account ID using a backend\
  \ secret\n  // You can find the secret in the website settings\n  // Recommended\
  \ to prevent spoofing\n  verification: \"hash\",\n\n  // optional\n  metadata: {\n\
  \    key: \"value\",\n    amount: 100,\n    allow_wire_transfer: true,\n  },\n});\n\
  ```\n\n## Identity verification\n\nIdentity verification ensures that one person\
  \ can't impersonate another.\n\nIdentity verification requires you to add an hash\
  \ (HMAC) (that you generate on your server using SHA256) to your installation snippet\
  \ alongside your user ID and account ID.\n\njourny.io won't accept requests for\
  \ a logged-in user without a valid hash. The hash is calculated using a secret key,\
  \ which you should never share. Without this secret key, no third party can send\
  \ journy.io a valid hash for one of your users, so they can't impersonate your users.\n\
  \nThis is optional but highly recommended.\n\nYou can enable identify verification\
  \ in the website settings in the connections view.\n\n```js\njourny(\"identify\"\
  , {\n  userId: \"userId\",\n  verification: \"USER_ID_HMAC_VALUE_HERE\"\n})\n\n\
  journy(\"account\", {\n  accountId: \"accountId\",\n  verification: \"ACCOUNT_ID_HMAC_VALUE_HERE\"\
  \n})\n\njourny(\"event\", {\n  accountId: \"accountId\",\n  verification: \"ACCOUNT_ID_HMAC_VALUE_HERE\"\
  \n})\n```\n\n### PHP\n\n```php\n<?php\n\nhash_hmac(\n  'sha256', // hash function\n\
  \  id, // user or account ID\n  'secret' // secret key (keep safe!)\n);\n```\n\n\
  ### Node.js\n\n```js\nimport { createHmac } from \"crypto\"\n\ncreateHmac(\n  \"\
  sha256\", // hash function\n  'secret' // secret key (keep safe!)\n).update(id).digest(\"\
  hex\") // user or account ID\n```\n\n### Ruby\n\n```ruby\nOpenSSL::HMAC.hexdigest(\n\
  \  'sha256', # hash function\n  'secret', # secret key (keep safe!)\n  id.to_s #\
  \ user or account ID\n)\n```\n\n### Python\n\n```\nimport hmac\nimport hashlib\n\
  \nhmac.new(\n  b'secret', # secret key (keep safe!)\n  bytes(id, encoding='utf-8'),\
  \ # user or account ID\n  digestmod=hashlib.sha256 # hash function\n).hexdigest()\n\
  ```\n\n## Single page application\n\nYou can use our JavaScript snippet inside single\
  \ page applications.\n\nYou should call `journy(\"screen\")` (or `journy(\"pageview\"\
  )`) whenever a user in your application transitions to another page. You can do\
  \ this by listening to router change events. The current page URL will always be\
  \ resolved using `window.location.href`.\n\nYou can trigger events using `journy(\"\
  event\")` whenever you need to.\n\n### Next.js\n\nWe built a demo app with Next.js.\
  \ You can find the code [here](https://github.com/journy-io/js-sdk-demo-app).\n\n\
  This [component](https://github.com/journy-io/js-sdk-demo-app/blob/main/components/Journy.js)\
  \ should be a great start.\n\nYou can use the `Script` component from Next.js to\
  \ load the web snippet and call `init`.\n\nDon't forget to listen on route changes.\
  \ You can use the `useRouter` hook for that.\n\n### React Router v6\n\nYou can use\
  \ the [`useLocation`](https://reactrouter.com/docs/en/v6/api#uselocation) hook to\
  \ listen for route changes:\n\n```js\nimport React, { useEffect } from \"react\"\
  ;\nimport { useLocation } from 'react-router-dom';\n\nfunction App() {\n  const\
  \ location = useLocation();\n\n  useEffect(() => {\n    journy(\"screen\", { name:\
  \ \"name\" });\n    // or\n    journy(\"pageview\");\n  }, [location]);\n\n  return\
  \ (\n      // ...\n  );\n}\n```\n\n### Vue Router\n\nYou can use [`router.afterEach`](https://router.vuejs.org/guide/advanced/navigation-guards.html#global-after-hooks)\
  \ to listen for route changes:\n\n```js\nconst router = new VueRouter({ ... });\n\
  \nrouter.afterEach((to, from) => {\n  journy(\"screen\", { name: \"name\" });\n\
  \  // or\n  journy(\"pageview\");\n});\n```\n\nNote: We don't accept a page URL\
  \ argument for `journy(\"pageview\")`. The current page URL will always be resolved\
  \ using `window.location.href`.\n\n## TypeScript\n\nWe published an [npm package](https://www.npmjs.com/package/@journyio/web-types)\
  \ with type definitions to enable type-safe usage of our JavaScript snippet. The\
  \ code and documentation is available on [GitHub](https://github.com/journy-io/web-types).\n\
  \n## Localhost\n\nBy default a site doesn't allow page views from other domains\
  \ than the registered domain. This makes it difficult to test your tracking implementation\
  \ locally.\n\nYou can enable \"Allow any domain\" in the site settings to disable\
  \ the domain check.\n\nThis will allow you to test the JavaScript snippet with localhost\
  \ as hostname.\n\n# Backend\n\nThe journy.io API is organized around REST. Our API\
  \ has predictable resource-oriented URLs, returns JSON-encoded responses, and uses\
  \ standard HTTP response codes, authentication, and verbs.\n\nThe API is hosted\
  \ on api.journy.io.\n\n## Official SDKs\n\nOur SDKs are designed to help you interact\
  \ with our APIs with less friction. They are written in several different languages\
  \ and help bridge the gap between your application and journy.io APIs. They take\
  \ away the need to know the exact URL and HTTP method to use for each API call among\
  \ other things leaving you more time to focus on making your application.\n\n| Language\
  \   | Package                                                                  \
  \      | Source code                                                           \
  \     |\n|------------|--------------------------------------------------------------------------------|----------------------------------------------------------------------------|\n\
  | 💚 Node.js | [npm install @journyio/sdk ](https://www.npmjs.com/package/@journyio/sdk)\
  \      | [github.com/journy-io/js-sdk](https://github.com/journy-io/js-sdk)    \
  \     |\n| 🐘 PHP     | [composer require journy-io/sdk](https://packagist.org/packages/journy-io/sdk)\
  \ | [github.com/journy-io/php-sdk](https://github.com/journy-io/php-sdk)       |\n\
  | 🐍 Python  | [pip install journyio-sdk](https://pypi.org/project/journyio-sdk/)\
  \             | [github.com/journy-io/python-sdk](https://github.com/journy-io/python-sdk)\
  \ |\n| 💎 Ruby    | Coming soon                                                \
  \                    | Coming soon                                             \
  \                   |\n\nYour favourite programming language not included? [Let\
  \ us know!](mailto:hi@journy.io)\n\nIn the meanwhile, you can use [OpenAPI Generator](https://github.com/OpenAPITools/openapi-generator)\
  \ to generate a client for your programming language.\n\n## Authentication\n\nThe\
  \ journy.io API uses API keys to authenticate requests. You can view and manage\
  \ your API keys in the [connections screen](https://system.journy.io).\n\nYour API\
  \ keys carry many privileges, so be sure to keep them secure! Do not share your\
  \ secret API keys in publicly accessible areas such as GitHub, client-side code,\
  \ and so forth.\n\nAll API requests must be made over HTTPS. Calls made over plain\
  \ HTTP will fail. API requests without authentication will also fail.\n\nFor every\
  \ request send to the API we expect a header `X-Api-Key` to be set with the API\
  \ Key.\n\n## Permissions\n\nWhen creating an API Key in [the application](https://system.journy.io)\
  \ you will have the choice to give permissions to an API Key (which you can change\
  \ later on). These permissions restrict the API Key from different actions. When\
  \ an API Key tries to perform a certain action it doesn't have the permissions for,\
  \ you will receive a `401: Unauthorized` response.\n\n## Rate limiting\n\nTo prevent\
  \ abuse of the API there is a maximum throughput of 1800 requests per minute. If\
  \ you need a higher throughput, please contact us.\n\nTo keep our platform healthy\
  \ and stable, we'll block API keys that consistently hit our rate limits. Therefore,\
  \ please consider taking this throughput into account.\n\nIn every response the\
  \ headers `X-RateLimit-Limit` and `X-RateLimit-Remaining` will be set. The `X-RateLimit-Limit`-header\
  \ will always contain the current limit of requests per minute. The `X-RateLimit-Remaining`-header\
  \ will always contain the amount of requests you have left in the current sliding\
  \ window.\n\n💡 The client-side tracking uses different rate limits.\n\n## Errors\n\
  \njourny.io uses conventional HTTP response codes to indicate the success or failure\
  \ of an API request. In general: Codes in the 2xx range indicate success. Codes\
  \ in the 4xx range indicate an error that failed given the information provided\
  \ (e.g. a required parameter was omitted). Codes in the 5xx range indicate an error\
  \ with journy.io's servers (these are rare).\n\nWhen performing a `POST`- or `PUT`-request\
  \ with a requestBody, or when including parameters, these parameters and fields\
  \ will automatically be checked and validated against the API Spec. When any error\
  \ occurs, you will get a response with an `errors`-field, structured as follows:\n\
  \n```json\n{\n  \"errors\": {\n    \"parameters\": {\n      \"header\": {\n    \
  \    \"headerParameterName\": \"Describe what's wrong with the header parameter.\"\
  ,\n        ...\n      },\n      \"query\": {\n        \"queryParameterName\": \"\
  Describe what's wrong with the query parameter.\",\n        ...\n      },\n    \
  \  \"path\": {\n        \"pathParameterName\": \"Describe what's wrong with the\
  \ path parameter.\",\n        ...\n      },\n    },\n    \"fields\": {\n      \"\
  fieldName\": \"Describe what's wrong with the fieldName.\",\n      \"object.fieldName\"\
  : \"Describe what's wrong with the fieldName of the included object.\",\n      \
  \ ...\n    }\n  }\n}\n```\n\n## Best practices\n\n### Track accounts & users immediately\
  \ on creation\n\nWhen you create an account in your database, immediately sending\
  \ data about that account to journy.io helps your team stay in sync. The same goes\
  \ for users. Call [Upsert account](#operation/upsertAccount) as soon as possible,\
  \ right after the account is first created in your database.\n\n### Update account\
  \ data daily\n\nNot every account is active every day. But, you may have properties\
  \ on the account that change through background processing. That's why we recommend\
  \ updating every one of your accounts' data in a recurring daily process. This way,\
  \ you know that your accounts are updated every day in journy.io.\n\n## Changelog\n\
  \n### December 2021\n\n[POST /events](#operation/trackJourneyEvent) will be moved\
  \ to [POST /track](#operation/trackEvent). [POST /events](#operation/trackJourneyEvent)\
  \ is deprecated and will be removed in the future."
logo: "journy.io-logo.png"
logoMediaType: "image/png"
tags:
- "customer_relation"
stubs: "journy.io-stubs.json"
swagger: "journy.io-swagger.json"
---
