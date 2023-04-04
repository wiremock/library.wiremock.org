---
slug: "paylocity-com"
title: "Paylocity API"
provider: "paylocity.com"
description: "For general questions and support of the API, contact: webservices@paylocity.com\r\
  \n# Overview\r\n\r\nPaylocity Web Services API is an externally facing RESTful Internet\
  \ protocol. The Paylocity API uses HTTP verbs and a RESTful endpoint structure.\
  \ OAuth 2.0 is used as the API Authorization framework. Request and response payloads\
  \ are formatted as JSON.\r\nPaylocity supports v1 and v2 versions of its API endpoints.\
  \ v1, while supported, won't be enhanced with additional functionality. For direct\
  \ link to v1 documentation, please click [here](https://docs.paylocity.com/weblink/guides/Paylocity_Web_Services_API/v1/Paylocity_Web_Services_API.htm).\
  \ For additional resources regarding v1/v2 differences and conversion path, please\
  \ contact webservices@paylocity.com.\r\n\r\n##### Setup\r\n\r\nPaylocity will provide\
  \ the secure client credentials and set up the scope (type of requests and allowed\
  \ company numbers). You will receive the unique client id, secret, and Paylocity\
  \ public key for the data encryption. The secret will expire in 365 days. \r\n*\
  \ Paylocity will send you an e-mail 10 days prior to the expiration date for the\
  \ current secret. If not renewed, the second e-mail notification will be sent 5\
  \ days prior to secret's expiration. Each email will contain the code necessary\
  \ to renew the client secret. \r\n* You can obtain the new secret by calling API\
  \ endpoint using your current not yet expired credentials and the code that was\
  \ sent with the notification email. For details on API endpoint, please see Client\
  \ Credentials section. \r\n* Both the current secret value and the new secret value\
  \ will be recognized during the transition period. After the current secret expires,\
  \ you must use the new secret. \r\n* If you were unable to renew the secret via\
  \ API endpoint, you can still contact Service and they will email you new secret\
  \ via secure email.\r\n\r\n\r\nWhen validating the request, Paylocity API will honor\
  \ the defaults and required fields set up for the company default New Hire Template\
  \ as defined in Web Pay.\r\n\r\n\r\n# Authorization\r\n\r\nPaylocity Web Services\
  \ API uses OAuth2.0 Authentication with JSON Message Format.\r\n\r\n\r\nAll requests\
  \ of the Paylocity Web Services API require a bearer token which can be obtained\
  \ by authenticating the client with the Paylocity Web Services API via OAuth 2.0.\r\
  \n\r\n\r\nThe client must request a bearer token from the authorization endpoint:\r\
  \n\r\n\r\nauth-server for production: https://api.paylocity.com/IdentityServer/connect/token\r\
  \n\r\n\r\nauth-server for testing: https://apisandbox.paylocity.com/IdentityServer/connect/token\r\
  \n\r\nPaylocity reserves the right to impose rate limits on the number of calls\
  \ made to our APIs. Changes to API features/functionality may be made at anytime\
  \ with or without prior notice.\r\n\r\n##### Authorization Header\r\n\r\nThe request\
  \ is expected to be in the form of a basic authentication request, with the \"Authorization\"\
  \ header containing the client-id and client-secret. This means the standard base-64\
  \ encoded user:password, prefixed with \"Basic\" as the value for the Authorization\
  \ header, where user is the client-id and password is the client-secret.\r\n\r\n\
  ##### Content-Type Header\r\n\r\nThe \"Content-Type\" header is required to be \"\
  application/x-www-form-urlencoded\".\r\n\r\n##### Additional Values\r\n\r\nThe request\
  \ must post the following form encoded values within the request body:\r\n\r\n \
  \   grant_type = client_credentials\r\n    scope = WebLinkAPI\r\n\r\n##### Responses\r\
  \n\r\nSuccess will return HTTP 200 OK with JSON content:\r\n\r\n    {\r\n      \"\
  access_token\": \"xxx\",\r\n      \"expires_in\": 3600,\r\n      \"token_type\"\
  : \"Bearer\"\r\n    }\r\n\r\n# Encryption\r\n\r\nPaylocity uses a combination of\
  \ RSA and AES cryptography. As part of the setup, each client is issued a public\
  \ RSA key.\r\n\r\nPaylocity recommends the encryption of the incoming requests as\
  \ additional protection of the sensitive data. Clients can opt-out of the encryption\
  \ during the initial setup process. Opt-out will allow Paylocity to process unencrypted\
  \ requests.\r\n\r\nThe Paylocity Public Key has the following properties:\r\n\r\n\
  * 2048 bit key size\r\n\r\n* PKCS1 key format\r\n\r\n* PEM encoding\r\n\r\n#####\
  \ Properties\r\n\r\n* key (base 64 encoded): The AES symmetric key encrypted with\
  \ the Paylocity Public Key. It is the key used to encrypt the content. Paylocity\
  \ will decrypt the AES key using RSA decryption and use it to decrypt the content.\r\
  \n\r\n* iv (base 64 encoded): The AES IV (Initialization Vector) used when encrypting\
  \ the content.\r\n\r\n* content (base 64 encoded): The AES encrypted request. The\
  \ key and iv provided in the secureContent request are used by Paylocity for decryption\
  \ of the content.\r\n\r\nWe suggest using the following for the AES:\r\n\r\n* CBC\
  \ cipher mode\r\n\r\n* PKCS7 padding\r\n\r\n* 128 bit block size\r\n\r\n* 256 bit\
  \ key size\r\n\r\n##### Encryption Flow\r\n\r\n* Generate the unencrypted JSON payload\
  \ to POST/PUT\r\n* Encrypt this JSON payload using your _own key and IV_ (NOT with\
  \ the Paylocity public key)\r\n* RSA encrypt the _key_ you used in step 2 with the\
  \ Paylocity Public Key, then, base64 encode the result\r\n* Base64 encode the IV\
  \ used to encrypt the JSON payload in step 2\r\n* Put together a \"securecontent\"\
  \ JSON object:\r\n \r\n{\r\n  'secureContent' : {\r\n    'key' : -- RSA-encrypted\
  \ & base64 encoded key from step 3,\r\n    'iv' : -- base64 encoded iv from step\
  \ 4\r\n    'content' -- content encrypted with your own key from step 2, base64\
  \ encoded\r\n  }\r\n}\r\n\r\n##### Sample Example\r\n\r\n    {\r\n      \"secureContent\"\
  : {\r\n        \"key\": \"eS3aw6H/qzHMJ00gSi6gQ3xa08DPMazk8BFY96Pd99ODA==\",\r\n\
  \        \"iv\": \"NLyXMGq9svw0XO5aI9BzWw==\",\r\n        \"content\": \"gAEOiQltO1w+LzGUoIK8FiYbU42hug94EasSl7N+Q1w=\"\
  \r\n      }\r\n    }\r\n\r\n##### Sample C# Code\r\n\r\n    using Newtonsoft.Json;\r\
  \n    using System;\r\n    using System.IO;\r\n    using System.Security.Cryptography;\r\
  \n    using System.Text;\r\n\r\n    public class SecuredContent\r\n    {\r\n   \
  \   [JsonProperty(\"key\")]\r\n      public string Key { get; set; }\r\n\r\n   \
  \   [JsonProperty(\"iv\")]\r\n      public string Iv { get; set; }\r\n\r\n     \
  \ [JsonProperty(\"content\")]\r\n      public string Content { get; set; }\r\n\r\
  \n    }\r\n\r\n    public class EndUserSecureRequestExample\r\n    {\r\n      public\
  \ string CreateSecuredRequest(FileInfo paylocityPublicKey, string unsecuredJsonRequest)\r\
  \n      {\r\n        string publicKeyXml = File.ReadAllText(paylocityPublicKey.FullName,\
  \ Encoding.UTF8);\r\n\r\n        SecuredContent secureContent = this.CreateSecuredContent(publicKeyXml,\
  \ unsecuredJsonRequest);\r\n\r\n        string secureRequest = JsonConvert.SerializeObject(new\
  \ { secureContent });\r\n\r\n        return secureRequest;\r\n      }\r\n\r\n  \
  \    private SecuredContent CreateSecuredContent(string publicKeyXml, string request)\r\
  \n      {\r\n        using (AesCryptoServiceProvider aesCsp = new AesCryptoServiceProvider())\r\
  \n        {\r\n          aesCsp.Mode = CipherMode.CBC;\r\n          aesCsp.Padding\
  \ = PaddingMode.PKCS7;\r\n          aesCsp.BlockSize = 128;\r\n          aesCsp.KeySize\
  \ = 256;\r\n\r\n          using (ICryptoTransform crt = aesCsp.CreateEncryptor(aesCsp.Key,\
  \ aesCsp.IV))\r\n          {\r\n            using (MemoryStream outputStream = new\
  \ MemoryStream())\r\n            {\r\n              using (CryptoStream encryptStream\
  \ = new CryptoStream(outputStream, crt, CryptoStreamMode.Write))\r\n           \
  \   {\r\n                byte[] encodedRequest = Encoding.UTF8.GetBytes(request);\r\
  \n                encryptStream.Write(encodedRequest, 0, encodedRequest.Length);\r\
  \n                encryptStream.FlushFinalBlock();\r\n                byte[] encryptedRequest\
  \ = outputStream.ToArray();\r\n\r\n                using (RSACryptoServiceProvider\
  \ crp = new RSACryptoServiceProvider())\r\n                {\r\n               \
  \   crp.FromXmlstring(publicKeyXml);\r\n                  byte[] encryptedKey =\
  \ crp.Encrypt(aesCsp.Key, false);\r\n\r\n                  return new SecuredContent()\r\
  \n                  {\r\n                    Key = Convert.ToBase64string(encryptedKey),\r\
  \n                    Iv = Convert.ToBase64string(aesCsp.IV),\r\n              \
  \      Content = Convert.ToBase64string(encryptedRequest)\r\n                  };\r\
  \n                }\r\n              }\r\n            }\r\n          }\r\n     \
  \   }\r\n      }\r\n    }\r\n\r\n## Support\r\n\r\nQuestions about using the Paylocity\
  \ API? Please contact webservices@paylocity.com.\r\n\r\n# Deductions (v1)\r\n\r\n\
  Deductions API provides endpoints to retrieve, add, update and delete deductions\
  \ for a company's employees. For schema details, click <a href=\"https://docs.paylocity.com/weblink/guides/Paylocity_Web_Services_API/v1/Paylocity_Web_Services_API.htm\"\
  \ target=\"_blank\">here</a>.\r\n\r\n# OnBoarding (v1)\r\n\r\nOnboarding API sends\
  \ employee data into Paylocity Onboarding to help ensure an easy and accurate hiring\
  \ process for subsequent completion into Web Pay. For schema details, click <a href=\"\
  https://docs.paylocity.com/weblink/guides/Paylocity_Web_Services_API/v1/Paylocity_Web_Services_API.htm\"\
  \ target=\"_blank\">here</a>."
logo: "paylocity.com-logo.jpeg"
logoMediaType: "image/jpeg"
tags:
- "financial"
stubs: "paylocity.com-stubs.json"
swagger: "paylocity.com-swagger.json"
---
