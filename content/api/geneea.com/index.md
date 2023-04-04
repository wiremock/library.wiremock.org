---
slug: "geneea-com"
title: "Geneea Natural Language Processing"
provider: "geneea.com"
description: "<div class=\"api-description\">\n    <h2>Authentication</h2>\n    <p>For\
  \ all calls, supply your API key. <a href=\"https://www.geneea.com/pricing\">Sign\
  \ up to <em>obtain the key</em></a>.</p>\n    <p>\n        Our API supports both\
  \ <em>unencrypted (HTTP)</em> and <em>encrypted (HTTPS)</em> protocols.\n      \
  \  However, for security reasons, we strongly encourage using only the encrypted\
  \ version.\n    </p>\n    <p>The API key should be supplied as either a request\
  \ parameter <code>user_key</code> or in <code>Authorization</code> header.</p>\n\
  \    <pre><code>Authorization: user_key &lt;YOUR_API_KEY&gt;</code></pre>\n\n  \
  \  <h2>API operations</h2>\n    <p>\n        All API operations can perform analysis\
  \ on supplied raw text or on text extracted from a given URL.\n        Optionally,\
  \ one can supply additional information which can make the result more precise.\
  \ An example\n        of such information would be the language of text or a particular\
  \ text extractor for URL resources.\n    </p>\n    <p>The supported types of analyses\
  \ are:</p>\n    <ul>\n        <li><strong>lemmatization</strong> &longrightarrow;\n\
  \            Finds out lemmata (basic forms) of all the words in the document.\n\
  \        </li>\n        <li><strong>correction</strong> &longrightarrow;\n     \
  \       Performs correction (diacritization) on all the words in the document.\n\
  \        </li>\n        <li><strong>topic detection</strong> &longrightarrow;\n\
  \            Determines a topic of the document, e.g. finance or sports.\n     \
  \   </li>\n        <li><strong>sentiment analysis</strong> &longrightarrow;\n  \
  \          Determines a sentiment of the document, i.e. how positive or negative\
  \ the document is.\n        </li>\n        <li><strong>named entity recognition</strong>\
  \ &longrightarrow;\n            Finds named entities (like person, location, date\
  \ etc.) mentioned the the document.\n        </li>\n    </ul>\n\n    <h2>Encoding</h2>\n\
  \    <p>The supplied text is expected to be in UTF-8 encoding, this is especially\
  \ important for non-english texts.</p>\n\n    <h2>Returned values</h2>\n    <p>The\
  \ API calls always return objects in serialized JSON format in UTF-8 encoding.</p>\n\
  \    <p>\n        If any error occurs, the HTTP response code will be in the range\
  \ <code>4xx</code> (client-side error) or\n        <code>5xx</code> (server-side\
  \ error). In this situation, the body of the response will contain information\n\
  \        about the error in JSON format, with <code>exception</code> and <code>message</code>\
  \ values.\n    </p>\n\n    <h2>URL limitations</h2>\n    <p>\n        All the requests\
  \ are semantically <code>GET</code>. However, for longer texts, you may run into\
  \ issues\n        with URL length limit. Therefore, it's possible to always issue\
  \ a <code>POST</code> request with all\n        the parameters encoded as a JSON\
  \ in the request body.\n    </p>\n    <p>Example:</p>\n    <pre><code>\n       \
  \ POST /s1/sentiment\n        Content-Type: application/json\n\n        {\"text\"\
  :\"There is no harm in being sometimes wrong - especially if one is promptly found\
  \ out.\"}\n    </code></pre>\n    <p>This is equivalent to <code>GET /s1/sentiment?text=There%20is%20no%20harm...</code></p>\n\
  \n    <h2>Request limitations</h2>\n    <p>\n        The API has other limitations\
  \ concerning the size of the HTTP requests. The maximum allowed size of any\n  \
  \      POST request body is <em>512 KiB</em>. For request with a URL resource, the\
  \ maximum allowed number of\n        extracted characters from each such resource\
  \ is <em>100,000</em>.\n    </p>\n\n    <h2>Terms of Service</h2>\n    <p>\n   \
  \     By using the API, you agree to our\n        <a href=\"https://www.geneea.com/terms.html\"\
  \ target=\"_blank\">Terms of Service Agreement</a>.\n    </p>\n\n    <h2>More information</h2>\n\
  \    <p>\n        <a href=\"https://help.geneea.com/index.html\" target=\"_blank\"\
  >\n        The Interpretor Public Documentation\n        </a>\n    </p>\n</div>\n"
logo: "geneea.com-logo.png"
logoMediaType: "image/png"
tags:
- "text"
stubs: "geneea.com-stubs.json"
swagger: "geneea.com-swagger.json"
---
