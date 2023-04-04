---
slug: "snyk-io"
title: "Snyk API"
provider: "snyk.io"
description: "The Snyk API is available to customers on [Business and Enterprise plans](https://snyk.io/plans)\
  \ and allows you to programatically integrate with Snyk.\n\n## REST API\n\nWe are\
  \ in the process of building a new, improved API (`https://api.snyk.io/rest`) built\
  \ using the OpenAPI and JSON API standards. We welcome you to try it out as we shape\
  \ and release endpoints until it, ultimately, becomes a full replacement for our\
  \ current API.\n\nLooking for our REST API docs? Please head over to [https://apidocs.snyk.io](https://apidocs.snyk.io)\n\
  \n## API vs CLI vs Snyk integration\n\nThe API detailed below has the ability to\
  \ test a package for issues, as they are defined by Snyk. It is important to note\
  \ that for many package managers, using this API will be less accurate than running\
  \ the [Snyk CLI](https://snyk.io/docs/using-snyk) as part of your build pipe, or\
  \ just using it locally on your package. The reason for this is that more than one\
  \ package version fit the requirements given in manifest files. Running the CLI\
  \ locally tests the actual deployed code, and has an accurate snapshot of the dependency\
  \ versions in use, while the API can only infer it, with inferior accuracy. It should\
  \ be noted that the Snyk CLI has the ability to output machine-readable JSON output\
  \ (with the `--json` flag to `snyk test`).\n\nA third option, is to allow Snyk access\
  \ to your development flow via the existing [Snyk integrations](https://snyk.io/docs/).\
  \ The advantage to this approach is having Snyk monitor every new pull request,\
  \ and suggest fixes by opening new pull requests. This can be achieved either by\
  \ integrating Snyk directly to your source code management (SCM) tool, or via a\
  \ broker to allow greater security and auditability.\n\nIf those are not viable\
  \ options, this API is your best choice.\n\n## API url\n\nThe base URL for all API\
  \ endpoints is https://api.snyk.io/api/v1/\n\n## Authorization\n\nTo use this API,\
  \ you must get your token from Snyk. It can be seen on https://snyk.io/account/\
  \ after you register with Snyk and login.\n\nThe token should be supplied in an\
  \ `Authorization` header with the token, preceded by `token`:\n\n```http\nAuthorization:\
  \ token API_KEY\n```\n\nOtherwise, a 401 \"Unauthorized\" response will be returned.\n\
  \n```http\nHTTP/1.1 401 Unauthorized\n\n        {\n            \"code\": 401,\n\
  \            \"error\": \"Not authorised\",\n            \"message\": \"Not authorised\"\
  \n        }\n```\n\n## Overview and entities\n\nThe API is a REST API. It has the\
  \ following entities:\n\n### Test result\n\nThe test result is the object returned\
  \ from the API giving the results of testing a package for issues. It has the following\
  \ fields:\n\n| Property        | Type    | Description                         \
  \                  | Example                                                   \
  \      |\n|----------------:|---------|-------------------------------------------------------|-----------------------------------------------------------------|\n\
  | ok              | boolean | Does this package have one or more issues?       \
  \      | false                                                           |\n| issues\
  \          | object  | The issues found. See below for details.              | See\
  \ below                                                       |\n| dependencyCount\
  \ | number  | The number of dependencies the package has.           | 9        \
  \                                                       |\n| org             | object\
  \  | The organization this test was carried out for.       | {\"name\": \"anOrg\"\
  , \"id\": \"5d7013d9-2a57-4c89-993c-0304d960193c\"} |\n| licensesPolicy  | object\
  \  | The organization's licenses policy used for this test | See in the examples\
  \                                             |\n| packageManager  | string  | The\
  \ package manager for this package                  | \"maven\"                \
  \                                         |\n|                 |         |     \
  \                                                  |                           \
  \                                      |\n\n### Issue\n\nAn issue is either a vulnerability\
  \ or a license issue, according to the organization's policy. It has the following\
  \ fields:\n\n| Property       | Type          | Description                    \
  \                                                                              \
  \              | Example                                |\n|---------------:|---------------|----------------------------------------------------------------------------------------------------------------------------|----------------------------------------|\n\
  | id             | string        | The issue ID                                \
  \                                                                              \
  \ | \"SNYK-JS-BACKBONE-10054\"               |\n| url            | string      \
  \  | A link to the issue details on snyk.io                                    \
  \                                                 | \"https://snyk.io/vuln/SNYK-JS-BACKBONE-10054\
  \ |\n| title          | string        | The issue title                        \
  \                                                                              \
  \      | \"Cross Site Scripting\"                 |\n| type           | string \
  \       | The issue type: \"license\" or \"vulnerability\".                    \
  \                                                          | \"license\"       \
  \                       |\n| paths          | array         | The paths to the dependencies\
  \ which have an issue, and their corresponding upgrade path (if an upgrade is available).\
  \ [More information about from and upgrade paths](#introduction/overview-and-entities/from-and-upgrade-paths)\
  \ | [<br>&nbsp;&nbsp;{<br>&nbsp;&nbsp;&nbsp;&nbsp;\"from\": [\"a@1.0.0\", \"b@4.8.1\"\
  ],<br>&nbsp;&nbsp;&nbsp;&nbsp;\"upgrade\": [false, \"b@4.8.2\"]<br>&nbsp;&nbsp;}<br>]\
  \ |\n| package        | string        | The package identifier according to its\
  \ package manager                                                              \
  \      | \"backbone\", \"org.apache.flex.blazeds:blazeds\"|\n| version        |\
  \ string        | The package version this issue is applicable to.             \
  \                                                              | \"0.4.0\"     \
  \                           |\n| severity       | string        | The Snyk defined\
  \ severity level: \"critical\", \"high\", \"medium\" or \"low\".               \
  \                                     | \"high\"                               \
  \  |\n| language       | string        | The package's programming language    \
  \                                                                              \
  \       | \"js\"                                   |\n| packageManager | string\
  \        | The package manager                                                 \
  \                                                       | \"npm\"              \
  \                    |\n| semver         | array[string] OR map[string]array[string]\
  \ | One or more [semver](https://semver.org) ranges this issue is applicable to.\
  \ The format varies according to package manager. | [\"<0.5.0, >=0.4.0\", \"<0.3.8,\
  \ >=0.3.6\"] OR { \"vulnerable\": [\"[2.0.0, 3.0.0)\"], \"unaffected\": [\"[1, 2)\"\
  , \"[3, )\"] } |\n\n### Vulnerability\n\nA vulnerability in a package. In addition\
  \ to all the fields present in an issue, a vulnerability also has these fields:\n\
  \nProperty        | Type    | Description                                      \
  \                                                                              \
  \                                                                              \
  \                    | Example                                        |\n----------------:|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------|\n\
  \ publicationTime | Date    | The vulnerability publication time               \
  \                                                                              \
  \                                                                              \
  \                    | \"2016-02-11T07:16:18.857Z\"                     |\n disclosureTime\
  \  | Date    | The time this vulnerability was originally disclosed to the package\
  \ maintainers                                                                  \
  \                                                                              \
  \   | \"2016-02-11T07:16:18.857Z\"                     |\n isUpgradable    | boolean\
  \ | Is this vulnerability fixable by upgrading a dependency?                   \
  \                                                                              \
  \                                                                        | true\
  \                                           |\n description     | string  | The\
  \ detailed description of the vulnerability, why and how it is exploitable. Provided\
  \ in markdown format. | \"## Overview\\n[`org.apache.logging.log4j:log4j-core`](http://search.maven.org/#search%7Cga%7C1%7Ca%3A%22log4j-core%22)\\\
  nIn Apache Log4j 2.x before 2.8.2, when using the TCP socket server or UDP socket\
  \ server to receive serialized log events from another application, a specially\
  \ crafted binary payload can be sent that, when deserialized, can execute arbitrary\
  \ code.\\n\\n# Details\\nSerialization is a process of converting an object into\
  \ a sequence of bytes which can be persisted to a disk or database or can be sent\
  \ through streams. The reverse process of creating object from sequence of bytes\
  \ is called deserialization. Serialization is commonly used for communication (sharing\
  \ objects between multiple hosts) and persistence (store the object state in a file\
  \ or a database). It is an integral part of popular protocols like _Remote Method\
  \ Invocation (RMI)_, _Java Management Extension (JMX)_, _Java Messaging System (JMS)_,\
  \ _Action Message Format (AMF)_, _Java Server Faces (JSF) ViewState_, etc.\\n\\\
  n_Deserialization of untrusted data_ ([CWE-502](https://cwe.mitre.org/data/definitions/502.html)),\
  \ is when the application deserializes untrusted data without sufficiently verifying\
  \ that the resulting data will be valid, letting the attacker to control the state\
  \ or the flow of the execution. \\n\\nJava deserialization issues have been known\
  \ for years. However, interest in the issue intensified greatly in 2015, when classes\
  \ that could be abused to achieve remote code execution were found in a [popular\
  \ library (Apache Commons Collection)](https://snyk.io/vuln/SNYK-JAVA-COMMONSCOLLECTIONS-30078).\
  \ These classes were used in zero-days affecting IBM WebSphere, Oracle WebLogic\
  \ and many other products.\\n\\nAn attacker just needs to identify a piece of software\
  \ that has both a vulnerable class on its path, and performs deserialization on\
  \ untrusted data. Then all they need to do is send the payload into the deserializer,\
  \ getting the command executed.\\n\\n> Developers put too much trust in Java Object\
  \ Serialization. Some even de-serialize objects pre-authentication. When deserializing\
  \ an Object in Java you typically cast it to an expected type, and therefore Java's\
  \ strict type system will ensure you only get valid object trees. Unfortunately,\
  \ by the time the type checking happens, platform code has already created and executed\
  \ significant logic. So, before the final type is checked a lot of code is executed\
  \ from the readObject() methods of various objects, all of which is out of the developer's\
  \ control. By combining the readObject() methods of various classes which are available\
  \ on the classpath of the vulnerable application an attacker can execute functions\
  \ (including calling Runtime.exec() to execute local OS commands).\\n- Apache Blog\\\
  n\\n\\n## References\\n- [NVD](https://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2017-5645)\\\
  n- [jira issue](https://issues.apache.org/jira/browse/LOG4J2-1863)\\n\" |\n isPatchable\
  \     | boolean | Is this vulnerability fixable by using a Snyk supplied patch?\
  \                                                                              \
  \                                                                              \
  \        | true                                           |\n isPinnable      |\
  \ boolean | Is this vulnerability fixable by pinning a transitive dependency   \
  \                                                                              \
  \                                                                              \
  \  | true                                           |\n identifiers     | object\
  \  | Additional vulnerability identifiers                                      \
  \                                                                              \
  \                                                                         | {\"\
  CWE\": [], \"CVE\": [\"CVE-2016-2402]}           |\n credit          | string  |\
  \ The reporter of the vulnerability                                            \
  \                                                                              \
  \                                                                      | \"Snyk\
  \ Security Team\"                           |\n CVSSv3          | string  | Common\
  \ Vulnerability Scoring System (CVSS) provides a way to capture the principal characteristics\
  \ of a vulnerability, and produce a numerical score reflecting its severity, as\
  \ well as a textual representation of that score. | \"CVSS:3.0/AV:N/AC:L/PR:N/UI:N/S:U/C:L/I:N/A:N\"\
  \ |\n cvssScore       | number  | CVSS Score                                   \
  \                                                                              \
  \                                                                              \
  \                        | 5.3                                            |\n patches\
  \         | array   | Patches to fix this issue, by snyk                       \
  \                                                                              \
  \                                                                              \
  \            | see \"Patch\" below.                             |\n upgradePath\
  \     | object  | The path to upgrade this issue, if applicable                \
  \                                                                              \
  \                                                                              \
  \        | see below                                      |\n isPatched       |\
  \ boolean | Is this vulnerability patched?                                     \
  \                                                                              \
  \                                                                              \
  \  | false                                          |\n exploitMaturity | string\
  \  | The snyk exploit maturity level\n\n#### Patch\n\nA patch is an object like\
  \ this one:\n\n```json\n{\n  \"urls\": [\n    \"https://snyk-patches.s3.amazonaws.com/npm/backbone/20110701/backbone_20110701_0_0_0cdc525961d3fa98e810ffae6bcc8e3838e36d93.patch\"\
  \n  ],\n  \"version\": \"<0.5.0 >=0.3.3\",\n  \"modificationTime\": \"2015-11-06T02:09:36.180Z\"\
  ,\n  \"comments\": [\n    \"https://github.com/jashkenas/backbone/commit/0cdc525961d3fa98e810ffae6bcc8e3838e36d93.patch\"\
  \n  ],\n  \"id\": \"patch:npm:backbone:20110701:0\"\n}\n```\n\n### From and upgrade\
  \ paths\n\nBoth from and upgrade paths are arrays, where each item within the array\
  \ is a package `name@version`.\n\nTake the following `from` path:\n\n```\n[\n  \"\
  my-project@1.0.0\",\n  \"actionpack@4.2.5\",\n  \"rack@1.6.4\"\n]\n```\n\nAssuming\
  \ this was returned as a result of a test, then we know:\n\n- The package that was\
  \ tested was `my-project@1.0.0`\n\n- The dependency with an issue was included in\
  \ the tested package via the direct dependency `actionpack@4.2.5`\n\n- The dependency\
  \ with an issue was [rack@1.6.4](https://snyk.io/vuln/rubygems:rack@1.6.4)\n\nTake\
  \ the following `upgrade` path:\n\n```\n[\n  false,\n  \"actionpack@5.0.0\",\n \
  \ \"rack@2.0.1\"\n]\n```\n\nAssuming this was returned as a result of a test, then\
  \ we know:\n\n- The package that was tested is not upgradable (`false`)\n\n- The\
  \ direct dependency `actionpack` should be upgraded to at least version `5.0.0`\
  \ in order to fix the issue\n\n- Upgrading `actionpack` to version `5.0.0` will\
  \ cause `rack` to be installed at version `2.0.1`\n\nIf the `upgrade` path comes\
  \ back as an empty array (`[]`) then this means that there is no upgrade path available\
  \ which would fix the issue.\n\n### License issue\n\nA license issue has no additional\
  \ fields other than the ones in \"Issue\".\n\n### Snyk organization\n\nThe organization\
  \ in Snyk this request is applicable to. The organization determines the access\
  \ rights, licenses policy and is the unit of billing for private projects.\n\nA\
  \ Snyk organization has these fields:\n\nProperty    | Type   | Description    \
  \               | Example                                |\n-----------:| ------\
  \ | ----------------------------- | -------------------------------------- |\nname\
  \        | string | The organization display name | \"deelmaker\"              \
  \              |\nid          | string | The ID of the organization    | \"3ab0f8d3-b17d-4953-ab6d-e1cbfe1df385\"\
  \ |\n\n## Errors\n\nThis is a beta release of this API. Therefore, despite our efforts,\
  \ errors might occur. In the unlikely event of such an error, it will have the following\
  \ structure as JSON in the body:\n\nProperty    | Type   | Description         \
  \          | Example                                |\n-----------:| ------ | -----------------------------\
  \ | -------------------------------------- |\nmessage     | string | Error message\
  \ with reference  | Error calling Snyk api (reference: 39db46b1-ad57-47e6-a87d-e34f6968030b)\
  \ |\nerrorRef    | V4 uuid | An error ref to contact Snyk with | 39db46b1-ad57-47e6-a87d-e34f6968030b\
  \ |\n\nThe error reference will also be supplied in the `x-error-reference` header\
  \ in the server reply.\n\nExample response:\n\n```http\nHTTP/1.1 500 Internal Server\
  \ Error\nx-error-reference: a45ec9c1-065b-4f7b-baf8-dbd1552ffc9f\nContent-Type:\
  \ application/json; charset=utf-8\nContent-Length: 1848\nVary: Accept-Encoding\n\
  Date: Sun, 10 Sep 2017 06:48:40 GMT\n```\n\n## Rate Limiting\n\nTo ensure resilience\
  \ against increasing request rates, we are starting to introduce rate-limiting.\n\
  We are monitoring the rate-limiting system to ensure minimal impact on users while\
  \ ensuring system stability.\nCurrent limit is up to 2000 requests per minute, per\
  \ user. This limit is above industry standards, and is subject to change. As such,\
  \ we recommend calls to the API are throttled regardless of the current limit.\n\
  All requests above the limit will get a response with status code `429` - `Too many\
  \ requests` until requests stop for the duration of the rate-limiting interval (currently\
  \ a minute).\n\n## Consuming Webhooks\n\nWebhooks are delivered with a `Content-Type`\
  \ of `application/json`, with the event payload as JSON in the request body. We\
  \ also send the following headers:\n\n- `X-Snyk-Event` - the name of the event\n\
  \n- `X-Snyk-Transport-ID` - a GUID to identify this delivery\n\n- `X-Snyk-Timestamp`\
  \ - an ISO 8601 timestamp for when the event occurred, for example: `2020-09-25T15:27:53Z`\n\
  \n- `X-Hub-Signature` - the HMAC hex digest of the request body, used to secure\
  \ your webhooks and ensure the request did indeed come from Snyk\n\n- `User-Agent`\
  \ - identifies the origin of the request, for example: `Snyk-Webhooks/XXX`\n\n---\n\
  \nAfter your server is configured to receive payloads, it listens for any payload\
  \ sent to the endpoint you configured. For security reasons, you should limit requests\
  \ to those coming from Snyk.\n\n### Validating payloads\n\nAll transports sent to\
  \ your webhooks have a `X-Hub-Signature` header, which contains the hash signature\
  \ for the transport. The signature is a HMAC hexdigest of the request body, generated\
  \ using sha256 and your `secret` as the HMAC key.\n\nYou could use a function in\
  \ Node.JS such as the following to validate these signatures on incoming requests\
  \ from Snyk:\n\n```javascript\nimport * as crypto from 'crypto';\n\nfunction verifySignature(request,\
  \ secret) {\n  const hmac = crypto.createHmac('sha256', secret);\n  const buffer\
  \ = JSON.stringify(request.body);\n  hmac.update(buffer, 'utf8');\n\n  const signature\
  \ = `sha256=${hmac.digest('hex')}`;\n\n  return signature === request.headers['x-hub-signature'];\n\
  }\n```\n\n### Payload versioning\n\nPayloads may evolve over time, and so are versioned.\
  \ Payload versions are supplied as a suffix to the `X-Snyk-Event` header. For example,\
  \ `project_snapshot/v0` indicates that the payload is `v0` of the `project_snapshot`\
  \ event.\n\nVersion numbers only increment when a breaking change is made; for example,\
  \ removing a field that used to exist, or changing the name of a field. Version\
  \ numbers do not increment when making an additive change, such as adding a new\
  \ field that never existed before.\n\n**Note:** During the BETA phase, the structure\
  \ of webhook payloads may change at any time, so we  recommend you check the payload\
  \ version.\n\n### Event types\n\nWhile consuming a webhook event, `X-Snyk-Event`\
  \ header must be checked, as an end-point may receive multiple event types.\n\n\
  #### ping\n\nThe ping event happens after a new webhook is created, and can also\
  \ be manually triggered using the ping webhook API. This is useful to test that\
  \ your webhook receives data from Snyk correctly.\n\nThe `ping` event makes the\
  \ following request:\n\n```jsx\nPOST /webhook-handler/snyk123 HTTP/1.1\nHost: my.app.com\n\
  X-Snyk-Event: ping/v0\nX-Snyk-Transport-ID: 998fe884-18a0-45db-8ae0-e379eea3bc0a\n\
  X-Snyk-Timestamp: 2020-09-25T15:27:53Z\nX-Hub-Signature: sha256=7d38cdd689735b008b3c702edd92eea23791c5f6\n\
  User-Agent: Snyk-Webhooks/044aadd\nContent-Type: application/json\n{\n  \"webhookId\"\
  : \"d3cf26b3-2d77-497b-bce2-23b33cc15362\"\n}\n```\n\n#### project_snapshot\n\n\
  This event is triggered every time an existing project is tested and a new snapshot\
  \ is created. It is triggered on every test of a project, whether or not there are\
  \ new issues. This event is not triggered when a new project is created or imported.\
  \ Currently supported targets/scan types are Open Source and container.\n\n```jsx\n\
  POST /webhook-handler/snyk123 HTTP/1.1\nHost: my.app.com\nX-Snyk-Event: project_snapshot/v0\n\
  X-Snyk-Transport-ID: 998fe884-18a0-45db-8ae0-e379eea3bc0a\nX-Snyk-Timestamp: 2020-09-25T15:27:53Z\n\
  X-Hub-Signature: sha256=7d38cdd689735b008b3c702edd92eea23791c5f6\nUser-Agent: Snyk-Webhooks/044aadd\n\
  Content-Type: application/json\n{\n  \"project\": { ... }, // project object matching\
  \ API responses\n  \"org\": { ... }, // organization object matching API responses\n\
  \  \"group\": { ... }, // group object matching API responses\n  \"newIssues\":\
  \ [], // array of issues object matching API responses\n  \"removedIssues\": [],\
  \ // array of issues object matching API responses\n}\n```\n\n####  Detailed example\
  \ of a payload\n\n##### project\n\nsee: [https://snyk.docs.apiary.io/#reference/projects](https://snyk.docs.apiary.io/#reference/projects)\n\
  \n```tsx\n\"project\": {\n  \"name\": \"snyk/goof\",\n  \"id\": \"af137b96-6966-46c1-826b-2e79ac49bbd9\"\
  ,\n  \"created\": \"2018-10-29T09:50:54.014Z\",\n  \"origin\": \"github\",\n  \"\
  type\": \"maven\",\n  \"readOnly\": false,\n  \"testFrequency\": \"daily\",\n  \"\
  totalDependencies\": 42,\n  \"issueCountsBySeverity\": {\n    \"low\": 13,\n   \
  \ \"medium\": 8,\n    \"high\": 4,\n    \"critical\": 5\n  },\n  \"imageId\": \"\
  sha256:caf27325b298a6730837023a8a342699c8b7b388b8d878966b064a1320043019\",\n  \"\
  imageTag\": \"latest\",\n  \"imageBaseImage\": \"alpine:3\",\n  \"imagePlatform\"\
  : \"linux/arm64\",\n  \"imageCluster\": \"Production\",\n  \"hostname\": null,\n\
  \  \"remoteRepoUrl\": \"https://github.com/snyk/goof.git\",\n  \"lastTestedDate\"\
  : \"2019-02-05T08:54:07.704Z\",\n  \"browseUrl\": \"https://app.snyk.io/org/4a18d42f-0706-4ad0-b127-24078731fbed/project/af137b96-6966-46c1-826b-2e79ac49bbd9\"\
  ,\n  \"importingUser\": {\n    \"id\": \"e713cf94-bb02-4ea0-89d9-613cce0caed2\"\
  ,\n    \"name\": \"example-user@snyk.io\",\n    \"username\": \"exampleUser\",\n\
  \    \"email\": \"example-user@snyk.io\"\n  },\n  \"isMonitored\": false,\n  \"\
  branch\": null,\n  \"targetReference\": null,\n  \"tags\": [\n    {\n      \"key\"\
  : \"example-tag-key\",\n      \"value\": \"example-tag-value\"\n    }\n  ],\n  \"\
  attributes\": {\n    \"criticality\": [\n      \"high\"\n    ],\n    \"environment\"\
  : [\n      \"backend\"\n    ],\n    \"lifecycle\": [\n      \"development\"\n  \
  \  ]\n  },\n  \"remediation\": {\n    \"upgrade\": {},\n    \"patch\": {},\n   \
  \ \"pin\": {}\n  }\n}\n```\n\n##### org\n\nsee: [https://snyk.docs.apiary.io/#reference/organizations](https://snyk.docs.apiary.io/#reference/organizations)\n\
  \n```tsx\n\"org\": {\n  \"name\": \"My Org\",\n  \"id\": \"a04d9cbd-ae6e-44af-b573-0556b0ad4bd2\"\
  ,\n  \"slug\": \"my-org\",\n  \"url\": \"https://api.snyk.io/org/my-org\",\n  \"\
  created\": \"2020-11-18T10:39:00.983Z\"\n}\n```\n\n##### group\n\nsee: [https://snyk.docs.apiary.io/#reference/groups](https://snyk.docs.apiary.io/#reference/groups)\n\
  \n```tsx\n\"group\": {\n  \"name\": \"ACME Inc.\",\n   \"id\": \"a060a49f-636e-480f-9e14-38e773b2a97f\"\
  \n}\n```\n\n##### issue\n\nsee: https://snyk.docs.apiary.io/#reference/users/user-organization-notification-settings/list-all-aggregated-issues\n\
  \n```tsx\n{\n  \"id\": \"npm:ms:20170412\",\n  \"issueType\": \"vuln\",\n  \"pkgName\"\
  : \"ms\",\n  \"pkgVersions\": [\n    \"1.0.0\"\n  ],\n  \"issueData\": {\n    \"\
  id\": \"npm:ms:20170412\",\n    \"title\": \"Regular Expression Denial of Service\
  \ (ReDoS)\",\n    \"severity\": \"low\",\n    \"url\": \"https://snyk.io/vuln/npm:ms:20170412\"\
  ,\n    \"description\": \"Lorem ipsum\",\n    \"identifiers\": {\n      \"CVE\"\
  : [],\n      \"CWE\": [\n        \"CWE-400\"\n      ],\n      \"ALTERNATIVE\": [\n\
  \        \"SNYK-JS-MS-10509\"\n      ]\n    },\n    \"credit\": [\n      \"Snyk\
  \ Security Research Team\"\n    ],\n    \"exploitMaturity\": \"no-known-exploit\"\
  ,\n    \"semver\": {\n      \"vulnerable\": [\n        \">=0.7.1 <2.0.0\"\n    \
  \  ]\n    },\n    \"publicationTime\": \"2017-05-15T06:02:45Z\",\n    \"disclosureTime\"\
  : \"2017-04-11T21:00:00Z\",\n    \"CVSSv3\": \"CVSS:3.0/AV:N/AC:H/PR:N/UI:N/S:U/C:N/I:N/A:L\"\
  ,\n    \"cvssScore\": 3.7,\n    \"language\": \"js\",\n    \"patches\": [\n    \
  \  {\n        \"id\": \"patch:npm:ms:20170412:2\",\n        \"urls\": [\n      \
  \    \"https://snyk-patches.s3.amazonaws.com/npm/ms/20170412/ms_071.patch\"\n  \
  \      ],\n        \"version\": \"=0.7.1\",\n        \"comments\": [],\n       \
  \ \"modificationTime\": \"2019-12-03T11:40:45.866206Z\"\n      }\n    ],\n    \"\
  nearestFixedInVersion\": \"2.0.0\"\n  },\n  \"isPatched\": false,\n  \"isIgnored\"\
  : false,\n  \"fixInfo\": {\n    \"isUpgradable\": false,\n    \"isPinnable\": false,\n\
  \    \"isPatchable\": true,\n    \"nearestFixedInVersion\": \"2.0.0\"\n  },\n  \"\
  priority\": {\n    \"score\": 399,\n    \"factors\": [\n      {\n        \"name\"\
  : \"isFixable\",\n        \"description\": \"Has a fix available\"\n      },\n \
  \     {\n        \"name\": \"cvssScore\",\n        \"description\": \"CVSS 3.7\"\
  \n      }\n    ]\n  }\n}\n```"
logo: "snyk.io-logo.svg"
logoMediaType: "image/svg+xml"
tags:
- "developer_tools"
stubs: "snyk.io-stubs.json"
swagger: "snyk.io-swagger.json"
---
