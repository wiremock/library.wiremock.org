---
slug: "prss-org"
title: "ContentDepot"
provider: "prss.org"
description: "ContentDepot hosts a range of API’s that allow clients to manage, discover,\
  \ and obtain content. The API spans many parts of the ContentDepot functionality\
  \ including MetaPub (a.k.a. metadata distribution) and content management.\n\n##\
  \ MetaPub\n\nMetaPub collects, normalizes and distributes publicly available program,\
  \ episode, and piece metadata through the public radio system. Backed by ContentDepot\
  \ and its data model, MetaPub allows producers to supply metadata through various\
  \ methods:\n\n1. MetaPub Agents that collect producer metadata by \"crawling\" existing\
  \ public feeds (e.g. C24, BBC) or the producer's production system (e.g. ATC, ME,\
  \ TED Radio Hour).\n2. Manually enter metadata in the ContentDepot Portal on each\
  \ program and episode.\n3. Publish/push the metadata to the MetaPub upload API and\
  \ execute an ingest job.\n\nMetaPub then distributes this data to stations through\
  \ an electronic program guide (EPG model) for display on various listener devices\
  \ such as smart phones, tablets, web streams, HD radios, RDBS enabled FM radios,\
  \ and more. The EPG format is based on the RadioDNS specifications.\n\n### RadioDNS\n\
  \nThe RadioDNS Service and Programme Information Specification ([ETSI TS 102 818\
  \ v3.4.1](https://www.etsi.org/deliver/etsi_ts/102800_102899/102818/03.04.01_60/ts_102818v030401p.pdf))\
  \ defines three primary documents: Service Information, Program Information, and\
  \ Group Information. These documents, along with the core RadioDNS Hybrid Lookup\
  \ for Radio Services Specification ([ETSI TS 103 270 v1.4.1](https://www.etsi.org/deliver/etsi_ts/103200_103299/103270/01.04.01_60/ts_103270v010401p.pdf)),\
  \ define a system where an end listener device can dynamically discover program\
  \ metadata and fetch the metadata via Internet Protocol (IP) requests. MetaPub's\
  \ use of RadioDNS differs slightly in that MetaPub (a.k.a PRSS) acts as the \"service\
  \ provider\" while the stations and related middleware act as the end devices. While\
  \ this is not the primary use case of RadioDNS, the flexibility in the specification,\
  \ service definitions, and DNS resolution allows this model to be easily represented.\
  \ MetaPub provides both _National Metadata_ and _Station Metadata_.\n\nIt is strongly\
  \ recommended that the related [RadioDNS specifications](https://radiodns.org/developers/documentation/)\
  \ be read for implementation details, definitions, and required XML schemas.\n\n\
  ## ContentDepot Drive\n\nContentDepot Drive (CD Drive) provides a private, per customer\
  \ file storage solution similar to other cloud storage solutions such as Google\
  \ Drive, Box, and Dropbox. The CD Drive is used to stage content uploads such as\
  \ metadata files, images, or segment audio before associating the content with specific\
  \ programs or episodes.\n\nCD Drive content can be referenced using a URI by some\
  \ operations such as synchronizing metadata. There are two possible CD Drive URI\
  \ formats supported: ID and hierarchical path. The ID reference takes the form ```cddrive:id:{value}```\
  \ where value is the integer ID of the file or folder being referenced. The hierarchical\
  \ path reference takes the form ```cddrive://{path}``` where path is the full, UNIX\
  \ style path to the file or folder starting with '/'. For example, two CD Drive\
  \ URIs pointing to the same file may be ```cddrive:id:12345``` and ```cddrive:///show1/episode2/metadata.xml```.\
  \ More information about URIs can be found at [Wikipedia](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier).\n\
  \n## Authentication\n\nThe API currently uses OAuth 2.0.  All operations require\
  \ ```cd:full``` access where the client access is only limited by the permissions\
  \ of the ContentDepot user after authentication. Limiting access scope per client\
  \ is not currently supported.\n"
logo: "prss.org-logo.svg"
logoMediaType: "image/svg+xml"
tags:
- "media"
stubs: "prss.org-stubs.json"
swagger: "prss.org-swagger.json"
---
