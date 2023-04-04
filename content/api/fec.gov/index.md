---
slug: "fec-gov"
title: "OpenFEC"
provider: "fec.gov"
description: "This application programming interface (API) allows you to explore the\
  \ way candidates and committees fund their campaigns. \n\n The Federal Election\
  \ Commission (FEC) API is a RESTful web service supporting full-text and field-specific\
  \ searches on FEC data. [Bulk downloads](https://www.fec.gov/data/advanced/?tab=bulk-data)\
  \ are available on the current site. Information is tied to the underlying forms\
  \ by file ID and image ID. Data is updated nightly. \n\n There are a lot of data,\
  \ and a good place to start is to use search to find interesting candidates and\
  \ committees. Then, you can use their IDs to find report or line item details with\
  \ the other endpoints. If you are interested in individual donors, check out contributor\
  \ information in the `/schedule_a/` endpoints. \n\n <b class=\"body\" id=\"getting_started_head\"\
  >Getting started with the openFEC API</b><br> \n\n If you would like to use the\
  \ FEC's API programmatically, you can sign up for your own API key using our form.\
  \ Alternatively, you can still try out our API without an API key by using the web\
  \ interface and using DEMO_KEY. Note that when you use the openFEC API you are subject\
  \ to the [Terms of Service](https://github.com/fecgov/FEC/blob/master/TERMS-OF-SERVICE.md)\
  \ and [Acceptable Use policy](https://github.com/fecgov/FEC/blob/master/ACCEPTABLE-USE-POLICY.md).\
  \ \n\n Signing up for an API key will enable you to place up to 1,000 calls an hour.\
  \ Each call is limited to 100 results per page. You can email questions, comments\
  \ or a request to get a key for 7,200 calls an hour (120 calls per minute) to <a\
  \ href=\"mailto:APIinfo@fec.gov\">APIinfo@fec.gov</a>. You can also ask questions\
  \ and discuss the data in a community led [group](https://groups.google.com/forum/#!forum/fec-data).\
  \ \n\n The model definitions and schema are available at [/swagger](/swagger/).\
  \ This is useful for making wrappers and exploring the data. \n\n A few restrictions\
  \ limit the way you can use FEC data. For example, you can’t use contributor lists\
  \ for commercial purposes or to solicit donations. [Learn more here](https://www.fec.gov/updates/sale-or-use-contributor-information/).\
  \ \n\n [Inspect our source code](https://github.com/fecgov/openFEC). We welcome\
  \ issues and pull requests! \n\n <p><br></p> <h2 class=\"title\" id=\"signup_head\"\
  >Sign up for an API key</h2> <div id=\"apidatagov_signup\">Loading signup form...</div>"
logo: "fec.gov-logo.png"
logoMediaType: "image/png"
tags:
- "open_data"
stubs: "fec.gov-stubs.json"
swagger: "fec.gov-swagger.json"
---
