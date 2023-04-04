---
slug: "envoice-in"
title: "API v1.0.0"
provider: "envoice.in"
description: "[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/80638214aa04722c9203)\r\
  \n<span style='margin-left: 0.5em;'>or</span>\r\n<a href='https://documenter.getpostman.com/view/3559821/TVeqcn2L'\
  \ class='openapi-button' _ngcontent-c6>View Postman docs</a>\r\n\r\n# Quickstart\r\
  \n\r\nVisit [github](https://github.com/EmitKnowledge/Envoice) to view the quickstart\
  \ tutorial.\r\n\r\n<div class='postman-tutorial'>\r\n\r\n# Tutorial for running\
  \ the API in postman\r\n\r\nClick on \"\"Run in Postman\"\" button\r\n<br /><br\
  \ />\r\n![postman - tutorial - 1](/Assets/images/api/postman-tutorial/postman-tutorial-1.png)\r\
  \n\r\n --- \r\n\r\nA new page will open.\r\nClick the \"\"Postman for windows\"\"\
  \ to run postman as a desktop app.\r\nMake sure you have already [installed](https://www.getpostman.com/docs/postman/launching_postman/installation_and_updates)\
  \ Postman.\r\n<br /><br />\r\n![postman - tutorial - 2](/Assets/images/api/postman-tutorial/postman-tutorial-2.png)\r\
  \n\r\n --- \r\n\r\nIn chrome an alert might show up to set a default app for opening\
  \ postman links. Click on \"\"Open Postman\"\".\r\n<br /><br />\r\n![postman - tutorial\
  \ - 3](/Assets/images/api/postman-tutorial/postman-tutorial-3.png)\r\n\r\n --- \r\
  \n\r\nThe OpenAPI specification will be imported in Postman as a new collection\
  \ named \"\"Envoice api\"\"\r\n<br /><br />\r\n![postman - tutorial - 4](/Assets/images/api/postman-tutorial/postman-tutorial-4.png)\r\
  \n\r\n --- \r\n\r\nWhen testing be sure to check and modify the environment variables\
  \ to suit your api key and secret. The domain is set to envoice's endpoint so you\
  \ don't really need to change that.  \r\n<sub>\\*Eye button in top right corner\
  \ </sub>\r\n<br /><br /> \r\n![postman - tutorial - 5](/Assets/images/api/postman-tutorial/postman-tutorial-5.png)\r\
  \n<br /><br /> \r\n![postman - tutorial - 6](/Assets/images/api/postman-tutorial/postman-tutorial-6.png)\r\
  \n\r\n --- \r\n\r\nYou don't need to change the values of the header parameters,\
  \ because they will be replaced automatically when you send a request with real\
  \ values from the environment configured in the previous step.\r\n<br /><br />\r\
  \n![postman - tutorial - 7](/Assets/images/api/postman-tutorial/postman-tutorial-7.png)\r\
  \n\r\n --- \r\n\r\nModify the example data to suit your needs and send a request.\r\
  \n<br /><br />\r\n![postman - tutorial - 8](/Assets/images/api/postman-tutorial/postman-tutorial-8.png)\r\
  \n</div>\r\n\r\n# Webhooks\r\n\r\nWebhooks allow you to build or set up Envoice\
  \ Apps which subscribe to invoice activities. \r\nWhen one of those events is triggered,\
  \ we'll send a HTTP POST payload to the webhook's configured URL. \r\nWebhooks can\
  \ be used to update an external invoice data storage.\r\n\r\nIn order to use webhooks\
  \ visit [this link](/account/settings#api-tab) and add upto 10 webhook urls that\
  \ will return status `200` in order to signal that the webhook is working.\r\nAll\
  \ nonworking webhooks will be ignored after a certain period of time and several\
  \ retry attempts.\r\nIf after several attempts the webhook starts to work, we will\
  \ send you all activities, both past and present, in chronological order.\r\n\r\n\
  The payload of the webhook is in format:\r\n```\r\n{\r\n    Signature: \"\"sha256\
  \ string\"\",\r\n    Timestamp: \"\"YYYY-MM-DDTHH:mm:ss.FFFFFFFZ\"\",\r\n    Activity:\
  \ {\r\n        Message: \"string\",\r\n        Link: \"share url\",\r\n        Type:\
  \ int,        \r\n        InvoiceNumber: \"string\",\r\n        InvoiceId: int,\
  \        \r\n        OrderNumber: \"string\",\r\n        OrderId: int,\r\n     \
  \   Id: int,\r\n        CreatedOn: \"YYYY-MM-DDTHH:mm:ss.FFFFFFFZ\"\r\n    }\r\n\
  }\r\n```            "
logo: "envoice.in-logo.jpeg"
logoMediaType: "image/jpeg"
tags:
- "financial"
stubs: "envoice.in-stubs.json"
swagger: "envoice.in-swagger.json"
---
