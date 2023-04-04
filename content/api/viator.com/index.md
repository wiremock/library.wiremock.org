---
slug: "viator-com"
title: "Viator API Documentation &amp; Specification – Merchant Partners"
provider: "viator.com"
description: "&lt;style type='text/css'&gt;\ncode { white-space: nowrap; }\na { font-weight:\
  \ bold; }\n\nfigure {\n  width: 100%;\n  text-align: center;\n  font-style: italic;\n\
  \  font-size: smaller;\n  text-indent: 0;\n  border: thin silver solid;\n  margin:\
  \ 0.5em;\n  padding: 0.5em;\n}\n\n&lt;/style&gt;\n\n## Updates\n\n### Latest update:\
  \ \n\n| Date | Description |\n|------|-------------|\n| 3 Feb 2021 | Added [Special\
  \ offers and on-sale pricing](#section/Key-concepts/Special-offers-and-on-sale-pricing)\
  \ section |\n| 28 Oct 2020 | Updated FAQ section re booking questions, traveler\
  \ names, and pricing |\n| 16 Sep 2020 | Modified FAQ section re booking currencies,\
  \ supplier name display and requesting additional reviews |\n| 20 July 2020 | Added\
  \ [Booking references](#section/Key-concepts/Booking-references) section |\n\n**Previous\
  \ updates**: See [Update log](#section/Appendices/Update-log)\n\n# Overview\n\n\
  The Viator Partner API comprises a set of endpoints that can support the operation\
  \ of a fully-featured tours and experiences booking website or application; or,\
  \ it can be integrated with your existing travel-booking software.\n\nThe API exposes\
  \ a variety of services that allow the retrieval of all product details, such as\
  \ descriptions, pricing, terms and conditions, photos and reviews. This data can\
  \ either be ingested periodically and managed on your local system, or calls can\
  \ be made in real time to retrieve content in response to your users' activity on\
  \ your systems.\n\nThe API allows product availability schedules to be retrieved\
  \ in bulk or queried in real-time, and it can perform pricing calculations according\
  \ to the number and type of traveler for the wide variety of product option combinations\
  \ typically available in the tours and activities sales workflow.\n\nThe API provides\
  \ booking and post-booking functionality, allowing booking requests, ticket purchase,\
  \ and booking status updates.\n\nVarious utility services are available to map between\
  \ yours and Viator's data taxonomy.\n\n**Please note:** The API does not provide\
  \ services for storing data, such as user accounts. We assume that merchant partners\
  \ have their own systems for storing this data.\n\n## Who is the API for?\n\nThe\
  \ Viator Partner API is designed for use by organizations and individuals partnered\
  \ with Viator in one of the following capacities:\n\n### Merchant partners\n\nA\
  \ merchant partner is one who operates as the merchant of record; i.e., takes full\
  \ responsibility for all monetary transactions carried out by their users, as well\
  \ as providing customer support with regard to providing help, processing cancellations\
  \ and refunds, and liaising between suppliers and customers when the need to communicate\
  \ information arises.\n\nMerchant partners are invoiced periodically by Viator for\
  \ all product sales. You will need to demonstrate that you have access to the appropriate\
  \ infrastructure to effectively support the requisite business operations in order\
  \ to become a merchant partner.\n\n### Viator Branded Affiliates (VBAs)\n\nVBAs\
  \ have full access to the areas of the API relating to content, but sales of Viator\
  \ products must be carried out on the Viator site itself; therefore, access to the\
  \ booking or transactional endpoints necessary to operate as the merchant of record\
  \ (i.e., merchant partners) is restricted. \n\nWhen a customer wishes to book a\
  \ product from a VBA partner's site, they are instead redirected to [viator.com](https://viator.com)\
  \ in order to complete the purchase; whereas, merchant partners are able to process\
  \ and manage bookings through the Viator API itself, allowing their customers to\
  \ book products without leaving the partner's site.\n\nViator affiliates instead\
  \ generate unique URLs that redirect their users to the Viator site, resulting in\
  \ a cookie being set such that all transactions will accrue a commission for that\
  \ partner until the cookie expires.\n\nPurchases of products originating from the\
  \ VBAs site are recorded and a commission on these sales is paid periodically.\n\
  \n- **Note**: VBA partners should refer to a different document for technical specifications\
  \ relevant to their partner type. If you are a VBA partner, please navigate to:\
  \ [https://docs.viator.com/partner-api/affiliate/technical/](https://docs.viator.com/partner-api/affiliate/technical)\n\
  \n### VBAs with booking capability\n\nVBAs also have the option of allowing their\
  \ customers to process bookings directly from their site and via the API – similar\
  \ to a merchant partner – without being redirected to viator.com to complete their\
  \ transaction. This partner type sends customer details, product details and credit\
  \ card payment information via the API, but Viator retains control of and responsibility\
  \ for processing payments and customer support.\n\n### White label partners\n\n\
  White label partners do not operate their own site infrastructure. Instead, Viator\
  \ provides a white label site with full functionality that can be branded according\
  \ to the partner’s wishes.\n\n## Uses of the Viator Partner API\n\nThe Viator Partner\
  \ API is used to carry out the following tasks:\n\n### Product search and ingestion\n\
  \nPartners can use the product search endpoints to retrieve lists of products from\
  \ Viator’s inventory relevant to their business. The available search criteria include:\n\
  \n- The location (destination) in which the product operates\n- Whether the product\
  \ is associated with a well-known tourist attraction; e.g., Empire State Building\n\
  - The type of product (known as its category and/or subcategory)\n- The time period\
  \ during which the product operates \n- Words or phrases that occur in a product's\
  \ description via a free-text search\n\nPartners who prefer to download product\
  \ details periodically (instead of performing all operations in real time in response\
  \ to user behavior) do so by using the product search endpoints to compile a list\
  \ of products that they wish to sell on their site. They then download comprehensive\
  \ product details for each via the /product endpoint.\n\n#### Product search endpoints:\n\
  \n| Endpoint | Use |\n|-|-|\n| [/search/products](#operation/searchProducts) | Allows\
  \ searching for products according to: destination / location, relationship to a\
  \ known tourist attraction; category and/or subcategory; date of operation |\n|\
  \ [/search/products/codes](#operation/searchProductsCodes) | Retrieves product details\
  \ for products that match a list of product codes (unique identifiers for the product)\
  \ |\n| [/search/freetext](#operation/searchFreetext) | Retrieves product details\
  \ for products that include the search terms in the product's description and details.\
  \ |\n| [/available/products](#operation/availableProducts) | Retrieves products\
  \ that are identified by specific product codes, operate during a specified day\
  \ range and accept a certain number of adult travelers |\n\n#### Product information\
  \ endpoints:\n\nAll information about a product that must be communicated to customers\
  \ prior to purchase is available via [/product](#operation/product) and its auxiliary\
  \ endpoints. This content is generally used to construct product display pages and\
  \ for performing local searches.\n\nImportant information about a product includes:\n\
  \n- Product and supplier names\n- Geographic location\n- Product description\n-\
  \ Category and subcategory\n- Photos (from both users and the supplier)\n- User\
  \ reviews and ratings\n- Product options (variants of the tour/activity, such as\
  \ starting times, passenger mix options, and inclusions/add-ons, including basic\
  \ pricing information for each)\n- Which age ranges can participate\n- Booking details\n\
  - Cancellation policies\n- Basic pricing\n- Logistics\n  + Inclusions (e.g., provided\
  \ meals)\n  + Exclusions (e.g., entrance fees to visited attractions)\n  + Health\
  \ restrictions and accessibility\n  + Departure times\n  + Passenger pick-up\n \
  \ + Duration\n  + Tour routes\n\n### Availability\n\nThe availability of a tour\
  \ is communicated via the API's availability endpoints. The availability aspects\
  \ of a product include:\n\n- On which days and at which times the product is available\
  \ to be booked\n- Whether the product option (variant) supports a certain combination\
  \ of passengers according to age and number\n- Pricing information\n\nSome partners\
  \ choose to bulk-ingest availability information for their products in order to\
  \ expedite this part of the customer workflow or to facilitate a local search functionality\
  \ on their website; but, because this information changes very regularly, a final\
  \ real-time call is generally recommended to ensure that when the booking request\
  \ is submitted by the customer it is unlikely to fail on account of a change in\
  \ availability.\n\n#### Availability endpoints\n\n| Endpoint | Use |\n|-|-|\n| [/booking/availability](#operation/bookingAvailability)\
  \ | Returns the product option with the lowest price that is available on each day\
  \ |\n| [/booking/availability/dates](#operation/bookingAvailabilityDates) | Returns\
  \ all available dates for a product (but without regard to product option) |\n|\
  \ [/booking/availability/tourgrades](#operation/bookingAvailabilityTourgrades) |\
  \ Returns all product options for a product that are available on the specified\
  \ day for the specified passenger mix |\n| [/booking/availability/tourgrades/pricingmatrix](#operation/bookingAvailabilityTourgradesPricingmatrix)\
  \ | Returns a detailed matrix of product options, passenger mixes and the pricing\
  \ applicable to each combination |\n| [/booking/calculateprice](#operation/bookingCalculateprice)\
  \ | Provides a reconfirmation of a product's availability with respect to the product\
  \ option and passenger mix provided and calculates a final price; used as a final\
  \ availability check immediately prior to making a booking |\n\n### Booking and\
  \ cancellations\n\nMerchant partners and VBAs with booking capabilities can use\
  \ the Viator Partner API to purchase the product through the [/booking/book](#operation/bookingBook)\
  \ endpoint.\n\nThe API also provides services to:\n\n- Enquire about the status\
  \ of an existing booking\n- Retrieve tickets/vouchers for the product\n- Cancel\
  \ a booking\n\n#### Booking endpoints\n\n| Endpoint | Use |\n|-|-|\n| [/booking/book](#operation/bookingBook)\
  \ | Make a booking / purchase a product |\n| [/booking/status](#operation/bookingStatus)\
  \ | Retrieve multiple detailed booking statuses based on a range of specified criteria\
  \ |\n| [/booking/status/items](#operation/bookingStatusItems) | Similar to [/booking/status](#operation/bookingStatus),\
  \ but provides slightly less detail and can be called more frequently |\n\n####\
  \ Cancellation endpoints\n\n| Endpoint | Use |\n|-|-|\n| [/bookings/{booking-reference}/cancel-quote](#operation/bookingQuote)\
  \ | Returns the expected outcome of a booking cancellation request (taking into\
  \ consideration the product's cancellation policy) were the cancellation request\
  \ performed immediately |\n| [/bookings/{booking-reference}/cancel](#operation/cancelBooking)\
  \ | Cancels the booking and assigns a refund depending on the product’s cancellation\
  \ policy |\n\n### Auxiliary services\n\nTaxonomical data sets are required to interact\
  \ meaningfully with the Viator Partner API; for example, mappings from destination\
  \ (location of operation) to their respective identification codes. This information\
  \ may occasionally change or be added to. Consequently, the API includes endpoints\
  \ that return the most up-to-date versions of this information.\n\n#### Taxonomy\
  \ endpoints\n\n| Endpoint | Use |\n|-|-|\n| [/taxonomy/destinations](#operation/taxonomyDestinations)\
  \ | Retrieves a list of destination names, types and unique identifiers to be used\
  \ when interacting with the Viator Partner API |\n| [/taxonomy/categories](#operation/taxonomyCategories)\
  \ | Retrieves a list of product categories for a destination that can be used as\
  \ a means of filtering when searching for products using the [/search/products](#operation/searchProducts)\
  \ endpoint |\n| [/taxonomy/attractions](#operation/taxonomyAttractions) | Retrieves\
  \ a list of tourist attractions (e.g., the Eiffel Tower or Empire State Building)\
  \ and their associated identification codes to be used as a means of searching for\
  \ available products; for example, in the [/search/products](#operation/searchProducts)\
  \ service |\n| [/booking/hotels](#operation/bookingHotels) | Retrieves a list of\
  \ hotels, including names and geographic locations, to be used when making booking\
  \ requests |\n\n---\n\n# Authentication\n\n**Note**:\n\n- The authentication mechanism\
  \ for this API has been updated recently. Now, partners can also authenticate using\
  \ a [new style of API key](#section/Authentication/exp-api-key) that is included\
  \ in each call as a &lt;u&gt;header parameter&lt;/u&gt;. Previously, authentication\
  \ was accomplished by including an API key as a query parameter.\n\n- Partners who\
  \ are currently authenticating via the [API key query parameter](#section/Authentication/Legacy-API-keys)\
  \ can continue to authenticate in this way; however, access to the new booking cancellation\
  \ endpoints ([/bookings/cancel-reasons](#operation/cancellationReasons), [/bookings/cancel-quote](#operation/cancelBookingQuote)\
  \ and [/bookings/cancel](#operation/cancelBooking)) does require the new-style of\
  \ API key. All other endpoints remain compatible with both authentication methods.\n\
  \n- If you would like to switch to the [new style of key](#section/Authentication/exp-api-key),\
  \ please speak to your business development account manager.\n\n## API key\n\nAccess\
  \ to the API is managed using an **API key** that is included as a **header parameter**\
  \ to every call made to all API endpoints described in this document.\n\n| Header\
  \ parameter name | Example value |\n|-----------------------|---------------|\n\
  | exp-api-key | bcac8986-4c33-4fa0-ad3f-75409487026c |\n\nIf you do not know the\
  \ API key for your organization, please contact your business development account\
  \ manager for these details.\n\nPlease note that language localization is now controlled\
  \ on a per-call basis. Previously, language localization was controlled via API-key\
  \ configuration, with one language available per API key. Under the present scheme,\
  \ you can access any language enabled for your organization's point of sale via\
  \ a **single API key**. \n\nLanguage selection is accomplished by specifying the\
  \ desired language as a header parameter (`Accept-Language`). See [Accept-Language\
  \ header](#section/Appendices/Accept-Language-header) for available language codes.\
  \ If you would like access to additional languages, please contact your business\
  \ development account manager.\n\n## Legacy API key\n\nPreviously, authenticating\
  \ to this API was accomplished by passing an API-key **as a query parameter** appended\
  \ to the URI for each call; e.g.:\n\n```html\nGET https://viatorapi.sandbox.viator.com/service/taxonomy/destinations?apiKey=xxxxxxxxxxxxxxxxxx\n\
  ```\n\nThis method of authentication remains available for backwards-compatibility\
  \ with existing implementations. If you would like to upgrade to the new style of\
  \ API key, please contact your business development account manager. \n\n# Key concepts\n\
  \n## Content ingestion and caching strategy\n\nMuch of the information you will\
  \ need to retrieve from the Viator API – such as the taxonomy, product lists and\
  \ product details – do not change frequently.\n\nTherefore, we recommend implementing\
  \ a caching strategy in order to eliminate unnecessary traffic to Viator’s servers\
  \ and improve the operation of your site. \n\nThis section discusses the different\
  \ strategies for retrieving and caching Viator’s product catalogue.\n\nYou will\
  \ need to decide on how you will retrieve and manage content from Viator’s product\
  \ catalogue. The two main options are as follows:\n\n### 1. API response caching\n\
  \n*Partners retrieve content as-needed and cache responses on a service-by-service\
  \ basis*\n\nIf you do not need to store product details locally, we recommend performing\
  \ caching of on a service-by-service basis; i.e., storing the entire response and\
  \ applying a time-to-live (TTL) of less than 24 hours.\n\n#### Benefits of API response\
  \ caching\n\n* All the benefits of caching with minimal overhead\n* Minimal risk\
  \ of serving stale or invalid data cached on the partner's side\n* No need to download\
  \ data about products that are not selling\n* A smaller volume of local data improves\
  \ cache hit performance\n* Fewer requests made of Viator's systems\n* Avoids rate\
  \ limitations\n* Closer adherence to best practices\n* Removes need to manage a\
  \ complex data structure locally\n\n#### Service endpoints to cache\n\nCaching should\
  \ only be applied to services that yield infrequently changing data; i.e.:\n\n*\
  \ [/taxonomy/destinations](](#operation/taxonomyDestinations)\n* [/taxonomy/categories](#operation/taxonomyCategories)\n\
  * [/taxonomy/attractions](#operation/taxonomyAttractions)\n* [/search/products](#operation/searchProducts)\n\
  * [/search/products/codes](#operation/searchProductsCodes)\n* [/search/freetext](#operation/searchFreetext)\n\
  * [/product](#operation/product)\n* [/product/reviews](#operation/productReviews)\n\
  * [/product/photos](#operation/productPhotos)\n* [/available/products](#operation/availableProducts)\n\
  \n**Note**: these services should be considered cacheable even though some are POST\
  \ and none include a Cache-Control HTTP header in their response.\n\n### 2. Periodic\
  \ content ingestion\n\n*Partners download either the full product catalogue or a\
  \ subset of the catalogue at regular intervals based on destination, linked attraction,\
  \ or product category filters.*\n\n#### Who should use periodic ingestion\nThis\
  \ approach may be preferable for partners whose requirements include:\n* **System\
  \ agnosticism/data centralization** – i.e., partners who are simultaneously selling\
  \ products from vendors other than Viator, have existing product databases or are\
  \ likely to want to maintain a central product catalogue with a unified taxonomy\
  \ / data structure\n* **Enhanced search capability** – i.e., the ability to apply\
  \ different categorization rules, filters, exclusions or search optimizations to\
  \ the product catalogue; e.g., grouping or filtering products according to criteria\
  \ other than those supported directly by the Viator API (destination, attraction-link\
  \ or category)\n\n#### Frequency of content ingestion\nWe recommend that you perform\
  \ an ingestion of the product catalogue once every 24 hours.\n\n#### How to retrieve\
  \ product codes\n\nMake a call to one of the product search services:\n\n* [/search/products](#operation/searchProducts)\
  \ – to search by `destId` (destination), `catId` (category), `subCatId` (subcategory)\
  \ or `seoId` (attraction)\n* [/search/freetext](#operation/searchFreetext) – free-text\
  \ search across all identifying fields \n\n#### How to retrieve all products in\
  \ the catalogue\n\nTo retrieve all products from the Viator catalogue:\n\n* Retrieve\
  \ all available destination identifiers (`destId`) from the [/taxonomy/destinations](#operation/taxonomyDestinations)\
  \ service\n* Iterate through the complete list of `destId`s you retrieved in the\
  \ previous step, and call [/search/products](#operation/searchProducts) for each\
  \ `destId`\n\n**Note**: As some products operate in multiple destinations, the same\
  \ product code may be returned for a range of different destinations. Therefore,\
  \ make sure your list of product codes only contains one copy of each code.\n\n\
  You may then iterate through this list of product codes to retrieve any other product\
  \ details necessary in order to properly populate your local database with the information\
  \ you require.\n\n#### Retrieving a subsection of the product catalogue\n\nYou may\
  \ wish to retrieve only some of the products available in the Viator catalogue;\
  \ for example, if your organization is only interested in selling products that\
  \ operate locally.\n\nYour top level search using [/search/products](#operation/searchProducts)\
  \ is restricted to one of the three main categorization methods for products; i.e.,\
  \ destination, category/subcategory, or attraction-link; however, you may employ\
  \ your own methods to filter the selection of products based on any attribute in\
  \ the product data structure.\n\n#### Dealing with pagination using `totalCount`\
  \ and `topX`\n\nDue to the large number of results that can be returned by the [/search/products](#operation/searchProducts)\
  \ service, the request might exceed the 30-second time-out limitation on both sandbox\
  \ and live servers. Therefore, you will need to make multiple requests to this service\
  \ including pagination information in order to retrieve all products that match\
  \ your search criteria.\n\nThis is accomplished by sequentially requesting successive\
  \ segments of the results using the `topX` request parameter together with the `totalCount`\
  \ response field; i.e.:\n\n* For your first request, specify a `topX` of `\"1-100\"\
  `\n  - **Note**: this range is *inclusive*; i.e., `\"topX\": 1-100\"` will yield\
  \ the first 100 records \n* The first response will indicate the total number of\
  \ records available through the value of the `totalCount` field in the response\
  \ object; e.g.: `\"totalCount\": 13843`\n* For each subsequent request, specify\
  \ the next logical 'chunk' of data via the `topX` parameter of the request; e.g.:\n\
  \  - \"topX\": \"1-100\"\n  - \"topX\": \"101-200\"\n  - ...\n  - \"topX\": \"13801-13843\"\
  \n\n#### Rate limiting\n\nDue to the heavy load that pre-caching can place on Viator's\
  \ servers and the downstream servers we connect to, we apply a rate limit of **150\
  \ requests per 10 second time window**.\n\nRequest rates exceeding this limit will\
  \ result in a **HTTP 429 (Too Many Requests)** status code being returned.\n\n**Note**:\
  \ The rate is calculated over a rolling 10-second time window\n\n* In order to avoid\
  \ running-up against rate limits:\n  - insert a delay of 2s if you receive a HTTP\
  \ 429 status code\n  - do not run this as a multi-threaded process\n\n## Categorization\
  \ of content\n\nThe products available in Viator’s catalogue are mainly categorized\
  \ according to:\n\n1. **Destination**: every product in the Viator catalogue is\
  \ categorized according to the destination/locale in which it operates. There are\
  \ three kinds of destination:\n&lt;table&gt;\n  &lt;thead&gt;\n    &lt;th&gt;Destination\
  \ type&lt;/th&gt;\n    &lt;th&gt;Meaning&lt;/th&gt;\n  &lt;/thead&gt;\n  &lt;tbody&gt;\n\
  \    &lt;tr&gt;\n      &lt;td&gt;“COUNTRY”&lt;/td&gt;\n      &lt;td&gt;A country;\
  \ e.g., “Australia”, “Japan”, “USA”&lt;/td&gt;\n    &lt;/tr&gt;\n    &lt;tr&gt;\n\
  \      &lt;td&gt;\"REGION\"&lt;/td&gt;\n      &lt;td&gt;A geographical region or\
  \ state; e.g., “South Australia”, “French Riviera”, “Punjab”&lt;/td&gt;\n    &lt;/tr&gt;\n\
  \    &lt;tr&gt;\n      &lt;td&gt;\"CITY\"&lt;/td&gt;\n      &lt;td&gt;A city within\
  \ a state; e.g., “Townsville”, “Osaka”, “Singapore”&lt;/td&gt;\n    &lt;/tr&gt;\n\
  \  &lt;/tbody&gt;\n&lt;/table&gt;\n&lt;table&gt;\n  &lt;thead&gt;\n    &lt;tr&gt;\n\
  \      &lt;th&gt;&lt;code&gt;destinationName&lt;/code&gt;&lt;/th&gt;\n      &lt;th&gt;&lt;code&gt;destId&lt;/code&gt;&lt;/th&gt;\n\
  \      &lt;th&gt;&lt;code&gt;destinationType&lt;/code&gt;&lt;/th&gt;\n    &lt;/tr&gt;\n\
  \  &lt;/thead&gt;\n  &lt;tbody&gt;\n    &lt;tr&gt;\n      &lt;td&gt;USA&lt;/td&gt;\n\
  \      &lt;td&gt;77&lt;/td&gt;\n      &lt;td&gt;COUNTRY&lt;/td&gt;\n    &lt;/tr&gt;\n\
  \    &lt;tr&gt;\n      &lt;td&gt;Wisconsin&lt;/td&gt;\n      &lt;td&gt;22231&lt;/td&gt;\n\
  \      &lt;td&gt;REGION&lt;/td&gt;\n    &lt;/tr&gt;\n    &lt;tr&gt;\n      &lt;td&gt;Madison&lt;/td&gt;\n\
  \      &lt;td&gt;24146&lt;/td&gt;\n      &lt;td&gt;CITY&lt;/td&gt;\n    &lt;/tr&gt;\n\
  \    &lt;tr&gt;\n      &lt;td&gt;France&lt;/td&gt;\n      &lt;td&gt;51&lt;/td&gt;\n\
  \      &lt;td&gt;COUNTRY&lt;/td&gt;\n    &lt;/tr&gt;\n    &lt;tr&gt;\n      &lt;td&gt;Brittany&lt;/td&gt;\n\
  \      &lt;td&gt;21942&lt;/td&gt;\n      &lt;td&gt;REGION&lt;/td&gt;\n    &lt;/tr&gt;\n\
  \    &lt;tr&gt;\n      &lt;td&gt;Rennes&lt;/td&gt;\n      &lt;td&gt;21943&lt;/td&gt;\n\
  \      &lt;td&gt;CITY&lt;/td&gt;\n    &lt;/tr&gt;\n  &lt;/tbody&gt;\n&lt;/table&gt;\n\
  \n1. **Category and subcategory**: the products in the Viator catalogue are grouped\
  \ according to the kind of activity they entail and may be subcategorized further\
  \ to provide greater specificity; for example:\n&lt;table&gt;\n  &lt;thead&gt;\n\
  \    &lt;tr&gt;\n      &lt;th&gt;Category&lt;/th&gt;\n      &lt;th&gt;Subcategories&lt;/th&gt;\n\
  \    &lt;/tr&gt;\n  &lt;/thead&gt;\n  &lt;tbody&gt;\n    &lt;tr&gt;\n      &lt;td\
  \ rowspan=3&gt;Air, Helicopter &amp; Balloon Tours&lt;/td&gt;\n      &lt;td&gt;Air\
  \ Tours&lt;/td&gt;\n    &lt;/tr&gt;\n    &lt;tr&gt;\n      &lt;td&gt;Helicopter\
  \ Tours&lt;/td&gt;\n    &lt;/tr&gt;\n    &lt;tr&gt;\n      &lt;td&gt;Balloon Rides&lt;/td&gt;\n\
  \    &lt;/tr&gt;\n    &lt;tr&gt;\n      &lt;td rowspan=2&gt;Weddings &amp; Honeymoons&lt;/td&gt;\n\
  \      &lt;td&gt;Wedding Packages&lt;/td&gt;\n    &lt;/tr&gt;\n    &lt;tr&gt;\n\
  \      &lt;td&gt;Honeymoon Packages&lt;/td&gt;\n    &lt;/tr&gt;\n  &lt;/tbody&gt;\n\
  &lt;/table&gt;\n1. **Attraction link** (i.e., association to a particular \"point\
  \ of interest\"); e.g.:\n&lt;table&gt;\n  &lt;thead&gt;\n    &lt;tr&gt;\n      &lt;th&gt;Attraction&lt;/th&gt;\n\
  \      &lt;th&gt;`seoId`&lt;/th&gt;\n    &lt;tr&gt;\n  &lt;/thead&gt;\n  &lt;tbody&gt;\n\
  \    &lt;tr&gt;\n      &lt;td&gt;Bellagio Fountains&lt;/td&gt;\n      &lt;td&gt;1243&lt;/td&gt;\n\
  \    &lt;/tr&gt;\n    &lt;tr&gt;\n      &lt;td&gt;Black Canyon&lt;/td&gt;\n    \
  \  &lt;td&gt;4437&lt;/td&gt;\n    &lt;/tr&gt;\n    &lt;tr&gt;\n      &lt;td&gt;Epcot\
  \ Centre&lt;/td&gt;\n      &lt;td&gt;1141&lt;/td&gt;\n    &lt;/tr&gt;\n  &lt;/tbody&gt;\n\
  &lt;/table&gt;\n\n\n## Booking concepts\n\n### Booking types - *on-request* and\
  \ *freesale*\n\nBookings made with Viator can be either *freesale* (immediate confirmation)\
  \ or *on-request*, which require us to confirm with our product supplier that the\
  \ product has not sold out and is still available. This difference must be clearly\
  \ communicated to the customer during the price check and on the *order summary*\
  \ post-purchase page.\n\nFor *freesale* bookings, the voucher becomes available\
  \ immediately, and the customer's credit card will be charged at the time of booking.\
  \ For *on-request* bookings, confirmation will be sent to the customer within a\
  \ timeframe supplied in the [/booking/calculateprice](#operation/bookingCalculateprice)\
  \ and [/booking](#operation/bookingBook) service responses.\n\nThe customer's credit\
  \ card will be charged once their *on-request* booking is confirmed.\n\n###  bookingEngineId\n\
  \n`bookingEngineId` is a field returned in the responses from several endpoints\
  \ documented in this manual. It is a **booking type specifier** indicating whether,\
  \ when the product in question is booked, the booking will be `CONFIRMED` immediately\
  \ or if it will remain `PENDING` even after the booking has been made, indicating\
  \ that it is an on-request product.\n\n`bookingEngineId` takes *one of* the following\
  \ values:\n\n  - `\"FreesaleBE\"` – the product will be confirmed immediately and\
  \ the supplier will be sent a notification.\n\n  - `\"UnconditionalBE\"` - the product\
  \ will be confirmed immediately and the supplier will not be notified.\n\n  - `\"\
  DeferredCRMBE\"` - the product is an on-request product and the booking will not\
  \ be confirmed immediately. The booking will remain with a `PENDING` status after\
  \ it is made, to be confirmed by the supplier within the time specified in the `hoursConfirmed`\
  \ field available in the booking response and post-booking services.\n\n  - `\"\
  FreesaleOnRequestBE\"` - The product is freesale up until a certain number of days\
  \ before the travel date, after which it becomes on-request. It is then referred\
  \ to as being within the *on-request period*. If a booking is made within the on-request\
  \ period, the product can be considered to be an on-request product. Once the booking\
  \ has been made, the `bookingEngineId` will change to either `\"FreesaleOnRequestBE:OnRequest\"\
  ` or `\"FreesaleOnRequestBE:Freesold\"` depending on the travel date and the on-request\
  \ period.                      \n\n### Tour grades\n\nProducts can have one or more\
  \ *tour grades*. Each tour grade might represent a departure time or different tour\
  \ option, such as additional meals, transport and so forth. If the tour grade code\
  \ is `\"DEFAULT\"`, *do not* display this to the customer, simply hide the product's\
  \ tour grade information.\n\n### Language options\n\nMany tours deliver a commentary\
  \ in multiple languages using multilingual tour guides or with written or prerecorded\
  \ information. Where available, the customer can preselect their preferred language\
  \ option.\n\n### Traveler mix (pax)\n\nSome tour grades have defined traveler mixes\
  \ used to price family passes; or, they might have special mixes for limited passenger\
  \ tours, such as small buggies or weddings.\n\nThese traveler mixes are provided\
  \ by the [/booking/availability/tourgrades](#operation/bookingAvailabilityTourgrades)\
  \ service. You may need to display these to your customers so that they are able\
  \ to understand why they can or cannot select a particular tour grade if there is\
  \ a traveler mix mismatch.\n\n### Pick-up location and hotel lists\n\nSome products\
  \ have pick-up and return shuttle bus services. For these tours, you will need the\
  \ customer to supply a pick-up hotel, or they must select *live locally* or *hotel\
  \ not yet booked* options.\n\nViator maintains pick-up hotel lists for many popular\
  \ destinations. These lists are available for customers to select their pick-up\
  \ location for various tours. For destinations without hotel lists, customers can\
  \ enter the name of their hotel. If a customer's hotel is not listed, they should\
  \ be able to enter a hotel name; however, pick-up may not be possible for that hotel.\n\
  \n### Lead traveler\n\nEach tour booking requires a lead traveler to be identified.\
  \ To identify the lead traveler in your request, set the `leadTraveller` flag to\
  \ `true` in the traveler class.\n\n### Booking questions\n\nSome products have a\
  \ list of one or more [booking questions](#section/Appendices/Booking-questions)\
  \ that need to be asked. Some are mandatory. The question, a description, etc are\
  \ provided in the product details object. The answers need to be included with the\
  \ booking request.\n\n### SSL/HTTPS\n\nCalls to the [/booking/book](#operation/bookingBook)\
  \ service *must* use a secure channel (https) as they contain credit card information.\n\
  \n### Promo codes\n\nViator can create promotional (promo) codes for discounts and\
  \ other purposes. As it's unlikely for you to wish to support this feature, we recommend\
  \ supplying `null` in the `promoCode` field and not including any customer-entered\
  \ fields during the checkout process.\n\n### Partner data\n\nPartners can also supply\
  \ additional information for their own internal purposes. These are attached to\
  \ booking reports and other materials for use in allocating commissions to agents\
  \ and so forth.\n\n## Availability services\n\nProduct availability information\
  \ can be retrieved with the following services:\n\n- [/booking/availability](#operation/bookingAvailability):\
  \ get the tourgrade with the lowest price available on a day\n- [/booking/availability/dates](#operation/bookingAvailabilityDates):\
  \ get all available dates for a product excluding days it does not operate and blockouts\n\
  - [/booking/availability/tourgrades](#operation/bookingAvailabilityTourgrades):\
  \ list all available tour grades for a specific day\n- [/booking/availability/tourgrades/pricingmatrix](#operation/bookingAvailabilityTourgradesPricingmatrix):\
  \ returns available days only (ie days which have at least one tour grade available),\
  \ and the pricing matrix for that tour grade on that day\n\n### Example: multiple\
  \ departures in a single day\n\nMultiple departures in a single day (each represented\
  \ by a tour grade) and the language options (langServices).\n\nThis request is for\
  \ 3 adults on a helicopter tour:\n- **Note:** No prices are returned if the tour\
  \ grade is unavailable.\n\n**Request object** ([/booking/availability/tourgrades](#operation/bookingAvailabilityTourgrades)):\n\
  \n```javascript\n{\n  \"productCode\": \"2280AAHT\",\n  \"bookingDate\": \"2013-05-11\"\
  ,\n  \"currencyCode\": \"EUR\",\n  \"ageBands\": [{\n    \"bandId\": 1,\n    \"\
  count\": 3\n  }]\n}\n```\n\n**Response object** ([/booking/availability/tourgrades](#operation/bookingAvailabilityTourgrades))\n\
  :\n\n```javascript\n{\n  \"data\": [{\n    \"available\": false,\n    \"ageBands\"\
  : null,\n    \"langServices\": null,\n    \"gradeCode\": \"EARLYM\",\n    \"unavailableReason\"\
  : \"BOOKING_CUTOFF_EXPIRED\",\n    \"gradeTitle\": \"Early Morning Departure\",\n\
  \    \"gradeDepartureTime\": \"\",\n    \"gradeDescription\": \"Flight departs Las\
  \ Vegas between 7am &amp; 8am\",\n    \"defaultLanguageCode\": \"en\",\n    \"ageBandsRequired\"\
  : null,\n    \"currencyCode\": \"ERROR\",\n    \"retailPrice\": 0,\n    \"bookingDate\"\
  : \"2013-05-11\",\n    \"retailPriceFormatted\": \"\",\n    \"merchantNetPrice\"\
  : 0,\n    \"merchantNetPriceFormatted\": \"\",\n    \"sortOrder\": 1\n  },\n  {\n\
  \    \"available\": false,\n    \"ageBands\": null,\n    \"langServices\": null,\n\
  \    \"gradeCode\": \"LATEM\",\n    \"unavailableReason\": \"BOOKING_CUTOFF_EXPIRED\"\
  ,\n    \"gradeTitle\": \"Late Morning Departure\",\n    \"gradeDepartureTime\":\
  \ \"\",\n    \"gradeDescription\": \"Flight departs Las Vegas between 9:45am &amp;\
  \ 10:45am\",\n    \"defaultLanguageCode\": \"en\",\n    \"ageBandsRequired\": null,\n\
  \    \"currencyCode\": \"ERROR\",\n    \"retailPrice\": 0,\n    \"bookingDate\"\
  : \"2013-05-11\",\n    \"retailPriceFormatted\": \"\",\n    \"merchantNetPrice\"\
  : 0,\n    \"merchantNetPriceFormatted\": \"\",\n    \"sortOrder\": 2\n  },\n  {\n\
  \    \"available\": false,\n    \"ageBands\": null,\n    \"langServices\": null,\n\
  \    \"gradeCode\": \"EARLYA\",\n    \"unavailableReason\": \"BOOKING_CUTOFF_EXPIRED\"\
  ,\n    \"gradeTitle\": \"Early Afternoon Departure\",\n    \"gradeDepartureTime\"\
  : \"2:50 PM\",\n    \"gradeDescription\": \"Flight departs Las Vegas between 12:30pm\
  \ &amp; 1:30pm\",\n    \"defaultLanguageCode\": \"en\",\n    \"ageBandsRequired\"\
  : null,\n    \"currencyCode\": \"ERROR\",\n    \"retailPrice\": 0,\n    \"bookingDate\"\
  : \"2013-05-11\",\n    \"retailPriceFormatted\": \"\",\n    \"merchantNetPrice\"\
  : 0,\n    \"merchantNetPriceFormatted\": \"\",\n    \"sortOrder\": 3\n  },\n  {\n\
  \    \"available\": false,\n    \"ageBands\": null,\n    \"langServices\": null,\n\
  \    \"gradeCode\": \"LATEA\",\n    \"unavailableReason\": \"BOOKING_CUTOFF_EXPIRED\"\
  ,\n    \"gradeTitle\": \"Late Afternoon Departure\",\n    \"gradeDepartureTime\"\
  : \"\",\n    \"gradeDescription\": \"Flight departs Las Vegas between 3:15pm &amp;\
  \ 4:15pm; available Ap\",\n    \"defaultLanguageCode\": \"en\",\n    \"ageBandsRequired\"\
  : null,\n    \"currencyCode\": \"ERROR\",\n    \"retailPrice\": 0,\n    \"bookingDate\"\
  : \"2013-05-11\",\n    \"retailPriceFormatted\": \"\",\n    \"merchantNetPrice\"\
  : 0,\n    \"merchantNetPriceFormatted\": \"\",\n    \"sortOrder\": 4\n  }],\n  \"\
  vmid\": \"221001\",\n  \"errorMessage\": null,\n  \"errorType\": null,\n  \"dateStamp\"\
  : \"2013-06-04T17:01:34+0000\",\n  \"totalCount\": 1,\n  \"errorReference\": null,\n\
  \  \"errorMessageText\": null,\n  \"success\": true,\n  \"errorName\": null\n}\n\
  ```\n\n### Example: traveler mix mismatch\n\nThe request is for five adults, but\
  \ this product only support up to four adults.\n\n**Example request object** ([/booking/availability/tourgrades](#operation/bookingAvailabilityTourgrades)):\n\
  ```javascript\n{\n  \"productCode\": \"2280ULTWED\",\n  \"bookingDate\": \"2013-12-11\"\
  ,\n  \"currencyCode\": \"EUR\",\n  \"ageBands\": [{\n    \"bandId\": 1,\n    \"\
  count\": 5\n  }]\n}\n```\n\n**Example response object**\nThe response contains `\"\
  TRAVELLER_MISMATCH\"` and you can see the `ageBandsRequired` values for the adult\
  \ (1) age band in the available tour grade.\n\n```javascript\n{\n  \"data\": [{\n\
  \    \"available\": false,\n    \"ageBands\": null,\n    \"langServices\": null,\n\
  \    \"gradeCode\": \"DEFAULT\",\n    \"unavailableReason\": \"TRAVELLER_MISMATCH\"\
  ,\n    \"gradeTitle\": \"DEFAULT\",\n    \"gradeDepartureTime\": \"12:00 AM\",\n\
  \    \"gradeDescription\": \"DEFAULT\",\n    \"defaultLanguageCode\": \"en\",\n\
  \    \"ageBandsRequired\": [\n    [{\n      \"bandId\": 1,\n      \"minimumCountRequired\"\
  : 2,\n      \"maximumCountRequired\": 2\n    }],\n    [{\n      \"bandId\": 1,\n\
  \      \"minimumCountRequired\": 3,\n      \"maximumCountRequired\": 3\n    }],\n\
  \    [{\n      \"bandId\": 1,\n      \"minimumCountRequired\": 4,\n      \"maximumCountRequired\"\
  : 4\n    }]],\n    \"currencyCode\": \"ERROR\",\n    \"retailPrice\": 0,\n    \"\
  bookingDate\": \"2013-12-11\",\n    \"retailPriceFormatted\": \"\",\n    \"merchantNetPrice\"\
  : 0,\n    \"merchantNetPriceFormatted\": \"\",\n    \"sortOrder\": 1\n  }],\n  \"\
  vmid\": \"221001\",\n  \"errorMessage\": null,\n  \"errorType\": null,\n  \"dateStamp\"\
  : \"2013-06-04T17:02:35+0000\",\n  \"totalCount\": 1,\n  \"errorReference\": null,\n\
  \  \"errorMessageText\": null,\n  \"success\": true,\n  \"errorName\": null\n}\n\
  ```\n\n## Understanding the pricingUnit field\n\nThis section explains the meaning\
  \ and function of the `pricingUnit` field in the response object received from the\
  \ [/booking/availability/tourgrades/pricingmatrix](#operation/bookingAvailabilityTourgradesPricingmatrix)\
  \ service.\n\n### Request body\nThe [/booking/availability/tourgrades/pricingmatrix](#operation/bookingAvailabilityTourgradesPricingmatrix)\
  \ service takes the following parameters as input in its request body:\n\n| Parameter\
  \ | Type | Meaning |\n|-----------|------|---------|\n| `productCode` | string |\
  \ unique alphanumeric identifier of the product to enquire about; e.g., `10040WORLD`\
  \ |\n| `month` | string | **month** of the year by which to filter results |\n|\
  \ `year` | string | **year** by which to filter results |\n| `currencyCode` | string\
  \ | **currency code** for the currency in which to display pricing information |\n\
  \n#### Example request body\n\nSending the following request body to the [/booking/availability/tourgrades/pricingmatrix](#operation/bookingAvailabilityTourgradesPricingmatrix)\
  \ service will retrieve pricing information for \"Skip the Line: World of Discoveries\
  \ Entrance Ticket in Porto\" (product code: 10040WORLD).\n\n```javascript\n{\n \
  \ \"productCode\": \"10040WORLD\",\n  \"currencyCode\": \"USD\",\n  \"month\": \"\
  06\",\n  \"year\": \"2019\"\n}\n```\n\n### Response object\n\nWithin each object\
  \ item of the `tourGrades` array – each of which gives the pricing details for a\
  \ specific tour grade – is a `pricingMatrix` array. Each object in this array details\
  \ the per-age-band pricing for a specific pricing unit (`pricingUnit`) associated\
  \ with that product.\n\nUsing this information, you should be able to calculate\
  \ the total cost of the booking – considering any booking options – with regard\
  \ to the number of participants.\n\nHow to identify the fundamental unit prices\
  \ for a booking, which are then summed in order to calculate a total price, is detailed\
  \ below.\n\nNote that in the response object received from the service, pricing\
  \ schedules are organized hierarchically as follows:\n\n```c\nbookingDate\n--tourGrade\n\
  ----ageBand\n------price\n```\n\n### Types of pricing unit\nThere are two fundamental\
  \ types of pricing unit – **per-person** and **per-group**.\n\n#### Per-person pricing\
  \ schedule\nIf the pricing is *per-person*, then the total price of the booking\
  \ will be directly proportional to the number of participants (passengers) of each\
  \ type that are booking the product; i.e., a direct multiple of the per-person price.\n\
  \nThe only pricing unit specifier for *per-person* pricing is “per person”, given\
  \ in the `pricingUnit` field; i.e.:\n\n- `\"pricingUnit\": \"per person\"`\n\n|\
  \ Pricing unit | Example product | Meaning |\n|--------------|---------|---------|\n\
  | `\"per person\"` | **10040WORLD** | **Per-person pricing** – the unit price refers\
  \ to the price for an individual participant.&lt;br /&gt;Some products have tiered\
  \ pricing arrangements; i.e., a different per-person price can apply if certain\
  \ numbers and combinations of participants in a particular age band are booking\
  \ the product; e.g.:&lt;br /&gt;&lt;ul&gt;&lt;li&gt;**1-2 adults**: $50 per person&lt;/li&gt;&lt;li&gt;**3-4\
  \ adults**: $45 per person&lt;/li&gt;&lt;/ul&gt;&lt;br /&gt;Whether a range is available\
  \ to be booked depends on whether the customer’s desired passenger mix satisfies\
  \ the `minimumCountRequired` and `maximumCountRequired` fields in each item of the\
  \ `ageBandPrices` array. |\n\n#### Per-group pricing\nIf the pricing is per-group,\
  \ then the total price of the booking will depend on the number of groups and types\
  \ of group that ideally accommodate the participant mix.\n\nThe following pricing\
  \ schedules follow “per-group” logic:\n\n- `\"pricingUnit\": \"per vehicle\"`\n\
  - `\"pricingUnit\": \"per car\"`\n- `\"pricingUnit\": \"per group\"`\n- `\"pricingUnit\"\
  : \"per boat\"`\n- `\"pricingUnit\": \"per package\"`\n- `\"pricingUnit\": \"per\
  \ jetski\"`\n- `\"pricingUnit\": \"per vessel\"`\n- `\"pricingUnit\": \"per helicopter\"\
  `\n- `\"pricingUnit\": \"per room\"`\n- `\"pricingUnit\": \"per bike\"`\n- `\"pricingUnit\"\
  : \"per flight\"`\n- `\"pricingUnit\": \"per plane\"`\n- `\"pricingUnit\": \"per\
  \ couple\"`\n\nEligibility for a certain individual pricing schedule; or, for inclusion\
  \ in a particular group type, depends on the tour grade for the product, the type\
  \ of participant (e.g., the age-band they fall into) and the date of the booking.\n\
  \n#### Group pricing schedules\n\n| Pricing unit  | Example product | Meaning |\n\
  |---------------|-----------|---------|\n| `\"per group\"` | **10847P42**  | **Per-group**\
  \ pricing – the unit price is calculated according to the number of groups the specified\
  \ passenger will fit into rather than the exact number of participants. `minimumCountRequired`\
  \ and `maximumCountRequired` must be considered as these fields relate to the available\
  \ group sizes. |\n| `\"per room\"`  | **6279P26** | **Per-room** pricing relates\
  \ the room price, which depends on the number of participants making the booking.\
  \ |\n| `\"per package\"` | **25941P70**  | **Per-package** pricing refers to products\
  \ that are sold as part of a package; for example a family package stipulating a\
  \ passenger mix of two adults and two children |\n| `\"per vehicle\"` | **6154SHOP**\
  \  | **Per-vehicle** pricing is calculated according to the number of vehicles required\
  \ for the specified passenger mix rather than the exact number of participants.\
  \ `minimumCountRequired` and `maximumCountRequired` must be considered as these\
  \ fields relate to the occupancy limitations for each vehicle. The minimum price\
  \ will depend on the rate for a single vehicle. |\n| `\"per car\"` | **10175P10**\
  \  | **Per-car** pricing – identical to \"per vehicle\", but refers specifically\
  \ to vehicles that are cars. |\n| `\"per boat\"`  | **11121P40**  | **Per-boat**\
  \ pricing – identical to \"per vehicle\", but refers specifically to vehicles that\
  \ are boats. |\n| `\"per jetski\"`  | **28965P127** | **Per-jetski** pricing – identical\
  \ to \"per vehicle\", but refers specifically to vehicles that are jet-skis. |\n\
  | `\"per vessel\"`  | **17295P24**  | **Per-vessel** pricing – identical to \"per\
  \ vehicle\", but refers specifically to maritime vessels that are not strictly boats.\
  \ |\n| `\"per helicopter\"`  | **12189P23**  | **Per-helicopter** pricing – identical\
  \ to \"per vehicle\", but refers specifically to vehicles that are helicopters.\
  \ |\n| `\"per bike\"`  | **17448P8** | **Per-bike** pricing – identical to \"per\
  \ vehicle\", but refers specifically to vehicles that are bikes. |\n| `\"per flight\"\
  `  | **28965P134** | **Per-flight** pricing – identical to \"per vehicle\", but\
  \ refers specifically to the act of being aboard a flying vehicle. |\n| `\"per plane\"\
  ` | **14876P5** | **Per-plane** pricing – identical to \"per vehicle\", but refers\
  \ specifically to vehicles that are aeroplanes. |\n\n### Interpreting response objects\
  \ by example\n\nIn this section, we’ll have a look at snippets from the response\
  \ objects received from the [/booking/availability/tourgrades/pricingmatrix](#operation/bookingAvailabilityTourgradesPricingmatrix)\
  \ service and interpret the results.\n\n#### Per-person pricing\n##### Request object\n\
  ```javascript\n{\n  \"productCode\": \"10040WORLD\",\n  \"currencyCode\": \"USD\"\
  ,\n  \"month\": \"06\",\n  \"year\": \"2019\"\n}\n```\n#### Response snippet\n\n\
  **Note:** `pricingMatrix` is an array of objects that detail the available pricing\
  \ schedules for the product:\n\n```javascript\n\"pricingMatrix\": [\n  {\n    \"\
  sortOrder\": 1,\n    \"pricingUnit\": \"per person\",\n    \"bookingDate\": \"2019-06-01\"\
  ,\n    \"ageBandPrices\": [\n      {\n        \"bandId\": 1,\n        \"prices\"\
  : [\n          {\n            \"sortOrder\": 1,\n            \"currencyCode\": \"\
  USD\",\n            \"price\": 13.85,\n            \"priceFormatted\": \"$13.85\"\
  ,\n            \"merchantNetPrice\": 11.05,\n            \"merchantNetPriceFormatted\"\
  : \"$11.05\",\n            \"minNoOfTravellersRequiredForPrice\": 1\n          }\n\
  \        ],\n        \"sortOrder\": 1,\n        \"minimumCountRequired\": 0,\n \
  \       \"maximumCountRequired\": 15\n      },\n      {\n        \"bandId\": 2,\n\
  \        \"prices\": [\n          {\n            \"sortOrder\": 1,\n           \
  \ \"currencyCode\": \"USD\",\n            \"price\": 6.92,\n            \"priceFormatted\"\
  : \"$6.92\",\n            \"merchantNetPrice\": 5.53,\n            \"merchantNetPriceFormatted\"\
  : \"$5.53\",\n            \"minNoOfTravellersRequiredForPrice\": 1\n          }\n\
  \        ],\n        \"sortOrder\": 2,\n        \"minimumCountRequired\": 0,\n \
  \       \"maximumCountRequired\": 15\n      },\n      {\n        \"bandId\": 3,\n\
  \        \"prices\": [\n          {\n            \"sortOrder\": 1,\n           \
  \ \"currencyCode\": \"USD\",\n            \"price\": 0,\n            \"priceFormatted\"\
  : \"$0.00\",\n            \"merchantNetPrice\": 0,\n            \"merchantNetPriceFormatted\"\
  : \"$0.00\",\n            \"minNoOfTravellersRequiredForPrice\": 1\n          }\n\
  \        ],\n        \"sortOrder\": 3,\n        \"minimumCountRequired\": 0,\n \
  \       \"maximumCountRequired\": 15\n      },\n      {\n        \"bandId\": 5,\n\
  \        \"prices\": [\n          {\n            \"sortOrder\": 1,\n           \
  \ \"currencyCode\": \"USD\",\n            \"price\": 10.39,\n            \"priceFormatted\"\
  : \"$10.39\",\n            \"merchantNetPrice\": 8.3,\n            \"merchantNetPriceFormatted\"\
  : \"$8.30\",\n            \"minNoOfTravellersRequiredForPrice\": 1\n          }\n\
  \        ],\n        \"sortOrder\": 4,\n        \"minimumCountRequired\": 0,\n \
  \       \"maximumCountRequired\": 15\n      }\n    ]\n  }\n]\n```\n\nIn this example,\
  \ four age bands (1, 2, 3 and 5) have pricing information available. These numerically-identified\
  \ age bands are the age bands allowed to book the product. Details of the age ranges\
  \ that the product operator has defined are available from the **/product** service.\n\
  \nA call to **/product** regarding `10040WORLD` yields the following information:\n\
  \n```javascript\n\"ageBands\": [\n  {\n    \"sortOrder\": 1,\n    \"ageFrom\": 13,\n\
  \    \"ageTo\": 64,\n    \"adult\": true,\n    \"bandId\": 1,\n    \"pluralDescription\"\
  : \"Adults\",\n    \"treatAsAdult\": true,\n    \"count\": 0,\n    \"description\"\
  : \"Adult\"\n  },\n  {\n    \"sortOrder\": 2,\n    \"ageFrom\": 65,\n    \"ageTo\"\
  : 99,\n    \"adult\": false,\n    \"bandId\": 5,\n    \"pluralDescription\": \"\
  Seniors\",\n    \"treatAsAdult\": true,\n    \"count\": 0,\n    \"description\"\
  : \"Senior\"\n  },\n  {\n    \"sortOrder\": 3,\n    \"ageFrom\": 4,\n    \"ageTo\"\
  : 12,\n    \"adult\": false,\n    \"bandId\": 2,\n    \"pluralDescription\": \"\
  Children\",\n    \"treatAsAdult\": false,\n    \"count\": 0,\n    \"description\"\
  : \"Child\"\n  },\n  {\n    \"sortOrder\": 4,\n    \"ageFrom\": 0,\n    \"ageTo\"\
  : 3,\n    \"adult\": false,\n    \"bandId\": 3,\n    \"pluralDescription\": \"Infants\"\
  ,\n    \"treatAsAdult\": false,\n    \"count\": 0,\n    \"description\": \"Infant\"\
  \n  }\n```\n\nProduct operators choose the age bands available for their product\
  \ from the following five categories and define the age ranges that pertain to each\
  \ band; i.e.:\n\n| `bandId` | `description` |\n|:----------:|:-----------:|\n| **1**\
  \ | Adult |\n| **2** | Child |\n| **3** | Infant |\n| **4** | Youth |\n| **5** |\
  \ Senior |\n\nFor this product, the age bands have been defined as follows:\n\n\
  | `bandId` | `description` | `ageFrom` | `ageTo` |\n|:--------:|:-----------:|:-------:|:-----:|\n\
  | **1** | Adult | 13 | 64 |\n| **5** | Senior | 65 | 99 |\n| **2** | Child | 4 |\
  \ 12 |\n| **3** | Infant | 0 | 3 |\n\nTherefore, for this product, the following\
  \ pricing applies:\n\n| Passenger type | Number | Price |\n|----------------|:------:|-------|\n\
  | **Adult** | 1-15 | $13.85 per person |\n| **Senior** | 1-15 | $10.39 per person\
  \ |\n| **Child** | 1-15 | $6.92 per person |\n| **Infant** | 1-15 | free ($0) |\n\
  \nPer-person pricing might depend on the mix of passengers booking the tour. In\
  \ the following example (`5010SYDNEY`), a \"48 Hour Family Pass Ticket\" has a different\
  \ price for children depending on how many are participating, which we'll see in\
  \ the following snippet.\n\n##### Response snippet\n```javascript\n\"tourGrades\"\
  : [\n  {\n    \"sortOrder\": 1,\n    \"gradeCode\": \"14HFAM\",\n    \"gradeTitle\"\
  : \"48 Hour Family Pass Ticket\",\n    \"pricingMatrix\": [\n      {\n        \"\
  sortOrder\": 1,\n        \"pricingUnit\": \"per person\",\n        \"bookingDate\"\
  : \"2019-08-01\",\n        \"ageBandPrices\": [\n          {\n            \"bandId\"\
  : 1,\n            \"prices\": [\n              {\n                \"sortOrder\"\
  : 1,\n                \"currencyCode\": \"USD\",\n                \"price\": 133.47,\n\
  \                \"minNoOfTravellersRequiredForPrice\": 1,\n                \"priceFormatted\"\
  : \"$133.47\",\n                \"merchantNetPrice\": 106.62,\n                \"\
  merchantNetPriceFormatted\": \"$106.62\"\n              }\n            ],\n    \
  \        \"sortOrder\": 1,\n            \"minimumCountRequired\": 1,\n         \
  \   \"maximumCountRequired\": 1\n          },\n          {\n            \"bandId\"\
  : 2,\n            \"prices\": [\n              {\n                \"sortOrder\"\
  : 1,\n                \"currencyCode\": \"USD\",\n                \"price\": 0,\n\
  \                \"minNoOfTravellersRequiredForPrice\": 1,\n                \"priceFormatted\"\
  : \"$0.00\",\n                \"merchantNetPrice\": 0,\n                \"merchantNetPriceFormatted\"\
  : \"$0.00\"\n              }\n            ],\n            \"sortOrder\": 2,\n  \
  \          \"minimumCountRequired\": 2,\n            \"maximumCountRequired\": 2\n\
  \          },\n          {\n            \"bandId\": 3,\n            \"prices\":\
  \ [\n              {\n                \"sortOrder\": 1,\n                \"currencyCode\"\
  : \"USD\",\n                \"price\": 0,\n                \"minNoOfTravellersRequiredForPrice\"\
  : 1,\n                \"priceFormatted\": \"$0.00\",\n                \"merchantNetPrice\"\
  : 0,\n                \"merchantNetPriceFormatted\": \"$0.00\"\n              }\n\
  \            ],\n            \"sortOrder\": 3,\n            \"minimumCountRequired\"\
  : 0,\n            \"maximumCountRequired\": null\n          }\n        ]\n     \
  \ },\n      {\n        \"sortOrder\": 2,\n        \"pricingUnit\": \"per person\"\
  ,\n        \"bookingDate\": \"2019-08-01\",\n        \"ageBandPrices\": [\n    \
  \      {\n            \"bandId\": 1,\n            \"prices\": [\n              {\n\
  \                \"sortOrder\": 1,\n                \"currencyCode\": \"USD\",\n\
  \                \"price\": 133.47,\n                \"minNoOfTravellersRequiredForPrice\"\
  : 1,\n                \"priceFormatted\": \"$133.47\",\n                \"merchantNetPrice\"\
  : 106.62,\n                \"merchantNetPriceFormatted\": \"$106.62\"\n        \
  \      }\n            ],\n            \"sortOrder\": 1,\n            \"minimumCountRequired\"\
  : 1,\n            \"maximumCountRequired\": 1\n          },\n          {\n     \
  \       \"bandId\": 2,\n            \"prices\": [\n              {\n           \
  \     \"sortOrder\": 1,\n                \"currencyCode\": \"USD\",\n          \
  \      \"price\": 3.71,\n                \"minNoOfTravellersRequiredForPrice\":\
  \ 1,\n                \"priceFormatted\": \"$3.71\",\n                \"merchantNetPrice\"\
  : 2.96,\n                \"merchantNetPriceFormatted\": \"$2.96\"\n            \
  \  }\n            ],\n            \"sortOrder\": 2,\n            \"minimumCountRequired\"\
  : 3,\n            \"maximumCountRequired\": 4\n          },\n          {\n     \
  \       \"bandId\": 3,\n            \"prices\": [\n              {\n           \
  \     \"sortOrder\": 1,\n                \"currencyCode\": \"USD\",\n          \
  \      \"price\": 0,\n                \"minNoOfTravellersRequiredForPrice\": 1,\n\
  \                \"priceFormatted\": \"$0.00\",\n                \"merchantNetPrice\"\
  : 0,\n                \"merchantNetPriceFormatted\": \"$0.00\"\n              }\n\
  \            ],\n            \"sortOrder\": 3,\n            \"minimumCountRequired\"\
  : 0,\n            \"maximumCountRequired\": null\n          }\n        ]\n     \
  \ }\n    ]\n  },\n  …\n]\n```\n\n##### Interpretation\n\nTo be eligible for a family\
  \ pass ticket, the group must consist of an adult and at least two children.\n\n\
  | Passenger mix | Adult price | Child price | Infant price |\n|---------------|:-----------:|:-----------:|:------------:|\n\
  | 1 Adult +&lt;br /&gt;1 Child | N/A | N/A | N/A |\n| 1 Adult +&lt;br /&gt;2 Children\
  \ +&lt;br /&gt;Any infants | $133.47 | FREE | FREE |\n| 1 Adult +&lt;br /&gt;3-4\
  \ Children +&lt;br /&gt;Any infants | $133.47 | $3.71 | FREE |\n\n#### Tiered per-person\
  \ pricing\n\nIn this example, we see a per-person pricing schedule with a tiered\
  \ arrangement, where the per-person price decreases depending on how many people\
  \ are booking the tour, but the total price is still calculated as the sum of the\
  \ individual per-person prices rather than an overall 'group' price.\n\n##### Request\
  \ object\n```javascript\n{\n  \"productCode\": \"17972P102\",\n  \"currencyCode\"\
  : \"USD\",\n  \"month\": \"08\",\n  \"year\": \"2019\"\n}\n```\n##### Response snippet\n\
  \n```javascript\n\"tourGrades\": [\n  {\n    \"sortOrder\": 1,\n    \"gradeCode\"\
  : \"TG1\",\n    \"gradeTitle\": \"Arrival transfer\",\n    \"pricingMatrix\": [\n\
  \      {\n        \"sortOrder\": 1,\n        \"pricingUnit\": \"per person\",\n\
  \        \"bookingDate\": \"2019-08-01\",\n        \"ageBandPrices\": [\n      \
  \    {\n            \"bandId\": 1,\n            \"prices\": [\n              {\n\
  \                \"sortOrder\": 1,\n                \"currencyCode\": \"USD\",\n\
  \                \"price\": 52.45,\n                \"priceFormatted\": \"$52.45\"\
  ,\n                \"merchantNetPrice\": 40.87,\n                \"merchantNetPriceFormatted\"\
  : \"$40.87\",\n                \"minNoOfTravellersRequiredForPrice\": 1\n      \
  \        }\n            ],\n            \"sortOrder\": 1,\n            \"maximumCountRequired\"\
  : 1,\n            \"minimumCountRequired\": 1\n          }\n        ]\n      },\n\
  \      {\n        \"sortOrder\": 2,\n        \"pricingUnit\": \"per person\",\n\
  \        \"bookingDate\": \"2019-08-01\",\n        \"ageBandPrices\": [\n      \
  \    {\n            \"bandId\": 1,\n            \"prices\": [\n              {\n\
  \                \"sortOrder\": 1,\n                \"currencyCode\": \"USD\",\n\
  \                \"price\": 26.22,\n                \"priceFormatted\": \"$26.22\"\
  ,\n                \"merchantNetPrice\": 20.44,\n                \"merchantNetPriceFormatted\"\
  : \"$20.44\",\n                \"minNoOfTravellersRequiredForPrice\": 1\n      \
  \        }\n            ],\n            \"sortOrder\": 1,\n            \"maximumCountRequired\"\
  : 2,\n            \"minimumCountRequired\": 2\n          }\n        ]\n      },\n\
  \      {\n        \"sortOrder\": 3,\n        \"pricingUnit\": \"per person\",\n\
  \        \"bookingDate\": \"2019-08-01\",\n        \"ageBandPrices\": [\n      \
  \    {\n            \"bandId\": 1,\n            \"prices\": [\n              {\n\
  \                \"sortOrder\": 1,\n                \"currencyCode\": \"USD\",\n\
  \                \"price\": 17.91,\n                \"priceFormatted\": \"$17.91\"\
  ,\n                \"merchantNetPrice\": 13.62,\n                \"merchantNetPriceFormatted\"\
  : \"$13.62\",\n                \"minNoOfTravellersRequiredForPrice\": 1\n      \
  \        }\n            ],\n            \"sortOrder\": 1,\n            \"maximumCountRequired\"\
  : 3,\n            \"minimumCountRequired\": 3\n          }\n        ]\n      },\n\
  \      {\n        \"sortOrder\": 4,\n        \"pricingUnit\": \"per person\",\n\
  \        \"bookingDate\": \"2019-08-01\",\n        \"ageBandPrices\": [\n      \
  \    {\n            \"bandId\": 1,\n            \"prices\": [\n              {\n\
  \                \"sortOrder\": 1,\n                \"currencyCode\": \"USD\",\n\
  \                \"price\": 19.19,\n                \"priceFormatted\": \"$19.19\"\
  ,\n                \"merchantNetPrice\": 14.99,\n                \"merchantNetPriceFormatted\"\
  : \"$14.99\",\n                \"minNoOfTravellersRequiredForPrice\": 1\n      \
  \        }\n            ],\n            \"sortOrder\": 1,\n            \"maximumCountRequired\"\
  : 4,\n            \"minimumCountRequired\": 4\n          }\n        ]\n      },\n\
  \      {\n        \"sortOrder\": 5,\n        \"pricingUnit\": \"per person\",\n\
  \        \"bookingDate\": \"2019-08-01\",\n        \"ageBandPrices\": [\n      \
  \    {\n            \"bandId\": 1,\n            \"prices\": [\n              {\n\
  \                \"sortOrder\": 1,\n                \"currencyCode\": \"USD\",\n\
  \                \"price\": 15.35,\n                \"priceFormatted\": \"$15.35\"\
  ,\n                \"merchantNetPrice\": 12.25,\n                \"merchantNetPriceFormatted\"\
  : \"$12.25\",\n                \"minNoOfTravellersRequiredForPrice\": 1\n      \
  \        }\n            ],\n            \"sortOrder\": 1,\n            \"maximumCountRequired\"\
  : 5,\n            \"minimumCountRequired\": 5\n          }\n        ]\n      },\n\
  \      {\n        \"sortOrder\": 6,\n        \"pricingUnit\": \"per person\",\n\
  \        \"bookingDate\": \"2019-08-01\",\n        \"ageBandPrices\": [\n      \
  \    {\n            \"bandId\": 1,\n            \"prices\": [\n              {\n\
  \                \"sortOrder\": 1,\n                \"currencyCode\": \"USD\",\n\
  \                \"price\": 12.66,\n                \"priceFormatted\": \"$12.66\"\
  ,\n                \"merchantNetPrice\": 10.08,\n                \"merchantNetPriceFormatted\"\
  : \"$10.08\",\n                \"minNoOfTravellersRequiredForPrice\": 1\n      \
  \        }\n            ],\n            \"sortOrder\": 1,\n            \"maximumCountRequired\"\
  : 6,\n            \"minimumCountRequired\": 6\n          }\n        ]\n      },\n\
  \      {\n        \"sortOrder\": 7,\n        \"pricingUnit\": \"per person\",\n\
  \        \"bookingDate\": \"2019-08-01\",\n        \"ageBandPrices\": [\n      \
  \    {\n            \"bandId\": 1,\n            \"prices\": [\n              {\n\
  \                \"sortOrder\": 1,\n                \"currencyCode\": \"USD\",\n\
  \                \"price\": 10.94,\n                \"priceFormatted\": \"$10.94\"\
  ,\n                \"merchantNetPrice\": 8.72,\n                \"merchantNetPriceFormatted\"\
  : \"$8.72\",\n                \"minNoOfTravellersRequiredForPrice\": 1\n       \
  \       }\n            ],\n            \"sortOrder\": 1,\n            \"maximumCountRequired\"\
  : 7,\n            \"minimumCountRequired\": 7\n          }\n        ]\n      }\n\
  \    ]\n  }\n```\n\n##### Interpretation\n\n| Travelers | Per-person price | Total\
  \ price |\n|:----------------:|:----------------:|:-----------:|\n| 1 | $52.45 |\
  \ $52.45 |\n| 2 | $26.22 | $52.44 |\n| 3 | $17.91 | $53.73 |\n| 4 | $19.19 | $76.76\
  \ |\n| 5 | $15.35 | $76.75 |\n| 6 | $12.66 | $75.96 |\n| 7 | $10.94 | $76.58 |\n\
  \n#### Per-group pricing\n##### Request object\n```javascript\n{\n  \"productCode\"\
  : \"10847P42\",\n  \"currencyCode\": \"USD\",\n  \"month\": \"06\",\n  \"year\"\
  : \"2019\"\n}\n```\n\n##### Response snippet\n\n```javascript\n\"pricingMatrix\"\
  : [\n  {\n    \"sortOrder\": 1,\n    \"pricingUnit\": \"per group\",\n    \"bookingDate\"\
  : \"2019-06-01\",\n    \"ageBandPrices\": [\n      {\n        \"bandId\": 1,\n \
  \       \"prices\": [\n          {\n            \"sortOrder\": 1,\n            \"\
  currencyCode\": \"USD\",\n            \"price\": 390,\n            \"minNoOfTravellersRequiredForPrice\"\
  : 1,\n            \"priceFormatted\": \"$390.00\",\n            \"merchantNetPrice\"\
  : 339.74,\n            \"merchantNetPriceFormatted\": \"$339.74\"\n          },\n\
  \          {\n            \"sortOrder\": 2,\n            \"currencyCode\": \"USD\"\
  ,\n            \"price\": 390,\n            \"minNoOfTravellersRequiredForPrice\"\
  : 2,\n            \"priceFormatted\": \"$390.00\",\n            \"merchantNetPrice\"\
  : 0,\n            \"merchantNetPriceFormatted\": \"$0.00\"\n          }\n      \
  \  ],\n        \"sortOrder\": 1,\n        \"minimumCountRequired\": 1,\n       \
  \ \"maximumCountRequired\": 10\n      }\n    ]\n  }\n]\n```\n\n##### Interpretation\n\
  \n- \"$390 per group of up to 10 adults\"\n\n#### Per-room pricing\n\n##### Request\
  \ object\n```javascript\n{\n  \"productCode\": \"100245P40\",\n  \"currencyCode\"\
  : \"USD\",\n  \"month\": \"08\",\n  \"year\": \"2019\"\n}\n```\n##### Response snippet\n\
  \n```javascript\n\"pricingMatrix\": [\n{\n    \"sortOrder\": 1,\n    \"pricingUnit\"\
  : \"per room\",\n    \"bookingDate\": \"2019-08-01\",\n    \"ageBandPrices\": [\n\
  \      {\n        \"bandId\": 1,\n        \"prices\": [\n          {\n         \
  \   \"sortOrder\": 1,\n            \"currencyCode\": \"USD\",\n            \"price\"\
  : 110,\n            \"minNoOfTravellersRequiredForPrice\": 1,\n            \"priceFormatted\"\
  : \"$110.00\",\n            \"merchantNetPrice\": 95.85,\n            \"merchantNetPriceFormatted\"\
  : \"$95.85\"\n          },\n          {\n            \"sortOrder\": 2,\n       \
  \     \"currencyCode\": \"USD\",\n            \"price\": 110,\n            \"minNoOfTravellersRequiredForPrice\"\
  : 2,\n            \"priceFormatted\": \"$110.00\",\n            \"merchantNetPrice\"\
  : 0,\n            \"merchantNetPriceFormatted\": \"$0.00\"\n          }\n      \
  \  ],\n        \"sortOrder\": 1,\n        \"minimumCountRequired\": 1,\n       \
  \ \"maximumCountRequired\": 10\n      }\n    ]\n  }\n]\n```\n\n##### Interpretation\n\
  - \"$110 per group of up to 10 adults\"\n\n#### Per-package pricing\n\n##### Request\
  \ object\n```javascript\n{\n  \"productCode\": \"25941P70\",\n  \"currencyCode\"\
  : \"USD\",\n  \"month\": \"02\",\n  \"year\": \"2019\"\n}\n```\n\n##### Response\
  \ snippet\n```javascript\n\"pricingMatrix\": [\n  {\n    \"sortOrder\": 1,\n   \
  \ \"pricingUnit\": \"per package\",\n    \"bookingDate\": \"2019-02-01\",\n    \"\
  ageBandPrices\": [\n      {\n        \"bandId\": 1,\n        \"prices\": [\n   \
  \       {\n            \"sortOrder\": 1,\n            \"currencyCode\": \"USD\"\
  ,\n            \"price\": 87.7,\n            \"minNoOfTravellersRequiredForPrice\"\
  : 1,\n            \"priceFormatted\": \"$87.70\",\n            \"merchantNetPrice\"\
  : 67.23,\n            \"merchantNetPriceFormatted\": \"$67.23\"\n          },\n\
  \          {\n            \"sortOrder\": 2,\n            \"currencyCode\": \"USD\"\
  ,\n            \"price\": 87.7,\n            \"minNoOfTravellersRequiredForPrice\"\
  : 2,\n            \"priceFormatted\": \"$87.70\",\n            \"merchantNetPrice\"\
  : 0,\n            \"merchantNetPriceFormatted\": \"$0.00\"\n          }\n      \
  \  ],\n        \"sortOrder\": 1,\n        \"minimumCountRequired\": 1,\n       \
  \ \"maximumCountRequired\": 10\n      }\n    ]\n  }\n]\n```\n\n##### Interpretation\n\
  - \"$87.70 per group of up to 10 adults\"\n\n#### Per-vehicle pricing\n\n##### Request\
  \ object\n```javascript\n{\n  \"productCode\": \"20190P4\",\n  \"currencyCode\"\
  : \"USD\",\n  \"month\": \"06\",\n  \"year\": \"2019\"\n}\n```\n\n##### Response\
  \ snippet\n```javascript\n\"pricingMatrix\": [\n  {\n    \"sortOrder\": 1,\n   \
  \ \"pricingUnit\": \"per vehicle\",\n    \"bookingDate\": \"2019-06-01\",\n    \"\
  ageBandPrices\": [\n      {\n        \"bandId\": 1,\n        \"prices\": [\n   \
  \       {\n            \"sortOrder\": 1,\n            \"currencyCode\": \"USD\"\
  ,\n            \"price\": 250,\n            \"minNoOfTravellersRequiredForPrice\"\
  : 1,\n            \"priceFormatted\": \"$250.00\",\n            \"merchantNetPrice\"\
  : 186.38,\n            \"merchantNetPriceFormatted\": \"$186.38\"\n          },\n\
  \          {\n            \"sortOrder\": 2,\n            \"currencyCode\": \"USD\"\
  ,\n            \"price\": 250,\n            \"minNoOfTravellersRequiredForPrice\"\
  : 2,\n            \"priceFormatted\": \"$250.00\",\n            \"merchantNetPrice\"\
  : 0,\n            \"merchantNetPriceFormatted\": \"$0.00\"\n          }\n      \
  \  ],\n        \"sortOrder\": 1,\n        \"minimumCountRequired\": 1,\n       \
  \ \"maximumCountRequired\": 7\n      }\n    ]\n  }\n]\n```\n\n##### Interpretation\n\
  - \"$250 per group of up to 7 adults\"\n\n#### Per-car pricing\n##### Request object\n\
  ```javascript\n{\n  \"productCode\": \"10175P10\",\n  \"currencyCode\": \"USD\"\
  ,\n  \"month\": \"06\",\n  \"year\": \"2019\"\n}\n```\n\n#### Response snippet\n\
  \n```javascript\n\"pricingMatrix\": [\n  {\n    \"sortOrder\": 1,\n    \"pricingUnit\"\
  : \"per car\",\n    \"bookingDate\": \"2019-06-01\",\n    \"ageBandPrices\": [\n\
  \      {\n        \"bandId\": 1,\n        \"prices\": [\n          {\n         \
  \   \"sortOrder\": 1,\n            \"currencyCode\": \"USD\",\n            \"price\"\
  : 98.08,\n            \"priceFormatted\": \"$98.08\",\n            \"merchantNetPrice\"\
  : 78.34,\n            \"merchantNetPriceFormatted\": \"$78.34\",\n            \"\
  minNoOfTravellersRequiredForPrice\": 1\n          },\n          {\n            \"\
  sortOrder\": 2,\n            \"currencyCode\": \"USD\",\n            \"price\":\
  \ 98.08,\n            \"priceFormatted\": \"$98.08\",\n            \"merchantNetPrice\"\
  : 0,\n            \"merchantNetPriceFormatted\": \"$0.00\",\n            \"minNoOfTravellersRequiredForPrice\"\
  : 2\n          }\n        ],\n        \"sortOrder\": 1,\n        \"minimumCountRequired\"\
  : 1,\n        \"maximumCountRequired\": 3\n      }\n    ]\n  }\n]\n```\n##### Interpretation\n\
  - \"$98.08 per group of up to 3 adults\"\n\n#### Per-boat pricing\n##### Request\
  \ object\n```javascript\n{\n  \"productCode\": \"11121P40\",\n  \"currencyCode\"\
  : \"USD\",\n  \"month\": \"08\",\n  \"year\": \"2018\"\n}\n```\n##### Response snippet\n\
  \n```javascript\n\"pricingMatrix\": [\n  {\n    \"sortOrder\": 1,\n    \"pricingUnit\"\
  : \"per boat\",\n    \"bookingDate\": \"2018-06-01\",\n    \"ageBandPrices\": [\n\
  \      {\n        \"bandId\": 1,\n        \"prices\": [\n          {\n         \
  \   \"sortOrder\": 1,\n            \"currencyCode\": \"USD\",\n            \"price\"\
  : 266.21,\n            \"merchantNetPrice\": 226.81,\n            \"merchantNetPriceFormatted\"\
  : \"$226.81\",\n            \"priceFormatted\": \"$266.21\",\n            \"minNoOfTravellersRequiredForPrice\"\
  : 1\n          },\n          {\n            \"sortOrder\": 2,\n            \"currencyCode\"\
  : \"USD\",\n            \"price\": 266.21,\n            \"merchantNetPrice\": 0,\n\
  \            \"merchantNetPriceFormatted\": \"$0.00\",\n            \"priceFormatted\"\
  : \"$266.21\",\n            \"minNoOfTravellersRequiredForPrice\": 2\n         \
  \ }\n        ],\n        \"sortOrder\": 1,\n        \"minimumCountRequired\": 1,\n\
  \        \"maximumCountRequired\": 2\n      }\n    ]\n  }\n]\n```\n\n##### Interpretation\n\
  - \"$266.21 per group of up to 2 adults\"\n\n#### Per-jetski pricing\n##### Request\
  \ object\n```javascript\n{\n  \"productCode\": \"28965P127\",\n  \"currencyCode\"\
  : \"USD\",\n  \"month\": \"08\",\n  \"year\": \"2018\"\n}\n```\n##### Response snippet\n\
  ```javascript\n\"tourGrades\": [\n  {\n    \"sortOrder\": 1,\n    \"gradeCode\"\
  : \"TG1\",\n    \"gradeTitle\": \"20 minutes for 1 person\",\n    \"pricingMatrix\"\
  : [\n      {\n        \"sortOrder\": 1,\n        \"pricingUnit\": \"per jetski\"\
  ,\n        \"bookingDate\": \"2018-06-01\",\n        \"ageBandPrices\": [\n    \
  \      {\n            \"bandId\": 1,\n            \"prices\": [\n              {\n\
  \                \"sortOrder\": 1,\n                \"currencyCode\": \"USD\",\n\
  \                \"price\": 55.46,\n                \"minNoOfTravellersRequiredForPrice\"\
  : 1,\n                \"priceFormatted\": \"$55.46\",\n                \"merchantNetPrice\"\
  : 47.25,\n                \"merchantNetPriceFormatted\": \"$47.25\"\n          \
  \    }\n            ],\n            \"sortOrder\": 1,\n            \"minimumCountRequired\"\
  : 1,\n            \"maximumCountRequired\": 1\n          }\n        ]\n      }\n\
  \    ]\n  },\n  {\n    \"sortOrder\": 2,\n    \"gradeCode\": \"TG3\",\n    \"gradeTitle\"\
  : \"20 minutes for 2 persons\",\n    \"pricingMatrix\": [\n      {\n        \"sortOrder\"\
  : 1,\n        \"pricingUnit\": \"per jetski\",\n        \"bookingDate\": \"2018-06-01\"\
  ,\n        \"ageBandPrices\": [\n          {\n            \"bandId\": 1,\n     \
  \       \"prices\": [\n              {\n                \"sortOrder\": 1,\n    \
  \            \"currencyCode\": \"USD\",\n                \"price\": 66.55,\n   \
  \             \"minNoOfTravellersRequiredForPrice\": 1,\n                \"priceFormatted\"\
  : \"$66.55\",\n                \"merchantNetPrice\": 56.7,\n                \"merchantNetPriceFormatted\"\
  : \"$56.70\"\n              },\n              {\n                \"sortOrder\":\
  \ 2,\n                \"currencyCode\": \"USD\",\n                \"price\": 66.55,\n\
  \                \"minNoOfTravellersRequiredForPrice\": 2,\n                \"priceFormatted\"\
  : \"$66.55\",\n                \"merchantNetPrice\": 0,\n                \"merchantNetPriceFormatted\"\
  : \"$0.00\"\n              }\n            ],\n            \"sortOrder\": 1,\n  \
  \          \"minimumCountRequired\": 1,\n            \"maximumCountRequired\": 2\n\
  \          }\n        ]\n      }\n    ]\n  }\n]\n```\n\n##### Interpretation\n\n\
  This example shows how group prices can differ according to the size of the group\
  \ in question. In this case, two adults can ride together on a two-person jet ski,\
  \ whereas a single adult requires his or her own jet ski, and therefore the unit\
  \ price is slightly higher for the single adult.\n\n| Travelers | Vehicle type |\
  \ Price per jet ski | Price per person |\n|:----------:|--------------|:-----------------:|:----------------:|\n\
  | 1 | Single-person jet ski | $55.46 | $55.46 |\n| 2 | Two-person jet ski | $66.55\
  \ | $33.275 |\n\n#### Per-vessel pricing\n\n##### Request object\n\n```javascript\n\
  {\n  \"productCode\": \"17295P24\",\n  \"currencyCode\": \"USD\",\n  \"month\":\
  \ \"06\",\n  \"year\": \"2019\"\n}\n```\n\n##### Response snippet\n\n```javascript\n\
  \"pricingMatrix\": [\n  {\n    \"sortOrder\": 1,\n    \"pricingUnit\": \"per vessel\"\
  ,\n    \"bookingDate\": \"2019-06-01\",\n    \"ageBandPrices\": [\n      {\n   \
  \     \"bandId\": 1,\n        \"prices\": [\n          {\n            \"sortOrder\"\
  : 1,\n            \"currencyCode\": \"USD\",\n            \"price\": 799,\n    \
  \        \"priceFormatted\": \"$799.00\",\n            \"merchantNetPrice\": 680.75,\n\
  \            \"merchantNetPriceFormatted\": \"$680.75\",\n            \"minNoOfTravellersRequiredForPrice\"\
  : 1\n          },\n          {\n            \"sortOrder\": 2,\n            \"currencyCode\"\
  : \"USD\",\n            \"price\": 799,\n            \"priceFormatted\": \"$799.00\"\
  ,\n            \"merchantNetPrice\": 0,\n            \"merchantNetPriceFormatted\"\
  : \"$0.00\",\n            \"minNoOfTravellersRequiredForPrice\": 2\n          }\n\
  \        ],\n        \"sortOrder\": 1,\n        \"minimumCountRequired\": 1,\n \
  \       \"maximumCountRequired\": 12\n      }\n    ]\n  }\n]\n```\n\n##### Interpretation\n\
  - \"$799.00 per group of up to 12 adults\"\n\n#### Per-helicopter pricing\n\n#####\
  \ Request object\n\n```javascript\n{\n  \"productCode\": \"12189P23\",\n  \"currencyCode\"\
  : \"USD\",\n  \"month\": \"08\",\n  \"year\": \"2018\"\n}\n```\n\n##### Response\
  \ snippet\n```javascript\n\"tourGrades\": [\n  {\n    \"sortOrder\": 1,\n    \"\
  gradeCode\": \"TG1\",\n    \"gradeTitle\": \"Private Helicopter 1 to 2 Pax\",\n\
  \    \"pricingMatrix\": [\n      {\n        \"sortOrder\": 1,\n        \"pricingUnit\"\
  : \"per helicopter\",\n        \"bookingDate\": \"2018-06-01\",\n        \"ageBandPrices\"\
  : [\n          {\n            \"bandId\": 1,\n            \"prices\": [\n      \
  \        {\n                \"sortOrder\": 1,\n                \"currencyCode\"\
  : \"USD\",\n                \"price\": 1714.83,\n                \"priceFormatted\"\
  : \"$1,714.83\",\n                \"merchantNetPrice\": 1461.03,\n             \
  \   \"merchantNetPriceFormatted\": \"$1,461.03\",\n                \"minNoOfTravellersRequiredForPrice\"\
  : 1\n              },\n              {\n                \"sortOrder\": 2,\n    \
  \            \"currencyCode\": \"USD\",\n                \"price\": 1714.83,\n \
  \               \"priceFormatted\": \"$1,714.83\",\n                \"merchantNetPrice\"\
  : 0,\n                \"merchantNetPriceFormatted\": \"$0.00\",\n              \
  \  \"minNoOfTravellersRequiredForPrice\": 2\n              }\n            ],\n \
  \           \"sortOrder\": 1,\n            \"minimumCountRequired\": 1,\n      \
  \      \"maximumCountRequired\": 2\n          }\n        ]\n      }\n    ]\n  },\n\
  \  {\n    \"sortOrder\": 2,\n    \"gradeCode\": \"TG2\",\n    \"gradeTitle\": \"\
  Private Helicopter 1 to 3 Pax\",\n    \"pricingMatrix\": [\n      {\n        \"\
  sortOrder\": 1,\n        \"pricingUnit\": \"per helicopter\",\n        \"bookingDate\"\
  : \"2018-06-01\",\n        \"ageBandPrices\": [\n          {\n            \"bandId\"\
  : 1,\n            \"prices\": [\n              {\n                \"sortOrder\"\
  : 1,\n                \"currencyCode\": \"USD\",\n                \"price\": 2047.41,\n\
  \                \"priceFormatted\": \"$2,047.41\",\n                \"merchantNetPrice\"\
  : 1744.4,\n                \"merchantNetPriceFormatted\": \"$1,744.40\",\n     \
  \           \"minNoOfTravellersRequiredForPrice\": 1\n              },\n       \
  \       {\n                \"sortOrder\": 2,\n                \"currencyCode\":\
  \ \"USD\",\n                \"price\": 2047.41,\n                \"priceFormatted\"\
  : \"$2,047.41\",\n                \"merchantNetPrice\": 0,\n                \"merchantNetPriceFormatted\"\
  : \"$0.00\",\n                \"minNoOfTravellersRequiredForPrice\": 2\n       \
  \       }\n            ],\n            \"sortOrder\": 1,\n            \"minimumCountRequired\"\
  : 1,\n            \"maximumCountRequired\": 3\n          }\n        ]\n      }\n\
  \    ]\n  }\n]\n```\n\n##### Interpretation\n| Travelers | Vehicle type | Price\
  \ per helicopter | Price per person |\n|:----------:|--------------|:--------------------:|:----------------:|\n\
  | 1 | 1-2-person helicopter | $1,714.83 | $1,714.83 |\n| 2 | 1-2-person helicopter\
  \ | $1,714.83 | $857.415 |\n| 3 | 1-3-person helicopter | $2,047.41 | $682.47 |\n\
  \n#### Per-bike pricing\n\n##### Request object\n```javascript\n{\n  \"productCode\"\
  : \"17448P8\",\n  \"currencyCode\": \"USD\",\n  \"month\": \"08\",\n  \"year\":\
  \ \"2018\"\n}\n```\n\n#### Response snippet\n```javascript\n\"pricingMatrix\": [\n\
  \  {\n    \"sortOrder\": 1,\n    \"pricingUnit\": \"per bike\",\n    \"bookingDate\"\
  : \"2018-06-01\",\n    \"ageBandPrices\": [\n      {\n        \"bandId\": 1,\n \
  \       \"prices\": [\n          {\n            \"sortOrder\": 1,\n            \"\
  currencyCode\": \"USD\",\n            \"price\": 208.53,\n            \"priceFormatted\"\
  : \"$208.53\",\n            \"merchantNetPrice\": 177.67,\n            \"merchantNetPriceFormatted\"\
  : \"$177.67\",\n            \"minNoOfTravellersRequiredForPrice\": 1\n         \
  \ },\n          {\n            \"sortOrder\": 2,\n            \"currencyCode\":\
  \ \"USD\",\n            \"price\": 208.53,\n            \"priceFormatted\": \"$208.53\"\
  ,\n            \"merchantNetPrice\": 0,\n            \"merchantNetPriceFormatted\"\
  : \"$0.00\",\n            \"minNoOfTravellersRequiredForPrice\": 2\n          }\n\
  \        ],\n        \"sortOrder\": 1,\n        \"minimumCountRequired\": 1,\n \
  \       \"maximumCountRequired\": 2\n      }\n    ]\n  }\n]\n```\n\n##### Interpretation\n\
  \n- \"$208.53 per bike, with up to two adults per bike\"\n\n#### Per-flight pricing\n\
  \n##### Request object\n\n```javascript\n{\n  \"productCode\": \"28965P134\",\n\
  \  \"currencyCode\": \"USD\",\n  \"month\": \"08\",\n  \"year\": \"2018\"\n}\n```\n\
  \n##### Response snippet\n\n```javascript\n\"tourGrades\": [\n  {\n    \"sortOrder\"\
  : 1,\n    \"gradeCode\": \"TG1\",\n    \"gradeTitle\": \"Individual flight\",\n\
  \    \"pricingMatrix\": [\n      {\n        \"sortOrder\": 1,\n        \"pricingUnit\"\
  : \"per flight\",\n        \"bookingDate\": \"2018-06-01\",\n        \"ageBandPrices\"\
  : [\n          {\n            \"bandId\": 1,\n            \"prices\": [\n      \
  \        {\n                \"sortOrder\": 1,\n                \"currencyCode\"\
  : \"USD\",\n                \"price\": 61.01,\n                \"merchantNetPrice\"\
  : 51.98,\n                \"merchantNetPriceFormatted\": \"$51.98\",\n         \
  \       \"priceFormatted\": \"$61.01\",\n                \"minNoOfTravellersRequiredForPrice\"\
  : 1\n              }\n            ],\n            \"sortOrder\": 1,\n          \
  \  \"minimumCountRequired\": 1,\n            \"maximumCountRequired\": 1\n     \
  \     }\n        ]\n      }\n    ]\n  },\n  {\n    \"sortOrder\": 2,\n    \"gradeCode\"\
  : \"TG2\",\n    \"gradeTitle\": \"Double\",\n    \"pricingMatrix\": [\n      {\n\
  \        \"sortOrder\": 1,\n        \"pricingUnit\": \"per flight\",\n        \"\
  bookingDate\": \"2018-06-01\",\n        \"ageBandPrices\": [\n          {\n    \
  \        \"bandId\": 1,\n            \"prices\": [\n              {\n          \
  \      \"sortOrder\": 1,\n                \"currencyCode\": \"USD\",\n         \
  \       \"price\": 94.28,\n                \"merchantNetPrice\": 80.33,\n      \
  \          \"merchantNetPriceFormatted\": \"$80.33\",\n                \"priceFormatted\"\
  : \"$94.28\",\n                \"minNoOfTravellersRequiredForPrice\": 1\n      \
  \        },\n              {\n                \"sortOrder\": 2,\n              \
  \  \"currencyCode\": \"USD\",\n                \"price\": 94.28,\n             \
  \   \"merchantNetPrice\": 0,\n                \"merchantNetPriceFormatted\": \"\
  $0.00\",\n                \"priceFormatted\": \"$94.28\",\n                \"minNoOfTravellersRequiredForPrice\"\
  : 2\n              }\n            ],\n            \"sortOrder\": 1,\n          \
  \  \"minimumCountRequired\": 1,\n            \"maximumCountRequired\": 2\n     \
  \     }\n        ]\n      }\n    ]\n  }\n]\n```\n\n##### Interpretation\n\n| Travelers\
  \ | `gradeTitle` | Price per flight | Price per person |\n|:----------:|-----------|:----------------:|:----------------:|\n\
  | 1 | Individual flight | $61.01 | $61.01 |\n| 2 | Double | $94.28 | $47.14 |\n\n\
  #### Per-plane pricing\n\n##### Request object\n\n```javascript\n{\n  \"productCode\"\
  : \"14876P5\",\n  \"currencyCode\": \"USD\",\n  \"month\": \"06\",\n  \"year\":\
  \ \"2019\"\n}\n```\n\n##### Response snippet\n\n```javascript\n\"pricingMatrix\"\
  : [\n  {\n    \"sortOrder\": 1,\n    \"pricingUnit\": \"per plane\",\n    \"bookingDate\"\
  : \"2019-01-02\",\n    \"ageBandPrices\": [\n      {\n        \"bandId\": 1,\n \
  \       \"prices\": [\n          {\n            \"sortOrder\": 1,\n            \"\
  currencyCode\": \"USD\",\n            \"price\": 433.03,\n            \"priceFormatted\"\
  : \"$433.03\",\n            \"merchantNetPrice\": 391.99,\n            \"merchantNetPriceFormatted\"\
  : \"$391.99\",\n            \"minNoOfTravellersRequiredForPrice\": 1\n         \
  \ },\n          {\n            \"sortOrder\": 2,\n            \"currencyCode\":\
  \ \"USD\",\n            \"price\": 433.03,\n            \"priceFormatted\": \"$433.03\"\
  ,\n            \"merchantNetPrice\": 0,\n            \"merchantNetPriceFormatted\"\
  : \"$0.00\",\n            \"minNoOfTravellersRequiredForPrice\": 2\n          }\n\
  \        ],\n        \"sortOrder\": 1,\n        \"minimumCountRequired\": 1,\n \
  \       \"maximumCountRequired\": 3\n      }\n    ]\n  }\n]\n```\n\n##### Interpretation\n\
  - \"$433.03 per group of up to three people\"\n\n## Working with age bands\n\n###\
  \ Age bands\n\nThe available age bands for a product, such as *adult*, *child*,\
  \ *infant*, etc., are returned by the [/product](#operation/product) service. The\
  \ customer can select a different number of people from each age band during the\
  \ price check and checkout process.\n\n### Why have age bands?\n\nTour and experience\
  \ product operators can set different prices for (and impose different rules on)\
  \ those wishing to make a booking for their product according to how old they are.\
  \ \n\nFor example, suppliers might choose to charge people 18 years and older ('adults')\
  \ the full ticket price, while 'children' can book at a lower price. \n\nOr, the\
  \ tour operator may only allow children to make a group booking for the tour so\
  \ long as the group contains 'at least one adult'.\n\nViator provides five categories\
  \ (age bands) that product operators can use to segregate travelers into age groups\
  \ (the limits of which they also define) in order to set pricing and traveler-count\
  \ participation rules for their product according to the age band categories.\n\n\
  ### Supported age band categories\n\nThe age bands supported by the Viator API are\
  \ as follows:\n\n| `bandId` | Description |\n|:------:|-------|\n| **1** | Adult\
  \ |\n| **2** | Child |\n| **3** | Infant |\n| **4** | Youth |\n| **5** | Senior\
  \ |\n\nThe names and corresponding numeric identifiers of these categories are fixed\
  \ as in the table above (i.e., `1` is always `Adult`); however, the exact age range\
  \ to which each category pertains must be defined manually by the supplier.\n\n\
  The maximum and minimum ages that each age band describes for each product can be\
  \ retrieved from the [/product](#operation/product) service.\n\n### Example of age\
  \ band definitions\n\nFor example, a call to [/product](#operation/product) regarding\
  \ `10040WORLD` yields the following `ageBands` array within its response object:\n\
  \n```javascript\n\"ageBands\": [\n  {\n    \"sortOrder\": 1,\n    \"ageFrom\": 13,\n\
  \    \"ageTo\": 64,\n    \"adult\": true,\n    \"bandId\": 1,\n    \"pluralDescription\"\
  : \"Adults\",\n    \"treatAsAdult\": true,\n    \"count\": 0,\n    \"description\"\
  : \"Adult\"\n  },\n  {\n    \"sortOrder\": 2,\n    \"ageFrom\": 65,\n    \"ageTo\"\
  : 99,\n    \"adult\": false,\n    \"bandId\": 5,\n    \"pluralDescription\": \"\
  Seniors\",\n    \"treatAsAdult\": true,\n    \"count\": 0,\n    \"description\"\
  : \"Senior\"\n  },\n  {\n    \"sortOrder\": 3,\n    \"ageFrom\": 4,\n    \"ageTo\"\
  : 12,\n    \"adult\": false,\n    \"bandId\": 2,\n    \"pluralDescription\": \"\
  Children\",\n    \"treatAsAdult\": false,\n    \"count\": 0,\n    \"description\"\
  : \"Child\"\n  },\n  {\n    \"sortOrder\": 4,\n    \"ageFrom\": 0,\n    \"ageTo\"\
  : 3,\n    \"adult\": false,\n    \"bandId\": 3,\n    \"pluralDescription\": \"Infants\"\
  ,\n    \"treatAsAdult\": false,\n    \"count\": 0,\n    \"description\": \"Infant\"\
  \n  }\n```\n\nFor this product, the age bands have been defined as follows:\n\n\
  | `bandId` | `description` | `ageFrom` | `ageTo` |\n|:--------:|:-----------:|:-------:|:-----:|\n\
  | **1** | Adult | 13 | 64 |\n| **5** | Senior | 65 | 99 |\n| **2** | Child | 4 |\
  \ 12 |\n| **3** | Infant | 0 | 3 |\n\nProduct operators must define at least one\
  \ age band for their tour, and there are no 'default' age ranges. Therefore, if\
  \ the product operator has only specified a single 'adult' age band covering ages\
  \ 18-99, it must be assumed that only people aged 18-99 are eligible to book the\
  \ tour, essentially excluding children and centenarians in this case.\n\n| Field\
  \ | Type | Definition |\n|-------|------|------|\n| `sortOrder` | integer | the\
  \ sort order for *this* age band |\n| `adult` | boolean | `true` if this age band\
  \ is the 'adult' age band |\n| `treatAsAdult` | boolean | `true` if this age band\
  \ can book the tour without the need for adult accompaniment |\n\n**Note**: `bandId`\
  \ must be supplied in the request body of the following services:\n\n- [/booking/availability](#operation/bookingAvailability)\n\
  - [/booking/availability/tourgrades](#operation/bookingAvailabilityTourgrades)\n\
  - [/booking/calculateprice](#operation/bookingCalculateprice)\n- [/booking/book](#operation/bookingBook)\n\
  \nAge bands are referenced by their `bandId` in the responses from the following\
  \ services:\n\n- [/product](#operation/product)\n- [/booking/availability/tourgrades](#operation/bookingAvailabilityTourgrades)\n\
  - [/booking/availability/tourgrades/pricingmatrix](#operation/bookingAvailabilityTourgradesPricingmatrix)\n\
  - [/booking/book](#operation/bookingBook)\n- [/booking/pastbooking](#operation/bookingPastbooking)\n\
  - [/booking/mybookings](#operation/bookingMybookings)\n- [/booking/calculateprice](#operation/bookingCalculateprice)\n\
  \n## How to report a product issue\n\nOccasionally, a product schema in the Viator\
  \ database will contain incorrect or invalid information. Usually, this occurs due\
  \ to a mistake made by the supplier of the product when creating the product or\
  \ updating its details.\n\nNonetheless, it's in all our best interests for product\
  \ information to be accurate and up-to-date; therefore, if you discover a problem\
  \ with a product, we would greatly appreciate it if you could report the error through\
  \ our [product issue reporting form](https://www.tfaforms.com/433240).\n\n### How\
  \ to use the product issue reporting form\n\n1. Navigate to the [product issue reporting\
  \ page](https://www.tfaforms.com/433240)\n2. Fill in the **Reporter**, **Supplier\
  \ ID**, **Product Code** and **Booking ID** fields:\n\n| Field | How to fill it\
  \ in | Example |\n|-------|-------------------|---------|\n| Reporter | Enter your\
  \ email address for tracking or correspondence | `you@emailserver.com` |\n| Supplier\
  \ ID | Enter the value returned in the `supplierCode` field by the [/product](#operation/product)\
  \ service for the product in question. | `3072` |\n| Product Code | Enter the value\
  \ returned in the `code` field by the [/product](#operation/product) service for\
  \ the product in question. | `3072LASALL` |\n| Booking ID | Leave this field blank\
  \ | |\n\n3. In the **Reason** box below, choose **Content** by clicking on its radio\
  \ selector. A list of categories will appear, with meanings as follows:\n\n| Category\
  \ | Included issues | \n|----------|---------|\n| Additional Info | clauses in the\
  \ `additionalInfo` array in the response from [/product](#operation/product); e.g.,\
  \ departure time or hotel pick-up information |\n| Availability &amp; Blockouts\
  \ | N/A |\n| Booking Details | N/A |\n| Highlights | `highlights` array items in\
  \ the response from [/product](#operation/product) |\n| Inclusions / Exclusions\
  \ | `inclusions` or `exclusions` array items in the response from [/product](#operation/product)\
  \ |\n| Images | `productPhotos` and `userPhotos` returned by [/product](#operation/product)\
  \ or [/product/photos](#operation/productPhotos) |\n| Product Title | `title` in\
  \ the response from [/product](#operation/product), [/search/products](#operation/searchProducts),\
  \ [/search/products/codes](#operation/searchProductsCodes) and [/search/products/freetext](#operation/searchFreetext)\
  \ |\n| Product Descriptions | `description` and `shortDescription` in the response\
  \ from [/product](#operation/product)|\n| SAPI | N/A |\n| Tour Options &amp; Pricing\
  \ | pricing issues; e.g. when the value of `merchantNetPrice` is `0`; or, if `merchantNetPrice`\
  \ &gt; `price` |\n| Taxonomy | &lt;ul&gt;&lt;li&gt;destination issues in response\
  \ from [/taxonomy/destination](#operation/taxonomyDestinations)&lt;/li&gt;&lt;li&gt;category\
  \ / subcategory issues in response from [/taxonomy/categories](#operation/taxonomyCategories)&lt;/li&gt;&lt;/ul&gt;\
  \ |\n| Translation Incorrect | mistakes in any natural-language field in the response\
  \ from any service where `translationLevel` is non-zero |\n| TVRM | N/A |\n| VUC\
  \ incorrect | N/A |\n\n4. After selecting the category of issue from the options\
  \ shown, fill-in the **Description / Action Required** box with a good, clear description\
  \ of the problem and any specific additional actions you would like us to take\n\
  5. Click **Submit** to send the report\n\n&lt;figure&gt;\n    &lt;img src=\"https://docs.viator.com/partner-api/resources/merchant/technical/img/tae-report-a-product-issue.jpg\"\
  \ alt=\"Tripadvisor experiences report a product form\"/&gt;\n    &lt;figcaption&gt;Example\
  \ Report a Product Issue form&lt;/figcaption&gt;\n&lt;/figure&gt;\n\nOnce your report\
  \ has been submitted, a member of our Supplier Support Team will contact the supplier\
  \ of the product in question to resolve any problems with their listing.\n\n## Selling\
  \ on-request products\n\nThis section explains what merchant API partners need to\
  \ do in order to be granted access to (and, ultimately, sell) the many on-request\
  \ products available in Viator's product catalogue.\n\n### 'Freesale' vs 'on-request'\
  \ products\n\nAmong the products in our inventory, a major differentiating feature\
  \ is whether they are 'freesale' or 'on-request':\n\n- **Freesale** products are\
  \ always available to be booked on their days of operation; therefore, when a freesale\
  \ product is purchased, the booking is confirmed and the customer is charged immediately.\n\
  - **On-request** products only operate at the discretion of the supplier, who must\
  \ confirm (or reject) each booking request, which will remain 'pending' in the interim.\
  \ The customer is only charged once confirmation is received.\n\n#### Access to\
  \ on-request products\n\nBy default, you will only have access to the freesale product\
  \ range; access to the on-request product range is restricted on account of the\
  \ extra complexities involved with handling this kind of booking.\n\n### Should\
  \ I elect to sell on-request products?\n\n#### Business case for including on-request\
  \ products in your inventory\n\nWhile the majority of products in our inventory\
  \ are 'freesale', a significant proportion remain 'on-request'. Upgrading your booking\
  \ platform to support on-request products can lead to an increase in revenue of\
  \ between 5% and 13%, depending on the locale(s) in which you operate.\n\n| Locale\
  \ | Revenue increase % |\n|:------:|:------------------------:|\n| en | 8% |\n|\
  \ es | 8% |\n| fr | 11% |\n| de | 10% |\n| pt | 5% |\n| nl | 12% |\n| it | 10% |\n\
  | ja | 10% |\n| sv | 8% |\n| no | 8% |\n| da | 13% |\n| tw | 13% |\n| zh | 6% |\n\
  \nHaving a wider range of products on offer can be a key differentiator with respect\
  \ to your competitors. \n\nCustomers often purchase multiple products in the same\
  \ session – if the product they're looking for isn't available on your platform,\
  \ they are likely to seek a competitor with a more complete range of products for\
  \ sale.\n\n#### Logistical considerations to enable on-request products\n\nIn order\
  \ to sell on-request products, you will need to:\n\n- Modify your back-end systems\
  \ to support extra logic and API requests\n- Establish and support an extra, email-based\
  \ communications channel with your customers\n- Create some email templates\n- Modify\
  \ your platform's front end to accommodate the extra steps required in the booking\
  \ process\n- Write copy that ensures customers clearly understand that they are\
  \ booking a product that will not be confirmed or charged immediately\n\nHowever,\
  \ as the on-request booking confirmation process is fully automated, you will not\
  \ need to:\n\n- Undertake any additional manual steps compared with booking a freesale\
  \ product\n- Personally contact the product supplier or our partner support team\n\
  \nInstead, checking the status of bookings (whether confirmed or not) can be accomplished\
  \ using the [/booking/status](#operation/bookingStatus) and [/booking/status/items](#operation/bookingStatusItems)\
  \ services. These services can be polled periodically to determine the confirmation\
  \ status of your bookings.\n\n&lt;u&gt;**Note**&lt;/u&gt;: We recommend using the\
  \ [/booking/status/items](#operation/bookingStatusItems) service to poll for booking\
  \ statuses, as it is both faster and can be polled more frequently than [/booking/status](#operation/bookingStatus),\
  \ which can only be polled once every thirty minutes.\n\n### How to support on-request\
  \ products\n\n#### Product detail page\n\nManaging customer expectations is a key\
  \ factor in supporting on-request products on your booking platform. \n\nMake clear\
  \ mention that this is a product for which confirmation will not be received immediately,\
  \ but rather within 48 hours of making the booking.\n\nThis fact, as well as other\
  \ pertinent tidbits, can be found in the `additionalInfo` array in the response\
  \ from **/product**. It is mandatory that all clauses in the `additionalInfo` array\
  \ are clearly displayed on your product detail page.\n\n&lt;figure&gt;\n    &lt;img\
  \ src=\"https://docs.viator.com/partner-api/resources/merchant/technical/img/additional-info-on-request-clause.jpg\"\
  \ alt=\"Additional info displayed on a product page on the Viator site\"/&gt;\n\
  \    &lt;figcaption&gt;Additional info displayed on a product page on the Viator\
  \ site\n     &lt;/figcaption&gt;\n&lt;/figure&gt;\n\n#### Check-out\n\nAs you will\
  \ only charge the customer's credit card once the on-request booking is confirmed\
  \ (i.e., after we have received confirmation of the booking from the product supplier)\
  \ it's best to display a message to this effect at a prominent point of the check-out\
  \ flow for all on-request products.\n\n&lt;figure&gt;\n    &lt;img src=\"https://docs.viator.com/partner-api/resources/merchant/technical/img/checkout-flow-confirmation-info.jpg\"\
  \ alt=\"Example checkout-flow instruction on the Viator site\"/&gt;\n    &lt;figcaption&gt;Example\
  \ checkout-flow instruction on the Viator site&lt;/figcaption&gt;\n&lt;/figure&gt;\n\
  \nIn this way, customers can be reassured that they are not being charged for a\
  \ booking that may never be confirmed, thereby minimizing needless calls to your\
  \ customer service team.\n\n#### Combination purchases\n\nIf a single booking includes\
  \ both freesale (instantly confirmed) and on-request products, only the amount for\
  \ the freesale product should be charged immediately; the portion corresponding\
  \ to the on-request booking should only be charged once confirmation is received.\
  \ \n\nUntil that time, a pre-authorization should be held against the customer’\
  s credit card until confirmation is received.\n\nIt is important that you clearly\
  \ differentiate between products that are confirmed and those that are pending confirmation,\
  \ and communicate the status of each and that the pre-authorization will only finalize\
  \ once the on-request products are confirmed.\n\n#### Confirmation page\n\nChanges\
  \ will need to be made to your confirmation page because it will not be possible\
  \ for your customer to download a voucher after completing an on-request booking.\n\
  \nVouchers for freesale products, however, must be made available immediately following\
  \ the completion of the booking process.\n\n#### Email communications\n\nYou will\
  \ need to create email templates for &lt;u&gt;all&lt;/u&gt; the following scenarios:\n\
  \n- Confirmation emails for bookings with on-request products should indicate that\
  \ the item is pending confirmation from the supplier; and, that confirmation for\
  \ this activity will take up to 48 hours, depending on availability.\n- If the on-request\
  \ booking is confirmed by the supplier (this time including the voucher details)\n\
  - If the on-request booking is rejected\n- If multiple on-request products have\
  \ been booked:\n    + If all items have been accepted/confirmed\n    + If all items\
  \ were rejected\n    + If there is a mixture of acceptance and rejection; i.e.,\
  \ 'pending' + 'rejected' + 'cancelled' + 'amended' and so forth.\n- If a mixture\
  \ of freesale and on-request products are booked at the same time; i.e., in the\
  \ same cart or booking\n\n&lt;u&gt;**Note**&lt;/u&gt;: When a booking is declined,\
  \ it is useful to mention that the customer's card was not charged.\n\n##### Example\
  \ email for an on-request booking pending confirmation:\n\n&lt;figure&gt;\n    &lt;img\
  \ src=\"https://docs.viator.com/partner-api/resources/merchant/technical/img/on-request-confirmation-email-1.jpg\"\
  \ alt=\"Viator website showing translation attribution\"/&gt;\n    &lt;img src=\"\
  https://docs.viator.com/partner-api/resources/merchant/technical/img/on-request-confirmation-email-2.jpg\"\
  \ alt=\"Viator website showing translation attribution\"/&gt;\n    &lt;img src=\"\
  https://docs.viator.com/partner-api/resources/merchant/technical/img/on-request-confirmation-email-3.jpg\"\
  \ alt=\"Viator website showing translation attribution\"/&gt;\n&lt;/figure&gt;\n\
  \n### Confirmation time-outs resulting in rejection\n\nAs mentioned above, once\
  \ a booking for an on-request product is made, it remains in a 'pending' state,\
  \ awaiting confirmation by the supplier. The supplier has the option of 'confirming'\
  \ or 'rejecting' the booking.\n\nSuch bookings will not remain 'pending' indefinitely,\
  \ however. If the supplier has not confirmed the booking within 72 hours –&nbsp;or\
  \ if they have not confirmed the booking by the time it reaches 24 hours from departure\
  \ – our systems will automatically reject the booking, and this will be reflected\
  \ in the response from the [/booking/status/items](#operation/bookingStatusItems)\
  \ and [/booking/status](#operation/bookingStatus) services.\n\nThere will be no\
  \ indication that the rejection occurred on account of the supplier being unable\
  \ to perform their duties. Therefore, you should simply inform the customer that,\
  \ for reasons out of your control, this on-request tour was unavailable.\n\n###\
  \ Building in the sandbox environment\n\nUpgrading your booking platform to support\
  \ on-request products will require you to build and test this functionality in the\
  \ sandbox environment. However, as no actual booking requests are made with the\
  \ supplier when using a sandbox-only API-key, you will need to contact our API tech\
  \ support team at [apitechsupport@viator.com](mailto:apitechsupport@viator.com)\
  \ and request that the booking be confirmed or rejected as you require.\n\nWhile\
  \ necessary, this is a manual process. We'd genuinely appreciate your effort in\
  \ keeping the number of these requests to a minimum.\n\n### Certification and going\
  \ live\n\nOnce you have completed all tasks mentioned here and sent your Viator\
  \ account manager the email copy for the different scenarios [described above](#email-communications),\
  \ we will change the status of your product API-key to include on-request products.\n\
  \n## Localization and translation\n\n### Foreign language products\n\nThe products\
  \ available through the Viator API have been created in a variety of languages,\
  \ often by the suppliers of those products themselves. \n\nAlthough the majority\
  \ of these have been created in English, many have been created in other languages.\
  \ For example, a tour that operates in Paris might have been created in French.\n\
  \nViator provides translation services to localize product descriptions to the language\
  \ of the locale in which they are being presented. In this way, products with descriptions\
  \ – for example, in French – can be displayed in English on English-language websites.\
  \ Conversely, products with English-language-descriptions can be displayed in French\
  \ on French-language websites.\n\n * **Note**: product descriptions are translated\
  \ into the language specified in the `Accept-Language` header parameter in the request\
  \ to each endpoint. \n\n### Human and machine translation\n\nSome products have\
  \ been translated by actual humans – 'human translated' –  while others have been\
  \ automatically translated using Google Translate – 'machine translated'.\n\nThe\
  \ type of translation that has been applied to a product (if any) is indicated by\
  \ its `translationLevel`, a numeric specifer with meanings as follows:\n\n| `translationLevel`\
  \ | Meaning |\n|-----------------|---------|\n| `0` | The product was created by\
  \ the supplier in the language you specifed using the `Accept-Language` header parameter\
  \ in the request; i.e., the natural-language text in this response has not been\
  \ translated |\n| `80` | All product information has been &lt;u&gt;machine translated&lt;/u&gt;\
  \ |\n| `90` or `100` | All product information has been &lt;u&gt;human translated&lt;/u&gt;\
  \ |\n\nTherefore, any product with a non-zero `translationLevel` has been translated\
  \ either by a human or via an automatic process.\n\nThe `translationLevel` field\
  \ is returned in the response objects from the following services:\n\n* [/search/products](#operation/searchProducts)\n\
  * [/search/products/codes](#operation/searchProductsCodes)\n* [/search/freetext](#operation/searchFreetext)\n\
  * [/product](#operation/product)\n* [/available/products](#operation/availableProducts)\n\
  \nWhen performing a product search using any of these services, you will receive\
  \ - by default - products with a `translationLevel` of:\n\n* `0` (products that\
  \ are in the language you specified in `Accept-Language` and are configured for\
  \ your API-keys), and\n* `90` or `100` (products that have been &lt;u&gt;fully human\
  \ translated&lt;/u&gt;)\n\n### Accessing machine-translated products\n\nIf your\
  \ implementation can support the large number of products available that are machine\
  \ translated, you can.\n\nHowever, access to the considerable volume of machine-translated\
  \ products (level `80`), is &lt;u&gt;not granted by default&lt;/u&gt;.\n\nTo access\
  \ machine-translated products, you will need to: \n\n1. Request access to machine-translated\
  \ products in sandbox from your Business Development account manager.\n2. Test your\
  \ site with sandbox to ensure that you can download and display all the available\
  \ content.\n3. Have your Business Development account manager review your implementation\
  \ and grant access in the production environment.\n\n## Merchant pricing\n\nMany\
  \ of the endpoints in the Viator API return pricing information. Due to the necessity\
  \ of supporting legacy implementations, some pricing fields may not be named in\
  \ an intuitive way.\n\nThis section seeks to clarify what each of the pricing fields\
  \ returned by each endpoint actually refer to and how you need to use this information\
  \ in your implementation.\n\n### Categories of pricing\n\n| Category | Meaning |\n\
  |----------|---------|\n| **Suggested retail price** | The recommended retail price\
  \ for the product and the price that the product is sold at on the Viator site |\n\
  | **Merchant net rate** | The amount that Viator will invoice the merchant for this\
  \ sale, **excluding the transaction fee** |\n| **Merchant total price** | The total\
  \ amount that Viator will invoice the merchant for this sale, **including the transaction\
  \ fee** |\n\n| Service | Suggested retail price | Merchant net rate |\n|---------|------------------------|-------------------|\n\
  | [/search/products](#operation/searchProducts) | `price`, `priceFormatted` | `merchantNetPriceFrom`,\
  \ `merchantNetPriceFromFormatted` |\n| [/product](#operation/product) | `price`,\
  \ `priceFormatted`, `priceFrom`, `priceFromFormatted` | `merchantNetPriceFrom`,\
  \ `merchantNetPriceFromFormatted` |\n| [/booking/availability](#operation/bookingAvailability)\
  \ | `retailPrice`, `retailPriceFormatted` | `merchantNetPrice`, `merchantNetPriceFormatted`\
  \ |\n| [/booking/availability/tourgrades](#operation/bookingAvailabilityTourgrades)\
  \ | `retailPrice`, `retailPriceFormatted` | `merchantNetPrice`, `merchantNetPriceFormatted`\
  \ |\n| [/booking/availability/tourgrades/pricingmatrix](#operation/bookingAvailabilityTourgradesPricingmatrix)\
  \ | `price`, `priceFormatted` | `merchantNetPrice`, `merchantNetPriceFormatted`\
  \ |\n| [/booking/book](#operation/bookingBook) | N/A | `merchantNetPrice`, `merchantNetPriceFormatted`,\
  \ `lastRetailPrice`, `lastRetailPriceFormatted` |\n| [/booking/pricingmatrix](#operation/bookingPricingmatrix)\
  \ | `price`, `priceFormatted` | `merchantNetPrice`, `merchantNetPriceFormatted`\
  \ |\n| [/booking/calculateprice](#operation/bookingCalculateprice) | N/A | `merchantNetPrice`,\
  \ `merchantNetPriceFormatted`, `lastRetailPrice`, `lastRetailPriceFormatted`, `itineraryFromPrice`,\
  \ `itineraryFromPriceFormatted`, `itineraryNewPrice`, `itineraryNewPriceFormatted`\
  \ |\n| [/booking/pastbooking](#operation/bookingPastbooking) | N/A | `merchantNetPrice`,\
  \ `merchantNetPriceFormatted`, `lastRetailPrice`, `lastRetailPriceFormatted`,  |\n\
  | [/booking/mybookings](#operation/bookingMybookings) | N/A | `merchantNetPrice`,\
  \ `merchantNetPriceFormatted`, `lastRetailPrice`, `lastRetailPriceFormatted` |\n\
  \nThe following services return the **merchant total price** (i.e., the merchant\
  \ net rate + transaction fee) in the fields shown:\n\n| Service | Merchant total\
  \ price fields |\n|---------|-----------------------------|\n| [/booking/book](#operation/bookingBook)\
  \ | `price`, `priceFormatted`, `totalPrice`, `totalPriceFormatted`, `priceUSD`,\
  \ `totalPriceUSD` |\n| [/booking/calculateprice](#operation/bookingCalculateprice)\
  \ | `price`, `priceFormatted`, `priceUSD`, `totalPrice`, `totalPriceFormatted`,\
  \ `totalPriceUSD` |\n| [/booking/pastbooking](#operation/bookingPastbooking) | `price`,\
  \ `priceFormatted`, `totalPrice`, `totalPriceFormatted`, `priceUSD`, `totalPriceUSD`,\
  \ |\n| [/booking/mybookings](#operation/bookingMybookings) | `price`, `priceFormatted`,\
  \ `priceUSD`, `totalPrice`, `totalPriceFormatted`, `totalPriceUSD` |\n\n### Using\
  \ the pricing fields\n\nLet's have a look at the various pricing fields for a specific\
  \ product - the Grand Canyon All-American Helicopter Tour (product code: 2280AAHT).\n\
  \nA search for this product (at the time of writing) on the Viator.com site gives\
  \ the 'from' price of the tour as **$601.11**:\n\n&lt;figure&gt;\n    &lt;img src=\"\
  https://docs.viator.com/partner-api/resources/merchant/technical/img/suggested-retail-price.jpg\"\
  \ alt=\"'from' price on viator.com product detail page\"/&gt;\n    &lt;figcaption&gt;Retail\
  \ price shown on viator.com&lt;/figcaption&gt;\n&lt;/figure&gt;\n\nThis value comes\
  \ from the `price` or `priceFormatted` fields in the response from [/product](#operation/product)\
  \ for this tour; i.e.,:\n\n```javascript\n{\n  ...,\n  \"price\": 601.11,\n  \"\
  priceFormatted\": \"$601.11\",\n  ...\n}\n```\n\nEssentially, this value is the\
  \ price that the product is sold at on the viator site, and is therefore the **suggested\
  \ retail price**; i.e., the price at which we recommend you advertise and sell the\
  \ product for.\n\nIt is also the price of the tour grade with the lowest price;\
  \ in this case, the \"Earlybird A-Star\" tour grade detailed here:\n\n```javascript\n\
  {\n    \"sortOrder\": 5,\n    \"currencyCode\": \"AUD\",\n    \"langServices\":\
  \ {\n        \"en/SERVICE_AUDIO\": \"English - Audio\"\n    },\n    \"gradeCode\"\
  : \"EB_ASTAR_SP\",\n    \"merchantNetPriceFrom\": 555.37,\n    \"priceFrom\": 601.11,\n\
  \    \"priceFromFormatted\": \"$601.11\",\n    \"merchantNetPriceFromFormatted\"\
  : \"$555.37\",\n    \"gradeTitle\": \"Special: Earlybird A-Star\",\n    \"gradeDepartureTime\"\
  : \"\",\n    \"gradeDescription\": \"Special Offer: Receive a discounted seat for\
  \ the Grand Canyon All American Helicopter Tour departing between 6:45am and 7am\
  \ on an A-Star helicopter\",\n    \"defaultLanguageCode\": \"en\"\n},\n```\n\nAs\
  \ you can see, the \"suggested retail price\" is given in the `priceFrom` field.\n\
  \n#### Low and zero-margin products\n\nWhen setting the retail price at which you\
  \ sell products on your site, it’s important to remember that the “suggested sell\
  \ price” is the price at which the product is currently advertised on the Viator\
  \ site and reflects the current standard industry price for the product. It &lt;u&gt;does\
  \ not&lt;/u&gt; take into consideration the merchant net price (i.e., the price\
  \ at which you as a merchant partner will be invoiced for the sale) and, in the\
  \ case of discounting scenarios, may in fact be less than the merchant net price.\n\
  \nTherefore, to ensure that you sell the product at a price which guarantees that\
  \ you receive at least as much as you will be invoiced for, as well as any extra\
  \ profit margin that you desire to generate, we recommend you include a check in\
  \ your implementation that these requirements are satisfied by comparing the suggested\
  \ retail and merchant net prices and adjusting the retail price at which you advertise\
  \ the product accordingly.\n\nFor example, if the merchant net price for a product\
  \ is $100, the suggested sell price is $101, and your requirement for a minimum\
  \ margin is 5%, you should adjust the price at which you advertise the product to\
  \ $105.\n\nWhile we recommend that you charge your customers this amount, it is\
  \ ultimately up to you as to the price you set for the product, bearing in mind\
  \ that  Viator will then invoice you for the **merchant net rate** (`merchantNetPriceFrom`)\
  \ of $555.37 &lt;u&gt;plus&lt;/u&gt; a **transaction fee** calculated as a percentage\
  \ of the net rate; i.e., the **merchant total price**. \n\n**The exact value of\
  \ this transaction fee is detailed in your contract with Viator.**\n\n## Special\
  \ offers and on-sale pricing\n\nSuppliers have the option of setting special pricing\
  \ deals for their products. When a product is 'on sale'; i.e., has a temporarily\
  \ lowered price, it will be reflected in the product content response, as follows:\n\
  \n| Field name | Standard pricing | Special offer / on-sale pricing |\n|------------|----------------|-------------------------|\n\
  | `specialOfferAvailable` | `false` | `true` |\n| `specialOffer` | `\"\"` (empty\
  \ string) | e.g.: `\"Book by February 28 to save 10%\"` |\n| `rrp` | `0.0` | pre-discount\
  \ price |\n| `rrpFormatted` | `\"\"` (empty string) | currency-formatted pre-discount\
  \ price |\n| `price` | standard price | special offer price |\n| `priceFormatted`\
  \ | currency-formatted **standard price** | currency-formatted **special-offer price**\
  \ |\n| `merchantNetPriceFrom` | standard merchant net rate | special offer merchant\
  \ net rate |\n| `merchantNetPriceFromFormatted` | currency formatted standard merchant\
  \ net rate | currency formatted special offer merchant net rate |\n| `priceFormatted`\
  \ | currency-formatted **standard price** | currency-formatted **special-offer price**\
  \ |\n| `priceFrom` (in `tourgrades`) | standard price | special offer price |\n\
  | `priceFromFormatted` (in `tourgrades`) | currency-formatted **standard price**\
  \ | currency-formatted **special-offer price** |\n\nYou can use this information\
  \ to highlight which products are on special and provide details to the user about\
  \ the special offer.\n\n## Supplier communications\n\n### How can suppliers communicate\
  \ with end customers?\n\nSuppliers occasionally need to reach out to customers for\
  \ a variety of reasons, such as:\n\n* Requesting pick-up locations, flight details\
  \ or passenger weight information\n* Providing weather alerts, sold-out notifications\
  \ or general messaging\n\nTo allow suppliers to contact customers directly, Viator\
  \ provides a **Closed Loop Communication (CLC)** system. \n\n### How to enable CLC\n\
  \nCLC is enabled per-booking and at the time of booking by supplying the customer’\
  s `email` and either `homePhone` or [`cellphone` + `cellPhoneCountryCode`] – or\
  \ both – in the `booker` object in the request body sent to the [/booking/book](#operation/bookingBook)\
  \ service when making a booking.\n\nThis will allow suppliers to send CLC messages\
  \ directly to the end customer.\n\n#### Note:\n\n* You will receive a CC of each\
  \ supplier message to your customer support email address in case further assistance\
  \ is required, but no action from your support team will be necessary for suppliers\
  \ to communicate with customers.\n\n* Merchants choosing this option should mention\
  \ to their customers that they are purchasing a product from a third-party supplier,\
  \ and that they may therefore receive communications regarding the purchase directly\
  \ from that supplier. \n\n#### Example request body snippet to enable direct CLC\n\
  ```javascript\n{\n    ...\n    \"booker\": {\n        \"homePhone\": \"(02)66987564\"\
  ,\n        \"firstname\": \"Homer Test\",\n        \"surname\": \"Simpson Test\"\
  ,\n        \"title\": \"Mr\",\n        \"cellPhoneCountryCode\": \"61\",\n     \
  \   \"cellPhone\": \"431532778\",\n        \"email\": \"hsimpson@customeremail.com\"\
  \n    }\n    ...\n}\n```\n\n### Supplier communications without CLC\n\nTo have CLCs\
  \ from the supplier sent &lt;u&gt;only&lt;/u&gt; to your (the merchant's) customer\
  \ support team:\n\n* Leave the `cellPhone`, `cellPhoneCountryCode` and `homePhone`\
  \ fields blank in the request to the [/booking/book](#operation/bookingBook) service\
  \ when making a booking.\n\n**Note:** Utilizing this option requires merchants to\
  \ manage the final loop of communication with the end customer to ensure that their\
  \ tour/activity can be fulfilled successfully.\n\n## Cancellation policy\n\nAs well\
  \ as *making* bookings, merchant partners are also able to *cancel* bookings through\
  \ the Viator API using the [/bookings/cancel-reasons](#operation/cancellationReasons),\
  \ [/bookings/{booking-ref}/cancel-quote](#operation/cancelBookingQuote) and [/bookings/{booking-ref}/cancel](#operation/cancelBooking)\
  \ endpoints. Items cancelled via the [/bookings/{booking-ref}/cancel](#operation/cancelBooking)\
  \ endpoint will be cancelled in full, and only one booking can be cancelled at a\
  \ time.\n\nFor more information about the content of the new `merchantTermsAndConditions`\
  \ object, see [Cancellation policy](#section/Key-concepts/Cancellation-policy).\n\
  \n\n### Cancellation policies\n\nAll products can be cancelled by the merchant;\
  \ however, the refund granted by the supplier to the customer differs depending\
  \ on the cancellation policy for the product in question.\n\nThere are &lt;u&gt;three&lt;/u&gt;\
  \ cancellation policy categories, **standard**, **custom** and **all sales final**,\
  \ represented by an integer in the `merchantTermsAndConditionsType` field in the\
  \ `merchantTermsAndConditions` object returned by [/product](#operation/product):\
  \ `1`, `2` or `3`, respectively.\n\n**Note:** *These policies are those provided\
  \ by Viator to our merchant partners. Merchants can choose whether to extend these\
  \ terms to their customers unchanged or set their own cancellation terms. For example,\
  \ the merchant partner can choose to make all products non-refundable; or, they\
  \ might change the full-refund cancellation window to 72 hours instead of 24 hours,\
  \ and so forth.*\n\n### `1` – Standard cancellation policy\nProducts in this category\
  \ are cancellable up to 24 hours before the travel date (local supplier time) for\
  \ a full refund. However, a &lt;u&gt;100% cancellation penalty&lt;/u&gt; applies\
  \ for cancellations submitted less than 24 hours before the start time. Most products\
  \ (about 85%) fall into this category.\n\n#### Example response snippet\n\n- **Source\
  \ endpoint**: [/product](#operation/product)\n- **Product**: `5010SYDNEY`\n\n```javascript\n\
  {\n  \"data\": {\n    \"merchantTermsAndConditions\": {\n      \"termsAndConditions\"\
  : \"For a full refund, cancel at least 24 hours in advance of the start date of\
  \ the experience.\",\n      \"merchantTermsAndConditionsType\": 1,\n      \"amountRefundable\"\
  : null,\n      \"cancellationFromTourDate\": [\n        {\n          \"dayRangeMin\"\
  : 0,\n          \"dayRangeMax\": 1,\n          \"percentageRefundable\": 0,\n  \
  \        \"policyStartTimestamp\": null,\n          \"policyEndTimestamp\": null\n\
  \        },\n        {\n          \"dayRangeMin\": 1,\n          \"dayRangeMax\"\
  : null,\n          \"percentageRefundable\": 100,\n          \"policyStartTimestamp\"\
  : null,\n          \"policyEndTimestamp\": null\n        }\n      ]\n    },\n  \
  \  \"...\": \"...\"\n  }\n}\n```\n\nThis product has the *standard* cancellation\
  \ policy; i.e., when a booking is cancelled:\n\n| Policy | **dayRangeMin** | **dayRangeMax**\
  \ | Logic | **percentageRefundable** |\n|--------|:-----------:|:-----------:|-------|:--------------------------:|\n\
  | *less than* &lt;u&gt;one&lt;/u&gt; day (24 hours) before the start time | 0 |\
  \ 1 | (product_start_time - cancellation_time) &gt;= 0 days &amp;&amp; (product_start_time\
  \ - cancellation_time) &lt; 1 days | 0 |\n| *more than* &lt;u&gt;one&lt;/u&gt; day\
  \ (24 hours) before the start time | 1 | null | (product_start_time - cancellation_time)\
  \ &gt;= 1 day | 100 |\n\n### `2` – Custom cancellation policy\nThe refund amount\
  \ for products in this category varies depending on how long before its start time\
  \ the product is cancelled. Many products on a custom policy are multi-day tours,\
  \ which require more sophisticated planning on the supplier’s end. Only a small\
  \ number of products (around 5%) fall into this category.\n\n#### Example response\
  \ snippet\n\n- **Source endpoint**: [/product](#operation/product)\n- **Product**:\
  \ `2264RJ410`\n\n```javascript\n\"data\": {\n  \"merchantTermsAndConditions\": {\n\
  \    \"termsAndConditions\": \"If you cancel at least 30 day(s) in advance of the\
  \ scheduled departure, there is no cancellation fee.&lt;br&gt;If you cancel between\
  \ 10 and 29 day(s) in advance of the scheduled departure, there is a 50 percent\
  \ cancellation fee.&lt;br&gt;If you cancel within 9 day(s) of the scheduled departure,\
  \ there is a 100 percent cancellation fee.&lt;br&gt;\",\n    \"merchantTermsAndConditionsType\"\
  : 2,\n    \"amountRefundable\": null,\n    \"cancellationFromTourDate\": [\n   \
  \   {\n        \"dayRangeMin\": 10,\n        \"dayRangeMax\": 30,\n        \"percentageRefundable\"\
  : 50,\n        \"policyStartTimestamp\": null,\n        \"policyEndTimestamp\":\
  \ null\n      },\n      {\n        \"dayRangeMin\": 30,\n        \"dayRangeMax\"\
  : null,\n        \"percentageRefundable\": 100,\n        \"policyStartTimestamp\"\
  : null,\n        \"policyEndTimestamp\": null\n      },\n      {\n        \"dayRangeMin\"\
  : 0,\n        \"dayRangeMax\": 10,\n        \"percentageRefundable\": 0,\n     \
  \   \"policyStartTimestamp\": null,\n        \"policyEndTimestamp\": null\n    \
  \  }\n    ]\n  },\n  \"...\": \"...\"\n}\n```\n\nThis product has a complex cancellation\
  \ policy; where cancellations processed:\n\n| Policy | **dayRangeMin** | **dayRangeMax**\
  \ | Logic | **percentageRefundable** |\n|--------|:-----------:|:-----------:|-------|:--------------------------:|\n\
  | &lt;u&gt;30&lt;/u&gt; days or more before the start time | 30 | null | (product_start_time\
  \ - cancellation_time) &gt;= 30 days | 100 |\n| &lt;u&gt;10&lt;/u&gt; days and *less\
  \ than* &lt;u&gt;30&lt;/u&gt; days (10 to 30 days) *before* the start time or more\
  \ | 10 | 30 | (product_start_time - cancellation_time) &gt;= 10 days &amp;&amp;\
  \ (product_start_time - cancellation_time) &lt; 30 days | 50 |\n| *less than* &lt;u&gt;10&lt;/u&gt;\
  \ days *before* the start time | 0 | 10 | (product_start_time - cancellation_time)\
  \ &lt; 10 days | 0 |\n\n**Note:** `null` in the `dateRangeMax` field means *negative\
  \ infinity*; i.e., *infinitely far in the past with respect to* `dateRangeMin`.\n\
  \nAdditional clauses will be included in the `termsAndConditions` field in natural\
  \ language. This field is for human consumption and is not classically machine-interpretable.\n\
  \n### `3` – All sales final (100% cancellation penalty / no refund offered)\n\n\
  Products in this category cannot be cancelled or amended without incurring a 100%\
  \ penalty; i.e., the refund amount will be zero. Around 10% of products fall into\
  \ this category.\n\n#### Example response snippet\n\n- **Source endpoint**: [/product](#operation/product)\n\
  - **Product**: `5985P7`\n\n```javascript\n{\n  \"data\": {\n    \"merchantTermsAndConditions\"\
  : {\n      \"termsAndConditions\": \"All sales are final and incur 100% cancellation\
  \ penalties.&lt;br&gt;\",\n      \"merchantTermsAndConditionsType\": 3,\n      \"\
  amountRefundable\": null,\n      \"cancellationFromTourDate\": [\n        {\n  \
  \        \"dayRangeMin\": 0,\n          \"dayRangeMax\": null,\n          \"percentageRefundable\"\
  : 0,\n          \"policyStartTimestamp\": null,\n          \"policyEndTimestamp\"\
  : null\n        }\n      ]\n    },\n    \"...\": \"...\"\n  }\n}\n```\nProducts\
  \ in this category can be cancelled, but no refund will be granted (in most cases...)\n\
  \n### Canceling items with a 'pending' booking status\n\nAs alluded, there is an\
  \ exception to this rule. Products with an 'on-request' [booking type](#section/Key-concepts/Booking)\
  \ can still be cancelled when their booking status is `\"pending\"` – i.e., before\
  \ the supplier has confirmed the booking – and a full refund will be granted.\n\n\
  It is impossible to predict how long an 'on-request' booking will remain 'pending'.\
  \ However, it is possible to check by enquiring about the booking using one of the\
  \ post-booking services; i.e.:\n\n* [/booking/status](#operation/bookingStatus)\n\
  * [/booking/status/items](#operation/bookingStatusItems)\n* [/booking/pastbooking](#operation/bookingPastbooking)\n\
  * [/booking/mybookings](#operation/bookingMybookings)\n\nAn 'all sales final' product\
  \ in a 'pending' state that can be cancelled and a refund granted will have the\
  \ following characteristics:\n\n1. The `bookingStatus` object returned from one\
  \ of the services above will have a `type` of `\"PENDING\"`, and `pending` will\
  \ be `true`.\n2. The `amountRefundable` field of the `merchantTermsAndConditions`\
  \ object will be non-zero and non-null. Rather, it will contain a currency-formatted\
  \ string showing the amount that would be refunded if the cancellation were performed\
  \ immediately; e.g., \"USD 55.33\".\n\n\n### Policy start and end times\n\nWithin\
  \ the `merchantTermsAndConditions` object returned in the response from [/booking/book](#operation/bookingBook),\
  \ [/booking/pastbooking](#operation/bookingPastbooking) and [/booking/mybookings](#operation/bookingMybookings),\
  \ the `amountRefundable` field shows the amount of money in the selected currency\
  \ that will be refunded if the cancellation is processed now, while the `policyStartTimestamp`\
  \ and `policyEndTimestamp` fields indicate the exact times between which the different\
  \ cancellation refund rates apply.\n\n#### Example response snippet (`merchantTermsAndConditions`)\
  \ from [/booking/book](#operation/bookingBook)\n\n- **Product**: `5010SYDNEY`\n\
  - **Note**: observe that `amountRefundable`, `policyStartTimestamp` and `policyEndTimestamp`\
  \ are populated here.\n\n```javascript\n\"data\": {\n  \"merchantTermsAndConditions\"\
  : {\n    \"termsAndConditions\": \"For a full refund, cancel at least 24 hours in\
  \ advance of the start date of the experience.\",\n    \"amountRefundable\": \"\
  USD 55.33\",\n    \"cancellationFromTourDate\": [\n      {\n        \"dayRangeMin\"\
  : 1,\n        \"dayRangeMax\": null,\n        \"percentageRefundable\": 100,\n \
  \       \"policyStartTimestamp\": null,\n        \"policyEndTimestamp\": 1551513600000\n\
  \      },\n      {\n        \"dayRangeMin\": 0,\n        \"dayRangeMax\": 1,\n \
  \       \"percentageRefundable\": 0,\n        \"policyStartTimestamp\": 1551340800000,\n\
  \        \"policyEndTimestamp\": 1551427200000\n      }\n    ]\n  },\n  \"...\"\
  : \"...\"\n}\n```\n\n### Post-travel cancellations\n\nOccasionally, customers seek\
  \ a refund for a product **after** completing their travels.\n\nThe reason for this\
  \ might be because they were unable to attend the tour due to the supplier having\
  \ cancelled the tour due to bad weather or some other reason out of the customer's\
  \ control; or, the customer might have been extremely dissatisfied with the tour\
  \ itself, felt that it was misrepresented in its advertising, or some other serious\
  \ complaint.\n\nWhen this occurs, you will need to [send a refund request by email\
  \ to dpsupport](mailto:dpsupport@viator.com) and include both \"CANCEL\" and the\
  \ booking reference number in the subject line.\n\nFor **all** post-travel cancellation\
  \ requests, you will need to include a detailed description of the issue. \n\nExcept\
  \ in cases of known service interruptions (e.g., due to extreme weather events),\
  \ we will first verify the issue and seek authorization from the product supplier.\
  \ \n\nOnce a decision regarding the refund has been made, we will notify your Customer\
  \ Services Department with this information. You will then need to advise your customer\
  \ directly and process the refund if granted.\n\n### Interpreting `policyStartTimestamp`\
  \ and `policyEndTimestamp`\n\nThe integers that populate the `policyStartTimestamp`\
  \ and `policyEndTimestamp` fields represent points in time that mark the boundaries\
  \ of the policy time period in the [Unix time format](https://en.wikipedia.org/wiki/Unix_time);\
  \ i.e., the number of seconds that have elapsed since 00:00:00 Thursday, 1 January\
  \ 1970, Coordinated Universal Time (UTC), minus leap seconds.\n\nUnix timestamps\
  \ can be easily read and interpreted using the 'time' (or similar) library of your\
  \ favorite programming language. For human purposes, an [online conversion tool](https://www.epochconverter.com/)\
  \ can be used.\n\nAs per the example above, canceling this booking between the following\
  \ times yields zero refund (because it is within the 24 hour window):\n\n| **Field\
  \ name** | `policyStartTimestamp` | `policyEndTimestamp` |\n|----------------|------------------------|----------------------|\n\
  | **Unix time** | 1551340800000 | 1551427200000 |\n| **Human readable time** | GMT:\
  \ Thursday, February 28, 2019 8:00:00 AM | GMT: Friday, March 1, 2019 8:00:00 AM\
  \ |\n\n* **Note**: Please use `policyStartTimestamp` and `policyEndTimestamp`, rather\
  \ than `dayRangeMin` and `dayRangeMax`, to determine which cancellation policy is\
  \ in effect.\n\n### Partial refunds\n\nWhile we recommend that you, as a merchant\
  \ partner, support the processing of partial refunds for your customers, it is up\
  \ to your whether you implement this functionality. \n\nIf you would prefer to only\
  \ grant the full (100%) refund that is offered on most products so long as the cancellation\
  \ is processed more than 24 hours prior to the product's start time, we recommend\
  \ that you implement logic that checks whether a 100% refund is available for the\
  \ product at the time the customer wishes to cancel their booking.\n\n| **Type 1:\
  \ Standard policy** (`merchantTermsAndConditionsType` is `1`) |\n|-------------------------------------------------------------|\n\
  | The 100% refund is available so long as the cancellation is performed more than\
  \ 24 hours prior to the product start time |\n\n| **Type 2: Custom policy** (`merchantTermsAndConditionsType`\
  \ is `2`) |\n|-----------------------------------------------------------|\n| You\
  \ will need to check whether any of the object-items in the `cancellationFromTourDate`\
  \ array have: &lt;ul&gt;&lt;li&gt;a `percentageRefundable` value of `100`, and&lt;/li&gt;&lt;li&gt;`dayRangeMin`\
  \ and `dayRangeMax` **or** `policyStartTimestamp` and `policyEndTimestamp` values\
  \ that include the present time&lt;/li&gt;&lt;/ul&gt; |\n\n| **Type 3: All sales\
  \ final** (`merchantTermsAndConditionsType` is `3`) |\n|-------------------------------------------------------------|\n\
  | No refunds are available; therefore, granting a refund to your customer for this\
  \ kind of product will be solely at *your* expense (i.e., you will still be invoiced\
  \ for the cost of the tour by Viator). Therefore, we recommend that you do not allow\
  \ refunds for products with this policy. |\n\n## Booking references \n\nWhen a booking\
  \ is made successfully via the [/booking/book](#operation/bookingBook) endpoint,\
  \ Viator assigns it a numeric identifier, now known as the **booking reference**.\n\
  \nThis booking reference is returned in the service's response in the `itemId` field;\
  \ however, this `itemId` is found in different locations depending on the endpoint\
  \ used:\n\n| Endpoint |  itemId element location |\n|----------|-------------------|\n\
  | [/booking/book](#operation/bookingBook) | `data.itemSummaries[].itemId` |\n| [/booking/status](#operation/bookingStatus)\
  \ | `data.itemSummaries[].itemId` |\n| [/booking/status/items](#operation/bookingStatusItems)\
  \ | `data[].itemId` |\n| [/booking/pastbooking](#operation/bookingPastbooking) |\
  \ `data.itemSummaries[].itemId` |\n| [/booking/mybookings](#operation/bookingMybookings)\
  \ | `data[].itemSummaries[].itemId` |\n\nThe booking reference can used in the **request**\
  \ in the following endpoints as the value in the `itemId` field or in the `itemIds`\
  \ array:\n\n- [/booking/status](#operation/bookingStatus)\n- [/booking/status/items](#operation/bookingStatusItems)\n\
  - [/booking/pastbooking](#operation/bookingPastbooking)\n- [/booking/mybookings](#operation/bookingMybookings)\n\
  - [/booking/voucher](#operation/bookingVoucher)\n\n### New booking references\n\n\
  The new booking cancellation endpoints; i.e.: \n\n- [/bookings/{booking-reference}/cancel-quote](#operation/cancelBookingQuote)\n\
  - [/bookings/{booking-reference}/cancel](#operation/cancelBooking)\n\n...use this\
  \ booking reference value as an in-URL request parameter, but its format is slightly\
  \ different. \n\nEssentially, it is the booking's numeric identifier (`itemId`),\
  \ but prepended with `BR-`.  For example, if the `itemId` is `580254558`, the `bookingId`\
  \ value in the cancellation request should be `BR-580254558`. \n\nThe booking cancellation\
  \ endpoints confirm the booking reference in the response in the `bookingId` field;\
  \ e.g.:\n\n```json\n{\n  \"bookingId\": \"BR-580669678\",\n  \"refundDetails\":\
  \ {\n    \"itemPrice\": 412.04,\n    \"refundAmount\": 412.04,\n    \"refundPercentage\"\
  : 100,\n    \"currencyCode\": \"USD\"\n  },\n  \"status\": \"CANCELLABLE\"\n}\n\
  ```\n\n# Common workflows and data validation\n\nUsers of the API usually implement\
  \ a booking process workflow. The common workflows are:\n- [add to cart](#section/Common-workflows-and-data-validation/Add-to-cart)\n\
  - [checkout](#section/Common-workflows-and-data-validation/Checkout)\n- [view voucher\
  \ or confirmation status](#section/Common-workflows-and-data-validation/View-voucher-or-confirmation-status)\n\
  - [make a booking](#section/Common-workflows-and-data-validation/Booking-process-flow)\n\
  \n## Add to cart\n\n### Summary\n\nBecause the Viator API is both stateless and\
  \ does not include services for managing a customer's shopping cart, this functionality\
  \ must be fully managed on the merchant's side.\n\nViator's servers can generate\
  \ a price quote for one or several items, but this collection will not be saved\
  \ by the server.\n\nWe recommend the following process:\n\n1. **View product** -\
  \ allow the customer to browse products and product details\n2. **Select date and\
  \ passengers** - allow the customer to check available dates and select the type\
  \ and number of passengers\n3. **Select tourgrade** - display the available tour\
  \ grades\n4. **View cart** -&gt; **price quote** - display a total price (including\
  \ multiple items)\n\n### View product\nFrom your *view product details* section,\
  \ a button should be presented to **check availability** or **book now** or something\
  \ similar. Use the [/product](#operation/product) service to retrieve product details\
  \ and schedules.\n\n### Select date and passengers\nHere, the customer is presented\
  \ with the dates that remain available for the product. Available dates can be obtained\
  \ via a request to [/booking/availability/dates](#operation/bookingAvailabilityDates).\
  \ The list of [age bands](#section/Key-concepts/Working-with-age-bands) (i.e.: 'adult',\
  \ 'child'; and, each band's maximum and minimum age) is available from the [/product](#operation/product)\
  \ service.\n\n**Validation** – ensure that:\n1. The total number of travelers being\
  \ booked does not exceed the limit returned in the `maxTravellerCount` field of\
  \ the [/product](#operation/product) service\n2. *At least one* adult (or adult\
  \ equivalent) passenger has been selected\n3. The selected dates are available (use\
  \ [/booking/availability/dates](#operation/bookingAvailabilityDates))\n\n### Select\
  \ tour grade\n\nOnce the date and traveler mix have been selected, the customer\
  \ may need to select a tour grade. Products that do not have this information recorded\
  \ in the Viator database are assigned a tour grade of `\"DEFAULT\"`. For these products,\
  \ it is unnecessary to select a tour grade.\n\nTour grade options must be displayed\
  \ to the customer when the product has multiple tour grades, due to:\n- different\
  \ departure times\n- traveler mix price deals, like family passes\n- different inclusions\
  \ and prices - e.g., limo pickup, different language delivery options), or...\n\
  - non-default tour grades – these tour grades *must* be presented to the customer.\n\
  \nThe tour grades for a product are retrieved with the [/booking/availability/tourgrades](#operation/bookingAvailabilityTourgrades)\
  \ service. If a tour grade is available (check the `available` flag), an 'add to\
  \ cart' button can be displayed. For unavailable tour grades (`available` is `false`),\
  \ a reason (`unavailableReason`) is provided, which will be one of:\n\n- `\"TRAVELLER_MISMATCH\"\
  `\n- `\"BLOCKED_OUT\"`, or\n- `\"UNAVAILABLE\"`\n\nYou may choose to hide the blocked-out\
  \ tour grades (if all tour grades are unavailable on a particular day, a day's tour\
  \ grades are all `\"BLOCKED_OUT\"`, or the product is not operating that day, the\
  \ [/booking/availability/dates](#operation/bookingAvailabilityDates) service will\
  \ not return that date).\n\nYou may also find that a product has no bookable tour\
  \ grades on a day if the traveler mix does not meet that tour grade's traveler mix\
  \ restrictions. For example, a honeymoon might require two adults as the only possible\
  \ traveler mix.\n\nYou can choose to hide the `\"BLOCKED_OUT\"` tour grades, but\
  \ you will probably want to display the `\"TRAVELLER_MISMATCH\"` grades with the\
  \ traveler mix requirements listed so that the customer can elect to alter their\
  \ traveler mix to suit (e.g., for family passes, etc.) You cannot allow the passenger\
  \ to book with an incompatible traveler mix.\n\nThe return object includes information\
  \ about tour grade restrictions:\n\n`ageBandsRequired`:\n- `minimumCountRequired`:\
  \ minimum number of travelers for an [age band](#section/Key-concepts/Working-with-age-bands)\n\
  - `maximumCountRequired`: maximum number of travelers for an [age band](#section/Key-concepts/Working-with-age-bands).\
  \ If this field is `null`, any number of travelers may be booked.\n\nYou will need\
  \ to present the `ageBandsRequired` information as in the following examples:\n\n\
  | In 'Adult' age band | Meaning |\n|---------------------|---------|\n| `minimumCountRequired`\
  \ = 1&lt;br&gt;`maximumCountRequired` = 3 | From 1 to 3 adults |\n| `minimumCountRequired`\
  \ = 0&lt;br&gt;`maximumCountRequired` = 3 | up to three adults |\n| `minimumCountRequired`\
  \ = 3&lt;br&gt;`MaximumCountRequired` =  | 3 or more adults |\n| `minimumCountRequired`\
  \ = 2&lt;br&gt;`MaximumCountRequired` = 2 | 2 adults |\n\n\n**Note:** There is a\
  \ singular and plural version for each age band definition. We recommend automatically\
  \ generating language that ensures the samples above are grammatically correct using\
  \ this information.\n\nThe user can click **back** and change their traveler mix;\
  \ or, they can try selecting another day.\n\n### View cart / price quote\n\nOnce\
  \ the item has been added to the cart, you will need to preserve this information\
  \ as part of the session data in your back-end, or as a browser cookie. In particular,\
  \ you will need to store the *product code* and *age band to quantity traveler mix*.\n\
  \n#### Sample PHP shopping cart item class\n**Note:** this is only an example and\
  \ is implementation dependent. Alternatively, you could use the item class (as used\
  \ in the API calls), but much of the information it contains does not need to be\
  \ stored:\n\n```javascript\nclass shoppingCartItem {\n  var $productCode;\n  var\
  \ $tourGrade;\n  var $date;\n  var $ageBandIdToQty; // assoc array\n}\n```\n\nTo\
  \ obtain a price quote, you must call the [/booking/calculateprice](#operation/bookingCalculateprice)\
  \ service. This service requires a currency code and an array of items to be specified.\
  \ Each item contains the date, product code, tour grade code and an associative\
  \ array of `ageBandIds` -&gt; `quantity`.\n\n**Validation** – the data must contain\
  \ [valid age bands](#section/Key-concepts/Working-with-age-bands), tour codes, dates,\
  \ etc. acquired in previous requests to the API.\n\n**Note:** A product's availability\
  \ can change in the time between API calls as tour grades or products may be blocked\
  \ out, or the booking window may close for upcoming dates.\n\n## Checkout\n\n###\
  \ Summary\n\nThe checkout process can be accomplished using the [/booking/book](#operation/bookingBook)\
  \ service, but you may need to make requests to other services to calculate prices,\
  \ display product information (age-band names, etc.) and list available pick-up\
  \ hotels for user selection.\n\nThe Viator mobile website breaks the workflow down\
  \ into three steps. For multiple items, some steps will need to be repeated, such\
  \ as capturing the traveler names for each tour. In your implementation, you can\
  \ reorganize/reorder the data collection to better suit your needs.\n\n**Example\
  \ workflow:**\n\n1. **Collect traveler details** - collect the names of the lead\
  \ traveler and all other travelers\n2. **Collect travel details** - ask any additional\
  \ questions, including those about any special requirements, and select pick-up\
  \ options.\n  - **Note:** the aforementioned steps will need to be repeated for\
  \ each item)\n3. **Collect booking details**\n  - **Note:** billing and payment\
  \ details *should not* be sent to Viator.\n\nThe classes for the booking request\
  \ are defined here in Booking Data Classes. You will need implement these in your\
  \ chosen programming language and verify that the correct JSON objects are generated\
  \ during serialization.\n\n### Traveler details\n\nThe traveler details are used\
  \ to populate the `booking-&gt;items[]-&gt;travellers[]` objects.\n\nOne passenger\
  \ must be identified as the \"lead traveler\". A boolean field in the traveler object\
  \ represents this flag. The lead traveler must be an adult or have the age band\
  \ `treatAsAdult` flag set to `true`.\n\nAll other travelers must be included.\n\n\
  **Validation** \n\nEnsure that:\n\n  - `bandId` is a [valid age band ID](#section/Key-concepts/Working-with-age-bands)\
  \ for the product\n  - `firstname` is less than 16 chars\n  - `surname` is less\
  \ than 36 chars\n  - `title` is not included unnecessarily (it is optional)\n  -\
  \ `leadTraveller` is set to `true` for one of the travelers who is in an [age band](#section/Key-concepts/Working-with-age-bands)\
  \ that has the `treatAsAdult` flag set to `true`\n\n### Other details\n\n#### Booking\
  \ questions\n\nThe travel details include the [booking questions](#section/Appendices/Booking-questions)\
  \ that are supplied in the [/product](#operation/product) service.\n\n**Sample question**\n\
  \n**Note:** There may be more than one.\n\n```javascript\nbookingQuestions: [{\n\
  \  \"message\": \"For safety reasons you must enter the weight of &lt;b&gt;all&lt;/b&gt;\
  \ passengers\",\n  \"required\": true,\n  \"questionId\": 23,\n  \"title\": \"Passenger\
  \ Weights\",\n  \"subTitle\": \"(e.g. 127 pounds, 145 kilos, etc)\",\n  \"sortOrder\"\
  : 1\n}]\n```\nThe questions should be displayed with the title, message, subtitle\
  \ and whether it is mandatory (required) or not.\n\n**Validation** – if the question\
  \ is mandatory, the user must enter at least one character.\n\n#### Special requirements\n\
  \n'Special requirements' should be presented as a text input field so that customers\
  \ can record whether they require wheelchair assistance, for example. It is not\
  \ mandatory for the customer to enter any text.\n\n#### Pick-up information\n\n\
  The last thing that must be collected for each item being booked is the pick-up\
  \ information. If the product includes pick-up, the `hotelPickup` flag will be set\
  \ to `true` (in the product object).\n\nIf pick-up is included, you will need to\
  \ make a request to [/booking/hotels](#operation/bookingHotels) to determine if\
  \ a hotel list exists. If it does, the list must be displayed so that the customer\
  \ can make their selection. If not, a text input field should be displayed for hotel\
  \ name collection.\n\nPlease note that the *first three results* in the list are\
  \ *not* hotels; rather, these three are alternative selections, comprising:\n\n\
  - 'Hotel not listed'\n- 'Live locally or staying with family/friends'\n- 'Hotel\
  \ not yet booked'\n\nIf the customer selects 'hotel not listed', you *must* provide\
  \ a hotel selection text input field. For the other two options, no hotel name is\
  \ required. In all cases, the hotel ID must be updated with either a hotel ID or\
  \ the IDs of the three items listed.\n\nIf no hotel list is available, you must\
  \ provide a text input field for collecting the customer's hotel name. Please include\
  \ instructions to enter 'live locally' or 'hotel not yet booked' if they cannot\
  \ provide a hotel name.\n\n**Validation** – if hotel list is available, the `hotelId`\
  \ must be supplied. If the `hotelId` is `notListed` the, `pickupPoint` field *must*\
  \ have at least one character.\n\nIf a hotel list is not available, then `pickupPoint`\
  \ must contain a value.\n\n#### Language services\n\nIf the response from the [/product](#operation/product)\
  \ service contains information in the `languageServices` field, e.g.:\n\n```javascript\n\
  \"langServices\": {\n  \"en/SERVICE_AUDIO\": \"English - Audio\"\n}\n```\n\n...you\
  \ must specify which language option you wish to book for this tour in the `languageOptionCode`\
  \ field (see request body schema of the [/booking/book service](#operation/bookingBook)).\n\
  \n## View voucher or confirmation status\n\nThe object returned by the [/booking/book](#operation/bookingBook)\
  \ service contains booking details that can be used to display an order summary\
  \ to the customer.\n\nConfirmed bookings of freesale products will return a `voucherKey`\
  \ and `voucherURL`. The `voucherURL` is accessible by the customer to view their\
  \ voucher.\n\nPending bookings of on-request products will return `null` in the\
  \ `voucherKey`/`voucherURL` fields. These fields will only contain values once the\
  \ booking is confirmed.\n\nA `bookingStatus` object is included in the response\
  \ that contains the status of the booking.\n\n```javascript\n\"bookingStatus\":\
  \ {\n  \"status\": 1,\n  \"text\": \"Paid &amp;amp; Confirmed\",\n  \"type\": \"\
  CONFIRMED\",\n  \"level\": \"ITEM\",\n  \"failed\": false,\n  \"confirmed\": true,\n\
  \  \"amended\": false,\n  \"pending\": false,\n  \"cancelled\": false\n}\n```\n\n\
  The status field corresponds to a number described in [bookingStatus field values\
  \ and meanings](#section/Appendices/bookingStatus-field-values-and-meanings).\n\n\
  Boolean flags that you can inspect to determine the booking status of the item:\n\
  - `failed`\n- `cancelled`\n- `confirmed`\n- `amended`\n- `pending`\n\n### Pending\
  \ bookings\nA booking is considered *pending* if the booking process is 'in progress'.\
  \ For example, an on-request booking would be *pending* until it is confirmed/rejected\
  \ by the supplier.\n\nIf a customer has made an amendment to an on-request booking\
  \ that is yet to be accepted by the supplier, the booking would then have a status\
  \ of *amended* when the supplier or customer service accepts the amendment.\n\n\
  **Example response object:**\n\n```javascript\n{\n  \"errorReference\": null,\n\
  \  \"data\": {\n    \"sortOrder\": 0,\n    \"rulesApplied\": [],\n    \"bookingStatus\"\
  : {\n      \"status\": 3,\n      \"text\": \"Confirmed\",\n      \"type\": \"CONFIRMED\"\
  ,\n      \"level\": \"ITINERARY\",\n      \"confirmed\": true,\n      \"pending\"\
  : false,\n      \"amended\": false,\n      \"cancelled\": false,\n      \"failed\"\
  : false\n    },\n    \"itemSummaries\": [{\n      \"sortOrder\": 0,\n      \"rulesApplied\"\
  : [],\n      \"bookingStatus\": {\n        \"status\": 1,\n        \"text\": \"\
  Paid &amp;amp; Confirmed\",\n        \"type\": \"CONFIRMED\",\n        \"level\"\
  : \"ITEM\",\n        \"pending\": false,\n        \"failed\": false,\n        \"\
  confirmed\": true,\n        \"amended\": false,\n        \"cancelled\": false\n\
  \      },\n      \"travellerAgeBands\": [{\n        \"sortOrder\": 0,\n        \"\
  count\": 1,\n        \"pluralDescription\": \"Adults\",\n        \"description\"\
  : \"Adult\",\n        \"ageBandId\": 1\n      }],\n      \"voucherKey\": \"1005851866:4af44c13ecf3f1a7d3f9ef2fc00c2257e08fa42ae20f877f3039ff9b52aba24e:580669678\"\
  ,\n      \"voucherURL\": \"https://viatorapi.live.rc.viator.com/service/merchant/voucher.jspa?code=1005851866:4af44c13ecf3f1a7d3f9ef2fc00c2257e08fa42ae20f877f3039ff9b52aba24e:580669678&amp;embedResources=false\"\
  ,\n      \"voucherRequirements\": \"You must present a paper voucher for this to\"\
  ,\n      \"productPulledDown\": false,\n      \"merchantCancellable\": true,\n \
  \     \"productWidgetList\": null,\n      \"savingAmount\": 0,\n      \"passbooks\"\
  : null,\n      \"termsAndConditions\": null,\n      \"itineraryId\": 1000024753,\n\
  \      \"tourGradeCode\": \"1DAYBOAT\",\n      \"productCode\": \"2065CPT\",\n \
  \     \"leadTravellerSurname\": \"Test\",\n      \"distributorItemRef\": \"distroItemRefJDP1803151135\"\
  ,\n      \"languageServicesLanguageCode\": \"en\",\n      \"travelDate\": \"2016-02-01\"\
  ,\n      \"price\": 3.72,\n      \"bookingEngineId\": \"UF\",\n      \"merchantNetPrice\"\
  : 3.51,\n      \"merchantNetPriceFormatted\": \"$3.51\",\n      \"leadTravellerTitle\"\
  : \"Mr\",\n      \"leadTravellerFirstname\": \"Homer\",\n      \"lastRetailPrice\"\
  : 3.51,\n      \"destId\": 318,\n      \"voucherOption\": \"VOUCHER_PAPER_ONLY\"\
  ,\n      \"productTitle\": \"Cape Town City Hop-on Hop-off Tour\",\n      \"itemId\"\
  : 700025496,\n      \"barcodeOption\": \"perperson\",\n      \"barcodeType\": \"\
  code128\",\n      \"obfsId\": 3696,\n      \"priceFormatted\": \"$3.72\",\n    \
  \  \"savingAmountFormated\": \"\",\n      \"priceUSD\": 3.72,\n      \"lastRetailPriceFormatted\"\
  : \"$3.51\",\n      \"departsFrom\": \"Cape Town, South Africa\",\n      \"hoursConfirmed\"\
  : 0,\n      \"currencyCode\": \"USD\"\n    }],\n    \"voucherKey\": \"1005851866:4af44c13ecf3f1a7d3f9ef2fc00c2257e08fa42ae20f877f3039ff9b52aba24e:580669678\"\
  ,\n    \"voucherURL\": \"https://viatorapi.live.rc.viator.com/service/merchant/voucher.jspa?code=1005851866:4af44c13ecf3f1a7d3f9ef2fc00c2257e08fa42ae20f877f3039ff9b52aba24e:580669678&amp;embedResources=false\"\
  ,\n    \"bookerEmail\": \"apitest@viator.com\",\n    \"userId\": null,\n    \"itineraryId\"\
  : 1000024753,\n    \"exchangeRate\": 1,\n    \"totalPriceFormatted\": \"$3.51\"\
  ,\n    \"totalPriceUSD\": 3.51,\n    \"bookingDate\": \"2015-03-17\",\n    \"distributorRef\"\
  : \"distroRefJDP1803151135\",\n    \"totalPrice\": 3.51,\n    \"hasVoucher\": true,\n\
  \    \"currencyCode\": \"USD\"\n  },\n  \"dateStamp\": \"2015-03-17T17:36:32+0000\"\
  ,\n  \"errorType\": null,\n  \"errorMessage\": null,\n  \"errorName\": null,\n \
  \ \"success\": true,\n  \"totalCount\": 1,\n  \"vmid\": \"321003\",\n  \"errorMessageText\"\
  : null\n}\n```\n\n### Checking the status of bookings\n\n#### Checking the status\
  \ of a single booking:\n\n- [/booking/mybookings](#operation/bookingMybookings)\
  \ can be used to check the status of a booking after it has been purchased. This\
  \ is useful for checking the status of a pending booking, particularly if there\
  \ are multiple items within the booking.\n\n  It is recommended that you poll the\
  \ service no more than once per hour.\n\n#### Checking the status of multiple bookings:\n\
  \n- [/booking/status](#operation/bookingStatus) will return the status of all bookings,\
  \ based on the following:\n  - booking date range\n  - travel date range\n  - specific\
  \ distributor/distributor item references\n  - lead traveler date/first name\n\n\
  This is useful for checking the status of recently-made, but still *pending* bookings,\
  \ or those that will commence soon.\n\n**Note:** You can only poll this service\
  \ (successful calls) once every 30 minutes.\n\n### Confirming the booking via email\n\
  \nUpon receiving a successful response from [/booking/book](#operation/bookingBook),\
  \ merchant partners should confirm the booking with the customer via email. This\
  \ email must be sent by the merchant partner (not Viator).\n\n#### Sample confirmation\
  \ email\n\n&lt;pre&gt;\nDear Traveller,\n\nThank you for booking with [PARTNER NAME]\
  \ on [www.domain.com]. Your booking is confirmed. This is your booking notification\
  \ and receipt. Please retain this email for your records.\n\nPlease note:\n\nWe\
  \ offer three types of vouchers. Be sure to check below for what type of voucher\
  \ your tour / activity requires. Voucher requirements vary by tour, so if you've\
  \ booked more than one tour, be sure to check each one. See below for instructions.\n\
  \nHOTEL/FLIGHT ITINERARY\n-----------------------------------------------------------------------\n\
  [Your standard reply here]\n\nTOURS\n-----------------------------------------------------------------------\n\
  \n1. Name: Whale Watching Cruise\n  e-Voucher or Paper Voucher Accepted\n  You can\
  \ present either a paper or an electronic voucher for this activity.\n  Voucher:\
  \ [VOUCHERURL]\n  Please click on the above link, follow the directions, and print\
  \ your voucher to present as per instructions on the voucher under 'Important Information'.\n\
  2. Name: Boston City Pass\n  Paper Voucher Required\n  You must present a paper\
  \ voucher for this tour. Voucher: [VOUCHERURL]\n  Please click on the above link,\
  \ follow the directions, and print your voucher to present as per instructions on\
  \ the voucher under 'Important Information'.\n3. Name: SuperShuttle Airport Transfer\n\
  \  Voucher Not Required\n  You must present a paper voucher for this tour. Voucher:\
  \ [VOUCHERURL]\n  You can present a paper or electronic voucher for this activity,\
  \ or you can simply present the Lead Traveller’s Photo ID. Our supplier has your\
  \ reservation on file and only requires proof of identity on the day of travel.\n\
  \nIMPORTANT INFORMATION\n-----------------------------------------------------------------------\n\
  [Your standard reply here]\n\nTERMS AND CONDITIONS\n-----------------------------------------------------------------------\n\
  [Your standard reply here]\n&lt;/pre&gt;\n\n## Booking process flow\n\nIn this section,\
  \ we show a sample booking process flow using Viator API services.\n\n### Search\
  \ for a product\n\n1. Determine the `destinationId` for the desired destination\
  \ using the [/taxonomy/destinations](#operation/taxonomyDestinations) service.\n\
  2. Search for products in the destination with the [/search/products](#operation/searchProducts)\
  \ service using the `destinationId`, along with optional parameters like the date\
  \ range (`startDate` and `endDate`), attraction link (`seoId`), category (`catId`)\
  \ and subcategory (`subCatId`).\n\n#### Example [/search/products](#operation/searchProducts)\
  \ POST request body:\n\n```javascript\n{\n  \"startDate\": \"2018-12-25\",\n  \"\
  endDate\": \"2018-12-28\",\n  \"topX\": \"1-15\", \n  \"destId\": 684, \n  \"currencyCode\"\
  : \"USD\",\n  \"sortOrder\": \"TOP_SELLERS\"\n}\n```\n**Note**: the `startDate`\
  \ and `endDate` must be in the future.\n\n3. Get the product details with the [/product](#operation/product)\
  \ service.\n\n#### Example parameters for a [/product](#operation/product) GET request:\n\
  \n```html\ncode=5010SYDNEY&amp;currencyCode=USD\n```\n\n### Determine the product's\
  \ available dates\n\nUse the [/booking/availability/dates](#operation/bookingAvailabilityDates)\
  \ service to retrieve a list of dates on which the product is operating. This list\
  \ can be used to populate a calendar display of available dates.\n\n#### Example\
  \ parameters for an availability check using the [/booking/availability/dates](#operation/bookingAvailabilityDates)\
  \ service:\n\n```html\nproductCode=5010SYDNEY\n```\n\n### Determine the available\
  \ age bands for the product\n\nBecause the product option (tour grade) availability\
  \ check requires the desired passenger mix, the user will first need to select the\
  \ number of travelers and the age band into which each can be classified.\n\nNote:\
  \ The exact ages to which each age band refers to differs between products. See\
  \ [Working with age bands](#section/Key-concepts/Working-with-age-bands) for more\
  \ information.\n\n1. Determine the number of passengers/travelers (and their respective\
  \ agebands) by having the user input the passenger mix for which they wish to make\
  \ a booking.\n2. Check for available tour grades for the date chosen using the [/booking/availability/tourgrades](#operation/bookingAvailabilityTourgrades)\
  \ service; or, check for available tour grades by month using the [/booking/availability/tourgrades/pricingmatrix](#operation/bookingAvailabilityTourgradesPricingmatrix)\
  \ service\n\n#### [/booking/availability/tourgrades](#operation/bookingAvailabilityTourgrades)\
  \ POST request:\n```javascript\n{\n  \"productCode\": \"5010SYDNEY\",\n  \"bookingDate\"\
  : \"2018-12-05\",\n  \"currencyCode\": \"USD\",\n  \"ageBands\": [\n    {      \n\
  \      \"bandId\": 1,\n      \"count\": 2    \n    }  \n  ]\n}\n```\n\n#### [/booking/availability/tourgrades/pricingmatrix](#operation/bookingAvailabilityTourgrades)\
  \ POST request:\n```javascript\n{\n  \"productCode\": \"5010SYDNEY\",\n  \"month\"\
  : \"12\",\n  \"year\": \"2018\",\n  \"currencyCode\": \"USD\"\n}\n```\n3. Finalize\
  \ pricing using the [/booking/availability/tourgrades/pricingmatrix](#operation/bookingAvailabilityTourgradesPricingmatrix)\
  \ service. \n  - **Note**: we strongly recommend using the [/booking/calculateprice](#operation/bookingCalculateprice)\
  \ service prior to making the booking, as it reconfirms the product availability\
  \ for the specified dates and passenger mix.\n\n4. Make the booking\n  - Note that\
  \ the [/booking/book](#operation/bookingBook) service supports multi-item bookings.\
  \ The response from the [/product](#operation/product) service indicates mandatory\
  \ information that must be sent when making the booking, such as required [booking\
  \ questions](#section/Appendices/Booking-questions) and hotel pick-up options.\n\
  \  - For hotel pick-up:\n    - Send a hotel ID to the [/booking/book](#operation/bookingBook)\
  \ service if `hotelPickup` is `true` for the product.\n    - [/booking/hotels](#operation/bookingHotels)\
  \ can be used to return a list of hotels available for the product.\n    - The `hotelId`\
  \ is the `id` field in the response from the [/booking/hotels](#operation/bookingHotels)\
  \ service. This can be:\n      -  a number (represented as a string) – e.g., `'4119'`\n\
  \      -  `'local'` – if the customer resides near the location in which the product\
  \ operates \n      -  `'notBooked'` – if the customer's hotel is not yet booked\n\
  \      -  `'notListed'` – if the customer's hotel is not listed in the response\
  \ from [/booking/hotels](#operation/bookingHotels). If this is the case, capture\
  \ the customer’s hotel details in a text box and pass this information in the `pickupPoint`\
  \ field in the request body of the [/booking/book](#operation/bookingBook) service.\n\
  \n#### [/booking/book](#operation/bookingBook) POST request example:\n\n```javascript\n\
  {\n  \"demo\": true,\n  \"currencyCode\": \"USD\",\n  \"partnerDetail\": {\n   \
  \   \"distributorRef\": \"distributorRef1550616101308\"\n  },\n  \"booker\": {\n\
  \      \"firstname\": \"Homer Test\",\n      \"surname\": \"Simpson Test\",\n  \
  \    \"title\": \"Mr\",\n      \"email\": \"apitest@viator.com\",\n      \"homePhone\"\
  : \"(02)66987564\"\n  },\n  \"items\": [\n    {\n      \"partnerItemDetail\": {\n\
  \        \"distributorItemRef\": \"distributorItemRef1550616101308\"\n      },\n\
  \      \"hotelId\": null,\n      \"pickupPoint\": null,\n      \"travelDate\": \"\
  2019-03-19\",\n      \"productCode\": \"5010SYDNEY\",\n      \"tourGradeCode\":\
  \ \"24HOUR\",\n      \"languageOptionCode\": \"en/SERVICE_GUIDE\",\n      \"bookingQuestionAnswers\"\
  : [\n        {\n          \"questionId\": 100,\n          \"answer\": \"120 kgs\"\
  \n        }\n      ],\n      \"specialRequirements\": \"\",\n      \"travellers\"\
  : [\n        {\n          \"bandId\":1,\n          \"firstname\": \"Homer\",\n \
  \         \"surname\": \"Simpson Test\",\n          \"title\": \"Mr\",\n       \
  \   \"leadTraveller\": true\n        }, {\n          \"bandId\": 1,\n          \"\
  firstname\": \"Marge\",\n          \"surname\": \"Merchant Viator Test\",\n    \
  \      \"title\": \"Mrs\"\n        }\n      ]\n    }\n  ]\n}\n```\n\n#### [/booking/hotels](#operation/bookingHotels)\
  \ GET example parameters:\n\n```html\nproductCode=5010SYDNEY\n```\nor\n```html\n\
  destId=684\n```\n\n5. You will receive different booking statuses depending on the\
  \ product's booking engine. \n  - For products that are free-sale (`'FreesaleBE'`),\
  \ unconditional free-sale (`'UnconditionalBE'`) and free-sale / on-request (`'FreesaleOnRequestBE'`)\
  \ - i.e., during the free-sale period, confirmation should occur instantly. \n \
  \ - The `'FreesaleOnRequestBE'` status means that the product will only remain free-sale\
  \ up until a certain number of days before the travel date, after which it becomes\
  \ on-request. \n  - Normally, if the product is on-request, its booking status will\
  \ be `'Pending'`.\n\n### Post-booking\n\n#### Displaying vouchers\n\nTo display\
  \ the voucher to your customer, direct them to the URL returned in the `voucherURL`\
  \ field in the response from the [/booking/book](#operation/bookingBook) service.\n\
  \n**Note**: the voucher will not be available until the booking is confirmed – the\
  \ value of the `hoursConfirmed` field in the response from the [/booking/book](#operation/bookingBook)\
  \ service can be shown to the customer to indicate the time frame within which they\
  \ are likely to be notified as to their booking confirmation.\n\n#### Viewing bookings\n\
  \n- To view a **single** booking, use the [/booking/pastbooking](#operation/bookingPastbooking)\
  \ service, which returns one booking at a time. \n- To retrieve **all** bookings\
  \ for a customer, use the [/booking/mybookings](#operation/bookingMybookings) service.\n\
  \n#### Viewing booking statuses\n\nTo view the booking statuses for multiple items\
  \ based on various criteria, use the [/booking/status](#operation/bookingStatus)\
  \ service.\n\nNote that this service can only be polled once every five minutes.\
  \ Ideally, this service should be used by your software implementation to perform\
  \ bulk updates of pending itineraries. The maximum number of itinerary results returned\
  \ is 1,000.\n\n#### `merchantNetPrice` and `price` in the [/search/products](#operation/searchProducts)\
  \ service\n\nThe difference between these fields is as follows:\n\n- `merchantNetPrice`\
  \ is the amount you, as the merchant partner will be invoiced for, excluding any\
  \ fees.\n- `price` is the price at which Viator sells the product\n\n**Note**: these\
  \ prices are also returned (per age band) by the following services:\n\n- [/booking/availability/tourgrades/pricingmatrix](#operation/bookingAvailabilityTourgradesPricingmatrix)\n\
  - [/booking/pricingmatrix](#operation/bookingPricingmatrix)\n- [/booking/book](#operation/bookingBook)\n\
  \n### Currency considerations for bookings\n\nIf the booking shows prices converted\
  \ to and formatted according to a different currency to that in which it was made,\
  \ it is because each API partner has a particular 'base currency', and all bookings\
  \ will be made in that currency.\n\n### Booking and transaction fees\n\nThe total\
  \ price may be different to the `merchantNetPrice` due to the fact that a booking\
  \ fee – i.e., a transaction fee or commission – is added to all bookings.\n\nThis\
  \ fee is a fixed percentage with a capped maximum. The exact percentage depends\
  \ on your merchant partner agreement with Viator and can be found in your contract\
  \ with Viator.\n\n### Making demo bookings\n\nTo make a demo booking, simply set\
  \ the `demo` field to `true` in the [/booking/book](#operation/bookingBook) service.\n\
  \nWhile demo bookings are allowed on the live production environment, we recommend\
  \ not doing so as it is possible that a notification could be sent to the supplier.\
  \ Performing a cancellation of the demo booking is therefore recommended.\n\nTo\
  \ cancel the booking, partners should use the [/bookings/{id}/cancel](#operation/cancelBooking)\
  \ service. For details on canceling a booking, see: [Cancellation API workflow](#section/Common-workflows-and-data-validation/Cancellation-API-workflow)\n\
  \n## Cancellation UX\n\nOn the Viator.com website, once the customer has made a\
  \ booking, they are able to access the details of all their upcoming, past and cancelled\
  \ bookings by navigating to the **bookings** section of the website.\n\nYou must\
  \ communicate to the user the terms and conditions that pertain to canceling their\
  \ booking; i.e., what to expect in terms of the refund they will receive if they\
  \ were to cancel their booking now.\n\nOn the Viator website, this information is\
  \ communicated in the cancellation button text. In the following example, the user\
  \ has booked the \"San Francisco City Tour with Alcatraz\", and is viewing their\
  \ **bookings** page.\n\nIn this way, the user is told that they can \"cancel for\
  \ free by Oct 22\" – i.e., they will be issued a full refund if they cancel the\
  \ product prior to October 22:\n\n![user bookings](https://docs.viator.com/partner-api/resources/merchant/technical/img/user-bookings.png)\n\
  \nThis text is programmatically generated by inspecting the product's cancellation\
  \ policy, which is contained within the `merchantTermsAndConditions` object, which\
  \ is included in the response object from the following endpoints:\n\n- [/booking/book](/partner-api/merchant/technical/#operation/bookingBook)\n\
  - [/booking/pastbooking](/partner-api/merchant/technical/#operation/bookingPastbooking)\n\
  - [/booking/mybookings](/partner-api/merchant/technical/#operation/bookingMybookings)\n\
  \nFor details on how to interpret the `merchantTermsAndConditions` object, see:\
  \ [Cancellation policy](#section/Key-concepts/Cancellation-policy)\n\nOnce the user\
  \ clicks the button labelled: **Cancel for free by Oct 22**, they are brought to\
  \ the cancellation confirmation page, where they are provided a more formal cancellation\
  \ quote prior to confirming their intention to cancel the product.\n\n### Cancellation\
  \ refund display\n\nAs the merchant of record, the amount your customer was charged\
  \ for the product was your decision; therefore, the amount that you elect to grant\
  \ the customer as a refund is also up to you, so you will need to retrieve the amount\
  \ the customer has paid for the product from your own records/databases.\n\nThe\
  \ amount that Viator would have invoiced you for the booking – equivalent to the\
  \ merchant net price at the time of booking plus the transaction fee – can be retrieved\
  \ using the [/bookings/{booking-ref}/cancel-quote](#operation/cancelBookingQuote)\
  \ endpoint. For more information see: [Get a cancellation quote](#get-a-cancellation-quote)\n\
  \nHere, the customer is shown that they will receive a full refund if they cancel\
  \ the product now:\n\n![cancellation quote](https://docs.viator.com/partner-api/resources/merchant/technical/img/cancellation-quote.png)\n\
  \n### Displaying and choosing cancellation reasons\n\nAt this point in the workflow,\
  \ the user must select a reason for their cancellation. Viator's systems require\
  \ that a reason for the cancellation be given in order to carry out the cancellation\
  \ process.\n\nAs the set of acceptable reasons for canceling a booking are formally\
  \ specified by the Viator Partner API and are not necessarily immutable (new reasons\
  \ may be added at any time) you should retrieve the presently available cancellation\
  \ reasons from the [/bookings/cancel-reasons](#operation/cancellationReasons) endpoint.\
  \ We require you to present these to the customer for them to select.\n\nUse the\
  \ `cancellationReasonText` fields in the response to populate the list from which\
  \ the customer can select the most-appropriate match for why they are canceling,\
  \ as on the Viator website:\n\n![user bookings](https://docs.viator.com/partner-api/resources/merchant/technical/img/cancellation-reasons.png)\n\
  \nFor more information about getting cancellation reasons, see: [Getting cancellation\
  \ reasons](#getting-cancellation-reasons)\n\n**Note**: As it is necessary for the\
  \ user to provide a cancellation reason, it is required that the **Cancel Booking**\
  \ button remain disabled until a reason has been selected by the customer.\n\n###\
  \ Completing the cancellation\n\nOnce the user has selected a reason, the **Cancel\
  \ Booking** button can be activated:\n\n![cancel booking](https://docs.viator.com/partner-api/resources/merchant/technical/img/cancel-booking.png)\n\
  \nClicking the **Cancel Booking** button is the final action required of the customer\
  \ to complete the cancellation.\n\nAt this point, you will want to cancel the booking\
  \ using the [/bookings/{booking-ref}/cancel](#operation/cancelBooking) API endpoint.\
  \ For more information on using this service, see: [Cancel the booking](#cancel-the-booking)\n\
  \n### Obtaining confirmation for the cancellation\n\nOn the Viator.com site, the\
  \ following confirmation message is displayed on the page that loads after the **Cancel\
  \ Booking** button is clicked:\n\n![cancellation confirmation](https://docs.viator.com/partner-api/resources/merchant/technical/img/cancellation-confirmation.png)\n\
  \n### Cancellation confirmation email\n\nOnce the cancellation is accepted, a short,\
  \ succinct email informing the customer that their booking has been successfully\
  \ canceled is sent immediately:\n\n![cancellation confirmation email](https://docs.viator.com/partner-api/resources/merchant/technical/img/cancellation-email.png)\n\
  \n### Viewing canceled bookings\n\nClicking on the **View reservation details**\
  \ button in the cancellation confirmation email returns the customer to their bookings\
  \ page, where the fact of the booking being canceled is communicated clearly:\n\n\
  ![canceled booking](https://docs.viator.com/partner-api/resources/merchant/technical/img/canceled-booking.png)\n\
  \n## Cancellation API workflow\n\n### Note:\n\n- All booking cancellations (except\
  \ for those requested after the date of travel) must now be performed via the API.\
  \ Viator no longer offers ordinary cancellation services via our customer support\
  \ function.\n- To cancel a booking after the tour or activity has occurred, please\
  \ contact [Viator Partner Support](mailto:dpsupport@viator.com)\n- **Legacy API\
  \ keys:** Bookings made via the [v1 /booking/book](#operation/bookingBook) endpoint\
  \ using a [v1 legacy API key](#section/Authentication/Legacy-API-keys) can be canceled\
  \ using the [v2 cancellation endpoint](#operation/cancelBooking) and a [v2 API key](#section/Authentication/API-key)\
  \ so long as the [legacy (v1) API key](#section/Authentication/Legacy-API-keys)\
  \ used to make the booking is linked to the partner's [v2 API key](#section/Authentication/API-key).\n\
  \n\n### Getting cancellation reasons\n&lt;a id=\"getting-cancellation-reasons\"\
  &gt;&lt;/a&gt;\n\nWhen canceling a booking, you are required to submit a valid 'reason\
  \ for the cancellation' to assist with Viator's internal processes. This is accomplished\
  \ via the inclusion of a valid reason code in the body of the request. The reason\
  \ codes can be retrieved from the [/bookings/cancel-reasons](#operation/cancellationReasons)\
  \ endpoint.\n\nAs the acceptable reasons for cancellation may be extended at any\
  \ point (existing reasons will not change or be removed), we recommend retrieving\
  \ an up-to-date list from this endpoint at least weekly.\n\nThe output from the\
  \ [/bookings/cancel-reasons](#operation/cancellationReasons) endpoint at the time\
  \ of writing is as follows:\n\n```javascript\n{\n    \"reasons\": [\n        {\n\
  \            \"cancellationReasonCode\": \"Customer_Service.I_canceled_my_entire_trip\"\
  ,\n            \"cancellationReasonText\": \"I canceled my entire trip\"\n     \
  \   },\n        {\n            \"cancellationReasonCode\": \"Customer_Service.Booked_wrong_tour_date\"\
  ,\n            \"cancellationReasonText\": \"Booked wrong tour/date\"\n        },\n\
  \        {\n            \"cancellationReasonCode\": \"Customer_Service.Duplicate_Booking\"\
  ,\n            \"cancellationReasonText\": \"Duplicate Booking\"\n        },\n \
  \       {\n            \"cancellationReasonCode\": \"Customer_Service.Chose_a_different_cheaper_tour\"\
  ,\n            \"cancellationReasonText\": \"Chose a different/cheaper tour\"\n\
  \        },\n        {\n            \"cancellationReasonCode\": \"Customer_Service.Weather\"\
  ,\n            \"cancellationReasonText\": \"Weather\"\n        },\n        {\n\
  \            \"cancellationReasonCode\": \"Customer_Service.Unexpected_medical_circumstances\"\
  ,\n            \"cancellationReasonText\": \"Unexpected/medical circumstances\"\n\
  \        },\n        {\n            \"cancellationReasonCode\": \"Customer_Service.Tour\
  \ operator asked me to cancel\",\n            \"cancellationReasonText\": \"Tour\
  \ operator asked me to cancel\"\n        }\n    ]\n}\n```\n\n### Canceling a booking\n\
  \n#### Getting a cancellation quote\n&lt;a id=\"get-a-booking-cancellation-quote\"\
  &gt;&lt;/a&gt;\n\nBefore canceling the booking, call the [/bookings/{booking-reference}/cancel-quote](#operation/cancelBookingQuote)\
  \ endpoint to get information about whether the booking can be canceled using this\
  \ endpoint and what the refund will be, for example:\n\n```html\nGET https://api.viator.com/partner/bookings/BR-580254558/cancel-quote\n\
  ```\n\n**Note**: For information about the **{booking-reference}** in URL parameter,\
  \ see [Key concepts: Booking references](#section/Key-concepts/Booking-references)\n\
  \nYou will receive a cancellation quote object, e.g.:\n\n```javascript\n{\n    \"\
  bookingId\": \"BR-580254558\",\n    \"status\": \"CANCELLABLE\",\n    \"refundDetails\"\
  : {\n        \"itemPrice\": 109.77,\n        \"refundAmount\": 109.77,\n       \
  \ \"currencyCode\": \"USD\",\n        \"refundPercentage\": 100.00\n    }\n}\n```\n\
  \n **Note**: Bookings that have not been confirmed by the supplier and have a status\
  \ of `\"PENDING\"` will report an `itemPrice`, `refundAmount` and `refundPercentage`\
  \ of `0`, as no fees are charged until the booking's status is `\"CONFIRMED\"`.\n\
  \nThe data elements in this object have meanings as follows:\n\n| Element | Meaning\
  \ | Example |\n|---------|---------|---------|\n| `bookingId` | the booking reference\
  \ number prepended with `BR-` | `BR-580254556` |\n| `status` | One of the following:\
  \ &lt;ul&gt;&lt;li&gt;`CANCELLABLE`: the booking is eligible to be cancelled&lt;/li&gt;&lt;li&gt;`CANCELLED`:\
  \ the booking has already been cancelled&lt;/li&gt;&lt;li&gt;`NOT_CANCELLABLE`:\
  \ the booking is for a product that operated in the past, and therefore cannot be\
  \ cancelled using this endpoint (you will need to [send an email to dpsupport](mailto:dpsupport@viator.com)\
  \ including both \"CANCEL\" and the booking reference number in the subject line\
  \ in order to request a refund for such a booking)&lt;/li&gt;&lt;/ul&gt; | `CANCELLABLE`\
  \ |\n| `refundDetails` | object containing information about the refund | |\n| `itemPrice`\
  \ | the **merchant net price** + **transaction fee** for this product at the time\
  \ of booking in the currency specified by `currencyCode` | `109.77` |\n| `refundAmount`\
  \ | the amount that will be deducted from your invoice if the booking is cancelled\
  \ now | `109.77` |\n| `currencyCode` | the currency code for the currency in which\
  \ pricing information is displayed | `USD` |\n| `refundPercentage` | the refund\
  \ amount expressed as a percentage of the `itemPrice` | `100.00` |\n\n#### Canceling\
  \ the booking\n&lt;a id=\"cancel-the-booking\"&gt;&lt;/a&gt;\n\nIf the `status`\
  \ field has a value of `CANCELLABLE` and you are happy with the `refundAmount`,\
  \ call the [/bookings/{booking-ref}/cancel](#operation/cancelBooking) endpoint to\
  \ cancel the booking, e.g.:\n\n```html\nPOST https://api.viator.com/partner/bookings/BR-580254558/cancel\n\
  ```\n\nA reason code corresponding to the reason for cancellation must be included\
  \ in the request body; e.g.:\n\n```javascript\n{\n  \"reasonCode\":\"Customer_Service.Chose_a_different_cheaper_tour\"\
  \n}\n```\n\nYou should receive a response indicating that the cancellation was successful,\
  \ e.g.:\n\n```javascript\n{\n    \"bookingId\": \"BR-580254558\",\n    \"status\"\
  : \"ACCEPTED\"\n}\n```\n\nA `status` of `ACCEPTED` indicates that the booking was\
  \ successfully canceled.\n\n## Calculating prices\n\nThe [/booking/calculateprice](#operation/bookingCalculateprice)\
  \ service is used to calculate a total price for one or more products, with the\
  \ ability to specify the date and passenger mix for each product individually. \n\
  \nIt also reconfirms the availability and pricing of the products for the requested\
  \ dates and passenger mixes. We strongly recommended that you call this service\
  \ prior to [making a booking](#section/Common-workflows-and-data-validation/Making-a-booking)\
  \ to establish that the booking will succeed once submitted.\n\nThis endpoint is\
  \ useful when implementing a shopping cart, as multiple product bookings can be\
  \ enquired about in a single call to this service.\n\n#### Example request body\
  \ (JSON)\n\n```javascript\n{\n  \"currencyCode\": \"USD\",\n  \"items\": [{\n  \
  \  \"travelDate\": \"2015-03-01\",\n    \"productCode\": \"2916ROME\",\n    \"tourGradeCode\"\
  :\"24HR\",\n    \"travellers\": [\n      {\n        \"bandId\": 1\n      },\n  \
  \    {\n        \"bandId\": 1\n      }\n    ]\n  }]\n}\n```\nThe quirky `travellers`\
  \ array is used to specify the number of travellers in each age band. Each member\
  \ object of this array corresponds to a single traveller. The example above signifies\
  \ \"two adults from bandId: 1\".\n\nAnother example might be \"three travelers from\
  \ bandId:1 and two travelers from bandId:2\". That would be as follows:\n\n```javascript\n\
  \"travellers\": [\n  {\n    \"bandId\": 1\n  },\n  {\n    \"bandId\": 1\n  },\n\
  \  {\n    \"bandId\": 1\n  },\n  {\n    \"bandId\": 2\n  },\n  {\n    \"bandId\"\
  : 2\n  }\n]\n```\n\n- **Note**: See [Working with age bands](#section/Key-concepts/Working-with-age-bands)\
  \ for more information.\n\n#### Price information\n\nThe **total price** (i.e.,\
  \ including the transaction fee) that you will be invoiced for the products to be\
  \ booked is given in the following fields in the response from this service:\n\n\
  - `data.itemSummaries[].price` (numeric total price of item)\n- `data.itemSummaries[].priceFormatted`\
  \ (currency formatted total price of item) \n- `data.itinerary.totalPrice` (numeric\
  \ total price of item)\n- `data.itinerary.totalPriceFormatted` (currency-formatted\
  \ total price of item)\n\nFor more information about pricing fields and their meaning\
  \ throughout this API, see: [Merchant pricing](#section/Key-concepts/Merchant-pricing).\n\
  \n#### Determining whether the product is 'freesale' or 'on request'\n\nYou can\
  \ determine whether the booking is *freesale* or *on-request* by examining the response\
  \ from this endpoint. 'Freesale' bookings are those that are confirmed immediately\
  \ (with a status of `\"CONFIRMED\"`) when booked, while *on-request* bookings are\
  \ instead confirmed by the supplier at a later time. \n\nThe approximate time window\
  \ for confirmation is provided in the `hoursConfirmed` (integer) field. This can\
  \ be presented to the customer. \n\n- An `hoursConfirmed` of `0` means that the\
  \ booking is *freesale*. \n- An `hoursConfirmed` greater than `0` indicates that\
  \ the booking is *on-request*.\n\n## Finding hotel pick-up points\n\n### Hotel pickup\
  \ example:\n\n#### Example response body ([/booking/hotels](#operation/bookingHotels))\n\
  ```javascript\n{\n  \"vmid\":\"221002\",\n  \"errorMessage\": null,\n  \"errorType\"\
  : null,\n  \"dateStamp\": \"2012-04-12T13:48:27+0000\",\n  \"success\": true,\n\
  \  \"errorReference\": null,\n  \"errorMessageText\": null,\n  \"totalCount\": 1,\n\
  \  \"errorName\": null\n  \"data\": [\n    {\n      \"address\": null,\n      \"\
  name\": \"I live locally / I'm staying with friends, relatives\",\n      \"id\"\
  : \"local\",\n      \"phone\": null,\n      \"productCodes\": null,\n      \"destinationId\"\
  : 0,\n      \"city\": null,\n      \"notes\": null,\n      \"latitude\": null,\n\
  \      \"longitude\": null,\n      \"postcode\": null,\n      \"brand\": null,\n\
  \      \"hotelString\": \"I live locally / I'm staying with friends, relatives\"\
  ,\n      \"sortOrder\": 1\n    },\n    {\n      \"address\": null,\n      \"name\"\
  : \"My hotel is not yet booked\",\n      \"id\": \"notBooked\",\n      \"phone\"\
  : null,\n      \"productCodes\": null,\n      \"destinationId\": 0,\n      \"city\"\
  : null,\n      \"notes\": null,\n      \"latitude\": null,\n      \"longitude\"\
  : null,\n      \"postcode\": null,\n      \"brand\": null,\n      \"hotelString\"\
  : \"My hotel is not yet booked\",\n      \"sortOrder\": 2\n    },\n    {\n     \
  \ \"address\": null,\n      \"name\": \"My hotel is not listed\",\n      \"id\"\
  : \"notListed\",\n      \"phone\": null,\n      \"productCodes\": null,\n      \"\
  destinationId\": 0,\n      \"city\": null,\n      \"notes\": null,\n      \"latitude\"\
  : null,\n      \"longitude\": null,\n      \"postcode\": null,\n      \"brand\"\
  : null,\n      \"hotelString\": \"My hotel is not listed\",\n      \"sortOrder\"\
  : 3\n    },\n    {\n      \"address\": \"375 East Harmon Avenue\",\n      \"name\"\
  : \"Alexis Park Resort Hotel\",\n      \"id\": \"684_2\",\n      \"phone\": \"\"\
  ,\n      \"productCodes\": null,\n      \"destinationId\": 684,\n      \"city\"\
  : \"Las Vegas\",\n      \"notes\": null,\n      \"latitude\": 36.106258,\n     \
  \ \"longitude\": -115.156146,\n      \"postcode\": \"89169\",\n      \"brand\":\
  \ \"\",\n      \"hotelString\": null,\n      \"sortOrder\": 4\n    },\n    {\n \
  \     \"address\": \"167 East Tropicana Avenue\",\n      \"name\": \"Americas Best\
  \ Value Inn\",\n      \"id\": \"684_3\",\n      \"phone\": \"\",\n      \"productCodes\"\
  : null,\n      \"destinationId\": 684,\n      \"city\": \"Las Vegas\",\n      \"\
  notes\": null,\n      \"latitude\": 36.100778,\n      \"longitude\": -115.165522,\n\
  \      \"postcode\": \"89109\",\n      \"brand\": \"\",\n      \"hotelString\":\
  \ null,\n      \"sortOrder\": 5\n    },\n    {\n      \"address\": \"3131 Las Vegas\
  \ Boulevard South\",\n      \"name\": \"Wynn Resort\",\n      \"id\": \"684_126\"\
  ,\n      \"phone\": \"\",\n      \"productCodes\": null,\n      \"destinationId\"\
  : 684,\n      \"city\": \"Las Vegas\",\n      \"notes\": null,\n      \"latitude\"\
  : 36.127563,\n      \"longitude\": -115.167704,\n      \"postcode\": \"89109\",\n\
  \      \"brand\": \"\",\n      \"hotelString\": null,\n      \"sortOrder\": 119\n\
  \    }\n  ]\n}\n```\n## Making a booking\n\nTo make a booking, use the [/booking/book](#operation/bookingBook)\
  \ service.\n\nTo make a *real* booking, ensure `demo` is set to `false` in the booking\
  \ request.\n\nDemo bookings will enter our system as a test booking and will not\
  \ charge the merchant. To enable demo bookings, set `demo` to `true` in the booking\
  \ request and pass `\"test\"` as the traveler's first or last name.\n\n**Note:**\
  \ Avoid testing on **Live**, as the booking may be sent to the supplier (depending\
  \ on the product). Any test bookings on live must be cancelled via the [/bookings/{id}/cancel](#operation/cancelBooking)\
  \ service; or, contact dpsupport@viator.com if you experience any other issues.\n\
  \n### distrbutorRef and distributorItemRef\n\nThe `distributorRef` and `distrbutorItemRef`\
  \ fields are the merchant partner's own reference for the booking. All merchant\
  \ partners must pass a `distributorRef` and a `distributorItemRef` in all bookings.\n\
  \nIt can be any alphanumeric string, and in for the `distrbutorRef`, it must be\
  \ unique to bookings made by the merchant.\n\nIf an existing `distributorRef` is\
  \ passed, the booking with the matching `distributorRef` will be returned in the\
  \ response, and a new booking will not be made.\n\nPlease see the description for\
  \ these fields in the table below for more information.\n\n**Example request**\n\
  \n```javascript\n{\n  \"demo\": true,\n  \"currencyCode\": \"USD\",\n  \"partnerDetail\"\
  : {\n    \"distributorRef\": \"distroRef0412141435\"\n  },\n  \"booker\": {\n  \
  \  \"email\": \"apitest@viator.com\",\n    \"firstname\": \"Homer Test\",\n    \"\
  surname\": \"Simpson Test\",\n    \"title\": \"Mr\"\n  },\n  \"items\": [{\n   \
  \ \"partnerItemDetail\": {\n      \"distributorItemRef\": \"distroItemRef0412141435_1\"\
  \n    },\n    \"hotelId\": null,\n    \"pickupPoint\": null,\n    \"travelDate\"\
  : \"2015-03-31\",\n    \"productCode\": \"2916ROME\",\n    \"tourGradeCode\": \"\
  24HR\",\n    \"languageOptionCode\": \"en/SERVICE_GUIDE\",\n    \"bookingQuestionAnswers\"\
  : [{\n      \"questionId\": 100,\n      \"answer\": \"120 kgs\"\n    }],\n    \"\
  specialRequirements\": \"\",\n    \"travellers\": [{\n      \"bandId\": 1,\n   \
  \   \"firstname\": \"Homer\",\n      \"surname\": \"Simpson Test\",\n      \"title\"\
  : \"Mr\",\n      \"leadTraveller\": true\n    }]\n  }]\n}\n```\n\n**Description\
  \ of JSON request parameters**\n\n| Object name | Element name | Type | Comments\
  \ | Mandatory |\n|-------------|--------------|:----:|----------|:---------:|\n\
  |        | `demo`      | boolean | If this is set to True, then it is a demo booking\
  \ only. Full demos do not send any notifications, are automatically confirmed and\
  \ OnRequest products become freesale products. Default value is true. Production\
  \ must have `demo` set to `false`. | ❌ |\n|        | `currencyCode` | string | The\
  \ currency the booking will be submitted in. You will be billed in this currency.\
  \ | ❌ |\n| `partnerDetail` | | object | Applicable only for extra partner detail\
  \ for either partner or merchant partner for sending partner specific information\
  \ | ❌ |\n|  | `distributorRef` | string | Merchant API partners must pass a `distributorRef`\
  \ at itinerary level in the `partnerDetails` object. The `distributorRef` passed\
  \ must be alphanumeric and unique to bookings made by the merchant. Passing an existing\
  \ `distributorRef`: If an existing distributorRef is passed, the booking with the\
  \ matching `distributorRef` will be returned in the response and a new booking will\
  \ not be made. The fields in the response are identical to the response for a new\
  \ booking.| ✅ |\n| `partnerItemDetail` |  | object | For extra partner detail at\
  \ an item level, for either partner or merchant partner. | ❌ |\n|  | `distributorItemRef`\
  \ | string | Merchant API partners must pass a `distributorItemRef` into the `partnerItemDetails`\
  \ object for each item in the items object. The `distributorItemRef` passed must\
  \ be alphanumeric and unique to the itinerary. | ✅ |\n| `booker` |  | object | The\
  \ information of the primary contact. This contact does not have to be a traveler.\
  \ | ✅ |\n|  | `email` | string | Email address of the primary contact | ❌ |\n| \
  \ | `homePhone` | string | Home phone number of the primary contact | ❌ |\n|  |\
  \ `firstname` | string | First name of the primary contact | ✅ |\n|  | `surname`\
  \ | string | Surname of the primary contact | ✅ |\n|  | `title` | string | Title\
  \ of the primary contact | ❌ |\n| `items` |  |  | Array of items in itinerary to\
  \ be booked | ✅ |\n|  | `productCode` | string | product code of the itinerary to\
  \ be booked | ✅ |\n|  | `tourGradeCode` | string | `tourGradeCode` of the item to\
  \ be booked. If tour grades are supplied in [/product](#operation/product), you\
  \ must allow the customer to select a tour grade code. If no tour grades are available\
  \ for the product, pass `\"DEFAULT\"`. | ✅ |\n|  | `languageOptionCode` | string\
  \ | The language service provided for this product that has been chosen for this\
  \ booking. Usually in the format langcode/Service eg `\"en/SERVICE_GUIDE\"`. If\
  \ the product details service [/product](#operation/product) for the product returns\
  \ a langService, this must be provided. | ✅&lt;br /&gt;(if `languageServices` are\
  \ provided in [/product](#operation/product)) |\n|  | `travelDate` | date | date\
  \ of travel for the item (format is YYYY-MM-DD; e.g. 2013-12-25) | ✅ |\n|  | `hotelId`\
  \ | string | If [/product](#operation/product) returns `hotelPickup`: `true` and\
  \ a list of hotels is available for this product in [/booking/hotels](#operation/bookingHotels),\
  \ a `hotelId` must be captured. The hotel id as per the hotel service (id field)\
  \ or use one of these alternative hotel ids:&lt;br /&gt;`local`: customer lives\
  \ locally&lt;br /&gt;`notBooked`:  Customer has not booked their hotel yet&lt;br\
  \ /&gt;`notListed`: Hotel not listed | ✅&lt;br /&gt;(if [/product](#operation/product)\
  \ returns `hotelPickup`: `true` for `productCode` and hotels available) |\n|  |\
  \ `pickupPoint` | string | Pickup point information related to hotel pickup. Details\
  \ of the hotel or pickup point must be provided if the `hotelId` selected by the\
  \ user is `\"notListed\"` or if no hotels are returned for the product in [/booking/hotels](#operation/bookingHotels)\
  \ where `hotelPickup`: `true` | ✅&lt;br /&gt;(if `hotelId` = `\"notListed\"` or\
  \ no hotels returned) |\n|  | `specialRequirements` | string | Capture any additional\
  \ requirements for the booking, such as dietary requirements or if a wheelchair\
  \ is required. Suggested workflow is if there are no `bookingQuestionAnswers` for\
  \ the product, to collect `specialRequirements`. | ❌ |\n| `travellers` |  |  | Array\
  \ of traveller names with a required lead traveller selected per item. | ✅ |\n|\
  \  | `bandId` | integer |  [Age band id](#section/Key-concepts/Working-with-age-bands).\
  \ Available age band details for the product is listed in [/product](#operation/product).\
  \ | ✅ |\n|  | `firstname` | string | First name of the traveller | ✅ |\n|  | `surname`\
  \ | string | Surname of the traveller | ✅ |\n|  | `title` | string | Title of the\
  \ traveller. Suggested options: Mr, Mrs, Ms, Miss, Mstr, Dr | ✅ |\n|  | `leadTraveller`\
  \ | boolean | Each item must have one traveller assigned as the lead traveller for\
  \ the tour. The lead traveller will have a value of true, all other travellers will\
  \ have a value of false. The lead traveller can have a mobile phone number added\
  \ to the booking. | ✅ |\n|  | `cellPhoneCountryCode` | string | Ideally only collect\
  \ the phone number country code for the lead traveller. Alternatively, collect the\
  \ phone number of the booker instead. | ❌ |\n|  | `cellPhone` | string | Ideally\
  \ only collect the phone number country code for the lead traveller. Alternatively,\
  \ collect the phone number of the booker instead. | ❌ |\n| `bookingQuestionAnswers`\
  \ |  | object | Answers to [booking questions](#section/Appendices/Booking-questions)\
  \ for the particular item. If a booking question is available in the `bookingQuestions`\
  \ array in [/product](#operation/product) for the product, the matching `bookingQuestionAnswers`\
  \ must be passed. If a product does not have any `bookingQuestion` items, you can\
  \ omit the `bookingQuestionAnswers` field completely. Any invalid or unnecessary\
  \ `bookingQuestionAnswers` that are passed to [/booking/book](#operation/bookingBook)\
  \ will be ignored (no exceptions will be raised) | ✅&lt;br /&gt;(if [/product](#operation/product)\
  \ returns `bookingQuestions`) |\n|  | `questionId` | integer | `questionId` (provided\
  \ in [/product](#operation/product)) | ✅ |\n|  | `answer` | string | Answer to the\
  \ question at the `questionId` listed. Recommended length for the answer is 500\
  \ characters. | ✅ |\n\n**JSON Response**\n\nThe prices returned in the booking response\
  \ represent the net rate, which is the amount merchant API partners will be invoiced\
  \ for. See [merchant pricing](#section/Key-concepts/Merchant-pricing) for more information.\n\
  \n### Booking errors\n\nA number of errors may be returned in the response to the\
  \ [/booking/book](#operation/bookingBook) service. If any errors are reported, NO\
  \ items will be booked, NO items/data will be returned in the response, and NO billing\
  \ will occur.\n\nThere are two error types:\n- `\"VALIDATION\"` - occurs if a required\
  \ field is missing or a field is not formatted properly\n- `\"EXCEPTION\"` - occurs\
  \ when there are issues with the booking date, product / tour grade code or the\
  \ payment.\n\nExample of an error message:\n\n```javascript\n{\n  \"data\": null,\n\
  \  \"vmid\": \"221001\",\n  \"errorMessage\": [ \"Missing distributor reference\"\
  \ ],\n  \"errorType\": \"EXCEPTION\",\n  \"dateStamp\": \"2013-04-24T15:50:05+0000\"\
  ,\n  \"errorReference\": \"~3713624959841553334512668\",\n  \"errorMessageText\"\
  : [\"Missing distributor reference\" ],\n  \"success\": false,\n  \"totalCount\"\
  : 1,\n  \"errorName\": \"Exception\"\n}\n```\n\nPlease see \"Standard JSON fields\"\
  \ in the Appendix for an explanation of the fields.\n\n| Scenario | `errorType`\
  \ | Example error message text |\n|----------|-----------|----------------------------|\n\
  | Lead traveller is not specified | `VALIDATION` | A traveler needs to be selected\
  \ as lead traveler. Lead Traveler's name must match credit card name. |\n| Traveller\
  \ names are not provided | `VALIDATION` | First name of traveler 1 is required,\
  \ Last name of traveler 1 is required |\n| No travellers provided | `VALIDATION`\
  \ | A traveler needs to be selected as lead traveler. Lead Traveler's name must\
  \ match credit card name. |\n| Product code does not exist | `EXCEPTION` | We're\
  \ sorry, we cannot find the tour, activity or attraction you are looking for\n|\
  \ Product code exists, but tour grade code does not exist | `EXCEPTION` | SICInvalidTourGrade\
  \ |\n| Booking date is in the past | `EXCEPTION` | We're sorry, the following tour\
  \ you are trying to book is sold out and no longer available: Grand Canyon All American\
  \ Helicopter Tour (2280AAHT) |\n| `languageOptionCode` is in the wrong format |\
  \ `EXCEPTION` | languageOptionCode should be LangCode/LangServices |\n| Missing\
  \ required answers for item | `EXCEPTION` | Additional questions missing |\n| Unsupported\
  \ currency | `EXCEPTION` | Could not lookup SGD:java.lang.RuntimeException: Could\
  \ not lookup SGDf:au.com.fim.v3.etravel.PiusRecordNotFoundException: No currency\
  \ found: select * from CurrencyFormat where currencyID = 'SGD' |\n| `distributorRef`\
  \ not provided in `partnerDetail` object | `EXCEPTION` | Missing distributor reference\
  \ |\n| `distributorItemRef` not provided in `partnerItemDetail` object | `EXCEPTION`\
  \ | Missing distributor item reference |\n| `partnerItemDetail` object not provided\
  \ for the item | `EXCEPTION` | Missing partner item details! |\n\n## Get the booking\
  \ status for multiple items\n\nThe [/booking/status](#operation/bookingStatus) service\
  \ retrieves the booking status for multiple items based on different criteria.\n\
  \nThis service can only be polled every 30 minutes. This would ideally be used in\
  \ software for bulk updates of pending itineraries.\n\nThe maximum number of results\
  \ returned is 1,000 itineraries. Narrow your search if you expect results greater\
  \ than this.\n\n**NOTE:** This will return both live and test bookings.\n\n**Example\
  \ request body**\n\n```javascript\n{\n  \"bookingDateFrom\": \"2013-03-22\",\n \
  \ \"bookingDateTo\": \"2013-03-25\",\n  \"itineraryIds\": null,\n  \"itemIds\":\
  \ null,\n  \"distributorRefs\": [\"Ref20132603_1\",\"Ref20132603_5\"],\n  \"distributorItemRefs\"\
  : null,\n  \"leadFirstName\": null,\n  \"leadSurname\": null,\n  \"test\": true\n\
  }\n```\n\nAll fields are optional and can be omitted, however at least one needs\
  \ to be provided.\n\n| Field | Meaning |\n|-------|---------|\n| `bookingDateFrom`\
  \ | The booking date is greater than or equal this date |\n| `bookingDateTo` | The\
  \ booking date is less than or equal this date |\n| `itemIds` | Array of item ids\
  \ (AKA Viator Item Reference) to check for; e.g., `[1234657,2345267,3245154]` |\n\
  | `distributorRefs` | Array of partner-defined distributor references; e.g., `[\"\
  ref1\",\"ref2\",\"ref3\"]` |\n| `distributorItemRefs` | Array of partner-defined\
  \ distributor item references; e.g., `[\"refItem1\",\"refItem2\",\"refItem3\"]`\
  \ |\n| `leadFirstName` | The lead traveller's first name |\n| `leadSurname` | The\
  \ lead traveller's surname |\n| `test` | Setting `test` to `true` will bypass the\
  \ poll limit on the sandbox environment only. The default value for `test` is `false`.\
  \ |\n\n**Example response object** ([/booking/status](#operation/bookingStatus))\n\
  \n```javascript\n{\n  \"data\": [\n  {\n    \"itineraryId\": 3332064,\n    \"bookingStatus\"\
  : {\n      \"type\": \"CONFIRMED\",\n      \"level\": \"ITINERARY\",\n      \"failed\"\
  : false,\n      \"text\": \"Confirmed\",\n      \"cancelled\": false,\n      \"\
  status\": 3,\n      \"confirmed\": true,\n      \"amended\": false,\n      \"pending\"\
  : false\n    },\n    \"bookingDate\": \"2013-03-25\",\n    \"distributorRef\": \"\
  Ref20132603_1\",\n    \"itemSummaries\": [{\n      \"itineraryId\": 3332064,\n \
  \     \"itemId\": 600088886,\n      \"bookingStatus\": {\n        \"type\": \"CONFIRMED\"\
  ,\n        \"level\": \"ITEM\",\n        \"failed\": false,\n        \"text\": \"\
  Paid &amp;amp; Confirmed\",\n        \"cancelled\": false,\n        \"status\":\
  \ 1,\n        \"confirmed\": true,\n        \"amended\": false,\n        \"pending\"\
  : false\n      },\n      \"travelDate\": \"2013-12-03\",\n      \"distributorItemRef\"\
  : \"ItemRefA\",\n      \"sortOrder\": 0\n    }],\n    \"sortOrder\": 1\n  },\n \
  \ {\n    \"itineraryId\": 3332076,\n    \"bookingStatus\": {\n      \"type\": \"\
  CONFIRMED\",\n      \"level\": \"ITINERARY\",\n      \"failed\": false,\n      \"\
  text\": \"Confirmed\",\n      \"cancelled\": false,\n      \"status\": 3,\n    \
  \  \"confirmed\": true,\n      \"amended\": false,\n      \"pending\": false\n \
  \   },\n    \"bookingDate\": \"2013-03-26\",\n    \"distributorRef\": \"Ref20132603_5\"\
  ,\n    \"itemSummaries\": [{\n      \"itineraryId\": 3332076,\n      \"itemId\"\
  : 600088907,\n      \"bookingStatus\": {\n        \"type\": \"CONFIRMED\",\n   \
  \     \"level\": \"ITEM\",\n        \"failed\": false,\n        \"text\": \"Paid\
  \ &amp;amp; Confirmed\",\n        \"cancelled\": false,\n        \"status\": 1,\n\
  \        \"confirmed\": true,\n        \"amended\": false,\n        \"pending\"\
  : false\n      },\n      \"travelDate\": \"2013-12-03\",\n      \"distributorItemRef\"\
  : \"ItemRefA\",\n      \"sortOrder\": 0\n    }],\n    \"sortOrder\": 2\n  }],\n\
  \  \"vmid\": \"221002\",\n  \"errorMessage\": null,\n  \"errorType\": null,\n  \"\
  dateStamp\": \"2013-03-26T10:25:57+0000\",\n  \"errorReference\": null,\n  \"errorMessageText\"\
  : null,\n  \"success\": true,\n  \"totalCount\": 2,\n  \"errorName\": null\n}\n\
  ```\n\n### Exceeding the poll limit\n\nYou will receive the following error if you\
  \ exceed the number of calls allowed to the service within the timeframe:\n\n```javascript\n\
  {\n  \"data\": null,\n  \"vmid\": \"221002\",\n  \"errorMessage\": [\n    \"Access\
  \ allowed every 30 minutes\"\n  ],\n  \"errorType\": \"EXCEPTION\",\n  \"dateStamp\"\
  : \"2013-03-26T10:28:51+0000\",\n  \"errorReference\": \"~55315512721712161381352771\"\
  ,\n  \"errorMessageText\": [\n    \"Access allowed every 30 minutes\"\n  ],\n  \"\
  success\": false,\n  \"totalCount\": 1,\n  \"errorName\": \"PollingDeniedException\"\
  \n}\n```\n\n## Get the tour grade pricing matrix\n\nThe [/booking/pricingmatrix](#operation/bookingPricingmatrix)\
  \ service retrieves the pricing matrix for tour grades, product age bands and pax\
  \ (passenger) mixes.\n\n**Example request object** ([/booking/pricingmatrix](#operation/bookingPricingmatrix))\n\
  \n```javascript\n  \"productCode\": \"5261HTLAP\",\n  \"tourGradeCode\": \"Zone\
  \ 1\",\n  \"bookingDate\": \"2013-12-01\",\n  \"currencyCode\": \"USD\",\n  \"specialReservation\"\
  : false\n```\n\n`bookingDate`: The date to check for pricing data. This is an optional\
  \ parameter for a normal product.\n\nIf the date is not provided then the nearest\
  \ available date is determined (i.e. not blocked out or unavailable for any reason)\n\
  \n**Example response object** ([/booking/pricingmatrix](#operation/bookingPricingmatrix))\n\
  \n```javascript\n{\n  \"data\": [{\n    \"pricingUnit\": \"per person\",\n    \"\
  bookingDate\": \"2013-12-01\",\n    \"sortOrder\": 1,\n    \"ageBandPrices\": [{\n\
  \      \"bandId\": 1,\n      \"prices\": [{\n        \"sortOrder\": 1,\n       \
  \ \"currencyCode\": \"USD\",\n        \"price\": 81.94,\n        \"priceFormatted\"\
  : \"$81.94\",\n        \"merchantNetPrice\": 65.44,\n        \"merchantNetPriceFormatted\"\
  : \"$65.44\",\n        \"minNoOfTravellersRequiredForPrice\": 1\n      }],\n   \
  \   \"sortOrder\": 1,\n      \"minimumCountRequired\": 1,\n      \"maximumCountRequired\"\
  : 1\n    }]\n  },\n  {\n    \"pricingUnit\": \"per person\",\n    \"bookingDate\"\
  : \"2013-12-01\",\n    \"sortOrder\": 2,\n    \"ageBandPrices\": [{\n      \"bandId\"\
  : 1,\n      \"prices\": [{\n        \"sortOrder\": 1,\n        \"currencyCode\"\
  : \"USD\",\n        \"price\": 40.97,\n        \"priceFormatted\": \"$40.97\",\n\
  \        \"merchantNetPrice\": 32.73,\n        \"merchantNetPriceFormatted\": \"\
  $32.73\",\n        \"minNoOfTravellersRequiredForPrice\": 1\n      }],\n      \"\
  sortOrder\": 1,\n      \"minimumCountRequired\": 2,\n      \"maximumCountRequired\"\
  : 2\n    }]\n  },\n  {\n    \"pricingUnit\": \"per person\",\n    \"bookingDate\"\
  : \"2013-12-01\",\n    \"sortOrder\": 3,\n    \"ageBandPrices\": [{\n      \"bandId\"\
  : 1,\n      \"prices\": [{\n        \"sortOrder\": 1,\n        \"currencyCode\"\
  : \"USD\",\n        \"price\": 27.32,\n        \"priceFormatted\": \"$27.32\",\n\
  \        \"merchantNetPrice\": 21.81,\n        \"merchantNetPriceFormatted\": \"\
  $65.44\",\n        \"minNoOfTravellersRequiredForPrice\": 1\n      }],\n      \"\
  sortOrder\": 1,\n      \"minimumCountRequired\": 3,\n      \"maximumCountRequired\"\
  : 3\n    }]\n  }],\n  \"errorReference\": null,\n  \"dateStamp\": \"2017-11-24T21:30:47+0000\"\
  ,\n  \"errorType\": null,\n  \"errorCodes\": null,\n  \"errorMessage\": null,\n\
  \  \"errorName\": null,\n  \"success\": true,\n  \"totalCount\": 3,\n  \"errorMessageText\"\
  : null,\n  \"vmid\": \"321050\"\n}\n```\n\n**Description of elements in JSON response\
  \ object**\n\n| Object | Element | Type | Comments | To be viewed by customer |\
  \ Required field |\n|--------|---------|------|----------|:------------------------:|:--------------:|\n\
  | `data`   | | object | main response object | ❌ | ✅ |\n|  | `sortOrder` | integer\
  \ | order in which to show the pricing | ✅ | ✅ |\n|  | `bookingDate` | date | booking\
  \ date criteria | ✅ | ✅ |\n|  | `pricingUnit` | string | unit for pricing: currently,\
  \ only \"per person\" is supported | ✅ | ✅ |\n| `ageBandPrices` | | object | available\
  \ age bands and their pricing | ❌ | ✅ |\n| | `sortOrder` | integer | sort order\
  \ for age band display | ✅ | ✅ |\n| | `bandId` | integer | **Note**: the numeric\
  \ `bandId` is associated with an age band description (e.g., `\"Adult\"`, `\"Infant\"\
  ` etc.) and a corresponding age range (e.g., from 12 to 99) - these details are\
  \ available from the [/product](#operation/product) service. See [Working with age\
  \ bands](#section/Key-concepts/Working-with-age-bands) | ❌ | ✅ |\n| | `minimumCountRequired`\
  \ | integer | minimum number of pricing units that apply to these prices | | ✅ |\n\
  | | `maximumCountRequired` | integer | maximum number of pricing units that apply\
  \ to these prices | | ✅ |\n| `prices` | | object | pricing available for the age\
  \ band (based on the min and max count requirements) | ✅ | ✅ |\n| | `currencyCode`\
  \ | string | currency of the pricing | ✅ | ✅ |\n| | `sortOrder` | integer | order\
  \ the pricing is to be shown within the `bandId` | ✅ | ✅ |\n| | `price` | number\
  \ | price in decimal format (for merchant API partners, this is the 'suggested sell\
  \ price') | ❌ | ✅ |\n| | `priceFormatted` | string | suggested sell price formatted\
  \ according to the currency selected (with two decimal places where applicable)\
  \ | ✅ | ✅ |\n| | `merchantNetPrice` | number | merchant net price in decimal format\
  \ | ❌ | ✅ |\n| | `merchantNetPriceFormatted` | string | merchant net price formatted\
  \ according to the selected currency | ❌ | ✅ |\n| | `minNoOfTravellersRequiredForPrice`\
  \ | integer | number of units that the pricing applies to (e.g., a `minNoOfTravellersRequiredForPrice`\
  \ of `3` means that the price is for three people) | ✅ | ✅ |\n\n\n\n## Dealing with\
  \ vouchers\n\nThe [/booking/voucher](#operation/bookingVoucher) service retrieves\
  \ details for a complete itinerary or a single itinerary item. The data is returned\
  \ as HTML that can be wrapped in a header/footer.\n\n### Sample URL parameters\n\
  \n`leadLastName=DP&amp;itemId=600033670`\n\nor\n\n`voucherKey=3299307:93c7f36a56b18ba1068787ba7fb7988da5c8ad08db77604110141ff21498603e:600033670`\n\
  \n### Key concepts\n\n#### `voucherKey`\n- Use either the `voucherKey` or the three\
  \ separate parameters.\n- If `voucherKey` is provided as well as other parameters,\
  \ then the `voucherKey` overrides the other parameters.\n- The `voucherKey` is obtained\
  \ from [/booking/mybookings](#operation/bookingMybookings) or in the [/booking/book](#operation/bookingBook)\
  \ response object when a booking is made.\n\n#### `fullHTML`\nThis is an optional\
  \ parameter: \n- If `true`, the full HTML (including `&lt;!DOCTYPE&gt;`, `&lt;html&gt;`\
  \ and `&lt;head&gt;` tags) will be returned.\n- If `false`, an HTML `&lt;div&gt;`\
  \ element will be returned.\n- The default for this parameter is `false`\n\n####\
  \ `mobileVoucher`\n- Optional parameter. Defaults to `true`. If `true`, the mobile\
  \ (cut down) voucher HTML is returned; otherwise, the full voucher HTML is returned\
  \ and `fullHTML` is ignored\n- This field should only be enabled for products that\
  \ have a `voucherOption` of `\"VOUCHER_E\"` (electronic voucher). Do not enable\
  \ `mobileVouchers` for paper vouchers (`voucherOption` of `\"VOUCHER_PAPER_ONLY\"\
  `) as no barcode is returned.\n- The voucher information is available in the responses\
  \ for:\n  - [/product](#operation/product)\n  - [/booking/book](#operation/bookingBook)\n\
  \  - [/booking/pastbooking](#operation/bookingPastbooking)\n  - [/booking/mybookings](#operation/bookingMybookings)\n\
  - Voucher information is also displayed under the **Redemption Info** heading in\
  \ the response from this service.\n\n**Example response object** ([/booking/voucher](#operation/bookingVoucher))\n\
  \n```javascript\n{\n  \"data\": \"&lt;div style=\\'line-height: 1.5;font-family:\\\
  'Arial\\',\\'Helvetica\\',\\'Verdana\\',sans-serif; font-size: 12px; padding: 0\
  \ 10px; border-bottom: 1pxsolid #CAE2EA;\\'&gt;&lt;h2 style=\\'font-size:16px;font-weight:bold;margin:0.5em\
  \ 0;padding:0;\\'&gt;San FranciscoBay Sunset Catamaran Cruise &amp;reg;&lt;/h2&gt;&lt;h2\
  \ style=\\'font-size:16px;font-weight:bold;margin:0.5em0;padding:0;\\'&gt;SAMPLE\
  \ ONLY&lt;/h2&gt;&lt;ul style=\\'margin:0 0 1em 1em; padding:0;\\'&gt; &lt;li&gt;&lt;strong&gt;Date:&lt;/strong&gt;Friday\
  \ April 13, 2012 &lt;/li&gt;&lt;li&gt;&lt;strong&gt;Time:&lt;/strong&gt;&lt;strong&gt;2011:&lt;/strong&gt;&lt;br&gt;&lt;ul&gt;&lt;li&gt;&lt;strong&gt;Nov.\
  \ 6 to Nov. 27&lt;/strong&gt;: 4:00pm (Fri., Sat. &amp;amp; Sun)&lt;/li&gt;&lt;/ul&gt;&lt;p&gt;&lt;strong&gt;2012:&lt;/strong&gt;&lt;/p&gt;&lt;ul&gt;&lt;li&gt;&lt;strong&gt;March\
  \ 2 to March 10:&lt;/strong&gt;&amp;nbsp; 5:00 pm (Fri., Sat. &amp;amp; Sun)&lt;/li&gt;&lt;li&gt;&lt;strong&gt;March\
  \ 11 to April 15:&lt;/strong&gt; 6:00pm Daily&lt;/li&gt;&lt;li&gt;&lt;strong&gt;April\
  \ 16 to May 20:&lt;/strong&gt; 6:30 pm Daily&lt;/li&gt;&lt;li&gt;&lt;strong&gt;May\
  \ 21 to July 22:&lt;/strong&gt; 7:00 pm Daily&lt;/li&gt;&lt;li&gt;&lt;strong&gt;July\
  \ 23 to Aug 26: &lt;/strong&gt;6:30 pm Daily&lt;/li&gt;&lt;li&gt;&lt;strong&gt;Aug\
  \ 27 to Sept 23:&lt;/strong&gt;6:00 pm Daily&lt;/li&gt;&lt;li&gt;&lt;strong&gt;Sept.\
  \ 24 to Nov. 3:&lt;/strong&gt; 5:30 pm Daily&lt;/li&gt;&lt;li&gt;&lt;strong&gt;Nov\
  \ 4 to Dec 2:&lt;/strong&gt; 4:00pm (Friday, Sat., &amp;amp; Sun.)&lt;/li&gt;&lt;/ul&gt;&lt;p&gt;Please\
  \ arrive 30 minutes prior to cruise departure.&lt;/li&gt;&lt;/ul&gt; &lt;ul style=\\\
  'margin:0 0 1em 1em; padding:0;\\'&gt; &lt;li&gt;&lt;strong&gt;Lead Traveler: &lt;/strong&gt;\
  \ jos dp&lt;/li&gt;&lt;li&gt;&lt;strong&gt;Number of Travelers: &lt;/strong&gt;\
  \ 1 Adult&lt;/li&gt; &lt;li&gt;&lt;strong&gt;Booking Reference: &lt;/strong&gt;VIATOR600033672&lt;/li&gt;&lt;li&gt;&lt;strong&gt;Product\
  \ Code: &lt;/strong&gt;2316SUN&lt;/li&gt;&lt;li&gt;&lt;strong&gt;Confirmation Details:&lt;/strong&gt;SUN\
  \ &lt;/li&gt; &lt;li&gt;&lt;strong&gt;Location &lt;/strong&gt;&lt;div&gt;&lt;p&gt;Pier\
  \ 39&lt;/p&gt;&lt;/div&gt;&lt;div&gt;&lt;/div&gt;&lt;div&gt;When you get to Pier\
  \ 39, stand on the sidewalk &amp;amp; look towards the water, do NOT go down the\
  \ center wherethe shops are, but take the left OUTSIDE walkway. Go towards the sea\
  \ lions &amp;amp; look for a gate with the letter J on it&lt;/div&gt;&lt;/li&gt;&lt;/ul&gt;&lt;h3\
  \ style=\\'font-size:14px;font-weight:bold;margin:0.5em 0;padding:0;\\'&gt; Redemption\
  \ Info&lt;/h3&gt;&lt;ul style=\\'margin:0 0 1em 1em; padding:0;\\'&gt; &lt;li&gt;You\
  \ can present either a paper or an electronic voucherfor this activity. &lt;/li&gt;\
  \ &lt;/ul&gt; &lt;h3 style=\\'font-size:14px;font-weight:bold;margin:0.5em 0;padding:0;\\\
  '&gt;Important&lt;/h3&gt; &lt;ul&gt;&lt;li&gt;Your local contact is Adventure Cat\
  \ Sailing Charters on +1 800 498 4228.&lt;/li&gt;&lt;li&gt;Please note: You mustreconfirm\
  \ directly with Adventure Cat Sailing Charters at &lt;ul&gt; &lt;li&gt;Locally on\
  \ 415 777 1630&lt;/li&gt;&lt;/ul&gt; at least 24 Hour(s)prior to your tour/activity\
  \ date. If you are not arriving within the specified timeframe, please contact Adventure\
  \ CatSailing Charters prior to your travels, or immediately upon arrival at your\
  \ destination.&lt;/li&gt;&lt;/ul&gt;&lt;ul&gt;&lt;li&gt;Duringthe months of March,\
  \ April and November, the weather in San Francisco can be unpredictable and sailings\
  \ are subject tocancellation or rescheduling. Please ensure that you call the operator\
  \ 1 day prior to sailing to confirm your tour&lt;/li&gt;&lt;/ul&gt;&lt;h3 style=\\\
  'font-size:14px;font-weight:bold;margin:0.5em 0;padding:0;\\'&gt;Inclusions&lt;/h3&gt;&lt;ul&gt;&lt;li&gt;1.5-hour\
  \ Sunset Cruise&lt;/li&gt;&lt;li&gt;Light hors d\\'oeuvres&lt;/li&gt;&lt;li&gt;Two\
  \ complimentary drinks&lt;/li&gt;&lt;/ul&gt;&lt;h3 style=\\'font-size:14px;font-weight:bold;margin:0.5em\
  \ 0;padding:0;\\'&gt;Terms and Conditions &lt;/h3&gt; Read our completeTerms &amp;\
  \ Conditions for information on cancellations, date changes and other modifications\
  \ to this confirmed reservation. &lt;/div&gt;&lt;!-- end of voucher_item --&gt;&lt;/div&gt;\"\
  ,\n  \"vmid\": \"221001\",\n  \"errorMessage\": null,\n  \"errorType\": null,\n\
  \  \"dateStamp\": \"2012-04-13T10:40:47+0000\",\n  \"success\": true,\n  \"errorReference\"\
  : null,\n  \"errorMessageText\": null,\n  \"totalCount\": 1,\n  \"errorName\": null\n\
  }\n```\n\n## Reviewing bookings\n\nThe [/booking/pastbooking](#operation/bookingPastbooking)\
  \ service gets the details of a single specific past booking based on the `voucherKey`\
  \ or `itemId` passed into it.\n\n### Sample query Parameters\n\n`\"email=john.doe@viator.com&amp;itemId=600033670\"\
  `\n\nor\n\n`\"voucherKey=3299307:93c7f36a56b18ba1068787ba7fb7988da5c8ad08db77604110141ff21498603e:600033670\"\
  `\n\n### Key concepts\n#### Email\n\nThe email address passed must match the email\
  \ address associated to the itinerary\n\n#### Departure Details\n\nDeparture details,\
  \ such as the `departurePoint`, `departurePointAddress` and `departurePointDirections`,\
  \ will be included in the response. These fields may contain HTML escape characters,\
  \ such as `&amp;amp;` and special characters that are escaped by a backslash. Ensure\
  \ that these fields are parsed after receiving the response, or it may cause your\
  \ JSON to be invalid.\n\n\n**Example response object** ([/booking/pastbooking](#operation/bookingPastbooking)):\n\
  \n```javascript\n{\n  \"errorReference\": null,\n  \"data\": {\n    \"sortOrder\"\
  : 0,\n    \"rulesApplied\": null,\n    \"bookingStatus\": {\n      \"status\": 3,\n\
  \      \"text\": \"Confirmed\",\n      \"type\": \"CONFIRMED\",\n      \"level\"\
  : \"ITINERARY\",\n      \"confirmed\": true,\n      \"pending\": false,\n      \"\
  amended\": false,\n      \"cancelled\": false,\n      \"failed\": false\n    },\n\
  \    \"itemSummaries\": [{\n      \"sortOrder\": 0,\n      \"rulesApplied\": null,\n\
  \      \"bookingStatus\": {\n        \"status\": 1,\n        \"text\": \"Paid &amp;amp;\
  \ Confirmed\", \"type\": \"CONFIRMED\",\n        \"level\": \"ITEM\",\n        \"\
  failed\": false,\n        \"confirmed\": true,\n        \"amended\": false,\n  \
  \      \"pending\": false,\n        \"cancelled\": false\n      },\n      \"travellerAgeBands\"\
  : [{\n        \"sortOrder\": 0,\n        \"count\": 2,\n        \"pluralDescription\"\
  : \"Adults\",\n        \"description\": \"Adult\",\n        \"ageBandId\": 1\n \
  \     }],\n      \"voucherKey\": \"1000308214:899757cf8b419ed11f39045636b0b30af986d19126d04547097f4b9c05fb4b69:700179574\"\
  ,\n      \"voucherURL\": \"https://viatorapi.sandbox.viator.com/service/merchant/voucher.jspa?code=1000308214:899757cf8b419ed11f39045636b0b30af986d19126d04547097f4b9c05fb4b69:700179574&amp;embedResources=false\"\
  ,\n      \"voucherRequirements\": \"You must present a paper voucher for this tour.\
  \ We will email a link to access and print your voucher at the Lead Travelers email\
  \ address.\",\n      \"productPulledDown\": false,\n      \"merchantCancellable\"\
  : true,\n      \"productWidgetList\": null,\n      \"savingAmount\": 0,\n      \"\
  vouchers\": null,\n      \"passbooks\": null,\n      \"termsAndConditions\": null,\n\
  \      \"itineraryId\": 1000308214,\n      \"productCode\": \"2065CPT\",\n     \
  \ \"tourGradeCode\": \"1DAY\",\n      \"distributorItemRef\": \"distroItemRefJDP1006151732\"\
  ,\n      \"languageServicesLanguageCode\": \"en\",\n      \"travelDate\": \"2015-09-03\"\
  ,\n      \"price\": 26.28,\n      \"leadTravellerSurname\": \"Test\",\n      \"\
  barcodeOption\": \"tour\",\n      \"barcodeType\": \"code128\",\n      \"destId\"\
  : 318,\n      \"voucherOption\": \"VOUCHER_PAPER_ONLY\",\n      \"productTitle\"\
  : \"City Sightseeing Cape Town Hop-On Hop-Off Tour\",\n      \"itemId\": 700179574,\n\
  \      \"obfsId\": 27643,\n      \"departurePoint\": \"Tour starts at V&amp;amp;A\
  \ Waterfront, outside the Two Oceans Aquarium, however you may board the bus at\
  \ any one of the stops throughout the city (see the Itinerary section below for\
  \ a list of stops)\",\n      \"departurePointAddress\": \"\",\n      \"departurePointDirections\"\
  : \"\",\n      \"leadTravellerTitle\": \"Mr\",\n      \"leadTravellerFirstname\"\
  : \"Homer\",\n      \"lastRetailPrice\": 26.28,\n      \"bookingEngineId\": \"UF\"\
  ,\n      \"priceFormatted\": \"$26.28\",\n      \"savingAmountFormated\": \"\",\n\
  \      \"merchantNetPrice\": 26.28,\n      \"merchantNetPriceFormatted\": \"$26.28\"\
  ,\n      \"currencyCode\": \"USD\",\n      \"lastRetailPriceFormatted\": \"$26.28\"\
  ,\n      \"departsFrom\": \"Cape Town, South Africa\",\n      \"tourGradeDescription\"\
  : \"1-Day Bus Tour (1DAY)\",\n      \"hoursConfirmed\": 0,\n      \"priceUSD\":\
  \ 26.28\n    }],\n    \"voucherURL\": \"https://viatorapi.sandbox.viator.com/service/merchant/voucher.jspa?code=1000308214:899757cf8b419ed11f39045636b0b30af986d19126d04547097f4b9c05fb4b69&amp;embedResources=false\"\
  ,\n    \"voucherKey\": \"1000308214:899757cf8b419ed11f39045636b0b30af986d19126d04547097f4b9c05fb4b69\"\
  ,\n    \"bookerEmail\": \"jocelyn@viator.com\",\n    \"itineraryId\": 1000308214,\n\
  \    \"exchangeRate\": 1,\n    \"distributorRef\": \"distroRefJDP1006151732\",\n\
  \    \"totalPrice\": 26.28,\n    \"bookingDate\": \"2015-06-10\",\n    \"totalPriceFormatted\"\
  : \"$26.28\",\n    \"totalPriceUSD\": 26.28,\n    \"hasVoucher\": true,\n    \"\
  userId\": null,\n    \"currencyCode\": \"USD\"\n  }\n}\n\n```\n\n\n## Checking bookings\n\
  \nThe [/booking/mybookings](#operation/bookingMybookings) service gets a user's\
  \ future bookings; i.e., those with travel dates in the future. This service can\
  \ also be used to check the status of a booking.\n\n### Key concepts\n#### Sample\
  \ URL parameters\n\n- `\"sessionId=xxx\"`, or\n- `\"voucherKey=xxx\"`, or\n- `\"\
  email=terry.smith@viator.com&amp;lastCCFourDigits=4242\"`, or\n- `\"email=terry.smith@viator.com&amp;itineraryOrItemId=3299307\"\
  `\n\nProvide *one* of:\n- a `sessionId` for all bookings related to a user account,\
  \ or\n- a `voucherKey`, or\n- an email address (`email`) and the last four digits\
  \ of the credit card number (`lastCCFourDigits`) used to make the booking to get\
  \ all associated bookings, or\n- an email address (`email`) and `itemId`\n\n...in\
  \ that order\n\nFor `\"Failed\"` items, display a message that communicates the\
  \ following information to your customers:\n\n&lt;pre&gt;\"The booking has failed\
  \ either because this tour or activity was not available or there was a technical\
  \ issue. Please contact Customer Service if you need more information.\"&lt;/pre&gt;\n\
  \n**See also**: [Booking and item status list](#section/Appendix/bookingStatus-field-values-and-meanings)\n\
  \n#### Departure details\n\nDeparture details, such as the `departurePoint`, `departurePointAddress`\
  \ and `departurePointDirections` will be included in the response. These fields\
  \ may contain HTML escape characters, such as `&amp;amp;` and special characters\
  \ that are escaped using a backslash. Ensure that these fields are parsed after\
  \ receiving the response or it may cause your JSON to be invalid.\n\n**Example response\
  \ object** ([/booking/mybookings](#operation/bookingMybookings)):\n\n```javascript\n\
  {\n  \"errorReference\": null,\n  \"data\": {\n    \"sortOrder\": 0,\n    \"rulesApplied\"\
  : null,\n    \"bookingStatus\": {\n      \"status\": 3,\n      \"text\": \"Confirmed\"\
  ,\n      \"type\": \"CONFIRMED\",\n      \"level\": \"ITINERARY\",\n      \"confirmed\"\
  : true,\n      \"pending\": false,\n      \"amended\": false,\n      \"cancelled\"\
  : false,\n      \"failed\": false\n    },\n    \"itemSummaries\": [{\n      \"sortOrder\"\
  : 0,\n      \"rulesApplied\": null,\n      \"bookingStatus\": {\n        \"status\"\
  : 1,\n        \"text\": \"Paid &amp;amp; Confirmed\",\n        \"type\": \"CONFIRMED\"\
  ,\n        \"level\": \"ITEM\",\n        \"failed\": false,\n        \"confirmed\"\
  : true,\n        \"amended\": false,\n        \"pending\": false,\n        \"cancelled\"\
  : false\n      },\n      \"travellerAgeBands\": [{\n        \"sortOrder\": 0,\n\
  \        \"count\": 2,\n        \"pluralDescription\": \"Adults\",\n        \"description\"\
  : \"Adult\",\n        \"ageBandId\": 1\n      }],\n      \"voucherKey\": \"1000308214:899757cf8b419ed11f39045636b0b30af986d19126d04547097f4b9c05fb4b69:700179574\"\
  ,\n      \"voucherURL\": \"https://viatorapi.sandbox.viator.com/service/merchant/voucher.jspa?code=1000308214:899757cf8b419ed11f39045636b0b30af986d19126d04547097f4b9c05fb4b69:700179574&amp;embedResources=false\"\
  ,\n      \"voucherRequirements\": \"You must present a paper voucher for this tour.\
  \ We will email a link to access and print your voucher at the Lead Travelers email\
  \ address.\",\n      \"productPulledDown\": false,\n      \"merchantCancellable\"\
  : true,\n      \"productWidgetList\": null,\n      \"savingAmount\": 0,\n      \"\
  vouchers\": null,\n      \"passbooks\": null,\n      \"termsAndConditions\": null,\n\
  \      \"itineraryId\": 1000308214,\n      \"productCode\": \"2065CPT\",\n     \
  \ \"tourGradeCode\": \"1DAY\",\n      \"distributorItemRef\": \"distroItemRefJDP1006151732\"\
  ,\n      \"languageServicesLanguageCode\": \"en\",\n      \"travelDate\": \"2015-09-03\"\
  ,\n      \"price\": 26.28,\n      \"leadTravellerSurname\": \"Test\",\n      \"\
  barcodeOption\": \"tour\",\n      \"barcodeType\": \"code128\",\n      \"destId\"\
  : 318,\n      \"voucherOption\": \"VOUCHER_PAPER_ONLY\",\n      \"productTitle\"\
  : \"City Sightseeing Cape Town Hop-On Hop-Off Tour\",\n      \"itemId\": 700179574,\n\
  \      \"obfsId\": 27643,\n      \"departurePoint\": \"Tour starts at V&amp;amp;A\
  \ Waterfront, outside the Two Oceans Aquarium, however you may board the bus at\
  \ any one of the stops throughout the city (see the Itinerary section below for\
  \ a list of stops)\",\n      \"departurePointAddress\": \"\",\n      \"departurePointDirections\"\
  : \"\",\n      \"leadTravellerTitle\": \"Mr\",\n      \"leadTravellerFirstname\"\
  : \"Homer\",\n      \"lastRetailPrice\": 26.28,\n      \"bookingEngineId\": \"UF\"\
  ,\n      \"priceFormatted\": \"$26.28\",\n      \"savingAmountFormatted\": \"\"\
  ,\n      \"merchantNetPrice\": 26.28,\n      \"merchantNetPriceFormatted\": \"$26.28\"\
  ,\n      \"currencyCode\": \"USD\",\n      \"lastRetailPriceFormatted\": \"$26.28\"\
  ,\n      \"departsFrom\": \"Cape Town, South Africa\",\n      \"tourGradeDescription\"\
  : \"1-Day Bus Tour (1DAY)\",\n      \"hoursConfirmed\": 0,\n      \"priceUSD\":\
  \ 26.28\n    }],\n    \"voucherURL\": \"https://viatorapi.sandbox.viator.com/service/merchant/voucher.jspa?code=1000308214:899757cf8b419ed11f39045636b0b30af986d19126d04547097f4b9c05fb4b69&amp;embedResources=false\"\
  ,\n    \"voucherKey\": \"1000308214:899757cf8b419ed11f39045636b0b30af986d19126d04547097f4b9c05fb4b69\"\
  ,\n    \"bookerEmail\": \"jocelyn@viator.com\",\n    \"itineraryId\": 1000308214,\n\
  \    \"exchangeRate\": 1,\n    \"distributorRef\": \"distroRefJDP1006151732\",\n\
  \    \"totalPrice\": 26.28,\n    \"bookingDate\": \"2015-06-10\",\n    \"totalPriceFormatted\"\
  : \"$26.28\",\n    \"totalPriceUSD\": 26.28,\n    \"hasVoucher\": true,\n    \"\
  userId\": null,\n    \"currencyCode\": \"USD\"\n  },\n  \"dateStamp\": \"2015-06-10T00:33:24+0000\"\
  , \"errorType\": null,\n  \"errorMessage\": null,\n  \"errorName\": null,\n  \"\
  success\": true,\n  \"totalCount\": 1,\n  \"vmid\": \"321004\",\n  \"errorMessageText\"\
  : null\n}\n```\n\n# Testing\n\n## Postman collection for testing\n\nTo facilitate\
  \ your testing of the APIs functionality in the sandbox environment, please use\
  \ the following file, which can be loaded into the [Postman](https://www.getpostman.com/)\
  \ API development environment via its **import** function:\n\n  - [Merchant partner\
  \ API Postman collection](https://docs.viator.com/partner-api/resources/merchant/technical/postman/Viator-API-merchant-Postman.json)\n\
  \n### Setting up API-key authentication in Postman\n\nBefore you start using the\
  \ linked Postman collection for testing, you will need to set up the authorization\
  \ method you wish to use. This can be either the new method (the `exp-api-key` &lt;u&gt;header&lt;/u&gt;\
  \ parameter) or, the legacy method (the `apiKey` &lt;u&gt;query&lt;/u&gt; parameter).\n\
  \nWhile both methods remain available, we strongly recommend that you use the new\
  \ method, as it:\n\n1. Provides access to all languages available for your organization\
  \ with a single API-key as opposed to one API-key per language\n2. Allows access\
  \ to the new [booking cancellation endpoints](#section/Common-workflows-and-data-validation/Cancellation-API-workflow),\
  \ as well as all newly-created endpoints in future\n \nPlease speak to your account\
  \ manager if you are still using the legacy apiKey and would like to switch to our\
  \ new authentication mechanism.\n\n#### How to set up the new exp-api-key header\
  \ parameter\n\n1. Select **Edit** from the collection menu:\n\n![postman-testing-1](/partner-api/resources/merchant/technical/img/postman-testing-1.png)\n\
  \n2. Set the following values:\n\n* **Key**: `exp-api-key`\n* **Value**: Your organization's\
  \ single exp-api-key, which will have an identical format to that shown in the image\
  \ below\n* **Add to**: Header\n\n![postman-testing-2](/partner-api/resources/merchant/technical/img/postman-testing-2.png)\n\
  \n3. Click **Update**\n\n#### How to set up the legacy apiKey query parameter\n\n\
  1. Select **Edit** from the collection menu:\n\n![postman-testing-1](/partner-api/resources/merchant/technical/img/postman-testing-1.png)\n\
  \n2. Set the following values:\n\n* **Key**: `apiKey`\n* **Value**: One of your\
  \ organization's legacy apiKeys, which will have an identical format to that shown\
  \ in the image below\n* **Add to**: Query Params\n\n![postman-testing-3](/partner-api/resources/merchant/technical/img/postman-testing-2.png)\n\
  \n3. Click **Update**\n\n# FAQs\n\n**Is a confirmation email sent to the customer\
  \ or supplier when a booking is made in the sandbox environment?**\n\n* No.\n\n\
  **How do I make a demo booking?**\n\n* To make a demo booking, make sure you set\
  \ `demo` to `true` in your request to the [/booking/book](#operation/bookingBook)\
  \ service.\n\n**What should I do if I successfully create a test booking in the\
  \ Live environment?**\n\n* Firstly, please don't make test bookings in the Live\
  \ environment, as doing so may cause a confirmation email to be sent to the product\
  \ supplier. Nonetheless, if you have made a test booking, cancel it using the [/bookings/{id}/cancel](#operation/cancelBooking)\
  \ service; or, send an email to dpsupport@viator.com and include both \"CANCEL\"\
  \ and the booking reference number in the subject line.\n\n**Which currencies can\
  \ I use when making a booking?**\n\n* You can make a booking using the [/booking/book](#operation/bookingBook)\
  \ endpoint using any of the [supported currencies](#section/Appendices/Supported-currency-codes).\n\
  * If you attempt to use a non-supported currency, you will receive an error message\
  \ similar to the following:\n\n```json\n{\n  \"errorReference\": \"3D45567E:2D4A_0A5D033A:01BB_5F616D10_1FBBC9:7035\"\
  ,\n  \"data\": null,\n  \"dateStamp\": \"2020-09-15T18:41:00+0000\",\n  \"errorType\"\
  : \"EXCEPTION\",\n  \"errorCodes\": [\n    \"UNKNOWN_ERROR\"\n  ],\n  \"errorMessage\"\
  : [\n    \"Merchant API does not allow the specified currency\"\n  ],\n  \"errorName\"\
  : \"RuntimeException\",\n  \"extraInfo\": {},\n  \"extraObject\": null,\n  \"success\"\
  : false,\n  \"totalCount\": 1,\n  \"errorMessageText\": [\n    \"Merchant API does\
  \ not allow the specified currency\"\n  ],\n  \"vmid\": \"331001\"\n}\n```\n\n**Why\
  \ am I having an SSL handshake issue?**\n\n* It may be that your SSL certificates\
  \ have expired. Check this. Also, if you are using Java, make sure that it's [updated\
  \ to the latest version](https://www.java.com/en/download/).\n\n**What is the difference\
  \ between `merchantNetPrice` and `price` in the response from the [/search/products](#operation/searchProducts)\
  \ service?**\n\n* `merchantNetPrice` is the amount you, as the merchant partner,\
  \ will be invoiced for, excluding any fees.\n* `price` is the price at which Viator\
  \ sells the product\n\n**Why is a different price displayed in [/booking/availability/tourgrades](#operation/bookingAvailabilityTourgrades)\
  \ and [/product](#operation/product)**\n\n* [/product](#operation/product) displays\
  \ the lowest possible price per traveller; whereas, [/booking/availability/tourgrades](#operation/bookingAvailabilityTourgrades)\
  \ shows the per-traveller price based on the age-band and number of travellers within\
  \ that age-band.\n\n**A destination is missing its latitude, longitude or time zone**\n\
  \n* Some destinations in the **sandbox** environment may be missing geolocation\
  \ or time zone data. However, if you encounter a destination in the **Live** environment\
  \ with missing information, this can be regarded as an unintended omission – please\
  \ contact us so that we can update our destination information.\n\n**How do I make\
  \ a test booking?**\n\nTo make a test booking, make sure you:\n\n- set `firstname`\
  \ and/or `surname` in the `booker` object to `'test'`.\n- set `demo` to `true`\n\
  \nExample:\n\n```javascript\n{\n  \"demo\": true,\n  \"currencyCode\": \"USD\",\n\
  \  \"partnerDetail\": {\n    \"distributorRef\": \"distroRef0412141435\"\n  },\n\
  \  \"booker\": {\n    \"email\": \"apitest@viator.com\",\n    \"firstname\": \"\
  Test\",\n    \"surname\": \"Test\",\n    \"title\": \"Mr\"\n  },\n  \"items\": [{\n\
  \    \"partnerItemDetail\": {\n      \"distributorItemRef\": \"distroItemRef0412141435_1\"\
  \n    },\n    \"hotelId\": null,\n    \"pickupPoint\": null,\n    \"travelDate\"\
  : \"2015-03-31\",\n    \"productCode\": \"2916ROME\",\n    \"tourGradeCode\": \"\
  24HR\",\n    \"languageOptionCode\": \"en/SERVICE_GUIDE\",\n    \"bookingQuestionAnswers\"\
  : [{\n      \"questionId\": 100,\n      \"answer\": \"120 kgs\"\n    }],\n    \"\
  specialRequirements\": \"\",\n    \"travellers\": [{\n      \"bandId\": 1,\n   \
  \   \"firstname\": \"Homer\",\n      \"surname\": \"Simpson Test\",\n      \"title\"\
  : \"Mr\",\n      \"leadTraveller\": true\n    }]\n  }]\n}\n```\n\n**Is it possible\
  \ to use a custom value for `distributorRef` and `distributorItemRef`**\n\n* Yes!\
  \ In fact, this is what you're supposed to do. You can pass anything you like in\
  \ these fields; however, if you use a `distributorRef` that has already been used,\
  \ the API will return the previous booking made with that `distributorRef` rather\
  \ than creating a new booking.\n* **Note**: `distributorRef` must be fewer than\
  \ 40 characters\n\n**What are some common reasons for bookings to fail in the Viator\
  \ API?**\n\n- `homePhone` or any phone field in the booking request contains spaces.\
  \ The only acceptable non-numeric characters are: “-“,  “+” , “(“,  and “)”\n\n\
  - `distributorRef` has been re-used.  When making a booking request, a `distributorRef`\
  \ and `distributorItemRef` must be provided. This is the partner’s ID for the booking,\
  \ and it must be unique. If a `distributorRef` has been re-used, a booking will\
  \ not be made and instead, the existing booking will be returned in the response.\n\
  \n- `distributorRef` exceeds 40 characters\n\n- No traveller or an incorrect traveller\
  \ has been set as the lead traveller in the booking request;\n  + `leadTraveller`:`true`\
  \ must be set for one traveller\n  + the `leadTraveller` must be from an `ageBand`\
  \ that has `treatAsAdult` set to `true`. The data is available in the `ageBands`\
  \ object in the product details service.\n\n- `languageOptionCode` is invalid\n\
  \  + To find the valid language option codes for a particular product, have a look\
  \ at the `langServices` object in the response from the [/product](#operation/product)\
  \ service; e.g.,\n\n```javascript\n\"langServices\": {\n  \"en/SERVICE_AUDIO\":\
  \ \"English - Audio\"\n}\n```\n  + You must then ensure that the `languageOptionCode`\
  \ in the request to the [/booking/book](#operation/bookingBook) service is populated\
  \ in the same way; i.e.,\n\n```javascript\n\"languageOptionCode\": \"en/SERVICE_AUDIO\"\
  \n```\n\n**What does it mean if I receive a \"Section level access denied\" error\
  \ message?**\n\n- This means that your API-key does not have the correct permissions\
  \ to access the particular service you were attempting to access when you received\
  \ this error message. If you feel you would like to use this service nonetheless\
  \ in your implementation, please contact your account manager to discuss having\
  \ access granted.\n\n**What does it mean if I receive a \"503 Service Unavailable\"\
  \ response?**\n\n- This means that there was a temporary service outage on our end\
  \ at that time. We recommend that you re-try the operation until you no longer receive\
  \ this error.\n\n**Does API rate limiting apply to all services?**\n\n- Yes, it\
  \ does. Regardless of the service you are making requests to, the fundamental rate\
  \ limits apply equally.\n\n**Can I cancel multiple bookings or items at the same\
  \ time using the Viator API?**\n\n- No, you may only cancel one booking at a time.\n\
  \n**How many concurrent requests can be made of the API from the same IP address?**\n\
  \n- Three.\n\n**Will my API-key expire?**\n\n- If any API-key is not used for a\
  \ period of six months, that key is automatically deactivated as a security measure.\
  \ If this has happened to you, contact your account manager to have the key reactivated\
  \ or a new key issued to you.\n\n**Why am I getting an empty response when checking\
  \ booking details?**\n\n- If you are attempting to check a booking using the [/booking/status](#operation/bookingStatus)\
  \ or [/booking/status/items](#operation/bookingStatusItems) endpoints and receive\
  \ an empty response, it may be that the booking was made with the demo parameter\
  \ set to `true`, as the booking status endpoints will ignore demo bookings. Please\
  \ try making the booking again, ensuring the demo parameter is set to `false`. If\
  \ this also fails, please email dpsupport@viator.com and include a copy of the request\
  \ and response JSON objects.\n\n**Must I always provide details for all travelers\
  \ when booking a product where `allTravellerNamesRequired`=`true`?**\n\n- Approximately\
  \ 45% of the products in our catalog require all traveller details to be supplied\
  \ at the time of booking, and this requirement is enforced by the API. While it\
  \ is technically possible to bypass this requirement – for example, by setting the\
  \ lead traveler's name, but using dummy values for the the remaining travelers'\
  \ details ('traveler 2', etc.) – we strongly advise against this, as it can cause\
  \ problems for suppliers for whom this is a strict requirement. Examples include:\
  \ Alcatraz tickets, theme park tickets that require a QR code, bookings for flights\
  \ needing to meet TSA requirements; or, vehicle, Segway or jet-ski rentals. If you\
  \ are unable to implement the collection of all traveler details on your site, we\
  \ recommend filtering-out products where this is a strict requirement. You may also\
  \ request that we filter-out these products for you so that they do not appear in\
  \ product search results.\n\n**Must I always provide answers to the required booking\
  \ questions when making a booking?**\n\n- Yes. You must provide answers to all necessary\
  \ booking questions when making a booking. Approximately 40% of the products in\
  \ our catalog have booking questions, some of which may be necessary to fulfil the\
  \ suplier's legal requirements. In the case that the customer cannot provide specific\
  \ details at the time of booking – e.g., a departure flight number – they may enter\
  \ 'unknown' and the supplier will manually send a follow-up message to ask for this\
  \ information.\n\n**Why is there such a big difference in price between that given\
  \ in the product endpoints and the actual price at the time of booking?**\n\n- The\
  \ price returned in the product endpoints is the 'From Price', which is the &lt;u&gt;lowest\
  \ possible price&lt;/u&gt; for an adult passenger when taking into account all available\
  \ tour grades, group bookings and so forth. The exact price can only be determined\
  \ when you check the availability for a specific date and passenger/traveler mix.\
  \ We recommend using the [/booking/availability/tourgrades](#operation/bookingAvailabilityTourgrades)\
  \ endpoint for this purpose.\n\n**Why doesn't the [/taxonomy/destinations](#operation/taxonomyDestinations)\
  \ endpoint return continent-level information?**\n\n- Products are categorized according\
  \ to their 'destination', which includes cities, regions and countries. The next\
  \ logical grouping would be 'by continent'; however, this would be too broad a grouping,\
  \ resulting in too many search results and lengthy response times if the product\
  \ catalogue were to be searched by continent. For more information, see: [Categorization\
  \ of content](#section/Key-concepts/Categorization-of-content)\n\n**Will there ever\
  \ be a discrepancy between the amount charged for a tour and the amount refunded\
  \ due to currency exchange-rate fluctuations?**\n\n- In short: no. Firstly, the\
  \ cost of the booking and the refund amount are always calculated in the product\
  \ supplier's native currency – no exchange rate calculations are applied. I.e.,\
  \ if the cost of the booking was USD 100 and the refund percentage is 100% (full\
  \ refund, as per the response from [/bookings/{booking-reference}/cancel-quote](#operation/cancelBookingQuote)),\
  \ Viator will simply not invoice you for that USD 100 that we would have if the\
  \ booking was not canceled. Furthermore, we do not invoice you for the cost of a\
  \ booking prior to its departure date. \n\n# Appendices\n\n## Update log\n\n| Date\
  \ | Description |\n|------|-------------|\n| 20 July 2020 | Added [Booking references](#section/Key-concepts/Booking-references)\
  \ section |\n| 14 July 2020 | Updated [Calculating prices](#section/Common-workflows-and-data-validation/Calculating-prices)\
  \ section |\n| 2 June 2020 | Updated Postman collections and [Testing](#section/Testing)\
  \ section |\n| 18 May 2020 | Added note regarding cancel codes to [Legacy merchant\
  \ cancellation](#section/Appendices/Legacy-merchant-cancellation) section |\n| 7\
  \ May 2020 | Upgraded search feature; enabled 'Try it Out' console |\n| 10 Mar 2020\
  \ | Created new [Overview](#section/Overview) section; removed 'Availability services'\
  \ section, moving section contents into [Key Concepts](#section/Key-concepts) section\
  \ |\n\n## Accept-Language header\n\nThe `Accept-Language` header parameter controls\
  \ which language the natural language fields in the response from each endpoint\
  \ will be translated into.\n\nNote that you can only specify languages that have\
  \ been configured for your API-key. Therefore, if you wish to access additional\
  \ languages, you will need to contact your business development account manager.\n\
  \n| Language | Accept-Language parameter value |\n|----------|-------|\n| English\
  \ | `en`, `en-US` |\n| Danish | `da`, `da-DK` |\n| Dutch | `nl`, `nl-NL` |\n| Norwegian\
  \ | `no`, `no-NO` |\n| Spanish | `es`, `es-ES` |\n| Swedish | `sv`, `sv-SE` |\n\
  | French | `fr`, `fr-FR` |\n| Italian | `it`, `it-IT` |\n| German | `de`, `de-DE`\
  \ |\n| Portuguese | `pt`, `pt-PT` |\n| Japanese | `ja`, `ja-JP` |\n| Chinese (simplified)\
  \ | `zh-CN` |\n| Chinese (traditional) | `zh-TW` |\n| Korean | `ko`, `ko-KR` |\n\
  \n## Standard JSON fields\n\nEvery service returns a standard set of JSON fields\
  \ at the end of the JSON response, which indicates if it was processed successfully\
  \ by the API.\n\nIn addition to the `success` flag, you will also need to check\
  \ the `errorMessage` values for the status of the response. \n\nAn error-free response\
  \ will have:\n\n- `\"success\"`:`true`\n- `\"errorType\"`:`null`\n- `\"errorMessage\"\
  `:`null`\n\n### Example JSON - successful:\n\n```javascript\n{\n  \"data\": [],\n\
  \  \"vmid\": \"321001\",\n  \"errorMessage\": null,\n  \"errorType\": null,\n  \"\
  dateStamp\": \"2013-03-06T19:45:10+0000\",\n  \"errorReference\": null,\n  \"errorMessageText\"\
  : null,\n  \"success\": true,\n  \"totalCount\": 114,\n  \"errorName\": null\n}\n\
  ```\n\n### Example JSON - unsuccessful:\n\n```javascript\n{\n  \"errorReference\"\
  : \"~5793740141815885188840666\",\n  \"data\": null,\n  \"dateStamp\": \"2013-09-09T11:29:48+0000\"\
  ,\n  \"errorType\": \"EXCEPTION\",\n  \"errorMessage\": [\"* Additional questions\
  \ missing\\n\"],\n  \"errorName\": \"ValidationException\",\n  \"success\": false,\n\
  \  \"totalCount\": 1,\n  \"vmid\": \"221001\",\n  \"errorMessageText\": [\"* Additional\
  \ questions missing\" ]\n}\n```\n\n| Element | Type | Comments | To be viewed by\
  \ customer | Required |\n|---------|------|----------|:------------------------:|:--------:|\n\
  | `vmid` | string | The server id that processed the service | ❌ | ✅ |\n| `errorMessage`\
  \ | string | The error message in HTML | ❌ | ✅ |\n| `errorType` | string | Type\
  \ of error: EXCEPTION | ❌ | ✅ |\n| `dateStamp` | string | timestamp of the response\
  \ | ❌ | ✅ |\n| `errorReference` | string | The error reference is logged for future\
  \ reference | ❌ | ✅ |\n| `errorMessageText` | string | The textual version of the\
  \ error message | ✅&lt;br /&gt; (if an error has occurred) | ✅ |\n| `success` |\
  \ boolean | &lt;ul&gt;&lt;li&gt;`true` if the API request was successful with no\
  \ errors&lt;/li&gt;&lt;li&gt;`false` if an error was encountered&lt;/li&gt;&lt;/ul&gt;\
  \ | ❌ | ✅ |\n| `totalCount` | integer | The number of results returned (minimum\
  \ = `1`) | ✅&lt;br /&gt; (if displaying the number of results found in a search\
  \ etc.) | ✅ |\n| `errorName` | string | The name of the error type | ❌ | ✅ |\n\n\
  ## Country codes\n| Country code | Country |\n|--------------|---------|\n| AF |\
  \ Afghanistan |\n| AL | Albania |\n| DZ | Algeria |\n| AS | American Samoa |\n|\
  \ AD | Andorra |\n| AO | Angola |\n| AI | Anguilla |\n| AQ | Antarctica |\n| AG\
  \ | Antigua and Barbuda |\n| AR | Argentina |\n| AM | Armenia |\n| AW | Aruba |\n\
  | AU | Australia |\n| AT | Austria |\n| AZ | Azerbaijan |\n| BS | Bahamas |\n| BH\
  \ | Bahrain |\n| BD | Bangladesh |\n| BB | Barbados |\n| BY | Belarus |\n| BE |\
  \ Belgium |\n| BZ | Belize |\n| BJ | Benin |\n| BM | Bermuda |\n| BT | Bhutan |\n\
  | BO | Bolivia |\n| BA | Bosnia Herzegovina |\n| BW | Botswana |\n| BR | Brazil\
  \ |\n| BN | Brunei |\n| BG | Bulgaria |\n| BF | Burkina Faso |\n| BI | Burundi |\n\
  | KH | Cambodia |\n| CM | Cameroon |\n| CA | Canada |\n| CV | Cape Verde |\n| KY\
  \ | Cayman Islands |\n| CF | Central Africa |\n| TD | Chad |\n| CL | Chile |\n|\
  \ CN | China |\n| CX | Christmas Island |\n| CC | Cocos (Keeling) Islands |\n| CO\
  \ | Colombia |\n| KM | Comoros |\n| CK | Cook Islands |\n| CR | Costa Rica |\n|\
  \ CI | Cote D'Ivoire |\n| HR | Croatia |\n| CY | Cyprus |\n| CZ | Czech Republic\
  \ |\n| DK | Denmark |\n| DJ | Djibouti |\n| DM | Dominica |\n| DO | Dominican Republic\
  \ |\n| EC | Ecuador |\n| EG | Egypt |\n| SV | El Salvador |\n| GQ | Equatorial Guinea\
  \ |\n| ER | Eritrea |\n| EE | Estonia |\n| ET | Ethiopia |\n| FK | Falkland Island\
  \ |\n| FO | Faroe Islands |\n| FJ | Fiji |\n| FI | Finland |\n| FR | France |\n\
  | GF | French Guiana |\n| PF | French Polynesia |\n| GA | Gabon |\n| GM | Gambia\
  \ |\n| GE | Georgia |\n| DE | Germany |\n| GH | Ghana |\n| GI | Gibraltar |\n| GR\
  \ | Greece |\n| GL | Greenland |\n| GD | Grenada |\n| GP | Guadeloupe |\n| GU |\
  \ Guam |\n| GT | Guatemala |\n| GN | Guinea |\n| GW | Guinea Bissau |\n| GY | Guyana\
  \ |\n| HT | Haiti |\n| HN | Honduras |\n| HK | Hong Kong |\n| HU | Hungary |\n|\
  \ IS | Iceland |\n| IN | India |\n| ID | Indonesia |\n| IQ | Iraq |\n| IE | Ireland\
  \ |\n| IL | Israel |\n| IT | Italy |\n| JM | Jamaica |\n| JP | Japan |\n| JO | Jordan\
  \ |\n| KZ | Kazakhstan |\n| KE | Kenya |\n| KI | Kiribati |\n| KW | Kuwait |\n|\
  \ KG | Kyrgyzstan |\n| LA | Lao People's Democratic Republic |\n| LV | Latvia |\n\
  | LB | Lebanon |\n| LS | Lesotho |\n| LR | Liberia |\n| LY | Libyan Arab Jamahiriya\
  \ |\n| LI | Liechtenstein |\n| LT | Lithuania |\n| LU | Luxembourg |\n| MO | Macau\
  \ |\n| MK | Macedonia |\n| MG | Madagascar |\n| MW | Malawi |\n| MY | Malaysia |\n\
  | MV | Maldives |\n| ML | Mali |\n| MT | Malta |\n| MQ | Martinique |\n| MR | Mauritania\
  \ |\n| MU | Mauritius |\n| YT | Mayotte |\n| MX | Mexico |\n| FM | Micronesia |\n\
  | MD | Moldova |\n| MC | Monaco |\n| MN | Mongolia |\n| MS | Monserrat |\n| MA |\
  \ Morocco |\n| MZ | Mozambique |\n| NA | Namibia |\n| NR | Nauru |\n| NP | Nepal\
  \ |\n| NL | Netherlands |\n| AN | Netherlands Antilles |\n| KN | Nevis- St Kitts\
  \ |\n| NC | New Caledonia |\n| NZ | New Zealand |\n| NI | Nicaragua |\n| NE | Niger\
  \ |\n| NG | Nigeria |\n| NU | Niue |\n| NF | Norfolk Island |\n| KP | North Korea\
  \ |\n| MP | Northern Mariana Islands |\n| NO | Norway |\n| OM | Oman |\n| PK | Pakistan\
  \ |\n| PW | Palau |\n| PS | Palestinian Territory, Occupied |\n| PA | Panama |\n\
  | PG | Papua New Guinea |\n| PY | Paraguay |\n| PE | Peru |\n| PH | Philippines\
  \ |\n| PN | Pitcairn |\n| PL | Poland |\n| PT | Portugal |\n| PR | Puerto Rico |\n\
  | QA | Qatar |\n| RE | Reunion |\n| RO | Romania |\n| RU | Russian Federation |\n\
  | RW | Rwanda |\n| SH | Saint Helena |\n| LC | Saint Lucia |\n| SM | San Marino\
  \ |\n| ST | Sao Tome and Principe |\n| SA | Saudi Arabia |\n| SN | Senegal |\n|\
  \ YU | Serbia and Montenegro |\n| SC | Seychelles |\n| SL | Sierra Leone |\n| SG\
  \ | Singapore |\n| SK | Slovakia |\n| SI | Slovenia |\n| SB | Solomon Islands |\n\
  | SO | Somalia |\n| ZA | South Africa |\n| KR | South Korea |\n| ES | Spain |\n\
  | LK | Sri Lanka |\n| PM | St Pierre Miquelon |\n| VC | St Vincent and Grenadines\
  \ |\n| SR | Suriname |\n| SZ | Swaziland |\n| SE | Sweden |\n| CH | Switzerland\
  \ |\n| SY | Syria |\n| TW | Taiwan |\n| TJ | Tajikistan |\n| TZ | Tanzania |\n|\
  \ TH | Thailand |\n| TL | Timor-Leste |\n| TG | Togo |\n| TK | Tokelau |\n| TO |\
  \ Tonga |\n| TT | Trinidad and Tobago |\n| TN | Tunisia |\n| TR | Turkey |\n| TM\
  \ | Turkmenistan |\n| TC | Turks and Caicos Islands |\n| TV | Tuvalu |\n| UG | Uganda\
  \ |\n| UA | Ukraine |\n| AE | United Arab Emirates |\n| GB | United Kingdom |\n\
  | UY | Uruguay |\n| UM | US Minor Outlying Islands |\n| US | United States of America\
  \ |\n| UZ | Uzbekistan |\n| VU | Vanuatu |\n| VE | Venezuela |\n| VN | Vietnam |\n\
  | VG | Virgin Islands-British |\n| VI | Virgin Islands-US |\n| WF | Wallis and Futuna\
  \ Islands |\n| WS | Western Samoa |\n| YE | Yemen Republic |\n| ZM | Zambia |\n\
  | ZW | Zimbabwe |\n\n## US state codes\n| State code | State |\n|------------|-------|\n\
  | AL | Alabama |\n| AK | Alaska |\n| AZ | Arizona |\n| AR | Arkansas |\n| CA | California\
  \ |\n| CO | Colorado |\n| CT | Connecticut |\n| DE | Delaware |\n| DC | District\
  \ of Columbia |\n| FL | Florida |\n| GA | Georgia |\n| HI | Hawaii |\n| ID | Idaho\
  \ |\n| IL | Illinois |\n| IN | Indiana |\n| IA | Iowa |\n| KS | Kansas |\n| KY |\
  \ Kentucky |\n| LA | Louisiana |\n| ME | Maine |\n| MD | Maryland |\n| MA | Massachusetts\
  \ |\n| MI | Michigan |\n| MN | Minnesota |\n| MS | Mississippi |\n| MO | Missouri\
  \ |\n| MT | Montana |\n| NE | Nebraska |\n| NV | Nevada |\n| NH | New Hampshire\
  \ |\n| NJ | New Jersey |\n| NM | New Mexico |\n| NY | New York |\n| NC | North Carolina\
  \ |\n| ND | North Dakota |\n| OH | Ohio |\n| OK | Oklahoma |\n| OR | Oregon |\n\
  | PA | Pennsylvania |\n| RI | Rhode Island |\n| SC | South Carolina |\n| SD | South\
  \ Dakota |\n| TN | Tennessee |\n| TX | Texas |\n| UT | Utah |\n| VT | Vermont |\n\
  | VA | Virginia |\n| WA | Washington |\n| WV | West Virginia |\n| WI | Wisconsin\
  \ |\n| WY | Wyoming |\n\n## Canadian provinces\n\n| Code | Province |\n|------|----------|\n\
  | Alberta | Alberta |\n| British Columbia | British Columbia |\n| Manitoba | Manitoba\
  \ |\n| New Brunswick | New Brunswick |\n| Newfoundland and Labrador | Newfoundland\
  \ |\n| Northwest Territories | Northwest Territories |\n| Nova Scotia | Nova Scotia\
  \ |\n| Nunavut | Nunavut |\n| Ontario | Ontario |\n| Prince Edward Island | Prince\
  \ Edward Island |\n| Quebec | Quebec |\n| Saskatchewan | Saskatchewan |\n| Yukon\
  \ | Yukon Territory |\n\n## Australian states\n\n| Code | State |\n|------|-------|\n\
  | ACT | Australian Capital Territory |\n| NSW | New South Wales |\n| NT | Northern\
  \ Territory |\n| QLD | Queensland |\n| SA | South Australia |\n| TAS | Tasmania\
  \ |\n| VIC | Victoria |\n| WA | Western Australia |\n\n## bookingStatus field values\
  \ and meanings\n\n| Field: `type` | Field: `status` | Meaning |\n|-------|:-----:|---------|\n\
  | `\"WAITING\"` | `0` | This item has not been booked. Part of an unfinished itinerary.\
  \ |\n| `\"CONFIRMED\"` | `1` | This item has been successfully booked |\n| `\"UNAVAILABLE\"\
  ` | `2` | This item has been had an availability check, that came back false. |\n\
  | `\"PENDING\"` | `3` | This item has begun booking, but has paused in a deferred\
  \ booking engine |\n| `\"FAILED\"` | `4` | A merchant partner with a freesale-only\
  \ API-key has attempted to book an on-request product |\n| `\"CANCELLED\"` | `5`\
  \ | This item has successfully been cancelled. |\n| `\"EXPIRED\"` | `6` | This item\
  \ is now expired. |\n| `\"AMENDED\"` | `7` | This item has been amended after booking.\
  \ |\n| `\"PENDING_AMEND\"` | `8` | This item has a pending amendment which can be\
  \ cancelled. |\n| `\"REJECTED\"` | `12` | Viator only |\n| `\"ON_HOLD\"` | `13`\
  \ | Viator only |\n\n## Supported currency codes\n\nSupported currency codes for\
  \ merchant partners:\n\n| Currency code | Currency |\n|---------------|----------|\n\
  | USD | US dollar |\n| GBP | British pound |\n| EUR | Euro |\n| AUD | Australian\
  \ dollar |\n\n**Note:** Partners will be billed in the currency of the booking.\n\
  \n## Viator API error codes\n\n| Error code | Services | Error message | Description\
  \ |\n|------------|----------|---------------|-------------|\n| ADDRESS_REQUIRED\
  \ | [/booking/book](#operation/bookingBook) | \"You have not entered an address.\
  \ Please enter your address information.\" | `ccAddress1` was empty |\n| ADDRESS_SIZE_EXCEEDED\
  \ | [/booking/book](#operation/bookingBook) | \"Billing address is restricted to\
  \ 50 characters long.\" | `address` field was longer than 51 characters |\n| ATTRIBUTE_NOT_FOUND\
  \ | [/product](#operation/product) |   |   |\n| AGE_BAND_INVALID | [/booking/book](#operation/bookingBook)\
  \ |  | a `bandId` has been submitted that does not correspond to any `bandId` available\
  \ for the tour grade in question |\n| BOOKING_QUESTIONS_MISSING | [/booking/book](#operation/bookingBook)\
  \ | \"Additional questions missing\" | one or more required [booking questions](#section/Appendices/Booking-questions)\
  \ are missing in the booking request |\n| CARD_EXPIRED | [/booking/book](#operation/bookingBook)\
  \  |   | submitted credit card details corresponding to an expired card  |\n| CITY_REQUIRED\
  \ | [/booking/book](#operation/bookingBook) | \"You have not entered a city in the\
  \ address section. Please enter your city.\" | address is required in the credit\
  \ card section |\n| CITY_SIZE_EXCEEDED | [/booking/book](#operation/bookingBook)\
  \ | \"City is restricted to 40 characters long.\" | city name submitted was more\
  \ than 40 characters long |\n| COUNTRY_REQUIRED | [/booking/book](#operation/bookingBook)\
  \ | \"You have not entered a country. Please enter your country.\" | no country\
  \ was submitted in the booking request  |\n| CREDIT_CARD_DECLINED | [/booking/book](#operation/bookingBook)\
  \ |   | credit card used for booking was declined by the payment processor  |\n\
  | CREDIT_CARD_EXPIRY_DATE_INVALID | [/booking/book](#operation/bookingBook) | \"\
  The expiration date for your credit card is not formatted properly. Please verify\
  \ and re-enter the expiration date.\" | incorrectly-formatted credit card expiration\
  \ date was submitted  |\n| CREDIT_CARD_HOLDER_NAME_INVALID | [/booking/book](#operation/bookingBook)\
  \ |  | credit card holder's name was invalid, perhaps due to the inclusion of invalid\
  \ characters |\n| CREDIT_CARD_NUMBER_INVALID | [/booking/book](#operation/bookingBook)\
  \ | \"Please verify and re-enter the credit card details, or use a different credit\
  \ card\" | invalid characters in credit card number |\n| CREDIT_CARD_NUMBER_REQUIRED\
  \ | [/booking/book](#operation/bookingBook) | \"Credit card number is required\"\
  \ | credit card number was omitted |\n| CREDIT_CARD_SECURITY_NUMBER_INVALID | [/booking/book](#operation/bookingBook)\
  \ | \"The card security number you entered for your credit card is invalid. It must\
  \ contain 3 digits (or 4 with American Express cards). Please re-enter the card\
  \ security number.\" | incorrect CCV code submitted |\n| CREDIT_CARD_SECURITY_NUMBER_REQUIRED\
  \ | [/booking/book](#operation/bookingBook) | \"Credit card security number is required\"\
  \ | CCV was not provided |\n| DEMO_BOOKING_WITH_REAL_CARD | [/booking/pricingmatrix](#operation/bookingPricingmatrix)\
  \ |  | `demo` is `true`, but credit card details are real |\n| DISTRIBUTOR_REFERENCE_MISMATCH\
  \ | [/booking/pastbooking](#operation/bookingPastbooking); [/booking/mybookings](#operation/bookingMybookings)\
  \ | \"The distributor reference associated with this itinerary does not match the\
  \ one provided.\" | attempt to retrieve a booking with an `itineraryId` or `itemId`\
  \ and `distributorRef`, but the reference doesn't match the one saved in the itinerary\
  \ |\n| EMAIL_ADDRESS_INVALID | [/booking/book](#operation/bookingBook) | \"Your\
  \ email address format is invalid\" | email address is formatted incorrectly  |\n\
  | EMAIL_REQUIRED | [/booking/book](#operation/bookingBook) | \"Email is required\"\
  \ | email address is missing in the booking request |\n| FIRST_NAME_INVALID | [/booking/book](#operation/bookingBook)\
  \ | \"You have entered a name for the credit-card holder that is not valid. Please\
  \ verify and re-enter the name of the credit card holder.\" | first name is formatted\
  \ incorrectly or contains invalid characters in the booking request - string length\
  \ must be &gt; 1 and must not contain the following characters: &lt;&gt;%;\"(),|\n\
  | FIRST_NAME_REQUIRED | [/booking/book](#operation/bookingBook) | \"First name of\
  \ credit card details is required\" | no first name specified |\n| FIRST_NAME_SIZE_EXCEEDED\
  \ | [/booking/book](#operation/bookingBook) | \"First name of credit card details\
  \ is restricted to 30 characters long\" | first name exceeds 30 characters |\n|\
  \ INTERNAL_ERROR | *any* | *any* | the API itself has experienced an unexpected\
  \ error |\n| LAST_NAME_INVALID | [/booking/book](#operation/bookingBook) |  \"You\
  \ have entered a name for the credit-card holder that is not valid. Please verify\
  \ and re-enter the name of the credit card holder.\" | last name is formatted incorrectly\
  \ in the booking request - string length must be &gt; 1 and must not contain the\
  \ following characters: &lt;&gt;%;\"(), |\n| LAST_NAME_REQUIRED | [/booking/book](#operation/bookingBook)\
  \ | \"Last name of credit card details is required\" | no last name supplied in\
  \ the `ccname` field of the `ccPayDetail` object |\n| LAST_NAME_SIZE_EXCEEDED |\
  \ [/booking/book](#operation/bookingBook) | \"Last name of credit card details is\
  \ restricted to 35 characters long\" | the surname in the `ccname` field of the\
  \ `ccPayDetail` object must not exceed 35 characters in length |\n| LEAD_TRAVELLER_REQUIRED\
  \ | [/booking/book](#operation/bookingBook) | \"A traveler needs to be selected\
  \ as lead traveler.\" | one traveller object within the `travellers` array in the\
  \ booking request needs to have `leadTraveller` set to `true` |\n| PAYMENT_AMOUNTS_CHANGED\
  \ |  [/booking/book](#operation/bookingBook) | e.g. \"PAYMENT_AMOUNTS_CHANGED: HKD\
  \ 2213.20 (was HKD 2210.26)\" | This error indicates that the exchange rate was\
  \ updated while the booking was being made. Refresh the product's pricing information\
  \ and retry the booking.  |\n| PAYMENT_CURRENCY_MISMATCH | [/booking/book](#operation/bookingBook)\
  \ |   |   |\n| PAYMENT_ENCRYPTION_ERROR | [/booking/book](#operation/bookingBook)\
  \  |   | Viator-only internal error - retry booking request |\n| PAYMENT_INTERNAL_ERROR\
  \ | [/booking/book](#operation/bookingBook)  |   | Viator-only internal error -\
  \ retry booking request |\n| PAYMENT_LIMIT_REACHED | [/booking/book](#operation/bookingBook)\
  \  |   | Viator-only internal error - retry booking request |\n| PAYMENT_REJECTED\
  \ | [/booking/book](#operation/bookingBook) | | triggered when expiry: `\"01/2018\"\
  ` and card number: `\"4539791001730106\"` were submitted |\n| POSTCODE_REQUIRED\
  \ | [/booking/book](#operation/bookingBook) | \"You have not entered a zip code\
  \ / post code. Please enter your zip code / post code.\", | `ccaddressZip` was empty\
  \ |\n| POSTCODE_SIZE_EXCEEDED | [/booking/book](#operation/bookingBook) | \"Zip\
  \ code / post code is restricted to 10 characters long.\" | `ccaddressZip` was more\
  \ than 10 characters in length |\n| PRICING_DATA_MISSING |   |   | Viator-only internal\
  \ error - retry booking request |\n| PRODUCT_TOUR_GRADE_UNKNOWN | [/booking/pricingmatrix](#operation/bookingPricingmatrix)\
  \ | Unknown tour grade: &lt;TOUR_GRADE&gt; for product | an invalid tour grade code\
  \ was submitted |\n| PRODUCT_UNAVAILABLE | [/booking/book](#operation/bookingBook)\
  \  |   | Viator-only internal error - retry booking request |\n| REFUND_REJECTED\
  \ |   |   |  Viator-only internal error - retry booking request |\n| STATE_REQUIRED\
  \ | [/booking/book](#operation/bookingBook) | | `ccaddressState` is required for\
  \ this billing request |\n| STATE_SIZE_EXCEEDED | [/booking/book](#operation/bookingBook)\
  \ | | `ccaddressState` must be fewer than 35 characters long |\n| TOUR_NOT_AVAILABLE\
  \ | [/booking/book](#operation/bookingBook) | \"We're sorry, the following tour\
  \ you are trying to book is sold out and no longer available\" | the tour is not\
  \ available on the requested date |\n| TOUR_GONE | [/product](#operation/product)\
  \ | \"We're sorry, we cannot find the tour, activity or attraction you are looking\
  \ for\" | no product corresponding to the supplied details was found |\n| TOUR_NOT_AVAILABLE_BETWEEN_DATES\
  \ | | | |\n| TOUR_NOT_FOUND | [/product](#operation/product) | \"We're sorry, we\
  \ cannot find the tour, activity or attraction you are looking for\" | no product\
  \ corresponding to the supplied details was found |\n| TRAVELLER_COUNT_EXCEEDED_MAX_LIMIT\
  \ |   |   | number of travellers in the booking request was greater than the limit\
  \ for the product being booked |\n| TRAVELLER_FIRST_NAME_INVALID | [/booking/book](#operation/bookingBook)\
  \ | \"First name of traveler 1 must only contain alphabetical characters\" | non-alphabetical\
  \ characters were used in the traveller's first name |\n| TRAVELLER_FIRST_NAME_REQUIRED\
  \ | [/booking/book](#operation/bookingBook) | \"First name of traveler 1 is required\"\
  \ | `firstname` in the `booker` object was omitted |\n| TRAVELLER_LAST_NAME_INVALID\
  \ | [/booking/book](#operation/bookingBook) | \"Last name of traveler 1 should contain\
  \ alphabet only\" | `surname` in the `booker` object contained non-alphabetical\
  \ characters |\n| TRAVELLER_LAST_NAME_REQUIRED | [/booking/book](#operation/bookingBook)\
  \ | \"Last name of traveler 1 is required\" | `surname` in the `booker` object was\
  \ omitted |\n| TRAVELLER_MISMATCH |  [/booking/availability/tourgrades](#operation/bookingAvailabilityTourgrades)\
  \ |   | the `bandId` is not available for the selected tour grade; or, the product\
  \ does not support the number of travelers requested |\n| UNKNOWN_ERROR | *any*\
  \ | *any* | the API reports this error when the exception from the underlying system\
  \ (e.g. booking server) is not recognized |\n| UNKNOWN_PAYMENT_METHOD |   |   |\
  \   |\n| UNSUPPORTED_CARD |   |   | `cctype` is not one of `\"Visa\"`, `\"Mastercard\"\
  ` or `\"Amex\"` |\n\n## Booking questions\n\nExample product codes were valid at\
  \ the time of writing. If you find that any of these product codes are invalid or\
  \ do not include the relevant booking question, please [inform us about it via email](apitechsupport@viator.com).\n\
  \n| Id | stringQuestionId | title | subtitle | message | example product |\n|:----------:|-------------|-------|----------|----------|-----|\n\
  | 1 | `dateOfBirth_dob` | Date of Birth | (e.g. 20 October 1970) | Enter your date\
  \ of birth. | 100009P2 |\n| 2 | `heights_passengerHeights` | Passenger Heights |\
  \ (eg. 5'2, 158cm etc) | For safety reasons you must enter the height of all passengers.\
  \ Please indicate inches or centimetres. | 100009P1 |\n| 3 | `passport_expiry` |\
  \ Passport Expiry Date | (e.g. 15 September 2015. If multiple passengers, separate\
  \ each entry e.g. 01 July 2012, 31 May 2014) | Enter passport expiry date for all\
  \ passengers | 100014P10 |\n| 4 | `passport_nationality` | Passport Nationality\
  \ | (e.g. United States of America. If multiple passengers, separate each entry\
  \ e.g. Australia, China) | Enter country of issue of passport for all passengers\
  \ | 100014P10 |\n| 5 | `passport_passportNo` | Passport Number | (e.g. 0123456789.\
  \ If multiple passengers, separate each entry e.g. 0123456789, 9876543210) | Enter\
  \ passport number for all passengers | 100014P10 |\n| 6 | N/A | N/A | N/A | N/A\
  \ | N/A |\n| 7 | `transfer_air_arrival_airline` | Arrival Airline | (e.g. United,\
  \ British Airways, Qantas, etc) | Enter the name of your airline. | 100006P15 |\n\
  | 8 | `transfer_air_arrival_flightNo` | Arrival Flight No | (e.g. UA 864, BA 923,\
  \ QA 233, etc) | Enter your flight number. | 100006P15 |\n| 9 | `transfer_air_departure_airline`\
  \ | Departure Airline | (e.g. United, British Airways, Qantas, etc) | Enter the\
  \ name of your airline. | 100006P17 |\n| 10 | `transfer_air_departure_flightNo`\
  \ | Departure Flight No | (e.g. UA 864, BA 923, QA 233, etc) | Enter your flight\
  \ number. | 100006P17 |\n| 11 | `transfer_arrival_dropOff` | Drop Off Location |\
  \ (e.g. 1234 Cedar Way, Brooklyn, NY 00123) | Enter the address for drop off. |\
  \ 100006P15 |\n| 12 | `transfer_arrival_time` | Arrival Time | (eg. 8pm, 20:30 etc)\
  \ | Enter your arrival time. Please indicate AM/PM or use the 24-hour clock. | 100006P15\
  \ |\n| 13 | `transfer_departure_date` | Departure date | (e.g. 15 September 2015)\
  \ | Enter your departure date. | 100006P15 |\n| 14 | `transfer_departure_pickUp`\
  \ | Pick up Location | (e.g. 1234 Cedar Way, Brooklyn, NY 00123) | Enter the address\
  \ for pick up. | 100006P17 |\n| 15 | `transfer_departure_time` | Departure Time\
  \ | (eg. 8pm, 20:30 etc) | Enter your departure time. Please indicate AM/PM or use\
  \ the 24-hour clock. | 100006P17 |\n| 16 | `transfer_port_arrival_time` | Disembarkation\
  \ Time | (eg. 8pm, 20:30 etc) | Enter your disembarkation time. Please indicate\
  \ AM/PM or use the 24-hour clock. | 100014P14 |\n| 17 | `transfer_port_cruiseShip`\
  \ | Cruise Ship | (e.g. Brilliance of the Seas, etc) | Enter your cruise ship. |\
  \ 100014P14 |\n| 18 | `transfer_port_departure_time` | Boarding Time | (eg. 8pm,\
  \ 20:30 etc) | Enter your boarding time. Please indicate AM/PM or use the 24-hour\
  \ clock. | 100014P4 |\n| 19 | `transfer_rail_arrival_line` | Arrival Rail Line |\
  \ (e.g. Amtrak, etc) | Enter the name of the rail provider. | 100006P15 |\n| 20\
  \ | `transfer_rail_arrival_station` | Arrival Rail Station | (e.g. Central Station,\
  \ etc) | Enter name of arrival and/or departure station. | 100006P15 |\n| 21 | `transfer_rail_departure_line`\
  \ | Departure Rail Line | (e.g. Amtrak, etc) | Enter the name of the rail provider.\
  \ | 100014P10 |\n| 22 | `transfer_rail_departure_station` | Departure Rail Station\
  \ | (e.g. Central Station, etc) | Enter name of arrival and/or departure station.\
  \ | 100014P10 |\n| 23 | `weights_passengerWeights` | Passenger Weights | (e.g. 127\
  \ pounds, 145 kilos, etc) | For safety reasons you must enter the weight of &lt;b&gt;all&lt;/b&gt;\
  \ passengers. Please indicate pounds or kilos. | 100111P12 |\n\n## Legacy merchant\
  \ cancellation\n\n**Note:** This functionality has been replaced by the [cancellationReasons](#operation/cancellationReasons),\
  \ [bookingQuote](#operation/bookingQuote) and [cancelBooking](#operation/cancelBooking)\
  \ endpoints.\n\n### Requirements for cancellations\n\n- To successfully cancel a\
  \ booking via the [/merchant/cancellation](#operation/merchantCancellation) service,\
  \ you must include the itinerary item to cancel (`itemId`). \n\n- `itineraryItemId`\
  \ and `itineraryId` need to match the `distributorRef` and `distributorItemRef`,\
  \ so these four values must also be included in the request body. \n\n- You must\
  \ also include a `cancelCode` - a number corresponding to the reason for cancellation.\
  \ You can use the &lt;a href=\"#suggested-cancellation-codes\"&gt;suggested cancel\
  \ codes&lt;/a&gt; shown in the table below.\n\n\n&lt;mark&gt;**Note**: Post-travel\
  \ cancellations **will not be processed** unless a cancel code of `62` or `66` is\
  \ passed in the `cancelCode` parameter.&lt;/mark&gt;\n### The [/merchant/cancellation](#operation/merchantCancellation)\
  \ service:\n\n#### Description of JSON request parameters for the [/merchant/cancellation](#operation/merchantCancellation)\
  \ service:\n\n| Parameter | Type | Comments | Required |\n|-----------|------|----------|:--------:|\n\
  | `itineraryId` | integer | Viator itinerary reference number | ✅ |\n| `distributorRef`\
  \ | string | Merchant partner's itinerary reference for booking | ✅ |\n| `cancelItems`\
  \ | array | Array of item to cancel in itinerary | ✅ |\n| `itemId` | integer | Viator\
  \ `itemId` of item to cancel in itinerary | ✅ |\n| `distributorItemRef` | string\
  \ | Merchant partner's itinerary item (booking) reference | ✅ |\n| `cancelCode`\
  \ | string | A number indicating the reason for cancelling the booking. A list of\
  \ &lt;a href=\"#suggested-cancellation-codes\"&gt;suggested cancel codes&lt;/a&gt;\
  \ is shown in the table below. | ✅ |\n| `cancelDescription` | string | Natural-language\
  \ reason for cancellation. A reason **must** be provided if a `cancelCode` of `'62'`\
  \ or `'66'` is passed. | ✅ for `cancelCode` `'62'` or `'66'`; otherwise ❌ |\n\n\
  #### Example [/merchant/cancellation](#operation/merchantCancellation) request:\n\
  \nIn this request, we wish to cancel the booking identified by the following:\n\n\
  | Parameter | Value |\n|-----------|-------|\n| `itneraryId` | `12345655` |\n| `distributorRef`\
  \ | `\"Jdp122\"` |\n| `itemId` | `330056` |\n| `distributorItemRef` | `\"JdpItin001\"\
  ` |\n| `cancelCode` | `\"82\"` (Honest mistake - incorrect purchase) |\n\nThis is\
  \ accomplished as follows:\n\n**API Service**\n\n```html\nPOST /merchant/cancellation\n\
  ```\n\n**Request body**\n\n```javascript\n{\n  \"itineraryId\": 1234655,\n  \"distributorRef\"\
  : \"Jdp122\",\n  \"cancelItems\": [\n  {\n    \"itemId\": 330056,\n    \"distributorItemRef\"\
  : \"JdpItin001\",\n    \"cancelCode\": \"82\"\n  }]\n}\n```\n\n#### Example response\n\
  ```javascript\n{\n  \"data\": {\n    \"itineraryId\": 1234655,\n    \"cancelItems\"\
  : [\n      {\n        \"cancellationResponseStatusCode\": \"Confirmed\",\n     \
  \   \"cancellationResponseDescription\": \"No further action required\",\n     \
  \   \"itemId\": 330056,\n        \"distributorItemRef\": \"JdpItin001\"\n      }],\n\
  \    \"distributorRef\": \"Jdp122\"\n  },\n  \"vmid\": \"221002\",\n  \"errorMessage\"\
  : null,\n  \"errorType\": null,\n  \"dateStamp\": \"2013-03-21T14:28:08+0000\",\n\
  \  \"errorReference\": null,\n  \"errorMessageText\": null,\n  \"success\": true,\n\
  \  \"totalCount\": 1,\n  \"errorName\": null\n}\n```\n\n### &lt;a name=\"suggested-cancellation-codes\"\
  &gt;&lt;/a&gt;Suggested cancellation codes:\n\n| cancelcode | meaning |\n|:-:|:-|\n\
  | `'00'` | Testing (use for test cancellations) |\n| `'51'` | Flight cancellation\
  \ affecting customer |\n| `'52'` | Flight schedule change unacceptable to customer\
  \ |\n| `'53'` | Death of the customer or a member of their immediate family |\n\
  | `'54'` | Jury duty/court summons affecting customer |\n| `'56'` | Medical emergency/hospitalization\
  \ involving the customer or their immediate family |\n| `'57'` | Customer is required\
  \ for military service |\n| `'58'` | National disaster (insurrection, terrorism,\
  \ war) affecting the customer |\n| `'59'` | Natural disaster (earthquake, fire,\
  \ flood) affecting the customer |\n| `'62'` | **Post-travel cancellation**: the\
  \ product was cancelled by the supplier and the traveller was not given sufficient\
  \ notice |\n| `'63'` | Transport strike/labor dispute affecting customer |\n| `'66'`\
  \ | **Post-travel cancellation**: the product was not cancelled, but the customer\
  \ was dissatisfied with the product |\n| `'71'` | Credit card fraud |\n| `'72'`\
  \ | Car segment cancellation affecting customer |\n| `'73'` | Package segment cancellation\
  \ affecting customer |\n| `'74'` | Hotel segment cancellation affecting customer\
  \ |\n| `'77'` | Re-book |\n| `'78'` | Duplicate purchase |\n| `'82'` | Honest mistake\
  \ (incorrect purchase) |\n| `'87'` | Non-refundable cancellation more than 24 hours\
  \ prior to travel |\n| `'88'` | Non-refundable cancellation less than 24 hours prior\
  \ to travel |\n| `'98'` | Customer service/technical support response outside time\
  \ limit |\n| `'99'` | Duplicate processing |\n\n### Cancellation errors\n\nIf the\
  \ cancellation was **not** successful, you will receive an error response.\n\n####\
  \ Example error response\n\n```javascript\n{\n  \"data\": {\n    \"itineraryId\"\
  : \"3331605\", \n    \"cancelItems\": [{\n      \"cancellationResponseStatusCode\"\
  : \"Error.ItineraryUnknown\", \n      \"cancellationResponseDescription\": \"Please\
  \ double check the details or contact...\"\n      \"itemId\": \"600088255\",\n \
  \     \"distributorItemRef\": \"ItinItemRef012\"\n    }],\n    \"distributorRef\"\
  : null \n  },\n  \"vmid\": \"221002\",\n  \"errorMessage\": null,\n  \"errorType\"\
  : null,\n  \"dateStamp\": \"2013-03-21T14:43:38+0000\", \n  \"errorReference\":\
  \ null, \n  \"errorMessageText\": null,\n  \"success\": true, \n  \"totalCount\"\
  : 1, \n  \"errorName\": null\n}\n```\n\n### &lt;a name=\"cancellation-response-status-codes-and-their-meanings\"\
  &gt;&lt;/a&gt;Cancellation response status codes and their meanings\n\n| `cancellationResponseStatusCode`\
  \ | Meaning | Action |\n|----------------------------------|----------|--------|\n\
  | `\"Confirmed\"` | The request to cancel and refund the item has been accepted\
  \ and processed | No further action is required. |\n| `\"Pending\"` | Confirmation\
  \ of the request to cancel and refund the item is pending. This only applies when\
  \ a `cancelCode` is `'62'` or `'66'` was sent and the booking was in a 'pending'\
  \ state. | No action required. Partner will be contacted when a decision to confirm/reject\
  \ has been made by the supplier. |\n| `\"Rejected\"` | The cancellation request\
  \ was denied | No action required. The item cannot be cancelled. |\n| `\"Error.ItemUnknown\"\
  ` | Item not found | Double-check `itemId`. Contact Viator Customer Service for\
  \ more information if required. |\n| `\"Error.ItineraryUnknown\"` | Itinerary not\
  \ found | Double-check `itineraryId`. Contact Viator Customer Service for more information\
  \ if required. |\n| `\"Error.MultipleRequests\"` | Cancellation request contains\
  \ multiple requests | Submit **only one** item per cancellation request. |\n| `\"\
  Error.NoCancellationCodeOrDescription\"` | Invalid `cancelCode` | `cancelCode` is\
  \ invalid – ensure it is **two** digits long |\n| `\"Error.Unknown\"` | An undefined\
  \ error has occurred | Double-check the `distributorRef` and `distributorItemRef`.\
  \ If the error is still occurring, [contact the Viator partner support team](mailto:dpsupport@viator.com).\
  \ |\n\n### Resubmitting a cancellation request\n\nIf the same cancellation request\
  \ is sent more than once, Viator will respond with the last known response."
logo: "viator.com-logo.svg"
logoMediaType: "image/svg+xml"
tags:
- "location"
- "ecommerce"
stubs: "viator.com-stubs.json"
swagger: "viator.com-swagger.json"
---
