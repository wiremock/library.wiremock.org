---
slug: "lgtm-com"
title: "LGTM API specification"
provider: "lgtm.com"
description: "The REST API for LGTM provides data so that you can customize how you\
  \ integrate LGTM analysis into your workflow. It includes the following resources:\n\
  \  * `/` ([API root](https://lgtm.com/help/lgtm/api/api-v1#LGTM-API-specification-API-root))&mdash;get\
  \ version information or download the specification in OpenAPI format.\n  * `/projects`\
  \ ([Projects](https://lgtm.com/help/lgtm/api/api-v1#LGTM-API-specification-Projects))&mdash;list\
  \ projects, get a summary of the current status for a project, or add new projects.\n\
  \  * `/analyses` ([Analyses](https://lgtm.com/help/lgtm/api/api-v1#LGTM-API-specification-Analyses))&mdash;get\
  \ a summary of results, download all the alerts, or trigger analysis for a specific\
  \ commit.\n  * `/codereviews` ([Code reviews](https://lgtm.com/help/lgtm/api/api-v1#LGTM-API-specification-Code-reviews))&mdash;trigger\
  \ code review for a patch, and view the results.\n  * `/operations` ([Operations](https://lgtm.com/help/lgtm/api/api-v1#LGTM-API-specification-Operations))&mdash;get\
  \ information about long-running tasks, for example, analyses or code reviews that\
  \ you've requested.\n  * `/snapshots` ([Snapshots](https://lgtm.com/help/lgtm/api/api-v1#LGTM-API-specification-Snapshots))&mdash;download\
  \ and upload databases representing a snapshot of a codebase.\n  * `/queryjobs`\
  \ ([Query jobs](https://lgtm.com/help/lgtm/api/api-v1#LGTM-API-specification-Query-jobs))&mdash;submit\
  \ queries to evaluate against existing projects, and download their results.\n \
  \ * `/system` ([System](https://lgtm.com/help/lgtm/api/api-v1#LGTM-API-specification-System))&mdash;get\
  \ information on the health or usage of the system.\n\nFor an overview and getting\
  \ started topics, see [API for LGTM](https://lgtm.com/help/lgtm/api/api-for-lgtm).\n"
logo: "lgtm.com-logo.svg"
logoMediaType: "image/svg+xml"
tags:
- "developer_tools"
stubs: "lgtm.com-stubs.json"
swagger: "lgtm.com-swagger.json"
---
