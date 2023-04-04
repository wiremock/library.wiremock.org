---
slug: "epa-gov-cwa"
title: "U.S. EPA Enforcement and Compliance History Online (ECHO) - Clean Water Act\
  \ (CWA) Rest Services"
provider: "epa.gov"
description: "Enforcement and Compliance History Online (ECHO) is a tool developed\
  \ and maintained by EPA's Office of Enforcement and Compliance Assurance for public\
  \ use. ECHO provides integrated compliance and enforcement information for over\
  \ 1 million regulated facilities nationwide.\n CWA Rest Services provides multiple\
  \ service endpoints, each with specific capabilities, to search and retrieve data\
  \ on facilities regulated under the Clean Water Act (CWA) and managed under the\
  \ National Pollutant Discharge Elimination System (NPDES) program. The returned\
  \ results reflect data drawn from EPA's ICIS-NPDES database.\n\\\nThe get_facilities,\
  \ get_map, get_qid, and get_download end points are meant to be used together, while\
  \ the enhanced get_facility_info end point is self contained.\n  The get_facility_info\
  \ end point returns either an array of state, county or zip clusters with summary\
  \ statistics per cluster or an array of facilities.\n\\\nThe recommended use scenario\
  \ for get_facilities, get_qid, get_map, and get_downoad is:\n\\\n <b>1)</b>  Use\
  \ get_facilities to validate passed query parameters, obtain summary statistics\
  \ and to obtain a query_id (QID).  QIDs are time sensitive and will be valid for\
  \ approximately 30 minutes.\n <b>2)</b>  Use get_qid, with the returned QID, to\
  \ paginate through arrays of facility results.\n <b>3)</b>  Use get_map, with the\
  \ returned QID, to zoom in/out and pan on the clustered and individual facility\
  \ coordinates that meet the QID query criteria.\n <b>4)</b>  Use get_download, with\
  \ the returned QID, to generate a Comma Separated Value (CSV) file of facility information\
  \ that meets the QID query criteria.\n\\\n\\\nUse the qcolumns parameter to customize\
  \ your search results.  Use the Metadata service endpoint for a list of available\
  \ output objects, their Column Ids, and their definitions to help you build your\
  \ customized output. \n\\\nAdditional ECHO Resources:   <a href=\"https://echo.epa.gov/tools/web-services\"\
  >Web Services</a>, <a href=\"https://echo.epa.gov/resources/echo-data/about-the-data\"\
  >About ECHO's Data</a>, <a href=\"https://echo.epa.gov/tools/data-downloads\">Data\
  \ Downloads</a>\n "
logo: "epa.gov-cwa-logo.png"
logoMediaType: "image/png"
tags:
- "open_data"
stubs: "epa.gov-cwa-stubs.json"
swagger: "epa.gov-cwa-swagger.json"
---
