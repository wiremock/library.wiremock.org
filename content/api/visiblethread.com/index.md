---
slug: "visiblethread-com"
title: "VisibleThread API"
provider: "visiblethread.com"
description: "## Introduction\nThe VisibleThread b API provides services for analyzing/searching\
  \ documents and web pages.\nTo use the service you need an API key. \n\n**Contact\
  \ us at support@visiblethread.com to request an API key**. \n\nThe services are\
  \ split into **Documents** and **Webscans**.\n\n### Documents\nUpload documents\
  \ and dictionaries so you can :\n- Measure the readability of your document\n- search\
  \ a document for all terms from a dictionary\n- retrieve all paragraphs from a document\
  \ or only matching paragraphs\n\n### Webscans\nAnalyze web pages so you can: \n\
  - Measure the readability of your web content\n- Identify & highlight content issues\
  \ e.g. long sentences, passive voice\n\nThe VisibleThread API allows you to programatially\
  \ submit webpage urls to be scanned, \ncheck on the results of a scan, and view\
  \ a list of previous scans you have performed.\n    \n-------------\n\nThe VisibleThread\
  \ API is a HTTP-based JSON API, accessible at https://api.visiblethread.com \nEach\
  \ request to the service requires your API key to be successful.\n\n## Getting Started\
  \ With Webscans\n\nSteps:\n1. Enter your API key above and hit **Explore**. \n2.\
  \ Run a new scan by submitting a **POST to /webscans** (title and some webUrls are\
  \ required).\n   The scan runs asynchronously in the background but returns immediately\
  \ with a JSON response containing an \"id\" that represents your scan.\n3. Check\
  \ on the status of a scan by submitting **GET /webscans/{scanId}**, if the scan\
  \ is still in progress it will return a HTTP 503. If \n   it is complete it will\
  \ return a HTTP 200 with the appropriate JSON outlining the urls scanned and the\
  \ summary statistics for each url.\n4. Retrieve all your previous scan results by\
  \ submitting **GET /webscans**.  \n5. Retrieve detailed results for a url within\
  \ a scan (readability, long sentence and passive language instances) by submitting\
  \ \n   **GET /webscans/{scanId}/webUrls/{urlId}** (scanId and urlId are required)\n\
  \n## Getting Started With Document scans:\n\nSteps:\n1. Enter your API key above\
  \ and hit **Explore**\n2. Run a new scan by submitting a **POST to /documents**\
  \ (document required). The scan runs asynchronously in the background but returns\n\
  \   immediately with a JSON response containins an \"id\" that represents your scan\n\
  3. Check on the status of a scan by submitting **GET /documents/{scanId}**, if the\
  \ scan is still in progress it will return a HTTP 503. If \n   it is complete it\
  \ will return a HTTP 200 with the appropriate JSON outlining the document readability\
  \ results. It will contain detailed\n   analysis of each paragraph in the document\n\
  4. Retrieve all your previous scan results by submitting **GET /documents**\n\n\
  ### Searching a document for keywords\n\nThe VisibleThread API allows you to upload\
  \ a set of keywords or a 'dictionary'. You can then perform a search of a already\
  \ uploaded document \nusing that dictionary\n\nSteps (Assuming you have uploaded\
  \ your document using the steps above):\n1. Upload a csv file to use as a keyword\
  \ dictionary by submitting a **POST to /dictionaries** (csv file required). This\
  \ returns a JSON \n   response with the dictionary Id \n2. Search a document with\
  \ the dictionary by submitting a **POST to /searches** (document id and dictionary\
  \ id required). \n3. Get the resuhlts of the search by submitting  **GET /searches/{docId}/{dictionaryId}\"\
  \ . This will return JSON response containing \n   detailed results of searching\
  \ the document using the dictionary.\n4. To view the list of all searches you have\
  \ performed submit a **GET /searches**. \n\nBelow is a list of the available API\
  \ endpoints, documentation & a form to try out each operation."
logo: "visiblethread.com-logo.jpeg"
logoMediaType: "image/jpeg"
tags:
- "text"
stubs: "visiblethread.com-stubs.json"
swagger: "visiblethread.com-swagger.json"
---
