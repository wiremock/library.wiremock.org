---
slug: "vtex-local-Master-Data-API-"
title: "Master Data API - v2"
provider: "vtex.local"
description: "# ATTENTION: **This version isn't compliant with data entities of old\
  \ version (e.g. CL and AD). It's possible to use this configuration only to new\
  \ data entities.**\r\n\r\n\r\n## Welcome!\r\n\r\nVTEX Master Data is an easy-to-use,\
  \ secure, fast, scalable and extensible repository. On it you can create your own\
  \ Entities, store data and consult directly from the storefront or use it to store\
  \ info for some external integration.\r\n\r\nThere are internal VTEX modules that\
  \ use VTEX Master Data as data repository. We have the VTEX Customer Service, VTEX\
  \ Profile System and VTEX InStore, for example. It is also used by other internal\
  \ services.\r\n\r\nThere are two ways to use Master Data:\r\n\r\n1. Directly from\
  \ the storefront\r\n2. External integration\r\n\r\n### Directly from the storefront\r\
  \n\r\nIf your scenario is to be used inside the storefront, be aware of the following\
  \ observations:\r\n\r\n1. Use the storefront host to query or store information\
  \ to avoid **CORS**;\r\n2. Configure which information should be public and which\
  \ shouldn't, inside the JSON Schema of the Data Entity;\r\n3. Do not create query\
  \ loops (the storefront may be affected with Throttling and apis may be turned off\
  \ as a security protection);\r\n4. Never add via JS any type of authentication key\
  \ (x-vtex-api-appkey or x-vtex-api-apptoken);\r\n\r\n**It's important to avoid CORS\
  \ using the relative path**\r\n\r\n### External Integration\r\n\r\nIf your scenario\
  \ is to perform external integration, such as migrating client data from another\
  \ service, be aware of the following observations:\r\n\r\n1. Use the host ```{{accountName}}.vtexcommercestable.com.br```;\r\
  \n2. Use the authentication keys (x-vtex-api-appkey ou x-vtex-api-apptoken);\r\n\
  \r\n### Most used attributes listed here\r\n\r\n| Name | Description |\r\n| --------\
  \ | -------- |\r\n| accountName | Account name in VTEX License Manager |\r\n| name\
  \ | Data Entity name |\r\n| schema | JSON Schema of a Data Entity |\r\n| id | Identifier\
  \ of a document |\r\n| x-vtex-api-appKey | User key |\r\n| x-vtex-api-appToken |\
  \ User token |"
logo: "vtex.local-Master-Data-API--logo.svg"
logoMediaType: "image/svg+xml"
tags: []
stubs: "vtex.local-Master-Data-API--stubs.json"
swagger: "vtex.local-Master-Data-API--swagger.json"
---
