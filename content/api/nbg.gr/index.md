---
slug: "nbg-gr"
title: "Account and Transaction API Specification - UK"
provider: "nbg.gr"
description: "## Functionality at a glance\r\n\r\nThe NBG \"UK OPB - Account and Transaction\
  \ v3.1.5\" API follows the [UK Open Banking Specification\r\n    v3.1.5](https://openbankinguk.github.io/read-write-api-site3/v3.1.5/profiles/account-and-transaction-api-profile.html)\r\
  \n\r\nThis Account and Transaction API Specification describes the flows and payloads\
  \ for retrieving a list of accounts and their transactions.\r\n\r\nThe API endpoints\
  \ described here allow a AISP to:  \r\n\r\n* Create the Consent with the appropriate\
  \ permissions in order to be able to access the API Endpoints\r\n\r\n* Retrieve\
  \ the list of accounts\r\n\r\n* Retrieve an account's details\r\n\r\n* Retrieve\
  \ an account's balances\r\n\r\n* Retrieve an account's transactions\r\n\r\n* Retrieve\
  \ an account's beneficiaries\r\n\r\n* Retrieve an account's standing orders\r\n\r\
  \n* Retrieve an account's party\r\n\r\n* Retrieve an account's scheduled payments\r\
  \n\r\n* Retrieve an account's statements\r\n\r\n\r\n\r\n## Quick Getting Started\r\
  \n\r\n\r\n1. **Login/Register** to the NBG Technology HUB\r\n\r\n2. Go to **\"APPS\"\
  **\r\n\r\n3. Select your Organization and go to step 4. If you want to create a\
  \ new Organization click **\\\"CREATE AN ORGANIZATION\\\"** and follow the steps\
  \ below:\r\n\t1. Enter the title of your Organization\r\n\t2. Enter a short description\
  \ of your Organization (optional)\r\n\t3. Click **\"SUBMIT\"**\r\n\r\n4. Select\
  \ the Organization of choice and click **\"ADD AN APPLICATION\"** \r\n\t  1. Fill\
  \ in the forms (title and short description)\r\n\t  2. Check **\\\"Authorization\
  \ Code\\\" and \\\"Client Credentials\\\"** \r\n\t  3. Enter the **OAuth Redirect\
  \ and Post Logout URIs** (these are the URIs that we will redirect the user upon\
  \ logging in and logging out respectively)\r\n\t\t  \r\n\t\t  You can use the following\
  \ redirect URL to easily test the API through the portal: *https://developer.nbg.gr/oauth2/redoc-callback*\r\
  \n\t  4. Click **\"SUBMIT\"**\r\n\t  5. Store the APPs **\"Client ID\"** and **\"\
  Client Secret\"**\r\n5. Go to **\"API PRODUCTS\"** and select the **ACCOUNT INFORMATION\
  \ - UK OPEN BANKING API**\r\n\r\n6. Click **\\\"START USING THIS API\\\"**, choose\
  \ your app and click\r\n**\"SUBSCRIBE\"**\r\n\r\n7. Get an Access Token using the\
  \ Access Token Flow and the API scopes provided in the Authentication and Authorization\
  \ (OAuth2) section below\r\n\r\n8. Create a Sandbox\r\n\r\n9. Play with the API\
  \ \r\n\r\n\r\n### Sandbox Flow\r\n\r\nThe Sandbox Flow matches the Production Flow.\
  \ The difference lies into the Data used. Instead of live\r\ndata, the Sandbox flow\
  \ uses mocked data.\r\n\r\n\r\n### Production Flow  \r\n\r\nThe Production Flow\
  \ is described in the [UK Open Banking v3.1.5\r\nSpecification](https://openbankinguk.github.io/read-write-api-site3/v3.1.5/profiles/account-and-transaction-api-profile.html)\r\
  \n\r\nMore details about the implementation specifics followed, please visit section\
  \ **UK OPB Implementation\r\nSpecifics**\r\n\r\n\r\n## Authentication and Authorization\
  \ (OAuth2)\r\n\r\nThis API version uses the OAuth2 protocol for authentication and\
  \ authorization, which means that a\r\nBearer (access token) should be acquired.\
  \ An access token can be retrieved using the client_id and\r\nclient_secret of the\
  \ APP that you created and subscribed in this API, and your own credentials\r\n\
  (username, password) that you use to sign in the NBG Technology HUB. The scopes\
  \ are defined below:\r\n\r\n**Authorization Endpoint:** \r\n\r\n\t  https://my.nbg.gr/identity/connect/authorize\r\
  \n\r\n\r\n**Token Endpoint:** \r\n\r\n\t  https://my.nbg.gr/identity/connect/token\r\
  \n\r\n### Authorization Code ###\r\n\r\n**Sandbox Scopes:** \r\n\r\n\t  sandbox-uk-account-info-api-v1\
  \ offline_access\r\n\r\n\r\n**Production Scopes:** \r\n\r\n\t  accounts offline_access\r\
  \n\r\n### Client Credentials ###\r\n\r\n**Sandbox Scopes:** \r\n\r\n\t  sandbox-uk-account-info-api-v1\r\
  \n\r\n\r\n**Production Scopes:** \r\n\r\n\t  accounts\r\n\r\n\r\nSee more [here](https://developer.nbg.gr/oauth-document)\r\
  \n\r\n## QWAC Certificates\r\n\r\nTPPs are required to present a QWAC certificate\
  \ during API consumption. The API checks that this certificate has been provided\
  \ and is valid. In sandbox mode the certificate validations are optional. To validate\
  \ your certificate in sandbox implementation, please send us your QWAC certificate\
  \ at developer@nbg.gr and set the HTTP Header **\\\"x-sandbox-qwac-certificate-check\\\
  \"** with the value **\\\"true\\\"** in your requests. \r\n\r\n## SMS Challenge\
  \ (One Time Password)\r\n\r\nIn order to successfully authorize an Accounts Access\
  \ you will need to provide the SMS OTP (One Time Password) in the corresponding\
  \ Accounts Consent UI Screen.\r\n\r\nBy default the SMS OTP will be sent to the\
  \ mobile number declared upon singing up in the NBG Technology HUB. \r\n\r\n\r\n\
  \r\n## Create your Sandbox\r\n\r\nCreate a new Sandbox application by invoking the\
  \ POST /sandbox. This call will generate a new Sandbox\r\nwith a unique sandbox-id.\r\
  \n\r\n\r\n__Important!__ Before proceeding save the sandbox id you just created.\r\
  \n\r\n\r\nWhen you create a sandbox, users and sandbox specific data are generated\
  \ as sample data.\r\n\r\n\r\n## Start Testing\r\n\r\nOnce you have your sandbox-id,\
  \ you can start invoking the rest of the operations by providing the\r\nmandatory\
  \ http header **sandbox-id**  and the http headers described below.\r\n\r\n\r\n\
  ## Important notes\r\n\r\n\r\n**Request headers**\r\n\r\n\r\nThe following HTTP\
  \ header parameters are required for every call:\r\n\r\n\r\n1. Authorization. The\
  \ Auth2 Token\r\n\r\n2. sandbox-id. Your Sandbox ID\r\n\r\n\r\n**Consent**\r\n\r\
  \n\r\nIn order to be able to effectively start using the Endpoints the appropriate\
  \ Consent needs to be\r\ncreated and set to the 'Authorised' status. \r\n\r\n\r\n\
  In order to create the Consent you need to at least set the required **permissions**\
  \ and the **Risk**\r\nsections. \r\n\r\n\r\nOptionally you may set the \r\n\r\n\r\
  \n1. ExpirationDateTime. When the Consent expires \r\n\r\n\r\n2. TransactionFromDateTime.\
  \ Start Date to retrieve the transactions \r\n\r\n\r\n3. TransactionToDateTime.\
  \ End Date to retrieve the transactions \r\n\r\n**Not Implemented Endpoints**\r\n\
  \r\nThe following endpoints are not implemented in the API\r\n\r\n1. GET /balances\r\
  \n2. GET /transactions\r\n3. GET /beneficiaries\r\n4. GET /accounts/\\{AccountId\\\
  }/direct-debits\r\n5. GET /direct-debits\r\n6. GET /standing-orders\r\n7. GET /accounts/\\\
  {AccountId\\}/product\r\n8. GET /products\r\n9. GET /accounts/\\{AccountId\\}/offers\r\
  \n10. GET /offers\r\n11. GET /scheduled-payments\r\n12. GET /statements\r\n\r\n\r\
  \n## Error Codes\r\n\r\nThe error codes and their description can be found\r\n[here](https://openbankinguk.github.io/read-write-api-site3/v3.1.5/profiles/read-write-data-api-profile.html#error-response-structure)\r\
  \n\r\n\r\n# UK OPB Implementation Specifics \r\n\r\nBelow you may find more specific\
  \ information &amp; limitations regarding the implementation followed in the Production\
  \ API.\r\n\r\n\r\n## Token Endpoint Client Authentication\r\n\r\nAt this point the\
  \ supported __Client Authentication__ method is \"__Client Secret Basic__\" - usage\
  \ of \"Client ID\" &amp; \"Client Secret\".\r\n\r\n\r\n## Consent Authorization\r\
  \n\r\nFor a PSU to Authorize a Consent, they need to be redirected to the appropriate\
  \ Consent UI.\r\n\r\nFor this redirection to take place the TPP needs to follow\
  \ the Authorization Endpoint by amending the generated \"Consent ID\", like this:\
  \ https://my.nbg.gr/identity/connect/authorize?consent_id={{consent_id}}&amp;client_id={{client_id}}&amp;scope={{scope}}&amp;redirect_uri={{redirect_uri}}&amp;response_type=code\r\
  \n\r\nOnce the PSU is redirected to the Consent Authorization Screen, they need\
  \ to enter their IBank (Production) or Developer Portal (Sandbox) Credentials and\
  \ either Authorize or Reject the Consent.\r\n\r\nAt this point the Consent is binded\
  \ with the PSU.\r\n\r\n\r\n## Debtor Account\r\nCurrently, only the \"UK.OBIE.IBAN\"\
  \ scheme is supported.\r\n\r\n\r\n\r\n# Feedback and Questions\r\n\r\nWe would love\
  \ to hear your feedback and answer your questions. Send us at\r\n[developer@nbg.gr](developer@nbg.gr)\r\
  \n\r\n\r\nCheck out our [Sandbox Postman\r\nCollection](https://github.com/NBG-Developer-Portal/Account-Information-UK-Open-Banking)!\r\
  \n\r\n\r\n________________________________________\r\n\r\nCreated by [**NBG**](https://www.nbg.gr/).\n\
  \n # Entities \n\n Below, the main entities are documented.\n &lt;a name=OBExternalPermissions1Code&gt;&lt;/a&gt;\
  \ \n## OBExternalPermissions1Code \n### Attributes \n\n| Type| Description| Example|\
  \ Values|\n| -----| -----| -----| -----|\n| enum| Specifies the Open Banking account\
  \ access data types. This is a list of the data clusters being consented by the\
  \ PSU, and requested for authorisation with the ASPSP.| &lt;ul style=\"padding-left:\
  \ 0\"&gt;&lt;li&gt;ReadAccountsBasic&lt;/li&gt;&lt;li&gt;ReadAccountsDetail&lt;/li&gt;&lt;li&gt;ReadBalances&lt;/li&gt;&lt;li&gt;ReadBeneficiariesBasic&lt;/li&gt;&lt;li&gt;ReadBeneficiariesDetail&lt;/li&gt;&lt;li&gt;ReadDirectDebits&lt;/li&gt;&lt;li&gt;ReadOffers&lt;/li&gt;&lt;li&gt;ReadPAN&lt;/li&gt;&lt;li&gt;ReadParty&lt;/li&gt;&lt;li&gt;ReadPartyPSU&lt;/li&gt;&lt;li&gt;ReadProducts&lt;/li&gt;&lt;li&gt;ReadScheduledPaymentsBasic&lt;/li&gt;&lt;li&gt;ReadScheduledPaymentsDetail&lt;/li&gt;&lt;li&gt;ReadStandingOrdersBasic&lt;/li&gt;&lt;li&gt;ReadStandingOrdersDetail&lt;/li&gt;&lt;li&gt;ReadStatementsBasic&lt;/li&gt;&lt;li&gt;ReadStatementsDetail&lt;/li&gt;&lt;li&gt;ReadTransactionsBasic&lt;/li&gt;&lt;li&gt;ReadTransactionsCredits&lt;/li&gt;&lt;li&gt;ReadTransactionsDebits&lt;/li&gt;&lt;li&gt;ReadTransactionsDetail&lt;/li&gt;&lt;/ul&gt;|\n\
  \n &lt;a name=OBReadData1&gt;&lt;/a&gt; \n## OBReadData1 \n\n\n### Attributes \n\
  \n| Name| Description| Values|\n| -----| -----| -----|\n| Permissions| Specifies\
  \ the Open Banking account access data types. This is a list of the data clusters\
  \ being consented by the PSU, and requested for authorisation with the ASPSP.| array[[OBExternalPermissions1Code](#OBExternalPermissions1Code)]|\n\
  | ExpirationDateTime| Specified date and time the permissions will expire. If this\
  \ is not populated, the permissions will be open ended. All dates in the JSON payloads\
  \ are represented in ISO 8601 date-time format.  All date-time fields in responses\
  \ must include the timezone. An example is below: 2017-04-05T10:43:07+00:00| string|\n\
  | TransactionFromDateTime| Specified start date and time for the transaction query\
  \ period. If this is not populated, the start date will be open ended, and data\
  \ will be returned from the earliest available transaction. All dates in the JSON\
  \ payloads are represented in ISO 8601 date-time format.  All date-time fields in\
  \ responses must include the timezone. An example is below: 2017-04-05T10:43:07+00:00|\
  \ string|\n| TransactionToDateTime| Specified end date and time for the transaction\
  \ query period. If this is not populated, the end date will be open ended, and data\
  \ will be returned to the latest available transaction. All dates in the JSON payloads\
  \ are represented in ISO 8601 date-time format.  All date-time fields in responses\
  \ must include the timezone. An example is below: 2017-04-05T10:43:07+00:00| string|\n\
  \n &lt;a name=OBRisk2&gt;&lt;/a&gt; \n## OBRisk2 \nThe Risk section is sent by the\
  \ initiating party to the ASPSP. It is used to specify additional details for risk\
  \ scoring for Account Info. \n\n### Attributes \n\n| Name| Description| Values|\n\
  | -----| -----| -----|\n\n &lt;a name=OBReadConsent1&gt;&lt;/a&gt; \n## OBReadConsent1\
  \ \n\n\n### Attributes \n\n| Name| Description| Values|\n| -----| -----| -----|\n\
  | Data | Entity | &lt;details&gt;&lt;summary&gt;[OBReadData1](#OBReadData1)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;Permissions\
  \ [array[[OBExternalPermissions1Code](#OBExternalPermissions1Code)]]&lt;/li&gt;\
  \ &lt;li&gt;ExpirationDateTime [string]&lt;/li&gt; &lt;li&gt;TransactionFromDateTime\
  \ [string]&lt;/li&gt; &lt;li&gt;TransactionToDateTime [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt;\
  \ | \n| Risk | Entity | &lt;details&gt;&lt;summary&gt;[OBRisk2](#OBRisk2)&lt;/summary&gt;&lt;ul&gt;&lt;/ul&gt;&lt;/details&gt;\
  \ | \n\n &lt;a name=ErrorCode&gt;&lt;/a&gt; \n## ErrorCode \n### Attributes \n\n\
  | Type| Description| Example| Values|\n| -----| -----| -----| -----|\n| enum| This\
  \ is Data Type gives a low level textual error code to help categorise an error\
  \ response. The applicable HTTP response code is also given.| &lt;ul style=\"padding-left:\
  \ 0\"&gt;&lt;li&gt;UK.OBIE.Field.Expected&lt;/li&gt;&lt;li&gt;UK.OBIE.Field.Invalid&lt;/li&gt;&lt;li&gt;UK.OBIE.Field.InvalidDate&lt;/li&gt;&lt;li&gt;UK.OBIE.Field.Missing&lt;/li&gt;&lt;li&gt;UK.OBIE.Field.Unexpected&lt;/li&gt;&lt;li&gt;UK.OBIE.Header.Invalid&lt;/li&gt;&lt;li&gt;UK.OBIE.Header.Missing&lt;/li&gt;&lt;li&gt;UK.OBIE.Resource.ConsentMismatch&lt;/li&gt;&lt;li&gt;UK.OBIE.Resource.InvalidConsentStatus&lt;/li&gt;&lt;li&gt;UK.OBIE.Resource.InvalidFormat&lt;/li&gt;&lt;li&gt;UK.OBIE.Resource.NotFound&lt;/li&gt;&lt;li&gt;UK.OBIE.Rules.AfterCutOffDateTime&lt;/li&gt;&lt;li&gt;UK.OBIE.Rules.DuplicateReference&lt;/li&gt;&lt;li&gt;UK.OBIE.Signature.Invalid&lt;/li&gt;&lt;li&gt;UK.OBIE.Signature.InvalidClaim&lt;/li&gt;&lt;li&gt;UK.OBIE.Signature.MissingClaim&lt;/li&gt;&lt;li&gt;UK.OBIE.Signature.Malformed&lt;/li&gt;&lt;li&gt;UK.OBIE.Signature.Missing&lt;/li&gt;&lt;li&gt;UK.OBIE.Signature.Unexpected&lt;/li&gt;&lt;li&gt;UK.OBIE.Unsupported.AccountIdentifier&lt;/li&gt;&lt;li&gt;UK.OBIE.Unsupported.AccountSecondaryIdentifier&lt;/li&gt;&lt;li&gt;UK.OBIE.Unsupported.Currency&lt;/li&gt;&lt;li&gt;UK.OBIE.Unsupported.EventType&lt;/li&gt;&lt;li&gt;UK.OBIE.Unsupported.Frequency&lt;/li&gt;&lt;li&gt;UK.OBIE.Unsupported.LocalInstrument&lt;/li&gt;&lt;li&gt;UK.OBIE.Unsupported.Scheme&lt;/li&gt;&lt;li&gt;UK.OBIE.Reauthenticate&lt;/li&gt;&lt;li&gt;UK.OBIE.Rules.ResourceAlreadyExists&lt;/li&gt;&lt;li&gt;UK.OBIE.UnexpectedError&lt;/li&gt;&lt;/ul&gt;|\n\
  \n &lt;a name=OBError1&gt;&lt;/a&gt; \n## OBError1 \n\n\n### Attributes \n\n| Name|\
  \ Description| Values|\n| -----| -----| -----|\n| ErrorCode | Entity | &lt;details&gt;&lt;summary&gt;[ErrorCode](#ErrorCode)&lt;/summary&gt;&lt;ul&gt;&lt;/ul&gt;&lt;/details&gt;\
  \ | \n| Message| A description of the error that occurred. e.g., 'A mandatory field\
  \ isn't supplied' or 'RequestedExecutionDateTime must be in future'OBIE doesn't\
  \ standardise this field| string|\n| Path| Recommended but optional reference to\
  \ the JSON Path of the field with error, e.g., Data.Initiation.InstructedAmount.Currency|\
  \ string|\n\n &lt;a name=OBErrorResponse1&gt;&lt;/a&gt; \n## OBErrorResponse1 \n\
  An array of detail error codes, and messages, and URLs to documentation to help\
  \ remediation. \n\n### Attributes \n\n| Name| Description| Values|\n| -----| -----|\
  \ -----|\n| Code| High level textual error code, to help categorize the errors.|\
  \ string|\n| Id| A unique reference for the error instance, for audit purposes,\
  \ in case of unknown/unclassified errors.| string|\n| Message| Brief Error message,\
  \ e.g., 'There is something wrong with the request parameters provided'| string|\n\
  | Errors| Gets or Sets Errors| array[[OBError1](#OBError1)]|\n\n &lt;a name=OBExternalRequestStatus1Code&gt;&lt;/a&gt;\
  \ \n## OBExternalRequestStatus1Code \n### Attributes \n\n| Type| Description| Example|\
  \ Values|\n| -----| -----| -----| -----|\n| enum| Specifies the status of consent\
  \ resource in code form.| &lt;ul style=\"padding-left: 0\"&gt;&lt;li&gt;Authorised&lt;/li&gt;&lt;li&gt;AwaitingAuthorisation&lt;/li&gt;&lt;li&gt;Rejected&lt;/li&gt;&lt;li&gt;Revoked&lt;/li&gt;&lt;/ul&gt;|\n\
  \n &lt;a name=OBReadDataConsentResponse1&gt;&lt;/a&gt; \n## OBReadDataConsentResponse1\
  \ \n\n\n### Attributes \n\n| Name| Description| Values|\n| -----| -----| -----|\n\
  | ConsentId| Unique identification as assigned to identify the account access consent\
  \ resource.| string|\n| CreationDateTime| Date and time at which the resource was\
  \ created. All dates in the JSON payloads are represented in ISO 8601 date-time\
  \ format.  All date-time fields in responses must include the timezone. An example\
  \ is below: 2017-04-05T10:43:07+00:00| string|\n| Status | Entity | &lt;details&gt;&lt;summary&gt;[OBExternalRequestStatus1Code](#OBExternalRequestStatus1Code)&lt;/summary&gt;&lt;ul&gt;&lt;/ul&gt;&lt;/details&gt;\
  \ | \n| StatusUpdateDateTime| Date and time at which the resource status was updated.\
  \ All dates in the JSON payloads are represented in ISO 8601 date-time format. \
  \ All date-time fields in responses must include the timezone. An example is below:\
  \ 2017-04-05T10:43:07+00:00| string|\n| Permissions| Specifies the Open Banking\
  \ account access data types. This is a list of the data clusters being consented\
  \ by the PSU, and requested for authorisation with the ASPSP.| array[[OBExternalPermissions1Code](#OBExternalPermissions1Code)]|\n\
  | ExpirationDateTime| Specified date and time the permissions will expire. If this\
  \ is not populated, the permissions will be open ended. All dates in the JSON payloads\
  \ are represented in ISO 8601 date-time format.  All date-time fields in responses\
  \ must include the timezone. An example is below: 2017-04-05T10:43:07+00:00| string|\n\
  | TransactionFromDateTime| Specified start date and time for the transaction query\
  \ period. If this is not populated, the start date will be open ended, and data\
  \ will be returned from the earliest available transaction. All dates in the JSON\
  \ payloads are represented in ISO 8601 date-time format.  All date-time fields in\
  \ responses must include the timezone. An example is below: 2017-04-05T10:43:07+00:00|\
  \ string|\n| TransactionToDateTime| Specified end date and time for the transaction\
  \ query period. If this is not populated, the end date will be open ended, and data\
  \ will be returned to the latest available transaction. All dates in the JSON payloads\
  \ are represented in ISO 8601 date-time format.  All date-time fields in responses\
  \ must include the timezone. An example is below: 2017-04-05T10:43:07+00:00| string|\n\
  \n &lt;a name=Links&gt;&lt;/a&gt; \n## Links \nLinks relevant to the payload \n\n\
  ### Attributes \n\n| Name| Description| Values|\n| -----| -----| -----|\n| Self|\
  \ -| string|\n| First| -| string|\n| Prev| -| string|\n| Next| -| string|\n| Last|\
  \ -| string|\n\n &lt;a name=Meta&gt;&lt;/a&gt; \n## Meta \nMeta Data relevant to\
  \ the payload \n\n### Attributes \n\n| Name| Description| Values|\n| -----| -----|\
  \ -----|\n| TotalPages| -| integer|\n| FirstAvailableDateTime| All dates in the\
  \ JSON payloads are represented in ISO 8601 date-time format. All date-time fields\
  \ in responses must include the timezone.An example is below: 2017-04-05T10:43:07+00:00|\
  \ string|\n| LastAvailableDateTime| All dates in the JSON payloads are represented\
  \ in ISO 8601 date-time format. All date-time fields in responses must include the\
  \ timezone.An example is below: 2017-04-05T10:43:07+00:00| string|\n\n &lt;a name=OBReadConsentResponse1&gt;&lt;/a&gt;\
  \ \n## OBReadConsentResponse1 \n\n\n### Attributes \n\n| Name| Description| Values|\n\
  | -----| -----| -----|\n| Data | Entity | &lt;details&gt;&lt;summary&gt;[OBReadDataConsentResponse1](#OBReadDataConsentResponse1)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;ConsentId\
  \ [string]&lt;/li&gt; &lt;li&gt;CreationDateTime [string]&lt;/li&gt; &lt;li&gt;&lt;details&gt;&lt;summary&gt;Status\
  \ [[OBExternalRequestStatus1Code](#OBExternalRequestStatus1Code)]&lt;/summary&gt;&lt;ul&gt;&lt;/ul&gt;&lt;/details&gt;&lt;/li&gt;&lt;li&gt;StatusUpdateDateTime\
  \ [string]&lt;/li&gt; &lt;li&gt;Permissions [array[[OBExternalPermissions1Code](#OBExternalPermissions1Code)]]&lt;/li&gt;\
  \ &lt;li&gt;ExpirationDateTime [string]&lt;/li&gt; &lt;li&gt;TransactionFromDateTime\
  \ [string]&lt;/li&gt; &lt;li&gt;TransactionToDateTime [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt;\
  \ | \n| Risk | Entity | &lt;details&gt;&lt;summary&gt;[OBRisk2](#OBRisk2)&lt;/summary&gt;&lt;ul&gt;&lt;/ul&gt;&lt;/details&gt;\
  \ | \n| Links | Entity | &lt;details&gt;&lt;summary&gt;[Links](#Links)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;Self\
  \ [string]&lt;/li&gt; &lt;li&gt;First [string]&lt;/li&gt; &lt;li&gt;Prev [string]&lt;/li&gt;\
  \ &lt;li&gt;Next [string]&lt;/li&gt; &lt;li&gt;Last [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt;\
  \ | \n| Meta | Entity | &lt;details&gt;&lt;summary&gt;[Meta](#Meta)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;TotalPages\
  \ [integer]&lt;/li&gt; &lt;li&gt;FirstAvailableDateTime [string]&lt;/li&gt; &lt;li&gt;LastAvailableDateTime\
  \ [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt; | \n\n &lt;a name=OBExternalAccountType1Code&gt;&lt;/a&gt;\
  \ \n## OBExternalAccountType1Code \n### Attributes \n\n| Type| Description| Example|\
  \ Values|\n| -----| -----| -----| -----|\n| enum| -| &lt;ul style=\"padding-left:\
  \ 0\"&gt;&lt;li&gt;Business&lt;/li&gt;&lt;li&gt;Personal&lt;/li&gt;&lt;/ul&gt;|\n\
  \n &lt;a name=OBExternalAccountSubType1Code&gt;&lt;/a&gt; \n## OBExternalAccountSubType1Code\
  \ \n### Attributes \n\n| Type| Description| Example| Values|\n| -----| -----| -----|\
  \ -----|\n| enum| -| &lt;ul style=\"padding-left: 0\"&gt;&lt;li&gt;ChargeCard&lt;/li&gt;&lt;li&gt;CreditCard&lt;/li&gt;&lt;li&gt;CurrentAccount&lt;/li&gt;&lt;li&gt;EMoney&lt;/li&gt;&lt;li&gt;Loan&lt;/li&gt;&lt;li&gt;Mortgage&lt;/li&gt;&lt;li&gt;PrePaidCard&lt;/li&gt;&lt;li&gt;Savings&lt;/li&gt;&lt;/ul&gt;|\n\
  \n &lt;a name=OBCashAccount5&gt;&lt;/a&gt; \n## OBCashAccount5 \n\n\n### Attributes\
  \ \n\n| Name| Description| Values|\n| -----| -----| -----|\n| SchemeName| Name of\
  \ the identification scheme, in a coded form as published in an external list.|\
  \ string|\n| Identification| Identification assigned by an institution to identify\
  \ an account. This identification is known by the account owner.| string|\n| Name|\
  \ The account name is the name or names of the account owner(s) represented at an\
  \ account level, as displayed by the ASPSP's online channels. Note, the account\
  \ name is not the product name or the nickname of the account.| string|\n| SecondaryIdentification|\
  \ This is secondary identification of the account, as assigned by the account servicing\
  \ institution. This can be used by building societies to additionally identify accounts\
  \ with a roll number(in addition to a sort code and account number combination).|\
  \ string|\n\n &lt;a name=OBBranchAndFinancialInstitutionIdentification5&gt;&lt;/a&gt;\
  \ \n## OBBranchAndFinancialInstitutionIdentification5 \n\n\n### Attributes \n\n\
  | Name| Description| Values|\n| -----| -----| -----|\n| SchemeName| Name of the\
  \ identification scheme, in a coded form as published in an external list.| string|\n\
  | Identification| Unique and unambiguous identification of the servicing institution.|\
  \ string|\n\n &lt;a name=OBAccount6&gt;&lt;/a&gt; \n## OBAccount6 \nUnambiguous\
  \ identification of the account to which credit and debit entries are made. \n\n\
  ### Attributes \n\n| Name| Description| Values|\n| -----| -----| -----|\n| AccountId|\
  \ A unique and immutable identifier used to identify the account resource. This\
  \ identifier has no meaning to the account owner.| string|\n| Currency| Identification\
  \ of the currency in which the account is held.  Usage: Currency should only be\
  \ used in case one and the same account number covers several currencies and the\
  \ initiating party needs to identify which currency needs to be used for settlement\
  \ on the account.| string|\n| AccountType | Entity | &lt;details&gt;&lt;summary&gt;[OBExternalAccountType1Code](#OBExternalAccountType1Code)&lt;/summary&gt;&lt;ul&gt;&lt;/ul&gt;&lt;/details&gt;\
  \ | \n| AccountSubType | Entity | &lt;details&gt;&lt;summary&gt;[OBExternalAccountSubType1Code](#OBExternalAccountSubType1Code)&lt;/summary&gt;&lt;ul&gt;&lt;/ul&gt;&lt;/details&gt;\
  \ | \n| Description| Specifies the description of the account type.| string|\n|\
  \ Nickname| The nickname of the account, assigned by the account owner in order\
  \ to provide an additional means of identification of the account.| string|\n| OpeningDate|\
  \ Date on which the account and related basic services are effectively operational\
  \ for the account owner.All dates in the JSON payloads are represented in ISO 8601\
  \ date-time format.  All date-time fields in responses must include the timezone.\
  \ An example is below: 2017-04-05T10:43:07+00:00| string|\n| Account| Provides the\
  \ details to identify an account.| array[[OBCashAccount5](#OBCashAccount5)]|\n|\
  \ Servicer | Entity | &lt;details&gt;&lt;summary&gt;[OBBranchAndFinancialInstitutionIdentification5](#OBBranchAndFinancialInstitutionIdentification5)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;SchemeName\
  \ [string]&lt;/li&gt; &lt;li&gt;Identification [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt;\
  \ | \n\n &lt;a name=OBReadDataAccount5&gt;&lt;/a&gt; \n## OBReadDataAccount5 \n\n\
  \n### Attributes \n\n| Name| Description| Values|\n| -----| -----| -----|\n| Account|\
  \ Unambiguous identification of the account to which credit and debit entries are\
  \ made.| array[[OBAccount6](#OBAccount6)]|\n\n &lt;a name=OBReadAccount5&gt;&lt;/a&gt;\
  \ \n## OBReadAccount5 \n\n\n### Attributes \n\n| Name| Description| Values|\n| -----|\
  \ -----| -----|\n| Data | Entity | &lt;details&gt;&lt;summary&gt;[OBReadDataAccount5](#OBReadDataAccount5)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;Account\
  \ [array[[OBAccount6](#OBAccount6)]]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt; | \n\
  | Links | Entity | &lt;details&gt;&lt;summary&gt;[Links](#Links)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;Self\
  \ [string]&lt;/li&gt; &lt;li&gt;First [string]&lt;/li&gt; &lt;li&gt;Prev [string]&lt;/li&gt;\
  \ &lt;li&gt;Next [string]&lt;/li&gt; &lt;li&gt;Last [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt;\
  \ | \n| Meta | Entity | &lt;details&gt;&lt;summary&gt;[Meta](#Meta)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;TotalPages\
  \ [integer]&lt;/li&gt; &lt;li&gt;FirstAvailableDateTime [string]&lt;/li&gt; &lt;li&gt;LastAvailableDateTime\
  \ [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt; | \n\n &lt;a name=OBCreditDebitCode&gt;&lt;/a&gt;\
  \ \n## OBCreditDebitCode \n### Attributes \n\n| Type| Description| Example| Values|\n\
  | -----| -----| -----| -----|\n| enum| -| &lt;ul style=\"padding-left: 0\"&gt;&lt;li&gt;Credit&lt;/li&gt;&lt;li&gt;Debit&lt;/li&gt;&lt;/ul&gt;|\n\
  \n &lt;a name=OBBalanceType1Code&gt;&lt;/a&gt; \n## OBBalanceType1Code \n### Attributes\
  \ \n\n| Type| Description| Example| Values|\n| -----| -----| -----| -----|\n| enum|\
  \ -| &lt;ul style=\"padding-left: 0\"&gt;&lt;li&gt;ClosingAvailable&lt;/li&gt;&lt;li&gt;ClosingBooked&lt;/li&gt;&lt;li&gt;ClosingCleared&lt;/li&gt;&lt;li&gt;Expected&lt;/li&gt;&lt;li&gt;ForwardAvailable&lt;/li&gt;&lt;li&gt;Information&lt;/li&gt;&lt;li&gt;InterimAvailable&lt;/li&gt;&lt;li&gt;InterimBooked&lt;/li&gt;&lt;li&gt;InterimCleared&lt;/li&gt;&lt;li&gt;OpeningAvailable&lt;/li&gt;&lt;li&gt;OpeningBooked&lt;/li&gt;&lt;li&gt;OpeningCleared&lt;/li&gt;&lt;li&gt;PreviouslyClosedBooked&lt;/li&gt;&lt;/ul&gt;|\n\
  \n &lt;a name=OBActiveOrHistoricCurrencyAndAmount&gt;&lt;/a&gt; \n## OBActiveOrHistoricCurrencyAndAmount\
  \ \n\n\n### Attributes \n\n| Name| Description| Values|\n| -----| -----| -----|\n\
  | Amount| A number of monetary units specified in an active currency where the unit\
  \ of currency is explicit and compliant with ISO 4217.| string|\n| Currency| A code\
  \ allocated to a currency by a Maintenance Agency under an international identification\
  \ scheme, as described in the latest edition of the international standard ISO 4217\
  \ \"Codes for the representation of currencies and funds\".| string|\n\n &lt;a name=OBExternalLimitType1Code&gt;&lt;/a&gt;\
  \ \n## OBExternalLimitType1Code \n### Attributes \n\n| Type| Description| Example|\
  \ Values|\n| -----| -----| -----| -----|\n| enum| -| &lt;ul style=\"padding-left:\
  \ 0\"&gt;&lt;li&gt;Available&lt;/li&gt;&lt;li&gt;Credit&lt;/li&gt;&lt;li&gt;Emergency&lt;/li&gt;&lt;li&gt;Pre-Agreed&lt;/li&gt;&lt;li&gt;Temporary&lt;/li&gt;&lt;/ul&gt;|\n\
  \n &lt;a name=OBCreditLine1&gt;&lt;/a&gt; \n## OBCreditLine1 \n\n\n### Attributes\
  \ \n\n| Name| Description| Values|\n| -----| -----| -----|\n| Included| Indicates\
  \ whether or not the credit line is included in the balance of the account. Usage:\
  \ If not present, credit line is not included in the balance amount of the account.|\
  \ boolean|\n| Type | Entity | &lt;details&gt;&lt;summary&gt;[OBExternalLimitType1Code](#OBExternalLimitType1Code)&lt;/summary&gt;&lt;ul&gt;&lt;/ul&gt;&lt;/details&gt;\
  \ | \n| Amount | Entity | &lt;details&gt;&lt;summary&gt;[OBActiveOrHistoricCurrencyAndAmount](#OBActiveOrHistoricCurrencyAndAmount)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;Amount\
  \ [string]&lt;/li&gt; &lt;li&gt;Currency [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt;\
  \ | \n\n &lt;a name=OBCashBalance1&gt;&lt;/a&gt; \n## OBCashBalance1 \nSet of elements\
  \ used to define the balance details. \n\n### Attributes \n\n| Name| Description|\
  \ Values|\n| -----| -----| -----|\n| AccountId| A unique and immutable identifier\
  \ used to identify the account resource. This identifier has no meaning to the account\
  \ owner.| string|\n| CreditDebitIndicator | Entity | &lt;details&gt;&lt;summary&gt;[OBCreditDebitCode](#OBCreditDebitCode)&lt;/summary&gt;&lt;ul&gt;&lt;/ul&gt;&lt;/details&gt;\
  \ | \n| Type | Entity | &lt;details&gt;&lt;summary&gt;[OBBalanceType1Code](#OBBalanceType1Code)&lt;/summary&gt;&lt;ul&gt;&lt;/ul&gt;&lt;/details&gt;\
  \ | \n| DateTime| Indicates the date (and time) of the balance.All dates in the\
  \ JSON payloads are represented in ISO 8601 date-time format.  All date-time fields\
  \ in responses must include the timezone. An example is below: 2017-04-05T10:43:07+00:00|\
  \ string|\n| Amount | Entity | &lt;details&gt;&lt;summary&gt;[OBActiveOrHistoricCurrencyAndAmount](#OBActiveOrHistoricCurrencyAndAmount)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;Amount\
  \ [string]&lt;/li&gt; &lt;li&gt;Currency [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt;\
  \ | \n| CreditLine| Set of elements used to provide details on the credit line.|\
  \ array[[OBCreditLine1](#OBCreditLine1)]|\n\n &lt;a name=OBReadDataBalance1&gt;&lt;/a&gt;\
  \ \n## OBReadDataBalance1 \n\n\n### Attributes \n\n| Name| Description| Values|\n\
  | -----| -----| -----|\n| Balance| Set of elements used to define the balance details.|\
  \ array[[OBCashBalance1](#OBCashBalance1)]|\n\n &lt;a name=OBReadBalance1&gt;&lt;/a&gt;\
  \ \n## OBReadBalance1 \n\n\n### Attributes \n\n| Name| Description| Values|\n| -----|\
  \ -----| -----|\n| Data | Entity | &lt;details&gt;&lt;summary&gt;[OBReadDataBalance1](#OBReadDataBalance1)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;Balance\
  \ [array[[OBCashBalance1](#OBCashBalance1)]]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt;\
  \ | \n| Links | Entity | &lt;details&gt;&lt;summary&gt;[Links](#Links)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;Self\
  \ [string]&lt;/li&gt; &lt;li&gt;First [string]&lt;/li&gt; &lt;li&gt;Prev [string]&lt;/li&gt;\
  \ &lt;li&gt;Next [string]&lt;/li&gt; &lt;li&gt;Last [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt;\
  \ | \n| Meta | Entity | &lt;details&gt;&lt;summary&gt;[Meta](#Meta)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;TotalPages\
  \ [integer]&lt;/li&gt; &lt;li&gt;FirstAvailableDateTime [string]&lt;/li&gt; &lt;li&gt;LastAvailableDateTime\
  \ [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt; | \n\n &lt;a name=OBBeneficiaryType1Code&gt;&lt;/a&gt;\
  \ \n## OBBeneficiaryType1Code \n### Attributes \n\n| Type| Description| Example|\
  \ Values|\n| -----| -----| -----| -----|\n| enum| Specifies the Beneficiary Type.|\
  \ &lt;ul style=\"padding-left: 0\"&gt;&lt;li&gt;Trusted&lt;/li&gt;&lt;li&gt;Ordinary&lt;/li&gt;&lt;/ul&gt;|\n\
  \n &lt;a name=OBBeneficiary5&gt;&lt;/a&gt; \n## OBBeneficiary5 \n\n\n### Attributes\
  \ \n\n| Name| Description| Values|\n| -----| -----| -----|\n| AccountId| A unique\
  \ and immutable identifier used to identify the account resource. This identifier\
  \ has no meaning to the account owner.| string|\n| BeneficiaryType | Entity | &lt;details&gt;&lt;summary&gt;[OBBeneficiaryType1Code](#OBBeneficiaryType1Code)&lt;/summary&gt;&lt;ul&gt;&lt;/ul&gt;&lt;/details&gt;\
  \ | \n| CreditorAccount | Entity | &lt;details&gt;&lt;summary&gt;[OBCashAccount5](#OBCashAccount5)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;SchemeName\
  \ [string]&lt;/li&gt; &lt;li&gt;Identification [string]&lt;/li&gt; &lt;li&gt;Name\
  \ [string]&lt;/li&gt; &lt;li&gt;SecondaryIdentification [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt;\
  \ | \n\n &lt;a name=OBReadDataBeneficiary5&gt;&lt;/a&gt; \n## OBReadDataBeneficiary5\
  \ \n\n\n### Attributes \n\n| Name| Description| Values|\n| -----| -----| -----|\n\
  | Beneficiary| -| array[[OBBeneficiary5](#OBBeneficiary5)]|\n\n &lt;a name=OBReadBeneficiary5&gt;&lt;/a&gt;\
  \ \n## OBReadBeneficiary5 \n\n\n### Attributes \n\n| Name| Description| Values|\n\
  | -----| -----| -----|\n| Data | Entity | &lt;details&gt;&lt;summary&gt;[OBReadDataBeneficiary5](#OBReadDataBeneficiary5)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;Beneficiary\
  \ [array[[OBBeneficiary5](#OBBeneficiary5)]]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt;\
  \ | \n| Links | Entity | &lt;details&gt;&lt;summary&gt;[Links](#Links)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;Self\
  \ [string]&lt;/li&gt; &lt;li&gt;First [string]&lt;/li&gt; &lt;li&gt;Prev [string]&lt;/li&gt;\
  \ &lt;li&gt;Next [string]&lt;/li&gt; &lt;li&gt;Last [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt;\
  \ | \n| Meta | Entity | &lt;details&gt;&lt;summary&gt;[Meta](#Meta)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;TotalPages\
  \ [integer]&lt;/li&gt; &lt;li&gt;FirstAvailableDateTime [string]&lt;/li&gt; &lt;li&gt;LastAvailableDateTime\
  \ [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt; | \n\n &lt;a name=OBParty2&gt;&lt;/a&gt;\
  \ \n## OBParty2 \n\n\n### Attributes \n\n| Name| Description| Values|\n| -----|\
  \ -----| -----|\n| PartyId| A unique and immutable identifier used to identify the\
  \ customer resource. This identifier has no meaning to the account owner.| string|\n\
  | Name| Name by which a party is known and which is usually used to identify that\
  \ party.| string|\n\n &lt;a name=OBReadDataParty2&gt;&lt;/a&gt; \n## OBReadDataParty2\
  \ \n\n\n### Attributes \n\n| Name| Description| Values|\n| -----| -----| -----|\n\
  | Party | Entity | &lt;details&gt;&lt;summary&gt;[OBParty2](#OBParty2)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;PartyId\
  \ [string]&lt;/li&gt; &lt;li&gt;Name [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt;\
  \ | \n\n &lt;a name=OBReadParty2&gt;&lt;/a&gt; \n## OBReadParty2 \n\n\n### Attributes\
  \ \n\n| Name| Description| Values|\n| -----| -----| -----|\n| Data | Entity | &lt;details&gt;&lt;summary&gt;[OBReadDataParty2](#OBReadDataParty2)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;&lt;details&gt;&lt;summary&gt;Party\
  \ [[OBParty2](#OBParty2)]&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;PartyId [string]&lt;/li&gt;\
  \ &lt;li&gt;Name [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt;&lt;/li&gt;&lt;/ul&gt;&lt;/details&gt;\
  \ | \n| Links | Entity | &lt;details&gt;&lt;summary&gt;[Links](#Links)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;Self\
  \ [string]&lt;/li&gt; &lt;li&gt;First [string]&lt;/li&gt; &lt;li&gt;Prev [string]&lt;/li&gt;\
  \ &lt;li&gt;Next [string]&lt;/li&gt; &lt;li&gt;Last [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt;\
  \ | \n| Meta | Entity | &lt;details&gt;&lt;summary&gt;[Meta](#Meta)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;TotalPages\
  \ [integer]&lt;/li&gt; &lt;li&gt;FirstAvailableDateTime [string]&lt;/li&gt; &lt;li&gt;LastAvailableDateTime\
  \ [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt; | \n\n &lt;a name=OBReadDataParty3&gt;&lt;/a&gt;\
  \ \n## OBReadDataParty3 \n\n\n### Attributes \n\n| Name| Description| Values|\n\
  | -----| -----| -----|\n| Party| -| array[[OBParty2](#OBParty2)]|\n\n &lt;a name=OBReadParty3&gt;&lt;/a&gt;\
  \ \n## OBReadParty3 \n\n\n### Attributes \n\n| Name| Description| Values|\n| -----|\
  \ -----| -----|\n| Data | Entity | &lt;details&gt;&lt;summary&gt;[OBReadDataParty3](#OBReadDataParty3)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;Party\
  \ [array[[OBParty2](#OBParty2)]]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt; | \n| Links\
  \ | Entity | &lt;details&gt;&lt;summary&gt;[Links](#Links)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;Self\
  \ [string]&lt;/li&gt; &lt;li&gt;First [string]&lt;/li&gt; &lt;li&gt;Prev [string]&lt;/li&gt;\
  \ &lt;li&gt;Next [string]&lt;/li&gt; &lt;li&gt;Last [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt;\
  \ | \n| Meta | Entity | &lt;details&gt;&lt;summary&gt;[Meta](#Meta)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;TotalPages\
  \ [integer]&lt;/li&gt; &lt;li&gt;FirstAvailableDateTime [string]&lt;/li&gt; &lt;li&gt;LastAvailableDateTime\
  \ [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt; | \n\n &lt;a name=SandboxRequest&gt;&lt;/a&gt;\
  \ \n## SandboxRequest \nRequest to create a new sandbox \n\n### Attributes \n\n\
  | Name| Description| Values|\n| -----| -----| -----|\n| sandboxId| Sandbox Id| string|\n\
  \n &lt;a name=ErrorResponse&gt;&lt;/a&gt; \n## ErrorResponse \n\n\n### Attributes\
  \ \n\n| Name| Description| Values|\n| -----| -----| -----|\n| errorMessage| -| string|\n\
  \n &lt;a name=SandboxRetryCacheEntry&gt;&lt;/a&gt; \n## SandboxRetryCacheEntry \n\
  Keeps the number of calls without x-fapi-customer-ip-address header present \n\n\
  ### Attributes \n\n| Name| Description| Values|\n| -----| -----| -----|\n| cacheKey|\
  \ Cache key| string|\n| count| Number of retries ( up to 4 )| integer|\n| expirationTimestamp|\
  \ Expiration timestamp of the entry| string|\n\n &lt;a name=SandboxBankAccountInfo&gt;&lt;/a&gt;\
  \ \n## SandboxBankAccountInfo \nGeneral account information \n\n### Attributes \n\
  \n| Name| Description| Values|\n| -----| -----| -----|\n| currency| Currency (EUR,\
  \ USD ...)| string|\n| iban| Account's IBAN| string|\n| accountType| Account's type\
  \ (Business, Personal)| string|\n| accountSubType| Account's sub-type (ChargeCard,\
  \ CreditCard, CurrentAccount ...)| string|\n| description| Account's description|\
  \ string|\n| alias| Account's alias| string|\n| openingDate| Account's opening date|\
  \ string|\n| availableBalance| Account's available balance| number|\n| ledgerBalance|\
  \ Account's ledger balance| number|\n| overdraftLimit| Account's overdraft limit|\
  \ number|\n\n &lt;a name=SandboxParty&gt;&lt;/a&gt; \n## SandboxParty \nConnected\
  \ party information \n\n### Attributes \n\n| Name| Description| Values|\n| -----|\
  \ -----| -----|\n| id| Party id| string|\n| name| Name| string|\n\n &lt;a name=SandboxBeneficiary&gt;&lt;/a&gt;\
  \ \n## SandboxBeneficiary \nBeneficiary information \n\n### Attributes \n\n| Name|\
  \ Description| Values|\n| -----| -----| -----|\n| name| Beneficiary name| string|\n\
  \n &lt;a name=SandboxStandingOrder&gt;&lt;/a&gt; \n## SandboxStandingOrder \nStanding\
  \ order information \n\n### Attributes \n\n| Name| Description| Values|\n| -----|\
  \ -----| -----|\n| description| Standing order short description| string|\n| frequency|\
  \ Standing order frequency| string|\n| firstPaymentDate| Standing order first collection\
  \ date| string|\n| nextPaymentDate| Standing order next collection date| string|\n\
  | finalPaymentDate| Standing order final collection date| string|\n| lastPaymentDate|\
  \ Standing order last executed payment date| string|\n| status| Standing order status\
  \ (Active, Inactive)| string|\n| amount| Standing order amount| number|\n\n &lt;a\
  \ name=SandboxScheduledPayment&gt;&lt;/a&gt; \n## SandboxScheduledPayment \nScheduled\
  \ payment information \n\n### Attributes \n\n| Name| Description| Values|\n| -----|\
  \ -----| -----|\n| description| Scheduled payment's short description| string|\n\
  | executionDate| Scheduled payment's execution date| string|\n| amount| Amount|\
  \ number|\n| senderReference| Debtor / Sender reference| string|\n\n &lt;a name=SandboxStatement&gt;&lt;/a&gt;\
  \ \n## SandboxStatement \nStatement information \n\n### Attributes \n\n| Name| Description|\
  \ Values|\n| -----| -----| -----|\n| number| Statement number| string|\n| year|\
  \ Statement year| integer|\n| month| Statement month| integer|\n\n &lt;a name=SandboxTransaction&gt;&lt;/a&gt;\
  \ \n## SandboxTransaction \nTransaction information \n\n### Attributes \n\n| Name|\
  \ Description| Values|\n| -----| -----| -----|\n| reference| Transaction reference|\
  \ string|\n| amount| Amount| number|\n| currency| Currency (EUR, USD ...)| string|\n\
  | creditDebit| Credit / Debit indicator| string|\n| valueDateTime| Valeur| string|\n\
  | bookingDateTime| Booking date time| string|\n| description| Description| string|\n\
  | accountingBalance| Balance| number|\n| relatedAccount| Related account| string|\n\
  | relatedName| Related account| string|\n| transactionCode| Transaction code| string|\n\
  \n &lt;a name=SandboxBankAccount&gt;&lt;/a&gt; \n## SandboxBankAccount \nSandbox\
  \ bank account \n\n### Attributes \n\n| Name| Description| Values|\n| -----| -----|\
  \ -----|\n| info | Entity | &lt;details&gt;&lt;summary&gt;[SandboxBankAccountInfo](#SandboxBankAccountInfo)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;currency\
  \ [string]&lt;/li&gt; &lt;li&gt;iban [string]&lt;/li&gt; &lt;li&gt;accountType [string]&lt;/li&gt;\
  \ &lt;li&gt;accountSubType [string]&lt;/li&gt; &lt;li&gt;description [string]&lt;/li&gt;\
  \ &lt;li&gt;alias [string]&lt;/li&gt; &lt;li&gt;openingDate [string]&lt;/li&gt;\
  \ &lt;li&gt;availableBalance [number]&lt;/li&gt; &lt;li&gt;ledgerBalance [number]&lt;/li&gt;\
  \ &lt;li&gt;overdraftLimit [number]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt; | \n\
  | party | Entity | &lt;details&gt;&lt;summary&gt;[SandboxParty](#SandboxParty)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;id\
  \ [string]&lt;/li&gt; &lt;li&gt;name [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt;\
  \ | \n| beneficiaries| List of account's beneficiaries| array[[SandboxBeneficiary](#SandboxBeneficiary)]|\n\
  | standingOrders| List of account's standing orders| array[[SandboxStandingOrder](#SandboxStandingOrder)]|\n\
  | scheduledPayments| List of account's scheduled payments| array[[SandboxScheduledPayment](#SandboxScheduledPayment)]|\n\
  | statements| List of account's statements| array[[SandboxStatement](#SandboxStatement)]|\n\
  | transactions| List of account's transactions| array[[SandboxTransaction](#SandboxTransaction)]|\n\
  \n &lt;a name=SandboxCardInfo&gt;&lt;/a&gt; \n## SandboxCardInfo \nSandbox card\
  \ information \n\n### Attributes \n\n| Name| Description| Values|\n| -----| -----|\
  \ -----|\n| number| Card number| string|\n| description| Description| string|\n\
  | holderName| Holder name| string|\n| expiration| Expiration date (05/2022)| string|\n\
  | type| Type| string|\n| subType| Sub type| string|\n| availableBalance| Available\
  \ balance| number|\n| ledgerBalance| Ledger balance| number|\n| creditLimit| Credit\
  \ limit ( applicable to credit cards )| number|\n\n &lt;a name=SandboxCard&gt;&lt;/a&gt;\
  \ \n## SandboxCard \nSandbox card \n\n### Attributes \n\n| Name| Description| Values|\n\
  | -----| -----| -----|\n| info | Entity | &lt;details&gt;&lt;summary&gt;[SandboxCardInfo](#SandboxCardInfo)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;number\
  \ [string]&lt;/li&gt; &lt;li&gt;description [string]&lt;/li&gt; &lt;li&gt;holderName\
  \ [string]&lt;/li&gt; &lt;li&gt;expiration [string]&lt;/li&gt; &lt;li&gt;type [string]&lt;/li&gt;\
  \ &lt;li&gt;subType [string]&lt;/li&gt; &lt;li&gt;availableBalance [number]&lt;/li&gt;\
  \ &lt;li&gt;ledgerBalance [number]&lt;/li&gt; &lt;li&gt;creditLimit [number]&lt;/li&gt;\
  \ &lt;/ul&gt;&lt;/details&gt; | \n| party | Entity | &lt;details&gt;&lt;summary&gt;[SandboxParty](#SandboxParty)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;id\
  \ [string]&lt;/li&gt; &lt;li&gt;name [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt;\
  \ | \n| statements| Card statements| array[[SandboxStatement](#SandboxStatement)]|\n\
  | transactions| Card transactions| array[[SandboxTransaction](#SandboxTransaction)]|\n\
  \n &lt;a name=SandboxUser&gt;&lt;/a&gt; \n## SandboxUser \nUser data \n\n### Attributes\
  \ \n\n| Name| Description| Values|\n| -----| -----| -----|\n| userId| Connected\
  \ user id| string|\n| retryCacheEntries| Retry cache entries| array[[SandboxRetryCacheEntry](#SandboxRetryCacheEntry)]|\n\
  | accounts| List of accounts| array[[SandboxBankAccount](#SandboxBankAccount)]|\n\
  | cards| List of cards| array[[SandboxCard](#SandboxCard)]|\n\n &lt;a name=Sandbox&gt;&lt;/a&gt;\
  \ \n## Sandbox \nSandbox model \n\n### Attributes \n\n| Name| Description| Values|\n\
  | -----| -----| -----|\n| sandboxId| Sandbox id| string|\n| users| List of users|\
  \ array[[SandboxUser](#SandboxUser)]|\n\n &lt;a name=OBExternalScheduleType1Code&gt;&lt;/a&gt;\
  \ \n## OBExternalScheduleType1Code \n### Attributes \n\n| Type| Description| Example|\
  \ Values|\n| -----| -----| -----| -----|\n| enum| -| &lt;ul style=\"padding-left:\
  \ 0\"&gt;&lt;li&gt;Arrival&lt;/li&gt;&lt;li&gt;Execution&lt;/li&gt;&lt;/ul&gt;|\n\
  \n &lt;a name=OBScheduledPayment3&gt;&lt;/a&gt; \n## OBScheduledPayment3 \n\n\n\
  ### Attributes \n\n| Name| Description| Values|\n| -----| -----| -----|\n| AccountId|\
  \ A unique and immutable identifier used to identify the account resource. This\
  \ identifier has no meaning to the account owner.| string|\n| ScheduledPaymentId|\
  \ A unique and immutable identifier used to identify the scheduled payment resource.\
  \ This identifier has no meaning to the account owner.| string|\n| ScheduledPaymentDateTime|\
  \ The date on which the scheduled payment will be made.All dates in the JSON payloads\
  \ are represented in ISO 8601 date-time format. All date-time fields in responses\
  \ must include the timezone.An example is below: 2017-04-05T10:43:07+00:00| string|\n\
  | ScheduledType | Entity | &lt;details&gt;&lt;summary&gt;[OBExternalScheduleType1Code](#OBExternalScheduleType1Code)&lt;/summary&gt;&lt;ul&gt;&lt;/ul&gt;&lt;/details&gt;\
  \ | \n| Reference| Unique reference, as assigned by the creditor, to unambiguously\
  \ refer to the payment transaction. Usage: If available, the initiating party should\
  \ provide this reference in the structured remittance information, to enable reconciliation\
  \ by the creditor upon receipt of the amount of money. If the business context requires\
  \ the use of a creditor reference or a payment remit identification, and only one\
  \ identifier can be passed through the end-to-end chain, the creditor's reference\
  \ or payment remittance identification should be quoted in the end-to-end transaction\
  \ identification.| string|\n| DebtorReference| A reference value provided by the\
  \ PSU to the PISP while setting up the scheduled payment.| string|\n| InstructedAmount\
  \ | Entity | &lt;details&gt;&lt;summary&gt;[OBActiveOrHistoricCurrencyAndAmount](#OBActiveOrHistoricCurrencyAndAmount)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;Amount\
  \ [string]&lt;/li&gt; &lt;li&gt;Currency [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt;\
  \ | \n| CreditorAccount | Entity | &lt;details&gt;&lt;summary&gt;[OBCashAccount5](#OBCashAccount5)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;SchemeName\
  \ [string]&lt;/li&gt; &lt;li&gt;Identification [string]&lt;/li&gt; &lt;li&gt;Name\
  \ [string]&lt;/li&gt; &lt;li&gt;SecondaryIdentification [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt;\
  \ | \n\n &lt;a name=OBReadDataScheduledPayment3&gt;&lt;/a&gt; \n## OBReadDataScheduledPayment3\
  \ \n\n\n### Attributes \n\n| Name| Description| Values|\n| -----| -----| -----|\n\
  | ScheduledPayment| -| array[[OBScheduledPayment3](#OBScheduledPayment3)]|\n\n &lt;a\
  \ name=OBReadScheduledPayment3&gt;&lt;/a&gt; \n## OBReadScheduledPayment3 \n\n\n\
  ### Attributes \n\n| Name| Description| Values|\n| -----| -----| -----|\n| Data\
  \ | Entity | &lt;details&gt;&lt;summary&gt;[OBReadDataScheduledPayment3](#OBReadDataScheduledPayment3)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;ScheduledPayment\
  \ [array[[OBScheduledPayment3](#OBScheduledPayment3)]]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt;\
  \ | \n| Links | Entity | &lt;details&gt;&lt;summary&gt;[Links](#Links)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;Self\
  \ [string]&lt;/li&gt; &lt;li&gt;First [string]&lt;/li&gt; &lt;li&gt;Prev [string]&lt;/li&gt;\
  \ &lt;li&gt;Next [string]&lt;/li&gt; &lt;li&gt;Last [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt;\
  \ | \n| Meta | Entity | &lt;details&gt;&lt;summary&gt;[Meta](#Meta)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;TotalPages\
  \ [integer]&lt;/li&gt; &lt;li&gt;FirstAvailableDateTime [string]&lt;/li&gt; &lt;li&gt;LastAvailableDateTime\
  \ [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt; | \n\n &lt;a name=OBExternalStandingOrderStatus1Code&gt;&lt;/a&gt;\
  \ \n## OBExternalStandingOrderStatus1Code \n### Attributes \n\n| Type| Description|\
  \ Example| Values|\n| -----| -----| -----| -----|\n| enum| -| &lt;ul style=\"padding-left:\
  \ 0\"&gt;&lt;li&gt;Active&lt;/li&gt;&lt;li&gt;Inactive&lt;/li&gt;&lt;/ul&gt;|\n\n\
  \ &lt;a name=OBStandingOrder5&gt;&lt;/a&gt; \n## OBStandingOrder5 \n\n\n### Attributes\
  \ \n\n| Name| Description| Values|\n| -----| -----| -----|\n| AccountId| A unique\
  \ and immutable identifier used to identify the account resource. This identifier\
  \ has no meaning to the account owner.| string|\n| StandingOrderId| A unique and\
  \ immutable identifier used to identify the standing order resource. This identifier\
  \ has no meaning to the account owner.| string|\n| Frequency| Individual Definitions:\
  \ IntrvlMnthDay - An interval specified in months(between 01, 02, 03, 04, 06, 12,\
  \ 24), specifying the day within the month(01 to 31) Full Regular Expression: ^(IntrvlMnthDay:(0[1,2,3,4,6]|12|24):(0[1-9]|[12]\
  \ [0-9]|3[01]))$| string|\n| Reference| Unique reference, as assigned by the creditor,\
  \ to unambiguously refer to the payment transaction. Usage: If available, the initiating\
  \ party should provide this reference in the structured remittance information,\
  \ to enable reconciliation by the creditor upon receipt of the amount of money.\
  \ If the business context requires the use of a creditor reference or a payment\
  \ remit identification, and only one identifier can be passed through the end-to-end\
  \ chain, the creditor's reference or payment remittance identification should be\
  \ quoted in the end-to-end transaction identification.| string|\n| FirstPaymentDateTime|\
  \ The date on which the first payment for a Standing Order schedule will be made.All\
  \ dates in the JSON payloads are represented in ISO 8601 date-time format. All date-time\
  \ fields in responses must include the timezone.An example is below: 2017-04-05T10:43:07+00:00|\
  \ string|\n| NextPaymentDateTime| The date on which the next payment for a Standing\
  \ Order schedule will be made.All dates in the JSON payloads are represented in\
  \ ISO 8601 date-time format. All date-time fields in responses must include the\
  \ timezone.An example is below: 2017-04-05T10:43:07+00:00| string|\n| LastPaymentDateTime|\
  \ The date on which the last (most recent) payment for a Standing Order schedule\
  \ was made.All dates in the JSON payloads are represented in ISO 8601 date-time\
  \ format. All date-time fields in responses must include the timezone.An example\
  \ is below: 2017-04-05T10:43:07+00:00| string|\n| FinalPaymentDateTime| The date\
  \ on which the final payment for a Standing Order schedule will be made.All dates\
  \ in the JSON payloads are represented in ISO 8601 date-time format. All date-time\
  \ fields in responses must include the timezone.An example is below: 2017-04-05T10:43:07+00:00|\
  \ string|\n| StandingOrderStatusCode | Entity | &lt;details&gt;&lt;summary&gt;[OBExternalStandingOrderStatus1Code](#OBExternalStandingOrderStatus1Code)&lt;/summary&gt;&lt;ul&gt;&lt;/ul&gt;&lt;/details&gt;\
  \ | \n| FirstPaymentAmount | Entity | &lt;details&gt;&lt;summary&gt;[OBActiveOrHistoricCurrencyAndAmount](#OBActiveOrHistoricCurrencyAndAmount)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;Amount\
  \ [string]&lt;/li&gt; &lt;li&gt;Currency [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt;\
  \ | \n| NextPaymentAmount | Entity | &lt;details&gt;&lt;summary&gt;[OBActiveOrHistoricCurrencyAndAmount](#OBActiveOrHistoricCurrencyAndAmount)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;Amount\
  \ [string]&lt;/li&gt; &lt;li&gt;Currency [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt;\
  \ | \n| LastPaymentAmount | Entity | &lt;details&gt;&lt;summary&gt;[OBActiveOrHistoricCurrencyAndAmount](#OBActiveOrHistoricCurrencyAndAmount)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;Amount\
  \ [string]&lt;/li&gt; &lt;li&gt;Currency [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt;\
  \ | \n| FinalPaymentAmount | Entity | &lt;details&gt;&lt;summary&gt;[OBActiveOrHistoricCurrencyAndAmount](#OBActiveOrHistoricCurrencyAndAmount)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;Amount\
  \ [string]&lt;/li&gt; &lt;li&gt;Currency [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt;\
  \ | \n| CreditorAccount | Entity | &lt;details&gt;&lt;summary&gt;[OBCashAccount5](#OBCashAccount5)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;SchemeName\
  \ [string]&lt;/li&gt; &lt;li&gt;Identification [string]&lt;/li&gt; &lt;li&gt;Name\
  \ [string]&lt;/li&gt; &lt;li&gt;SecondaryIdentification [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt;\
  \ | \n\n &lt;a name=OBReadDataStandingOrder5&gt;&lt;/a&gt; \n## OBReadDataStandingOrder5\
  \ \n\n\n### Attributes \n\n| Name| Description| Values|\n| -----| -----| -----|\n\
  | StandingOrder| -| array[[OBStandingOrder5](#OBStandingOrder5)]|\n\n &lt;a name=OBReadStandingOrder6&gt;&lt;/a&gt;\
  \ \n## OBReadStandingOrder6 \n\n\n### Attributes \n\n| Name| Description| Values|\n\
  | -----| -----| -----|\n| Data | Entity | &lt;details&gt;&lt;summary&gt;[OBReadDataStandingOrder5](#OBReadDataStandingOrder5)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;StandingOrder\
  \ [array[[OBStandingOrder5](#OBStandingOrder5)]]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt;\
  \ | \n| Links | Entity | &lt;details&gt;&lt;summary&gt;[Links](#Links)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;Self\
  \ [string]&lt;/li&gt; &lt;li&gt;First [string]&lt;/li&gt; &lt;li&gt;Prev [string]&lt;/li&gt;\
  \ &lt;li&gt;Next [string]&lt;/li&gt; &lt;li&gt;Last [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt;\
  \ | \n| Meta | Entity | &lt;details&gt;&lt;summary&gt;[Meta](#Meta)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;TotalPages\
  \ [integer]&lt;/li&gt; &lt;li&gt;FirstAvailableDateTime [string]&lt;/li&gt; &lt;li&gt;LastAvailableDateTime\
  \ [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt; | \n\n &lt;a name=OBExternalStatementType1Code&gt;&lt;/a&gt;\
  \ \n## OBExternalStatementType1Code \n### Attributes \n\n| Type| Description| Example|\
  \ Values|\n| -----| -----| -----| -----|\n| enum| -| &lt;ul style=\"padding-left:\
  \ 0\"&gt;&lt;li&gt;AccountClosure&lt;/li&gt;&lt;li&gt;AccountOpening&lt;/li&gt;&lt;li&gt;Annual&lt;/li&gt;&lt;li&gt;Interim&lt;/li&gt;&lt;li&gt;RegularPeriodic&lt;/li&gt;&lt;/ul&gt;|\n\
  \n &lt;a name=OBStatement2&gt;&lt;/a&gt; \n## OBStatement2 \nProvides further details\
  \ on a statement resource. \n\n### Attributes \n\n| Name| Description| Values|\n\
  | -----| -----| -----|\n| AccountId| A unique and immutable identifier used to identify\
  \ the account resource. This identifier has no meaning to the account owner.| string|\n\
  | StatementId| Unique identifier for the statement resource within an servicing\
  \ institution. This identifier is both unique and immutable.| string|\n| StatementReference|\
  \ Unique reference for the statement. This reference may be optionally populated\
  \ if available.| string|\n| Type | Entity | &lt;details&gt;&lt;summary&gt;[OBExternalStatementType1Code](#OBExternalStatementType1Code)&lt;/summary&gt;&lt;ul&gt;&lt;/ul&gt;&lt;/details&gt;\
  \ | \n| StartDateTime| Date and time at which the statement period starts.All dates\
  \ in the JSON payloads are represented in ISO 8601 date-time format. All date-time\
  \ fields in responses must include the timezone.An example is below: 2017-04-05T10:43:07+00:00|\
  \ string|\n| EndDateTime| Date and time at which the statement period starts.All\
  \ dates in the JSON payloads are represented in ISO 8601 date-time format. All date-time\
  \ fields in responses must include the timezone.An example is below: 2017-04-05T10:43:07+00:00|\
  \ string|\n| CreationDateTime| Date and time at which the statement period starts.All\
  \ dates in the JSON payloads are represented in ISO 8601 date-time format. All date-time\
  \ fields in responses must include the timezone.An example is below: 2017-04-05T10:43:07+00:00|\
  \ string|\n\n &lt;a name=OBReadDataStatement2&gt;&lt;/a&gt; \n## OBReadDataStatement2\
  \ \n\n\n### Attributes \n\n| Name| Description| Values|\n| -----| -----| -----|\n\
  | Statement| Provides further details on a statement resource.| array[[OBStatement2](#OBStatement2)]|\n\
  \n &lt;a name=OBReadStatement2&gt;&lt;/a&gt; \n## OBReadStatement2 \n\n\n### Attributes\
  \ \n\n| Name| Description| Values|\n| -----| -----| -----|\n| Data | Entity | &lt;details&gt;&lt;summary&gt;[OBReadDataStatement2](#OBReadDataStatement2)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;Statement\
  \ [array[[OBStatement2](#OBStatement2)]]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt;\
  \ | \n| Links | Entity | &lt;details&gt;&lt;summary&gt;[Links](#Links)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;Self\
  \ [string]&lt;/li&gt; &lt;li&gt;First [string]&lt;/li&gt; &lt;li&gt;Prev [string]&lt;/li&gt;\
  \ &lt;li&gt;Next [string]&lt;/li&gt; &lt;li&gt;Last [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt;\
  \ | \n| Meta | Entity | &lt;details&gt;&lt;summary&gt;[Meta](#Meta)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;TotalPages\
  \ [integer]&lt;/li&gt; &lt;li&gt;FirstAvailableDateTime [string]&lt;/li&gt; &lt;li&gt;LastAvailableDateTime\
  \ [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt; | \n\n &lt;a name=OBEntryStatus1Code&gt;&lt;/a&gt;\
  \ \n## OBEntryStatus1Code \n### Attributes \n\n| Type| Description| Example| Values|\n\
  | -----| -----| -----| -----|\n| enum| -| &lt;ul style=\"padding-left: 0\"&gt;&lt;li&gt;Booked&lt;/li&gt;&lt;li&gt;Pending&lt;/li&gt;&lt;/ul&gt;|\n\
  \n &lt;a name=ProprietaryBankTransactionCodeStructure1&gt;&lt;/a&gt; \n## ProprietaryBankTransactionCodeStructure1\
  \ \nSet of elements to fully identify a proprietary bank transaction code. \n\n\
  ### Attributes \n\n| Name| Description| Values|\n| -----| -----| -----|\n| Code|\
  \ Proprietary bank transaction code to identify the underlying transaction.| string|\n\
  | Issuer| Identification of the issuer of the proprietary bank transaction code.|\
  \ string|\n\n &lt;a name=OBTransactionCashBalance&gt;&lt;/a&gt; \n## OBTransactionCashBalance\
  \ \nSet of elements used to define the balance as a numerical representation of\
  \ the net increases and decreases in an account after a transaction entry is applied\
  \ to the account. \n\n### Attributes \n\n| Name| Description| Values|\n| -----|\
  \ -----| -----|\n| CreditDebitIndicator | Entity | &lt;details&gt;&lt;summary&gt;[OBCreditDebitCode](#OBCreditDebitCode)&lt;/summary&gt;&lt;ul&gt;&lt;/ul&gt;&lt;/details&gt;\
  \ | \n| Type | Entity | &lt;details&gt;&lt;summary&gt;[OBBalanceType1Code](#OBBalanceType1Code)&lt;/summary&gt;&lt;ul&gt;&lt;/ul&gt;&lt;/details&gt;\
  \ | \n| Amount | Entity | &lt;details&gt;&lt;summary&gt;[OBActiveOrHistoricCurrencyAndAmount](#OBActiveOrHistoricCurrencyAndAmount)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;Amount\
  \ [string]&lt;/li&gt; &lt;li&gt;Currency [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt;\
  \ | \n\n &lt;a name=OBCashAccount6&gt;&lt;/a&gt; \n## OBCashAccount6 \nUnambiguous\
  \ identification of the account of the creditor, in the case of a debit transaction.\
  \ \n\n### Attributes \n\n| Name| Description| Values|\n| -----| -----| -----|\n\
  | SchemeName| Name of the identification scheme, in a coded form as published in\
  \ an external list.| string|\n| Identification| Identification assigned by an institution\
  \ to identify an account. This identification is known by the account owner.| string|\n\
  | Name| The account name is the name or names of the account owner(s) represented\
  \ at an account level, as displayed by the ASPSP's online channels. Note, the account\
  \ name is not the product name or the nickname of the account.| string|\n\n &lt;a\
  \ name=OBTransaction6&gt;&lt;/a&gt; \n## OBTransaction6 \nProvides further details\
  \ on an entry in the report. \n\n### Attributes \n\n| Name| Description| Values|\n\
  | -----| -----| -----|\n| AccountId| A unique and immutable identifier used to identify\
  \ the account resource. This identifier has no meaning to the account owner.| string|\n\
  | TransactionReference| Unique reference for the transaction. This reference is\
  \ optionally populated, and may as an example be the FPID in the Faster Payments\
  \ context.| string|\n| CreditDebitIndicator | Entity | &lt;details&gt;&lt;summary&gt;[OBCreditDebitCode](#OBCreditDebitCode)&lt;/summary&gt;&lt;ul&gt;&lt;/ul&gt;&lt;/details&gt;\
  \ | \n| Status | Entity | &lt;details&gt;&lt;summary&gt;[OBEntryStatus1Code](#OBEntryStatus1Code)&lt;/summary&gt;&lt;ul&gt;&lt;/ul&gt;&lt;/details&gt;\
  \ | \n| BookingDateTime| Date and time when a transaction entry is posted to an\
  \ account on the account servicer's books. Usage: Booking date is the expected booking\
  \ date, unless the status is booked, in which case it is the actual booking date.All\
  \ dates in the JSON payloads are represented in ISO 8601 date-time format. All date-time\
  \ fields in responses must include the timezone.An example is below: 2017-04-05T10:43:07+00:00|\
  \ string|\n| ValueDateTime| Date and time at which assets become available to the\
  \ account owner in case of a credit entry, or cease to be available to the account\
  \ owner in case of a debit transaction entry. Usage: If transaction entry status\
  \ is pending and value date is present, then the value date refers to an expected/requested\
  \ value date. For transaction entries subject to availability/float and for which\
  \ availability information is provided, the value date must not be used.In this\
  \ case the availability component identifies the number of availability days.All\
  \ dates in the JSON payloads are represented in ISO 8601 date-time format. All date-time\
  \ fields in responses must include the timezone.An example is below: 2017-04-05T10:43:07+00:00|\
  \ string|\n| TransactionInformation| Further details of the transaction. This is\
  \ the transaction narrative, which is unstructured text.| string|\n| Amount | Entity\
  \ | &lt;details&gt;&lt;summary&gt;[OBActiveOrHistoricCurrencyAndAmount](#OBActiveOrHistoricCurrencyAndAmount)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;Amount\
  \ [string]&lt;/li&gt; &lt;li&gt;Currency [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt;\
  \ | \n| ProprietaryBankTransactionCode | Entity | &lt;details&gt;&lt;summary&gt;[ProprietaryBankTransactionCodeStructure1](#ProprietaryBankTransactionCodeStructure1)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;Code\
  \ [string]&lt;/li&gt; &lt;li&gt;Issuer [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt;\
  \ | \n| Balance | Entity | &lt;details&gt;&lt;summary&gt;[OBTransactionCashBalance](#OBTransactionCashBalance)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;&lt;details&gt;&lt;summary&gt;CreditDebitIndicator\
  \ [[OBCreditDebitCode](#OBCreditDebitCode)]&lt;/summary&gt;&lt;ul&gt;&lt;/ul&gt;&lt;/details&gt;&lt;/li&gt;&lt;li&gt;&lt;details&gt;&lt;summary&gt;Type\
  \ [[OBBalanceType1Code](#OBBalanceType1Code)]&lt;/summary&gt;&lt;ul&gt;&lt;/ul&gt;&lt;/details&gt;&lt;/li&gt;&lt;li&gt;&lt;details&gt;&lt;summary&gt;Amount\
  \ [[OBActiveOrHistoricCurrencyAndAmount](#OBActiveOrHistoricCurrencyAndAmount)]&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;Amount\
  \ [string]&lt;/li&gt; &lt;li&gt;Currency [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt;&lt;/li&gt;&lt;/ul&gt;&lt;/details&gt;\
  \ | \n| CreditorAccount | Entity | &lt;details&gt;&lt;summary&gt;[OBCashAccount6](#OBCashAccount6)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;SchemeName\
  \ [string]&lt;/li&gt; &lt;li&gt;Identification [string]&lt;/li&gt; &lt;li&gt;Name\
  \ [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt; | \n| DebtorAccount | Entity |\
  \ &lt;details&gt;&lt;summary&gt;[OBCashAccount6](#OBCashAccount6)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;SchemeName\
  \ [string]&lt;/li&gt; &lt;li&gt;Identification [string]&lt;/li&gt; &lt;li&gt;Name\
  \ [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt; | \n\n &lt;a name=OBReadDataTransaction6&gt;&lt;/a&gt;\
  \ \n## OBReadDataTransaction6 \n\n\n### Attributes \n\n| Name| Description| Values|\n\
  | -----| -----| -----|\n| Transaction| Provides further details on an entry in the\
  \ report.| array[[OBTransaction6](#OBTransaction6)]|\n\n &lt;a name=OBReadTransaction6&gt;&lt;/a&gt;\
  \ \n## OBReadTransaction6 \n\n\n### Attributes \n\n| Name| Description| Values|\n\
  | -----| -----| -----|\n| Data | Entity | &lt;details&gt;&lt;summary&gt;[OBReadDataTransaction6](#OBReadDataTransaction6)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;Transaction\
  \ [array[[OBTransaction6](#OBTransaction6)]]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt;\
  \ | \n| Links | Entity | &lt;details&gt;&lt;summary&gt;[Links](#Links)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;Self\
  \ [string]&lt;/li&gt; &lt;li&gt;First [string]&lt;/li&gt; &lt;li&gt;Prev [string]&lt;/li&gt;\
  \ &lt;li&gt;Next [string]&lt;/li&gt; &lt;li&gt;Last [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt;\
  \ | \n| Meta | Entity | &lt;details&gt;&lt;summary&gt;[Meta](#Meta)&lt;/summary&gt;&lt;ul&gt;&lt;li&gt;TotalPages\
  \ [integer]&lt;/li&gt; &lt;li&gt;FirstAvailableDateTime [string]&lt;/li&gt; &lt;li&gt;LastAvailableDateTime\
  \ [string]&lt;/li&gt; &lt;/ul&gt;&lt;/details&gt; | \n\n# Authentication\n\n&lt;!--\
  \ ReDoc-Inject: &lt;security-definitions&gt; --&gt;"
logo: "nbg.gr-logo.svg"
logoMediaType: "image/svg+xml"
tags:
- "financial"
stubs: "nbg.gr-stubs.json"
swagger: "nbg.gr-swagger.json"
---
