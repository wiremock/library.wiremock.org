---
slug: "contract-p-fit"
title: "Contract.fit API"
provider: "contract-p.fit"
description: "This OpenAPI describes the API exposed by the contract.fit backend.\n\
  \n## Security\n\n### Authentication\n\nAll endpoints are protected: you need to\
  \ make authenticated calls. There are 3 authentication mechanisms:\n- HTTP Basic\
  \ (Username + Password)\n- JWT Token\n- API-Key\n\nBy default you should have an\
  \ account allowing you to bootstrap your tenant and create users and roles, using\
  \ Basic Auth or after creating a Token  - see */auth* endpoints.\n\nIf you are missing\
  \ credentials or permissions, please [contact us](https://contract.fit/contact-us).\n\
  \n### Authorization\n\nThe security system is RBAC based: users must be granted\
  \ scoped roles, allowing them to access resources.\nEach role grants a defined set\
  \ of permissions, which can be restricted to a given inbox or document - see */roles*\
  \ endpoints.\n\n## Upload and Processing\n\nBelow is a short description of common\
  \ use cases of the API.\n\n### Simple Upload\n\nThe easiest and simplest way to\
  \ get started is to use POST /documents : it will make a synchronous upload of your\
  \ file and wait for the result.\n\nThis is a simplified version of POST /documents/{inbox_id}\
  \ with less arguments and settings; it may not be suitable for real workload as\
  \ it offers less capabilities.\n\n### Upload to Inbox\n\nThe favored endpoint to\
  \ upload files is POST /documents/{inbox_id}: it is also highly recommended to make\
  \ async call using sync=false.\n\n**Sync / Async**\n\nFor convenience uploads can\
  \ be synchronous: it will make the request blocks until the document is processed.\n\
  \nIt is however discouraged to rely on sync requests, as our service is designed\
  \ to process documents asynchronously. You might run into timeouts and unprocessed\
  \ document depending on factors such as server load and number of pending documents.\n\
  \nAsynchronous calls will only schedule the processing and directly return the document\
  \ ID without waiting: the document will be processed as soon as possible. You can\
  \ then wait for the processed result using GET */documents/{document_id}*.\n\n###\
  \ Reprocessing\n\nYou can reprocess a document using POST */documents/{document_id}/reprocess*\
  \ : it will schedule an async processing of the document (note: it is not possible\
  \ to make a sync reprocessing)\n"
logo: "contract-p.fit-logo.svg"
logoMediaType: "image/svg+xml"
tags:
- "text"
stubs: "contract-p.fit-stubs.json"
swagger: "contract-p.fit-swagger.json"
---
