---
slug: "epa-gov-sdw"
title: "U.S. EPA Enforcement and Compliance History Online (ECHO) - Safe Drinking\
  \ Water Act"
provider: "epa.gov"
description: "Enforcement and Compliance History Online (ECHO) is a tool developed\
  \ and maintained by EPA's Office of Enforcement and Compliance Assurance for public\
  \ use. ECHO provides integrated compliance and enforcement information for over\
  \ 1 million regulated facilities nationwide.\n   SDW Rest Services provides multiple\
  \ service endpoints, each with specific capabilities, to search and retrieve data\
  \ on public water systems regulated under the Safe Drinking Water Act (SDWA).  The\
  \ returned results reflect data drawn from EPA's Federal Safe Drinking Water Information\
  \ System (SDWIS) database.\n\\\nThe get_systems, get_qid, and get_download end points\
  \ are meant to be used together.\n\\\nThe recommended use scenario for get_systems,\
  \ get_qid, and get_downoad is:\n\\\n <b>1)</b>  Use get_systems to validate passed\
  \ query parameters, obtain summary statistics and to obtain a query_id (QID).  QIDs\
  \ are time sensitive and will be valid for approximately 30 minutes.\n <b>2)</b>\
  \  Use get_qid, with the returned QID, to paginate through arrays of water system\
  \ results.\n <b>3)</b>  Use get_download, with the returned QID, to generate a Comma\
  \ Separated Value (CSV) file of water system information that meets the QID query\
  \ criteria.\n\\\n\\\nUse the qcolumns parameter to customize your search results.\
  \  Use the Metadata service endpoint for a list of available output objects, their\
  \ Column Ids, and their definitions to help you build your customized output. \n\
  \\\nAdditional ECHO Resources:   <a href=\"https://echo.epa.gov/tools/web-services\"\
  >Web Services</a>, <a href=\"https://echo.epa.gov/resources/echo-data/about-the-data\"\
  >About ECHO's Data</a>, <a href=\"https://echo.epa.gov/tools/data-downloads\">Data\
  \ Downloads</a>\n "
logo: "epa.gov-sdw-logo.png"
logoMediaType: "image/png"
tags:
- "open_data"
stubs: "epa.gov-sdw-stubs.json"
swagger: "epa.gov-sdw-swagger.json"
---
