---
slug: "epa-gov-case"
title: "U.S. EPA Enforcement and Compliance History Online (ECHO) - Enforcement Case\
  \ Search"
provider: "epa.gov"
description: "Enforcement and Compliance History Online (ECHO) is a tool developed\
  \ and maintained by EPA's Office of Enforcement and Compliance Assurance for public\
  \ use. ECHO provides integrated compliance and enforcement information for over\
  \ 1 million regulated facilities nationwide.\n CASE Rest Services provide multiple\
  \ service endpoints, each with specific capabilities, to search and retrieve data\
  \ on civil cases entered into the \nIntegrated Compliance Information System (ICIS)\
  \ and criminal cases entered into the Summary of Criminal Prosecutions database.\
  \  \nSee Enforcement Case Search Help (https://echo.epa.gov/help/enforcement-case-search-help)\
  \ for additional information on searching civil and criminal cases. \n\\\nThe get_cases,\
  \ get_map, get_qid, and get_download end points are meant to be used together, while\
  \ the enhanced get_case_info end point is self contained..   \nThe recommended use\
  \ scenario for get_cases, get_qid, get_map, and get_downoad is:\n\\\n <b>1)</b>\
  \  Use get_cases to validate passed query parameters, obtain summary statistics\
  \ and to obtain a query_id (QID).  QIDs are time sensitive and will be valid for\
  \ approximately 30 minutes.\n <b>2)</b>  Use get_qid, with the returned QID, to\
  \ paginate through arrays of case results.\n <b>3)</b>  Use get_map, with the returned\
  \ QID, to zoom in/out and pan on the clustered and individual facility coordinates,\
  \ related to the returned cases, that meet the QID query criteria.\n <b>4)</b> \
  \ Use get_download, with the returned QID, to generate a Comma Separated Value (CSV)\
  \ file of facility information that meets the QID query criteria.\n\\\nIn addition\
  \ to the service endpoints listed above there are two detailed case report services,\
  \ one for civil cases (get_case_report) and one for criminal cases (get_crcase_report).\
  \ \nSee the Civil Enforcement Case Report Help (https://echo.epa.gov/help/reports/enforcement-case-report-help)\
  \ and the Criminal Case Report Help (https://echo.epa.gov/help/reports/criminal-case-report-help)\
  \ for additional information \non then data returned from these two services.  \
  \ \n\\\nAdditional ECHO Resources:   <a href=\"https://echo.epa.gov/tools/web-services\"\
  >Web Services</a>, <a href=\"https://echo.epa.gov/resources/echo-data/about-the-data\"\
  >About ECHO's Data</a>, <a href=\"https://echo.epa.gov/tools/data-downloads\">Data\
  \ Downloads</a>\n "
logo: "epa.gov-case-logo.png"
logoMediaType: "image/png"
tags:
- "open_data"
stubs: "epa.gov-case-stubs.json"
swagger: "epa.gov-case-swagger.json"
---
