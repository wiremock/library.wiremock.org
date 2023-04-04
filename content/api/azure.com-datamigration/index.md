---
slug: "azure-com-datamigration"
title: "Azure Data Migration Service Resource Provider"
provider: "azure.com"
description: "The Data Migration Service helps people migrate their data from on-premise\
  \ database servers to Azure, or from older database software to newer software.\
  \ The service manages one or more workers that are joined to a customer's virtual\
  \ network, which is assumed to provide connectivity to their databases. To avoid\
  \ frequent updates to the resource provider, data migration tasks are implemented\
  \ by the resource provider in a generic way as task resources, each of which has\
  \ a task type (which identifies the type of work to run), input, and output. The\
  \ client is responsible for providing appropriate task type and inputs, which will\
  \ be passed through unexamined to the machines that implement the functionality,\
  \ and for understanding the output, which is passed back unexamined to the client."
logo: "azure.com-datamigration-logo.png"
logoMediaType: "image/png"
tags:
- "cloud"
stubs: "azure.com-datamigration-stubs.json"
swagger: "azure.com-datamigration-swagger.json"
---
