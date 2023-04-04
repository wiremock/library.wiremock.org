---
slug: "pandascore-co"
title: "PandaScore REST API for All Videogames"
provider: "pandascore.co"
description: "\n# Introduction\n\nWhether you're looking to build an official Pandascore\
  \ integration for your service, or you just want to build something awesome, [we\
  \ can help you get started](/home).\n\nThe API works over the HTTPS protocol, and\
  \ is accessed from the `api.pandascore.co` domain.\n\n- The current endpoint is\
  \ [https://api.pandascore.co](https://api.pandascore.co).\n- All data is sent and\
  \ received as JSON by default.\n- Blank fields are included with `null` values instead\
  \ of being omitted.\n- All timestamps are returned in ISO-8601 format\n\n### About\
  \ this documentation\n\nClicking on a query parameter like `filter` or `search`\
  \ will show you the available options: ![filter](/doc/images/query_param_details.jpg)\n\
  \nYou can also click on a response to see the detailed response schema: ![response](/doc/images/response_schema.jpg)\n\
  \n## Events hierarchy\n\nThe PandaScore API allows you to access data about eSports\
  \ events by using a certain structure detailed below.\n\n**Leagues**\n\nLeagues\
  \ are the top level events. They don't have a date and represent a regular competition.\
  \ A League is composed of one or several series.  \nSome League of Legends leagues\
  \ are: _EU LCS, NA LCS, LCK, etc._  \nSome Dota 2 leagues are: _ESL One, GESC, The\
  \ International, PGL, etc._\n\n**Series**\n\nA Serie represents an occurrence of\
  \ a league event.  \nThe EU LCS league has two series per year: _spring 2017, summer\
  \ 2017, spring 2016, summer 2016 etc._  \nSome Dota2 Series examples would be: _Changsha\
  \ Major, Open Bucharest, Frankfurt, i-League Invitational etc._\n\n**Tournaments**\n\
  \nTournaments groups all the matches of a serie under \"stages\" and \"groups\"\
  .  \nThe tournaments of the EU LCS of summer 2017 are: _Group A, Group B, Playoffs,\
  \ etc._  \nSome Dota 2 tournaments are: _Group A, Group B, Playoffs, etc._\n\n**Matches**\n\
  \nFinally we have matches which have two players or teams (depending on the played\
  \ videogame) and several games (the rounds of the match).  \nMatches of the group\
  \ A in the EU LCS of summer 2017 are: _G2 vs FNC, MSF vs NIP, etc._  \nMatches of\
  \ the group A in the ESL One, Genting tournamnet are: _Lower Round 1, Quarterfinal,\
  \ Upper Final, etc._  \n\n**Please note that some matches may be listed as \"TBD\
  \ vs TBD\" if the matchup is not announced yet, for example the date of the Final\
  \ match is known but the quarterfinal is still being played.**  \n![Structure](/doc/images/structure.png)\n\
  \n## Formats\n\n&lt;!-- The API currently supports the JSON format by default, as\
  \ well as the XML format. Add the desired extension to your request URL in order\
  \ to get that format. --&gt;\nThe API currently supports the JSON format by default.\n\
  \nOther formats may be added depending on user needs.\n\n## Pagination\n\nThe Pandascore\
  \ API paginates all resources on the index method.\n\nRequests that return multiple\
  \ items will be paginated to 50 items by default. You can specify further pages\
  \ with the `page[number]` parameter. You can also set a custom page size (up to\
  \ 100) with the `page[size]` parameter.\n\nThe `Link` HTTP response header contains\
  \ pagination data with `first`, `previous`, `next` and `last` raw page links when\
  \ available, under the format\n\n```\nLink: &lt;https://api.pandascore.co/{Resource}?page=X+1&gt;;\
  \ rel=\"next\", &lt;https://api.pandascore.co/{Resource}?page=X-1&gt;; rel=\"prev\"\
  , &lt;https://api.pandascore.co/{Resource}?page=1&gt;; rel=\"first\", &lt;https://api.pandascore.co/{Resource}?page=X+n&gt;;\
  \ rel=\"last\"\n```\n\nThere is also:\n\n* A `X-Page` header field, which contains\
  \ the current page.\n* A `X-Per-Page` header field, which contains the current pagination\
  \ length.\n* A `X-Total` header field, which contains the total count of items across\
  \ all pages.\n\n## Filtering\n\nThe `filter` query parameter can be used to filter\
  \ a collection by one or several fields for one or several values. The `filter`\
  \ parameter takes the field to filter as a key, and the values to filter as the\
  \ value. Multiples values must be comma-separated (`,`).\n\nFor example, the following\
  \ is a request for all the champions with a name matching Twitch or Brand exactly,\
  \ but only with 21 armor:\n\n```\nGET /lol/champions?filter[name]=Brand,Twitch&amp;filter[armor]=21&amp;token=YOUR_ACCESS_TOKEN\n\
  ```\n\n## Range\n\nThe `range` parameter is a hash that allows filtering fields\
  \ by an interval.\nOnly values between the given two comma-separated bounds will\
  \ be returned. The bounds are inclusive.\n\nFor example, the following is a request\
  \ for all the champions with `hp` within 500 and 1000:\n\n```\nGET /lol/champions?range[hp]=500,1000&amp;token=YOUR_ACCESS_TOKEN\n\
  ```\n\n## Search\n\nThe `search` parameter is a bit like the `filter` parameter,\
  \ but it will return all results where the values **contain** the given parameter.\n\
  \nNote: this only works on strings.\nSearching with integer values is not supported\
  \ and `filter` or `range` parameters may be better suited for your needs here.\n\
  \nFor example, to get all the champions with a name containing `\"twi\"`:\n\n```\n\
  $ curl -sg -H 'Authorization: Bearer YOUR_ACCESS_TOKEN' 'https://api.pandascore.co/lol/champions?search[name]=twi'\
  \ | jq -S '.[].name'\n\"Twitch\"\n\"Twisted Fate\"\n```\n\n## Sorting\n\nAll index\
  \ endpoints support multiple sort fields with comma-separation (`,`); the fields\
  \ are applied in the order specified.\n\nThe sort order for each field is ascending\
  \ unless it is prefixed with a minus (U+002D HYPHEN-MINUS, “-“), in which case it\
  \ is descending.\n\nFor example, `GET /lol/champions?sort=attackdamage,-name&amp;token=YOUR_ACCESS_TOKEN`\
  \ will return all the champions sorted by attack damage.\nAny champions with the\
  \ same attack damage will then be sorted by their names in descending alphabetical\
  \ order.\n\n## Rate limiting\n\nDepending on your current plan, you will have a\
  \ different rate limit. Your plan and your current request count [are available\
  \ on your dashboard](https://pandascore.co/settings).\n\nWith the **free plan**,\
  \ you have a limit of 1000 requests per hour, others plans have a limit of 4000\
  \ requests per hour. The number of remaining requests is available in the `X-Rate-Limit-Remaining`\
  \ response header.\n\nYour API key is included in all the examples on this page,\
  \ so you can test any example right away. **Only you can see this value.**\n\n#\
  \ Authentication\n\nThe authentication on the Pandascore API works with access tokens.\n\
  \nAll developers need to [create an account](https://pandascore.co/users/sign_in)\
  \ before getting started, in order to get an access token. The access token should\
  \ not be shared.\n\n**Your token can be found and regenerated from [your dashboard](https://pandascore.co/settings).**\n\
  \nThe access token can be passed in the URL with the `token` query string parameter,\
  \ or in the `Authorization: Bearer` header field.\n\n&lt;!-- ReDoc-Inject: &lt;security-definitions&gt;\
  \ --&gt;\n"
logo: "pandascore.co-logo.svg"
logoMediaType: "image/svg+xml"
tags:
- "entertainment"
stubs: "pandascore.co-stubs.json"
swagger: "pandascore.co-swagger.json"
---
