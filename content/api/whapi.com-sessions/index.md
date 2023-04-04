---
slug: "whapi-com-sessions"
title: "Sessions API"
provider: "whapi.com"
description: "The William Hill Sessions API uses a central authentication service\
  \ (CAS*) on all resources that require access to a customer’s account or betting\
  \ functionality. To authenticate, you’ll need to supply a sportsbook username and\
  \ password, in return you will be given an authentication ticket, which you can\
  \ use on the majority of requests found within our services. <br /><br /><br />\
  \ The Sessions API should be used whenever you want to login a customer and:<br\
  \ /><br /> <ul> <li>continue to use the William Hill API for that customer’s transactions</li>\
  \ <li>use other CAS-enabled William Hill services outside the suite of APIs</li>\
  \ </ul> <br /> CAS is an enterprise Single Sign-On solution for web services (see\
  \ https://wiki.jasig.org/display/CAS/Home). It is used by many William Hill services.\
  \ <br /> Note: all requests must be executed over HTTPS and include an API key and\
  \ secret.<br /><br /><br /> <b>Authentication Ticket Expiration Times</b><br /><br\
  \ /> When a customer is logged in using the Sessions API, they are given an Authentication\
  \ Ticket; using this ticket on subsequent API requests gives you access to account\
  \ activities (such as placing a bet, deposits, etc). However, this ticket is only\
  \ valid for a given period of time depending on how it is used. If the ticket is\
  \ used and then has a period of inactivity longer than 7,200 seconds (2 hours),\
  \ then the ticket will expire and further requests using the ticket will be denied\
  \ - in effect, a customer has been logged out and will need to authenticate again.\
  \ <br /><br /><br /> Normally, any ticket issued only has a maximum life expectancy\
  \ of 28,000 seconds (8 hours) after which it can no longer be used, even if it has\
  \ been used regularly. The customer again will be effectively logged out and will\
  \ need to authenticate again. If you wish to avoid this, you need to set the query\
  \ parameter extended to Y, which will enable your application to generate a ticket\
  \ valid for 60 days without expiring due to inactivity. <br />"
logo: "whapi.com-sessions-logo.jpeg"
logoMediaType: "image/jpeg"
tags:
- "entertainment"
stubs: "whapi.com-sessions-stubs.json"
swagger: "whapi.com-sessions-swagger.json"
---
