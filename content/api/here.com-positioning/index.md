---
slug: "here-com-positioning"
title: "HERE Network Positioning API v2"
provider: "here.com"
description: "Positioning API accepts requests with radio network measurements and\
  \ replies with corresponding location estimate. For more details and examples, see\
  \ [Developer's Guide](https://developer.here.com/documentation/positioning). Cellular\
  \ measurements are given in terms defined in 3GPP and 3GGP2 specifications, see\
  \ the corresponsing documentation at http://www.3gpp.org.\n\nBreaking changes from\
  \ v1:\n  - JSON fields\n    `altaccuracy`, `baselat`, `baselng`, `cellparams`, `pilotpower`,\
  \ `pnoffset`, `powrx`, `rxlevel`,\n    have been deprecated and replaced with\n\
  \    `altAccuracy`, `baseLat`, `baseLng`, `cellParams`, `pilotPower`, `pnOffset`,\
  \ `rss`, `rxLevel`\n    respectively.\n  - Dependent parameters combined as a subobject.\n\
  \    - CDMA, GSM, WCDMA, TD-SCDMA and LTE local identification parameters for serving\
  \ cell moved under `localId` property.\n    - GSM neighbor global ID: `lac` and\
  \ `cid` for neighbor cell moved under `globalIdentity` property.\n"
logo: "here.com-positioning-logo.png"
logoMediaType: "image/png"
tags:
- "location"
stubs: "here.com-positioning-stubs.json"
swagger: "here.com-positioning-swagger.json"
---
