---
slug: "lumminary-com"
title: "Lumminary API"
provider: "lumminary.com"
description: "# Introduction\nThe Lumminary API was built to allow third parties to\
  \ interact with Lumminary customers and gain access to their genetic data. The Lumminary\
  \ API is fast, scalable and highly secure. All requests to the Lumminary API take\
  \ place over SSL, which means all communication of Customer data is encrypted.\n\
  \nBefore we dive in, some definitions. This is what we mean by:\n\n|Term|Definition|\n\
  |-----------|-----------|\n|**Third party**|A third party (also referred to as \"\
  partner\" or as \"you\") is a company which offers services and products using genetic\
  \ data.|\n|**Lumminary clients**|The Lumminary client (also referred to as \"customer\"\
  ) is an individual who has created an account on the Lumminary platform.|\n|**Lumminary**|This\
  \ is  us - our services including the Lumminary platform, the API, the DNA App Store,\
  \ the DNA Vault, the \"Connect with Lumminary\" button, and the website in its totality.\
  \ |\n|**CWL**|This is the acronym for the \"Connect with Lumminary\" button.|\n\
  |**dataset**|This is the term we use when we refer to a customer's genetic data.|\n\
  |**Lumminary API**|This is a library/module that you can use to integrate your apps\
  \ with the Lumminary platform.|\n|**Lumminary toolkit**|This is a stand alone application\
  \ which helps you integrate with Lumminary without writing any code or interacting\
  \ with the Lumminary API.|\n\nLet's dive in, now. \n* [**Overview**](#section/Introduction/Overview)\n\
  \n* [**Install Lumminary API Client and Toolkit**](#Install-Lumminary-API-Client-andor-Toolkit)\n\
  * [**Obtaining credentials**](#Obtaining-credentials)\n* [**Query customers authorizations**](#Query-customers-authorizations)\n\
  * [**Query customer genetic data**](#Query-customer-genetic-data)\n* [**Submit reports**](#Submit-reports)\n\
  \n* [**\"Connect with Lumminary\" button**](#the-connect-with-lumminary-button)\n\
  \n* [**API specs**](#tag/Lumminary)\n\n## Overview\n\nIn order to use Lumminary\
  \ services, you'll need to install the Lumminary API Client or Toolkit. The Lumminary\
  \ API Client and Toolkit are available in multiple programming languages, and we\
  \ also provide a sandbox environment which you can use for integration and tests.\n\
  \nThere are a couple of differences between the API Client and the Toolkit. Mainly,\
  \ it's about the ease of use for integration. The Toolkit is basically a stand-alone\
  \ application that facilitates the integration with the Lumminary API without the\
  \ need to modify your already existing code.\n\nYou use the Lumminary API Client\
  \ when you want to integrate it inside your own application. This means it gives\
  \ you full flexibility regarding the integration into your own workflow.\n\nYou\
  \ use the Lumminary Toolkit for an integration where the Toolkit is placed alongside\
  \ your own application. You can use the Toolkit from the CLI - for example, to run\
  \ a cronjob that processes incoming orders. The Toolkit uses the Lumminary API Client.\n\
  \n# Install Lumminary API Client and/or Toolkit\n\nWe provide the Lumminary API\
  \ Client and Toolkit in multiple programming languages - default are PHP (minimum\
  \ version 7.0), Python2.7 and Python3. However, if you need them in another language\
  \ (Java, Obj-C, JavaScript, C#, Perl, CURL), please contact us.\n\n\n## How to install\
  \ the Lumminary API Client\n\n#### PHP example:\nThe PHP Lumminary API Client is\
  \ available at: https://github.com/Lumminary/lumminary-api-client-php\n\nIf you\
  \ are already using [Composer](https://getcomposer.org), you can import the project\
  \ by adding the following to your `composer.json`\n```json\n\"repositories\": [\n\
  \    {\n        \"type\": \"git\",\n        \"url\": \"https://github.com/Lumminary/lumminary-api-client-php.git\"\
  ,\n        \"reference\": \"master\"\n    }\n],\n\"require\": {\n    \"lumminary/api-client-php\"\
  : \"v1.0.6\"\n}\n```\n\nThen run `composer update lumminary/api-client-php`\n\n\
  #### Python example:\n\nThe Python Lumminary API Client is available at: https://github.com/Lumminary/lumminary-api-client-python\n\
  \nTo install directly, run\n\n```bash\npip install git+https://git@github.com/Lumminary/lumminary-api-client-python.git@v1.0.7#egg=lumminary-api-client\n\
  ```\n\nOr add the following line in your requirements.txt\n\n```bash\ngit+https://git@github.com/Lumminary/lumminary-api-client-python.git@v1.0.7#egg=lumminary-api-client\n\
  ```\n\n## How to install the Lumminary Toolkit\n\n#### PHP example:\nThe PHP Lumminary\
  \ Toolkit is available at: https://github.com/Lumminary/lumminary-toolkit-php\n\n\
  To install the Lumminary Toolkit, run the following command where 'lumminary-toolkit-directory'\
  \ is the directory where you want to install the Lumminary Toolkit:\n\n`git clone\
  \ git@github.com:Lumminary/lumminary-toolkit-php.git lumminary-toolkit-directory`\n\
  \n#### PYTHON example:\n\nThe Python Lumminary Toolkit is available at: https://github.com/Lumminary/lumminary-toolkit-python\n\
  \nTo install the Lumminary Toolkit, run the following command where 'lumminary-toolkit-directory'\
  \ is the directory where you want to install the Lumminary Toolkit:\n\n```bash\n\
  git clone git@github.com:Lumminary/lumminary-toolkit-python.git lumminary-toolkit-directory\n\
  cd lumminary-toolkit-directory\nvirtualenv env\nsource env/bin/activate\npip install\
  \ -r requirements.txt\n```\n\nNote that before running the toolkit, you should have\
  \ the virtualenv enabled, like so : `source lumminary-toolkit-directory/env/bin/activate`\n\
  \n## Toolkit Setup\n\nWe recommend to run the Toolkit in a cronjob; at every run\
  \ it will check for new Authorizations (Orders) and will download them; afterwards\
  \ it will check for a new reports folder inside the old authorizations, process\
  \ the reports, and delete the processed Authorizations and Reports from your server.\
  \ \n\nThe first step after you clone the Lumminary Toolkit project for your language\
  \ is to configure it with your credentials. \n\nGo to the Lumminary Toolkit base\
  \ diretory `cd lumminary-toolkit-directory`. Under the Toolkit directory, you will\
  \ find a file `config/config_template.json` which has the following structure:\n\
  \n```json\n{\n    \"api_key\": <your-api-key>,\n    \"product_uuid\": <your-product-uuid>,\n\
  \    \"api_host\": \"https:\\/\\/api.lumminary.com\\/v1\",\n    \"output_root\"\
  : <your-authorization-data-basepath>,\n    \"export_handler\": <your-export-handler-class>,\n\
  \    \"product_name\": <your-product-name>,\n    \"operations\": [\n        \"pull_datasets\"\
  ,\n        \"push_reports\"\n    ],\n    \"optional\": {\n        \"dna_data_filename\"\
  : \"dna-data.tsv\",\n        \"authorization_metadata_filename\": \"authorization-metadata.json\"\
  \n    }\n}\n```\n\nYou should copy this config `cp config/config_template.json config/my-product1-config.json`\
  \ then edit it `vim config/my-product1-config.json` to contain the following values:\n\
  \n| Config attribute | Example Value                      | Description |\n|------------------|------------------------------------|-------------|\n\
  | api_key        | `\"TiiU...bqg==\"`                   |Your Lumminary API key.<br>\
  \ You can obtain it from the Lumminary Admin  |\n| product_uuid   | `\"1234-1234-1234-1234\"\
  `            |Your product UUID. This value can be obtained from the Lumminary Admin\
  \ |\n| api_host       | `\"https:\\/\\/api.lumminary.com\\/v1\"`   |   The API endpoint\
  \ to use.<br>For the sandbox environment you can use \"https:\\/\\/sandbox-api.lumminary.com\\\
  /v1\"    |\n| output_root    | `\"/var/lumminary-orders/product1/\"`         | The\
  \ base directory where the Toolkit places the Authorizations for your Product <br>\
  \ The Lumminary Toolkit will *never* overwrite Authorization data or create this\
  \ directory, to protect from overwrites or typos    |\n| export_handler |`\"export_handler_tsv\"\
  `  | If you have a custom export handler, then your Lumminary contact will provide\
  \ you with the name of your export handler.   |\n| operations       |`[\"pull_datasets\"\
  , \"push_reports\"]`        | These are two optional parameters that define the\
  \ tasks that the Toolkit should perform. Possible values are: <br> 1. `pull_datasets`\
  \ - this tells the Toolkit to download the Customer Authorization (Customer details\
  \ and genetic data) <br> 2. `push_reports` - this tells the Toolkit to push the\
  \ results to the API; see below for more details|\n| optional       | `{}`     \
  \                          | Export handler specific value |\n\nAfter updating the\
  \ config file for your Toolkit, it should look similar to (Note that these are all\
  \ dummy values) :\n\n```json\n{\n    \"api_key\": \"TiiU...bqg==\",\n    \"product_uuid\"\
  : \"1234-1234-1234-1234\",\n    \"api_host\": \"https:\\/\\/api.lumminary.com\\\
  /v1\",\n    \"output_root\": \"\\/var\\/lumminary-orders\\/product1\\/\",\n    \"\
  export_handler\": \"export_handler_tsv\",\n    \"product_name\": \"product 1\",\n\
  \    \"operations\": [\n        \"pull_datasets\",\n        \"push_reports\"\n \
  \   ],\n    \"optional\": {\n        \"dna_data_filename\": \"dna-data.tsv\",\n\
  \        \"authorization_metadata_filename\": \"authorization-metadata.json\"\n\
  \    }\n}\n```\n\nYou can now save and exit the text editor `:wq` and start polling\
  \ the API for new Authorizations :\n\nPython\n\n```bash\n# While still in the <lumminary-toolkit>\
  \ directory\nsource env/bin/activate;\npython lumminary_partner_toolkit.py --config-path\
  \ config/my-lumminary-product1-config.json\n```\n\nPHP\n\n```bash\n# While still\
  \ in the <lumminary-toolkit> directory\nphp lumminary-partner-toolkit.php --config-path\
  \ config/my-lumminary-product1-config.json\n```\n\nWhen your Product receives new\
  \ Authorizations, the Toolkit will pull all the relevant data and save it in the\
  \ following files:\n\n```bash\n# The DNA data file. Format compatible with 23AndMe\
  \ by default\n<output_root>/<authorization_uuid>/dna-data.tsv\n\n# The Authorization\
  \ metadata\n<output_root>/<authorization_uuid>/authorization.json\n```\n\nThe contents\
  \ of the files pulled when processing an Authorization are as follows:\n\n```bash\n\
  $ head -n 5 <output_root>/<authorization_uuid>/dna-data.tsv\n# rsid      chromosome\
  \  position        genotype\nrs12070387  1           6267531         CC\nrs149124387\
  \ 1           12025561        CC\nrs116458387 1           14920119        AA\nrs4436387\
  \   1           15498452        CC\n\n$ cat <output_root>/<authorization_uuid>/authorization.json\
  \ \n{\n    \"authorization\": <authorization_uuid>,\n    \"created_timestamp_utc\"\
  : 1542920184,\n    \"customer\": <customer_uuid>,\n    \"customer_address\": {\n\
  \        \"address1\": <address1>,\n        \"address2\": <address2>,\n        \"\
  city\": <city>,\n        \"country\": <country>,\n        \"state\": <state>,\n\
  \        \"zipcode\": <zipcode> \n    },\n    \"customer_email\": <customer_email>,\n\
  \    \"customer_name\": {\n        \"first_name\": <customer_first_name>,\n    \
  \    \"last_name\": <customer_last_name>\n    },\n    \"dataset\": <dataset_uuid>,\n\
  \    \"product\": <your_product_uuid>\n}\n```\n\nAfter the Toolkit downloaded the\
  \ Authorizations, you need to process the Customer genetic data file and the Customer\
  \ details, individually. The Lumminary API supports multiple types of products:\n\
  \n| Scenario | How to Report |                    \n|------------------|------------------------------------|\n\
  |The product is a file (.pdf, .jpeg etc.) | Put the result file(s) into the `tmp_reports`\
  \ directory. Please refer to the Note underneath this table. |\n|The product requires\
  \ authentication | Create a file with the name `result.json` into the `tmp_reports`\
  \ directory, with the following content: <br> `{ \"credentials\": { \"username\"\
  : \"username@example.com\", \"password\": \"your generated password\", \"url\":\
  \ \"https://your-website.com/report\"}}`<br> The `url` should point to a login page\
  \ that upon authentication redirects the user to the report page. You can find the\
  \ customer's email address in the `authorization-metadata.json` and the `password`\
  \ attribute must be a secure password. Please refer to the Note underneath this\
  \ table. |\n|The product is a physical product| Create a file with the name `result.json`\
  \ into the `tmp_reports` directory, with the following content: <br> `{\"physical_product\"\
  : { \"physical_product_completed\": true }}` <br> This should be done upon dispatch.\
  \ Please refer to the Note underneath this table. |\n|An error occurred| Create\
  \ a file with the name `result.json` into the `tmp_reports` directory, with the\
  \ following content: <br> `{ \"unfulfillable\": {\"error\": \"Reasons for why it\
  \ is unfulfillable\", }}` <br> The error message is for Lumminary internal usage,\
  \ and it won't be visible to the customer. This will delete your Authorization,\
  \ making it unuseable thereafter. So please use this only for unfixable errors,\
  \ and never for temporary errors you attempt to resolve. Please refer to the Note\
  \ underneath this table. |\n\n###### Note\nFor each scenario above, we recommend\
  \ you use a temporary directory to avoid uploading incomplete files or reports.\
  \ So your workflow should be:\n* create a temporary directory inside the `<output_root>/<authorization_uuid>`,\
  \ such as `<output_root>/<authorization_uuid>/tmp_reports/`  \n* place your result\
  \ file(s) in the `tmp_reports` directory (as in the above table)\n* rename the directory\
  \ from `tmp_reports` to `reports`\n\nWe recommend running the Toolkit in a cronjob,\
  \ wrapped by some locking mechanism. Also, Toolkit logs are very minimal but can\
  \ be very helpful when debugging an issue, so please consider saving them to a file.\
  \ For example, the following cronjob runs the Toolkit every minute:\n\n```bash\n\
  # Open the crontab\ncrontab -e\n```\n\nPHP Toolkit\n\n```bash\n# Add the following\
  \ line (replace <lumminary-toolkit-directory> with the absolute path of the Lumminary\
  \ Toolkit)\n* * * * * flock /var/lock/lumminary-toolkit.lock php <lumminary-toolkit-directory>/lumminary-partner-toolkit.php\
  \ --config-path <lumminary-toolkit-directory>/config/my-product1-config.json >>\
  \ /var/log/lumminary-toolkit.log\n```\n\nPython Toolkit\n\n```bash\n# Add the following\
  \ line (replace <lumminary-toolkit-directory> with the absolute path of the Lumminary\
  \ Toolkit)\n* * * * * flock /var/lock/lumminary-toolkit.lock source env/bin/activate;\
  \ python <lumminary-toolkit-directory>/lumminary_partner_toolkit.py --config-path\
  \ <lumminary-toolkit-directory>/config/my-product1-config.json\n```\n\n## API endpoints\n\
  Lumminary provides two endpoint APIs, sandbox and production. You can use the sandbox\
  \ for your integration and testing, simulate orders, upload genetic data, and generate\
  \ reports. The sandbox works exactly like the production environment, and you can\
  \ test your end-to-end integration.\n\nIn order to simulate a complete order, you\
  \ need to use this test credit card: \n\n|Credit card number  | Expiration date|\
  \ CVV2|\n|--------------------|----------------|-----|\n|4242 4242 4242 4242 | \
  \ 12/30         | 123 |\n\n### Sandbox\nwebsite: [sandbox-www.lumminary.com](https://sandbox-www.lumminary.com)\n\
  \napi-hostname: [sandbox-api.lumminary.com/v1](https://sandbox-api.lumminary.com/v1)\n\
  \n### Production\nwebsite: [lumminary.com](https://lummianary.com)\n\napi-hostname:\
  \ [api.lumminary.com/v1](https://api.lumminary.com/v1)\n\n# Obtaining credentials\n\
  To obtain credentials, you need to register as a Lumminary partner. You can do this\
  \ by [filling in this form](https://lumminary.com/register-for-connect-with-lumminary).\n\
  \nYou will then receive the following:\n\n|Credentials|Description|\n|-------|-------|\n\
  |Product UUID|Each product you register on the Lumminary platform gets an UUID which\
  \ will be used to identify that product to the Lumminary API|\n|API key|The secret\
  \ API key associated with the Product UUID|\n|Partner UUID|Upon your first registration\
  \ on the Lumminary platform, you will receive a single Partner UUID, which identifies\
  \ you as one entity, regardless of product. This identifier is used for the Connect\
  \ with Lumminary (CWL) functionality.|\n|CWL Encryption Key|The CWL encryption key\
  \ is associated with the Partner UUID and is used to encrypt all communication for\
  \ the Connect with Lumminary functionality.|\n\nEach product or service needs to\
  \ have its own product UUID and API key, which means you have to fill in the form\
  \ for all products and services that require access to Lumminary customer data.\
  \  \n\n## Configure the credentials to the Lumminary API Client\nThe easiest way\
  \ to set up your credentials is to use an environment file.\n\nFor this, you must\
  \ create a file named `env.json` (but any name will do) in your project directory,\
  \ which should contain:\n```json\n{\n    \"product_uuid\": <your_product_uuid>,\n\
  \    \"api_key\": <your_product_api_key>,\n    \"role\": \"role_product\",\n   \
  \ \"api_host\": <lumminary_api_hostname_endpoint>\n}\n```\n\nIn order to load the\
  \ Credentials from the `env.json`, you can use the following code:\n\n#### PHP example:\n\
  ```php\nrequire_once(__DIR__.\"/vendor/autoload.php\");\n$credentials = new Lumminary\\\
  Client\\Credentials();\n$credentials->loadJSONCredentials(__DIR__.\"/env.json\"\
  );\n```\n\n#### Python example:\n```python\nimport lumminary_sdk as lumminary\n\
  import os\n\ncredentials = lumminary.Credentials()\ncredentials.load_json_credentials(\n\
  \    os.path.join(\n        os.getcwd(),\n        \"env.json\"\n    )\n)\n```\n\n\
  ## Alternative credentials configuration\nYou also have the option of passing the\
  \ credentials as constructor parameters when instantiating the `Credentials` class.\n\
  \n#### PHP example:\n\n```php\nrequire_once(__DIR__.\"/vendor/autoload.php\");\n\
  $credentials = new Lumminary\\Client\\Credentials(\n    <lumminary_api_hostname_endpoint>,\n\
  \    <your_product_uuid>,\n    <your_product_api_key>\n);\n```\n\n#### Python example:\n\
  \n```python\nimport lumminary_sdk as lumminary\n\ncredentials = lumminary.Credentials(\n\
  \    product_uuid = <your_product_uuid>,\n    api_key = <your_product_api_key>,\n\
  \    api_host = <lumminary_api_hostname_endpoint>,\n    role = \"role_product\"\n\
  )\n```\n\n## Create an API instance\n\nWith the credentials configured and loaded,\
  \ you can create an API client like so : \n\n#### PHP example\n\n```php\n$apiClient\
  \ = new Lumminary\\Client\\ApiClient($credentials);\n```\n\n#### Python example\n\
  \n```python\napiClient = lumminary.LumminaryApi(credentials)\n```\n\n# Query customers\
  \ authorizations\nAn Authorization represents permission from a client to access\
  \ their personal and genetic data. \n\nThere are 2 situations where customers grant\
  \ you access to their data: \n* when a customer buys your product from the Lumminary\
  \ DNA App Store\n* when a customer clicks on the \"Connect with Lumminary\" button\
  \ on your website\n\nEach time either of the above situations happens, our platform\
  \ creates an Authorization UUID. You can reliably assume that if you have an Authorization\
  \ UUID, you automatically have access to all the personal information and genetic\
  \ data needed by your products and services. After you process an Authorization\
  \ you need to mark it as processed; processed Authorizations will no longer be on\
  \ the list of new authorizations.\n\nThere are two ways to obtain the Authorization\
  \ UUID:\n* _polling_ - this method allows you to periodically interrogate our API\
  \ and pulls the list of Authorization UUIDs. \n* _webhooks_ (coming soon) - this\
  \ method allows our API to push the Authorization UUIDs into your platform.\n\n\
  ## Poll method\n\nTo use the polling method, your servers periodically interrogate\
  \ for new Authorization UUIDs. Please keep in mind that Authorizations not marked\
  \ as processed will always be returned when polling for new Authorizations. This\
  \ means there's a risk of parallel processing the same Authorization. To avoid this,\
  \ you can, for example, consider using locking when processing.\n\n#### A PHP example\
  \ of using the polling API looks like:\n\n```php\n$productAuthorizations = $apiClient->getAuthorizationsQueue(\n\
  \    $apiClient->getCredentials()->getProductUuid(),\n);\n\nforeach($productAuthorizations\
  \ as $productAuthorization)\n{\n    /**\n     *  Add your code for processing customer\
  \ data here\n     **/ \n    \n    // Mark Authorization as processed \n    $apiClient->postProductAuthorization(\n\
  \        $productAuthorization[\"productUuid\"],\n        $productAuthorization[\"\
  authorizationUuid\"]\n    );\n}\n```\n\n#### A Python example of using the polling\
  \ API looks like:\n\n```python\nproductAuthorizations = apiClient.get_authorizations_queue(\n\
  \    apiClient.get_credentials().product_uuid\n)\n\nfor productAuthorization in\
  \ productAuthorizations:\n    #######\n    #   Add your code for processing customer\
  \ data here\n    #######\n\n    # Mark Authorization as processed\n    apiClient.post_product_authorization(\n\
  \        productAuthorization.product_uuid,\n        productAuthorization.authorization_uuid\n\
  \    )\n```\n\nBased on the Authorization object obtained previously, we can now\
  \ query the customer's information (personal details and genetic data).\n\n####\
  \ PHP example:\n```php\n$authorizationMetadata = $apiClient->authorizationMetadata($productAuthorization[\"\
  authorizationUuid\"]);\n```\n\n#### Python example:\n```python\nauthorizationMetadata\
  \ = apiClient.authorization_metadata(productAuthorization.authorization_uuid)\n\
  ```\n\n#### authorizationMetadata object object structure\n\n| Attribute name  \
  \          | Description                                                       \
  \                         |\n|:-------------------------:|:-------------------------------------------------------------------------------------------|\n\
  | `customer`                | The UUID of the customer granting the Authorization\
  \                                        |\n| `product`                 | The UUID\
  \ of the product that was authorized (your product UUID)                       \
  \     |\n| `authorization`           | The UUID of the granted Authorization.  \
  \                                                   |\n| `created_timestamp_utc`\
  \   | The unix timestamp in UTC time zone when the customer granted the Authorization\
  \            |\n| `dataset`                 | (present only if requested) The UUID\
  \ of the dataset authorized by the customer             |\n| `customer_email`  \
  \        | (present only if requested) Customer contact email                  \
  \                       |\n| `customer_name`           | (present only if requested)\
  \ Customer name                                                  |\n| `customer_address`\
  \        | (present only if requested) Customer address                        \
  \                       |\n\nBy *present only if requested* we mean this attribute\
  \ will be returned if at the time of configuring either the \"Connect with Lumminary\"\
  \ button or your product, you have explicitly requested for that particular set\
  \ of data.\n\n# Query customer genetic data\nBased on the Authorization object obtained\
  \ previously, now we have authorizationMetadata which contains the customer's information\
  \ (personal details and genetic data). Let's use this information to extract some\
  \ customer genetic data.\n\n## Get individual SNPs\nOut of all the available SNPs\
  \ in the dataset, you can only access those for which the customer has previously\
  \ granted permission.\n\nFor example, fetching details for a particular SNP:\n\n\
  #### PHP example:\n```php\n$rsId = \"rs114326054\";\n$snpDetails = null;\n\n// check\
  \ to see if you have access to the customer genetic data\nif (isset($productAuthorization[\"\
  scopes\"][\"dataset\"]))\n{\n    // get SNP information\n    $snpDetails = $apiClient->getClientSnp(\n\
  \        $productAuthorization[\"clientUuid\"],\n        $productAuthorization[\"\
  scopes\"][\"dataset\"],\n        $rsId\n    );\n}\n```\n\n#### Python example:\n\
  ```python\nrsId = \"rs114326054\"\nsnpDetails = None\n\n# check to see if you have\
  \ access to the customer genetic data\nif hasattr(productAuthorization.scopes, \"\
  dataset\"):\n    # get SNP information\n    snpDetails = apiClient.get_client_snp(\n\
  \        productAuthorization.client_uuid,\n        productAuthorization.scopes.dataset,\n\
  \        rsId\n    )\n```\n\n##### The snpDetails object will contain these important\
  \ attributes:\n\n| Attribute name PHP     | Attribute name Python        | Description\
  \                                               |\n|:-------------------------:|:-------------------------:|:----------------------------------------------------------|\n\
  | `snpId`                 | `snp_id`                    | The rsid of the SNP  \
  \                                     |\n| `referenceGenome`        |`reference_genome`\
  \          | The reference genome known to be used by the Dataset's source. <br>\
  \ This impacts the reference allele, location, and based on the dbSNP build, also\
  \ the SNP's accession |\n| `genotypedAlleles`       | `genotyped_alleles`      \
  \  | The genotype value of the customer's queried SNP. <br><br> If the attribute\
  \ of this SNP has the `phased` flag set to True, <br>the first items in the lists\
  \ for all SNPs will be on the same inherited chromosome, <br>and analogous for the\
  \ second item. <br><br> If the SNP is unphased, the order of the items is irrelevant\
  \ |\n|`phased`                   | `phased`                  | A boolean. True if\
  \ the SNP is known to be phased, False otherwise |\n|`chromosomeAccession`     |\
  \ `chromosome_accession`     | This is the chromosome accession number where the\
  \ SNP is located; in the format of NC_00x |\n|`location`                 | `location`\
  \                | This is the customer's SNP's location on the chromosome |\n\n\
  When trying to access any customer's SNP for which you don't have permission, an\
  \ `Unauthorized` exception will be raised.\n\n## Get all authorized SNPs\n\nThe\
  \ function below returns all SNPs your product has access to. These are all the\
  \ SNPs configured as mandatory for your product, as well as all SNPs that are configured\
  \ as optional and available in the customer's data set. We encourage you to use\
  \ this option if you need to get all available SNPs, because it is faster than fetching\
  \ SNP details one by one.\n\nFor example, fetching all authorized SNPs:\n\n####\
  \ PHP example:\n```php\n$datasetSnps = null;\n\n// check to see if you have access\
  \ to the customer genetic data\nif (isset($productAuthorization[\"scopes\"][\"dataset\"\
  ]))\n{\n    // get all authorized SNPs\n    $datasetSnps = $apiClient->getClientSnpGroup(\n\
  \        $productAuthorization[\"clientUuid\"], \n        $productAuthorization[\"\
  scopes\"][\"dataset\"]\n    );\n}\n```\n\n#### Python example:\n```python\ndatasetSnps\
  \ = None\n\n# check to see if you have access to the customer genetic data\nif hasattr(productAuthorization.scopes,\
  \ \"dataset\"):\n    # get all authorized SNPs\n    datasetSnps = apiClient.get_client_snp_group(\n\
  \        productAuthorization.client_uuid,\n        productAuthorization.scopes.dataset\n\
  \    )\n```\n\n##### The datasetSnps variable will be a list of objects each having\
  \ the following attributes:\n\n| Attribute name PHP     | Attribute name Python\
  \        | Description                                               |\n|:-------------------------:|:-------------------------:|:----------------------------------------------------------|\n\
  | `snpId`                  | `snp_id`                   | The rsid of the SNP  \
  \                                     |\n| `referenceGenome`        |`reference_genome`\
  \          | The reference genome known to be used by the Dataset's source. <br>\
  \ This impacts the reference allele, location, and based on the dbSNP build, also\
  \ the SNP's accession |\n| `genotypedAlleles`       | `genotyped_alleles`      \
  \  | The genotype value of the customer's queried SNP. <br><br> If the attribute\
  \ of this SNP has the `phased` flag set to True, <br>the first items in the lists\
  \ for all SNPs will be on the same inherited chromosome, <br>and analogous for the\
  \ second item. <br><br> If the SNP is unphased, the order of the items is irrelevant\
  \ |\n|`phased`                   | `phased`                  | A boolean. True if\
  \ the SNP is known to be phased, False otherwise |\n|`chromosomeAccession`     |\
  \ `chromosome_accession`     | This is the chromosome accession number where the\
  \ SNP is located; in the format of NC_00x |\n|`location`                 | `location`\
  \                | This is the customer's SNP's location on the chromosome |\n\n\
  When trying to access any customer's SNP for which you don't have permission, an\
  \ `Unauthorized` exception will be raised.\n\n## Get Genes\n\nAlong with individual\
  \ SNPs, you can also get all the authorized SNPs from a particular gene, that are\
  \ available in the customer's dataset.\n\nHere, by genes, we refer strictly to the\
  \ genomic region that produces some protein, without considering regulatory or noncoding\
  \ regions that influence gene expression.\n\nThe gene name (known as symbol) can\
  \ be from either of these two databases - NCBI and Ensembl.\n\nFor example, fetching\
  \ details for a gene symbol:\n\n#### PHP example\n```php\n$geneSymbol = \"C1ORF159\"\
  ;\n$geneDetails = null;\n// check to see if you have access to the customer genetic\
  \ data\nif (isset($productAuthorization[\"scopes\"][\"dataset\"]))\n{\n    // get\
  \ all authorized SNPs within a gene\n    $geneDetails = $apiClient->getClientGene(\n\
  \        $productAuthorization[\"clientUuid\"],\n        $productAuthorization[\"\
  scopes\"][\"dataset\"],\n        $geneSymbol\n    );\n}\n```\n\n#### Python example\n\
  ```python\ngeneSymbol = \"C1ORF159\"\ngeneDetails = None\n# check to see if you\
  \ have access to the customer genetic data\nif hasattr(productAuthorization.scopes,\
  \ \"dataset\"):\n    # get all authorized SNPs within a gene\n    geneDetails =\
  \ apiClient.get_client_gene(\n        productAuthorization.client_uuid,\n      \
  \  productAuthorization.scopes.dataset,\n        geneSymbol\n    )\n```\n\n#####\
  \ All the geneDetails object attributes are\n\n| Attribute name PHP | Attribute\
  \ name Python    | Description                                                 \
  \                             |\n|:---------------------:|:---------------------:|:-----------------------------------------------------------------------------------------|\n\
  | `molecularLocation`  | `molecular_location`   | An object containing the location\
  \ of the gene within the chromosome - see below the molecular location object structure\
  \  |\n| `snps`                | `snps`                | A list of SNP objects present\
  \ in the gene - see below the SNP object structure           |\n| `symbol`     \
  \         | `symbol`              | The gene's accession string (name)         \
  \                                              |\n\n##### Molecular location attributes\
  \ \n\n| Attribute name PHP     | Attribute name Python    | Description        \
  \                                                                      |\n|:-------------------------:|:---------------------:|:-----------------------------------------------------------------------------------------|\n\
  | `chromosomeAccession`    | `chromosome_accession` | The scaffold/chromosome on\
  \ which the gene is placed                                      |\n| `start`   \
  \                | `start`               | The gene's start position on the scaffold\
  \                                                |\n| `stop`                   \
  \ | `stop`                | The gene's stop position on the scaffold           \
  \                                      |\n\n##### SNP object structure\n\n| Attribute\
  \ name PHP     | Attribute name Python    | Description                        \
  \                                                      |\n|:-------------------------:|:---------------------:|:-----------------------------------------------------------------------------------------|\n\
  | `referenceGenome`        | `reference_genome`     | The reference genome known\
  \ to be used by the Dataset's source. <br> This impacts the reference allele, location,\
  \ and based on the dbSNP build, also the SNP's accession|\n| `genotypedAlleles`\
  \       | `genotyped_alleles`    | The genotype value of the customer's queried\
  \ SNP. <br><br> If the attribute of this SNP has the `phased` flag set to True,\
  \ <br>the first items in the lists for all SNPs will be on the same inherited chromosome,\
  \ <br>and analogous for the second item. <br><br> If the SNP is unphased, the order\
  \ of the items is irrelevant                                          |\n| `phased`\
  \                  | `phased`              | A boolean. True if the SNP is known\
  \ to be phased, False otherwise                         |\n| `chromosomeAccession`\
  \    | `chromosome_accession` | This is the chromosome accession number where the\
  \ SNP is located; in the format of NC_00x |\n| `location`                | `location`\
  \            | This is the customer's SNP's location on the chromosome         \
  \                          |\n\n## Get customer genetic data in 23andMe tsv format\n\
  \nIf your platform is already compatible with 23andMe genotype data files, you can\
  \ use this specific function to generate data in the 23andMe format - list of rows\
  \ in tab separated values.\n\n#### PHP example:\n```PHP\n$authorizationDnaData =\
  \ $apiClient->authorizationDnaData($productAuthorization[\"authorizationUuid\"]);\n\
  ```\n\n#### Python example\n```python\nauthorizationDnaData = apiClient.authorization_dna_data(productAuthorization.authorization_uuid)\n\
  ```\n\n`authorizationDnaData` contains a list of rows in a tsv (tab delimited values)/csv\
  \ format (23andme-compatible)\n\n# Submit reports\n\nAfter you finish analysing\
  \ the customer's genetic data, we need to inform the customer their analysis is\
  \ complete. To do this, you will notify us using the function below. Finally, the\
  \ customer will then:\n\n* access their report file through a written electronic\
  \ document (eg. .pdf or .doc)\n* access their report on your website under an account\
  \ with a username and a password or\n* receive a physical product\n\n## How to submit\
  \ a report file\n\nWhen you submit such a report file, Lumminary will save this\
  \ document into the customer's account, from which the customer will then be able\
  \ to access it directly.\n\n#### PHP example\n```php\n$pathToReportFile = <path_to_report_file>;\n\
  $fileReport = new \\SplFileObject($pathToReportFile); \n$friendlyFileName = \"report_file_name\"\
  ; //optional, give a friendly name to your report file\n$apiClient->postAuthorizationResultFile(\n\
  \   $productAuthorization[\"productUuid\"],\n   $productAuthorization[\"authorizationUuid\"\
  ],\n   $fileReport,\n   $friendlyFileName\n);\n```\n\n#### Python example\n```python\n\
  pathToReport = <path_to_report_file>\noriginalFilename = \"report_file_name\" #optional,\
  \ give a friendly name to your report file\napiClient.post_authorization_result_file(\n\
  \   productAuthorization.product_uuid,\n   productAuthorization.authorization_uuid,\n\
  \   pathToReport,\n   originalFilename\n)\n```\n\nIf you need to upload multiple\
  \ files, you have to call the function for each file, one at a time. \n\n## How\
  \ to submit a report so the customer can access it on your website\n\nIf the customer's\
  \ results can be accessed on your website, you will need to create a customer account\
  \ on your platform, generating a user and password which will be sent through the\
  \ Lumminary API into the customer's Lumminary account. \n\nIn case you don't generate\
  \ a user and a password for the customer to access their report, use the function\
  \ below with \"null\" value to username and password. We recommend you use the URL\
  \ for customer reports on a dedicated page for reports only, rather than your homepage\
  \ or some other generic page.\n\n#### PHP example:\n```php\n$apiClient->postAuthorizationResultCredentials(\n\
  \   $productAuthorization[\"productUuid\"],\n   $productAuthorization[\"authorizationUuid\"\
  ],\n   <username_generated_by_you>, //optional, default null\n   <password_generated_by_you>,\
  \ //optional, default null\n   <report_on_your_website_url> // https://partnerwebsite.com/reports.php?reportid=a7508\n\
  );\n```\n\n#### Python example:\n```python\napiClient.post_authorization_result_credentials(\n\
  \   productAuthorization.product_uuid,\n   productAuthorization.authorization_uuid,\n\
  \   <username_generated_by_you>, # optional, default null\n   <password_generated_by_you>,\
  \ # optional, default null\n   <report_on_your_website_url> # https://partnerwebsite.com/reports.php?reportid=a7508\n\
  )\n```\n\n## How to submit a physical product\nIn case you only send the customer\
  \ a physical product and you don't generate any reports, you need to run the function\
  \ below so we can mark the order as fulfilled and can inform the client.\n\n####\
  \ PHP example:\n```php\n$apiClient->postProductAuthorization(\n  $productAuthorization[\"\
  productUuid\"],\n  $productAuthorization[\"authorizationUuid\"]\n);\n```\n\n####\
  \ Python example:\n```python\napiClient.post_product_authorization(\n   productAuthorization.product_uuid,\n\
  \   productAuthorization.authorization_uuid\n)\n```\n\n# The Connect with Lumminary\
  \ button\n\nThe \"Connect with Lumminary\" functionality allows you to get customer\
  \ details and genetic data from the Lumminary platform for free, anytime you want,\
  \ for as long the customer grants you access. This functionality offers your customers\
  \ the option to share their genetic data and other personal information (e.g. name,\
  \ address, email etc.) stored on the Lumminary platform. \n\nHaving this button\
  \ on your website makes it very easy for the customer to share their genetic data\
  \ with you, as they don't have to download and re-upload their data on your site.\
  \ The customer always has the option to revoke your access to both their personal\
  \ details and their genetic data.\n\n**`To protect the customer's privacy, you are\
  \ not allowed to save their data anywhere. You can, however, always access their\
  \ data on the Lumminary platform, for as long as they grant you access. If you generate\
  \ a report based on customer data, you are allowed to save that report on your platform.`**\n\
  \nIn order to implement this functionality on your website, this is what you need\
  \ to know:\n* Register your product on the Lumminary platform\n* Add the \"Connect\
  \ with Lumminary\" button to your website\n* Configure your website to retrieve\
  \ customer data\n* Possible errors\n\n## Register your product on the Lumminary\
  \ platform\n\nIf you're new to the Lumminary platform and don't already have any\
  \ products in the DNA App Store, then you need to register by [filling in this form](https://lumminary.com/register-for-connect-with-lumminary).\n\
  \nYou have to fill in the form for all products and services that require access\
  \ to Lumminary customers' genetic data.  \n\n## Add the Connect with Lumminary button\
  \ to your website\n\nSince the CWL flow involves encrypting and decrypting data,\
  \ we recommend installing the Lumminary API Client, where you'll find some specific\
  \ helper functions. \n\nIn order to enable the button, you have to include the following\
  \ script in the `<head>` tag of all the pages where you want to enable the “Connect\
  \ with Lumminary” button:\n\n```html\n<head>\n    <script defer src=\"https://lumminary.com/cwl/cwl.js\"\
  ></script>\n</head>\n```\n\nThe Javascript creates a CSRF token and attaches it\
  \ to the button to be transmitted and verified on our servers each time a user clicks\
  \ on the button. The CSRF token expires after 5 minutes. In case the CSRF token\
  \ is expired or tampered, the user will be redirected to your website where it's\
  \ up to you to decide what to do next - reload the page with the button or show\
  \ the customer an error message.\n\nThe `cwl.js` file is loaded as a deferred resource,\
  \ which means that it will load after all the webpage code execution has been finished,\
  \ so it will not have any impact on your website load speed.\n\n### Chose a button\
  \ colour\n\nThere are two type of buttons, so you can pick one that matches your\
  \ branding. The buttons are SVG images, which means that you can scale them up or\
  \ down to fit your design, without compromising on image quality. You can do this\
  \ by changing the image height.\n\n##### a. White button version\n\n\n<img src=\"\
  https://lumminary.com/cwl/connect-with-lumminary-white.svg\" alt=\"Lumminary DNA\
  \ tests\" height=\"50\" title=\"Connect with Lumminary\"/>\n\n<br>\n\n```html\n\
  <a class=\"lumminary-connect-btn\" data-partner-uuid=\"<partner-UUID>\" data-request=\"\
  <request>\" style=\"cursor:pointer; text-decoration:none;\" href=\"https://lumminary.com\"\
  >\n   <img src=\"https://lumminary.com/cwl/connect-with-lumminary-white.svg\" alt=\"\
  Lumminary DNA tests\" height=\"50\" title=\"Connect with Lumminary\"/>\n</a>\n```\n\
  \n##### b.  Black button version\n\n<img src=\"https://lumminary.com/cwl/connect-with-lumminary-black.svg\"\
  \ alt=\"Lumminary DNA tests\" height=\"50\" title=\"Connect with Lumminary\"/>\n\
  \n<br>\n\n```html\n<a class=\"lumminary-connect-btn\" data-partner-uuid=\"<partner-UUID>\"\
  \ data-request=\"<request>\" style=\"cursor:pointer; text-decoration:none;\" href=\"\
  https://lumminary.com\">\n   <img src=\"https://lumminary.com/cwl/connect-with-lumminary-black.svg\"\
  \ alt=\"Lumminary DNA tests\" height=\"50\" title=\"Connect with Lumminary\"/>\n\
  </a>\n```\n\n## Button configuration\n\nEach button has 2 attributes which need\
  \ to be configured:\n\n1. **data-partner-uuid** where you have to add your partner\
  \ UUID (you have received the partner UUID after filling in the form for product\
  \ registration). \n2. **data-request** which is a string obtained by encrypting\
  \ a serialized JSON (you have received the CWL encryption key after filling in the\
  \ form for product registration). See details below. \n\n#### Data-request object\n\
  \nThe data-request object has a standard format which needs to be preserved. It\
  \ is formed of two types of data, some mandatory and some optional. You can use\
  \ the optional fields to add any metadata or other information for your own use.\
  \ The data-request object is going to be returned with the response from the authentication\
  \ without being altered.\n\n##### Mandatory information\n\nThe mandatory information\
  \ is a list of scopes which you ask the client to grant permission for. These scopes\
  \ are comma delimited, and the possible options are: `address`, `email`, `dataset`.\n\
  \nThe scopes _address_, _email_, and _dataset_ can be used in any combination; you\
  \ must request at least one scope.\n\n| Attribute name    | Description        \
  \                                 |\n|:-----------------:|:----------------------------------------------------|\n\
  | `address`         | Requests access to a customer's name and address.   |\n| `email`\
  \           | Requests access to a customer's email address.      |\n| `dataset`\
  \         | Requests access to a customer's genetic data        |\n\n#### PHP example:\n\
  ```php\n$objAuthorizationRequest [\"scopes\"] = \"address,dataset,email\";\n```\n\
  \n#### Python example:\n```python\nobjAuthorizationRequest [\"scopes\"] = \"address,dataset,email\"\
  \n```\n\nProduct UUID is your `productUuid` for which you ask customer permissions.\n\
  \n#### PHP example:\n```php\n$objAuthorizationRequest[\"productUuid\"] = $credentials->getProductUuid();\n\
  ```\n\n#### Python example:\n```python\nobjAuthorizationRequest[\"productUuid\"\
  ] = credentials.product_uuid\n```\n\n##### Optional information\n\nIn the optional\
  \ part of the object, you can add any useful data, such as customer ID,  session\
  \ ID, or any parameter which can help you identify the response from Lumminary.\n\
  \n#### PHP example:\n```php\n$objAuthorizationRequest[\"customData\"] = array();\n\
  $objAuthorizationRequest[\"customData\"][\"customerId\"] = <partner-customer-id>;\n\
  $objAuthorizationRequest[\"customData\"][\"websiteSession\"] = <customer-session>;\n\
  $objAuthorizationRequest[\"customData\"][\"customData3\"] = <Some addional data>;\n\
  ```\n\n#### Python example:\n```python\nobjAuthorizationRequest[\"customData\"]\
  \ = {}\nobjAuthorizationRequest[\"customData\"][\"customerId\"] = <partner-customer-id>\n\
  objAuthorizationRequest[\"customData\"][\"websiteSession\"] = <customer-session>\n\
  objAuthorizationRequest[\"customData\"][\"customData3\"] = <Some addional data>\n\
  ```\n\nSee below a complete example for a data-request object:\n\n#### PHP example:\n\
  ```php\n$objAuthorizationRequest[\"scopes\"] = \"address,dataset,email\";\n$objAuthorizationRequest[\"\
  productUuid\"] = <product-UUID>;\n\n$objAuthorizationRequest[\"customData\"] = array();\n\
  $objAuthorizationRequest[\"customData\"][\"customerId\"] = <partner-customer-id>;\n\
  $objAuthorizationRequest[\"customData\"][\"websiteSession\"] = <customer-session>;\n\
  $objAuthorizationRequest[\"customData\"][\"customData3\"] = <Some addional data>;\n\
  ```\n\n#### Python example:\n```python\nobjAuthorizationRequest = {}\nobjAuthorizationRequest[\"\
  scopes\"] = \"address,dataset,email\"\nobjAuthorizationRequest[\"productUuid\"]\
  \ = <product-UUID>\n\nobjAuthorizationRequest[\"customData\"] = {}\nobjAuthorizationRequest[\"\
  customData\"][\"customerId\"] = <partner-customer-id>\nobjAuthorizationRequest[\"\
  customData\"][\"websiteSession\"] = <customer-session>\nobjAuthorizationRequest[\"\
  customData\"][\"customData3\"] = <Some addional data>\n```\n\n## Creating the Authorization\
  \ Request\n\nThe previously generated object (`objAuthorizationRequest`) will now\
  \ need to be encrypted. In order to be able to encrypt the object and also query\
  \ the Lumminary API to obtain the customer details and genetic data, you need to\
  \ have the Lumminary API Client installed. If you haven't done this already, please\
  \ follow these [steps](#Install-Lumminary-API-Client-andor-Toolkit).\n\n### Add\
  \ data-request attribute\n\nAfter you have the Lumminary API Client installed correctly\
  \ you can use the command below:\n\n#### PHP example:\n```php\n// You have recieved\
  \ the CWL encryption key after filling in the form for product registration\n$partnerCwlKey\
  \ = <partner-encryption-key>;\n$requestValueEncryptedUrlEncoded = Lumminary\\Client\\\
  LumminaryApi::cwl_data_request_build(\n    $objAuthorizationRequest,\n    $partnerCwlKey\n\
  );\n```\n\n#### Python example:\n```python\nimport lumminary_sdk as lumminary\n\n\
  # You have recieved the CWL encryption key after filling in the form for product\n\
  partnerCwlKey = <partner-encryption-key> \nrequestValueEncryptedUrlEncoded = lumminary.LumminaryApi.cwl_data_request_build(objAuthorizationRequest,\
  \ partnerCwlKey)\n```\n\nThe resulting string should be added in the `data-request`\
  \ attribute of the `<a>` tag of the \"Connect with Lumminary\" button.\n\n### Add\
  \ data-partner-uuid attribute\n\nAdd the `data-partner-uuid` in the `data-partner-uuid`\
  \ attribute of the `<a>` tag of the \"Connect with Lumminary\" button. You have\
  \ received the partner UUID after filling in the form for product registration.\n\
  \nAn example of a button correctly configured should look like this:\n\n```html\n\
  <a class=\"lumminary-connect-btn\" data-partner-uuid=\"4231-7446-2543-6542\" data-request=\"\
  7LfMX811Als0l%2FAvf84pB7n3mcycnTjgWl1FaVNffdqiOApMn4HAnk0Ux6eatObfYmxf1xPRjo7nBojsL4ImgOL932NK2Ei4VoUXjs9Y%2BcvphI0kxBSblLaeVXNPbJO9LsuNP%2BHJzDBAnZZdAObgYxHH2QDY3VD%2Ff%2FBXKw9WYDdBssAoegMFEJ9GgYutFQ4nTPXAt%2FdWCqoxYbZrYpCj2Pphk9lstc4Ib%2BLNxKiEtNCmVGr6sgmR2lPBwgylTsEX%2FMRCJb6sdQyZBhvSQCMFb0p3%2B9tEwV0%3D\"\
  \ style=\"cursor:pointer; text-decoration:none;\" href=\"https://lumminary.com\"\
  >\n   <img src=\"https://lumminary.com/cwl/connect-with-lumminary-white.svg\" alt=\"\
  Lumminary DNA tests\" height=\"50\" title=\"Connect with Lumminary\">\n</a>\n```\n\
  \n## Connect with Lumminary summary of user interaction\n\nWhen a customer clicks\
  \ on the “Connect with Lumminary” button, a pop-up window opens. After they choose\
  \ which genetic file to share, the pop-up will automatically close and the user\
  \ will be redirected to your callback URL in the parent window. Your callback URL\
  \ needs to be predefined in the Lumminary partner portal. \n\nThe GET request from\
  \ the client to your callback URL will contain two querystring parameters - `request`\
  \ and `response`:\n\n1. `request` – this is exactly the same request that you previously\
  \ sent in the `data-request` field. You can decrypt it with the CWL encryption key\
  \ which you used to encrypt it.\n2. `response` – the response is an urlencoded encrypted\
  \ serialized JSON object which contains the Authorization UUID and the Authorization\
  \ UTC unix timestamp. You will use the Authorization UUID to get the customer's\
  \ data with the Lumminary API Client. The response string is encrypted with your\
  \ CWL encryption key, the same as the `data-request` parameter. \n\nIn order to\
  \ decrypt the `response` parameter, you can use the following function:\n\n####\
  \ PHP example:\n```php\n// the entire callback URL, including the querystring parameters\n\
  $callbackUrlWithPayload = \"https://partnerwebsite.con/callback?request=...&response=...\"\
  ;\n\n$cwlReturnObject = Lumminary\\Client\\LumminaryApi::cwl_url_query_extract(\n\
  \    $callbackUrlWithPayload, \n    $partnerCwlKey  \n);\n```\n\n#### Python example:\n\
  ```python\n// the entire callback URL, including the querystring parameters\ncallback_url_with_payload\
  \ = \"https://partnerwebsite.con/callback?request=...&response=...\"\n\ncwlReturnObject\
  \ = apiClient.cwl_url_query_extract(\n    callback_url_with_payload,\n    partner_cwl_key\n\
  )\n```\n\nThe `cwlReturnObject` will now contain an object like the example below:\n\
  \n```json\n{\n    \"request\": <your-request-parameter-echoed>,\n    \"response\"\
  : {\n        \"authorizationUuid\": <cwl-authorization-uuid>,\n        \"authorizationTimestamp\"\
  : <cwl-authorization-created-timestamp>\n    }\n}\n```\n\nWith the Authorization\
  \ UUID (`authorizationUuid`) you can [query all the customer details](#Query-customer-genetic-data)\
  \ from the Lumminary platform.\n\n## Possible errors\n\nWhen an error occurs, the\
  \ customer is redirected to your callback URL. The redirect contains two querystring\
  \ parameters - `request` and `response` - exactly like a regular response, but the\
  \ `response` parameter contains an error object (see below) instead of an Authorization\
  \ object.\n\n#### PHP example:\n```php\n// the entire callback url, including the\
  \ querystring parameters\n$callbackUrlWithPayload = \"https://partnerwebsite.con/callback?request=...&response=...\"\
  ;\n\n$cwlReturnObject = Lumminary\\Client\\LumminaryApi::cwl_url_query_extract(\n\
  \    $callbackUrlWithPayload, \n    $partnerCwlKey  \n);\n```\n\n#### Python example:\n\
  ```python\n# the entire callback url, including the querystring parameters\ncallback_url_with_payload\
  \ = \"https://partnerwebsite.con/callback?request=...&response=...\"\n\ncwlReturnObject\
  \ = apiClient.cwl_url_query_extract(\n    callback_url_with_payload,\n    partner_cwl_key\n\
  )\n```\n\nExample of a return object (`cwlReturnObject`) containing an error message:\n\
  \n```json\n{\n    \"request\": <your-request-parameter-echoed>,\n    \"response\"\
  : {\n        \"error\": {\n            \"id\": <error id>,\n            \"message\"\
  : <error message>\n        }\n    }\n}\n```\n\n| Error Id          | Error Message\
  \                                                                              \
  \  |\n|:-----------------:|:---------------------------------------------------------------------------------------------|\n\
  | 1                 | Invalid Security Token                                   \
  \                                    |\n| 2                 | Invalid Access Scopes\
  \                                                                        |\n| 3\
  \                 | Customer refuses your request (this happens when the customer\
  \ cancels instead of granting access) |"
logo: "lumminary.com-logo.png"
logoMediaType: "image/png"
tags:
- "open_data"
stubs: "lumminary.com-stubs.json"
swagger: "lumminary.com-swagger.json"
---