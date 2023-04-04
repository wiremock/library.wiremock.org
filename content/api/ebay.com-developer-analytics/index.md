---
slug: "ebay-com-developer-analytics"
title: "Analytics API"
provider: "ebay.com"
description: "The <b>Analytics API</b> retrieves call-limit data and the quotas that\
  \ are set for the RESTful APIs and the legacy Trading API.  <br><br>Responses from\
  \ calls made to <b>getRateLimits</b> and <b>getUerRateLimits</b> include a list\
  \ of the applicable resources and the \"call limit\", or quota, that is set for\
  \ each resource. In addition to quota information, the response also includes the\
  \ number of remaining calls available before the limit is reached, the time remaining\
  \ before the quota resets, and the length of the \"time window\" to which the quota\
  \ applies.  <br><br>The <b>getRateLimits</b> and <b>getUserRateLimits</b> methods\
  \ retrieve call-limit information for either an application or user, respectively,\
  \ and each method must be called with an appropriate OAuth token. That is, <b>getRateLimites</b>\
  \ requires an access token generated with a client credentials grant and <b>getUserRateLimites</b>\
  \ requires an access token generated with an authorization code grant. For more\
  \ information, see <a href=\"/api-docs/static/oauth-tokens.html\">OAuth tokens</a>.\
  \  <br><br>Users can analyze the response data to see whether or not a limit might\
  \ be reached, and from that determine if any action needs to be taken (such as programmatically\
  \ throttling their request rate). For more on call limits, see <a href=\"https://developer.ebay.com/support/app-check\
  \ \" target=\"_blank\">Compatible Application Check</a>."
logo: "ebay.com-developer-analytics-logo.jpeg"
logoMediaType: "image/jpeg"
tags:
- "ecommerce"
stubs: "ebay.com-developer-analytics-stubs.json"
swagger: "ebay.com-developer-analytics-swagger.json"
---
