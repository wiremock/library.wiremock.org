---
slug: "graphhopper-com"
title: "GraphHopper Directions API"
provider: "graphhopper.com"
description: "\nWith the [GraphHopper Directions API](https://www.graphhopper.com/products/)\
  \ you can integrate A-to-B route planning, turn-by-turn navigation,\nroute optimization,\
  \ isochrone calculations and other tools in your application.\n\nThe GraphHopper\
  \ Directions API consists of the following RESTful web services:\n\n * [Routing\
  \ API](#tag/Routing-API),\n * [Route Optimization API](#tag/Route-Optimization-API),\n\
  \ * [Isochrone API](#tag/Isochrone-API),\n * [Map Matching API](#tag/Map-Matching-API),\n\
  \ * [Matrix API](#tag/Matrix-API),\n * [Geocoding API](#tag/Geocoding-API) and\n\
  \ * [Cluster API](#tag/Cluster-API).\n\n# Explore our APIs\n\n## Get started\n\n\
  1. [Sign up for GraphHopper](https://support.graphhopper.com/a/solutions/articles/44001976025)\n\
  2. [Create an API key](https://support.graphhopper.com/a/solutions/articles/44001976027)\n\
  \nEach API part has its own documentation. Jump to the desired API part and learn\
  \ about the API through the given examples and tutorials.\n\nIn addition, for each\
  \ API there are specific sample requests that you can send via Insomnia or Postman\
  \ to see what the requests and responses look like.\n\n## Insomnia\n\nTo explore\
  \ our APIs with [Insomnia](https://insomnia.rest/), follow these steps:\n\n1. Open\
  \ Insomnia and Import [our workspace](https://raw.githubusercontent.com/graphhopper/directions-api-doc/master/web/restclients/GraphHopper-Direction-API-Insomnia.json).\n\
  2. Specify [your API key](https://graphhopper.com/dashboard/#/register) in your\
  \ workspace: Manage Environments -> Base Environment -> `\"api_key\": your API key`\n\
  3. Start exploring\n\n![Insomnia](./img/insomnia.png)\n\n## Postman\n\nTo explore\
  \ our APIs with [Postman](https://www.getpostman.com/), follow these steps:\n\n\
  1. Import our [request collections](https://raw.githubusercontent.com/graphhopper/directions-api-doc/master/web/restclients/graphhopper_directions_api.postman_collection.json)\
  \ as well as our [environment file](https://raw.githubusercontent.com/graphhopper/directions-api-doc/master/web/restclients/graphhopper_directions_api.postman_environment.json).\n\
  2. Specify [your API key](https://graphhopper.com/dashboard/#/register) in your\
  \ environment: `\"api_key\": your API key`\n3. Start exploring\n\n![Postman](./img/postman.png)\n\
  \n## API Client Libraries\n\nTo speed up development and make coding easier, we\
  \ offer the following client libraries:\n\n * [JavaScript client](https://github.com/graphhopper/directions-api-js-client)\
  \ - try the [live examples](https://graphhopper.com/api/1/examples/)\n * [Others](https://github.com/graphhopper/directions-api-clients)\
  \ like C#, Ruby, PHP, Python, ... automatically created for the Route Optimization\
  \ API\n\n### Bandwidth reduction\n\nIf you create your own client, make sure it\
  \ supports http/2 and gzipped responses for best speed.\n\nIf you use the Matrix,\
  \ the Route Optimization API or the Cluster API and want to solve large problems,\
  \ we recommend you to reduce bandwidth\nby [compressing your POST request](https://gist.github.com/karussell/82851e303ea7b3459b2dea01f18949f4)\n\
  and specifying the header as follows: `Content-Encoding: gzip`. This will also avoid\
  \ the HTTP 413 error \"Request Entity Too Large\".\n\n## Contact Us\n\nIf you have\
  \ problems or questions, please read the following information:\n\n- [FAQ](https://graphhopper.com/api/1/docs/FAQ/)\n\
  - [Public forum](https://discuss.graphhopper.com/c/directions-api)\n- [Contact us](https://www.graphhopper.com/contact-form/)\n\
  - [GraphHopper Status Page](https://status.graphhopper.com/)\n\nTo stay informed\
  \ about the latest developments, you can\n\n- follow us on [twitter](https://twitter.com/graphhopper/),\n\
  - read [our blog](https://graphhopper.com/blog/),\n- watch [our documentation repository](https://github.com/graphhopper/directions-api-doc),\n\
  - sign up for our newsletter or\n- [our forum](https://discuss.graphhopper.com/c/directions-api).\n\
  \nSelect the channel you like the most.\n\n\n# Map Data and Routing Profiles\n\n\
  Currently, our main data source is [OpenStreetMap](https://www.openstreetmap.org).\
  \ We also integrated other network data providers.\nThis chapter gives an overview\
  \ about the options you have.\n\n## OpenStreetMap\n\n#### Geographical Coverage\n\
  \n[OpenStreetMap](https://www.openstreetmap.org) covers the whole world. If you\
  \ want to see for yourself if we can provide data suitable for your region,\nplease\
  \ visit [GraphHopper Maps](https://graphhopper.com/maps/).\nYou can edit and modify\
  \ OpenStreetMap data if you find that important information is missing, e.g. a weight\
  \ limit for a bridge.\n[Here](https://wiki.openstreetmap.org/wiki/Beginners%27_guide)\
  \ is a beginner's guide that shows how to add data. If you have edited data, we\
  \ usually consider your data after 1 week at the latest.\n\n#### Supported Vehicle\
  \ Profiles\n\nThe Routing, Matrix and Route Optimization APIs support the following\
  \ vehicle profiles:\n\nName       | Description           | Restrictions       \
  \       | Icon\n-----------|:----------------------|:--------------------------|:---------------------------------------------------------\n\
  car        | Car mode              | car access                | ![car image](https://graphhopper.com/maps/img/car.png)\n\
  small_truck| Small truck like a Mercedes Sprinter, Ford Transit or Iveco Daily |\
  \ height=2.7m, width=2+0.4m, length=5.5m, weight=2080+1400 kg | ![small truck image](https://graphhopper.com/maps/img/small_truck.png)\n\
  truck      | Truck like a MAN or Mercedes-Benz Actros | height=3.7m, width=2.6+0.5m,\
  \ length=12m, weight=13000 + 13000 kg, hgv=yes, 3 Axes | ![truck image](https://graphhopper.com/maps/img/truck.png)\n\
  scooter    | Moped mode | Fast inner city, often used for food delivery, is able\
  \ to ignore certain bollards, maximum speed of roughly 50km/h | ![scooter image](https://graphhopper.com/maps/img/scooter.png)\n\
  foot       | Pedestrian or walking without dangerous [SAC-scales](https://wiki.openstreetmap.org/wiki/Key:sac_scale)\
  \ | foot access         | ![foot image](https://graphhopper.com/maps/img/foot.png)\n\
  hike       | Pedestrian or walking with priority for more beautiful hiking tours\
  \ and potentially a bit longer than `foot`. Walking duration is influenced by elevation\
  \ differences.  | foot access         | ![hike image](https://graphhopper.com/maps/img/hike.png)\n\
  bike       | Trekking bike avoiding hills | bike access  | ![bike image](https://graphhopper.com/maps/img/bike.png)\n\
  mtb        | Mountainbike          | bike access         | ![Mountainbike image](https://graphhopper.com/maps/img/mtb.png)\n\
  racingbike| Bike preferring roads | bike access         | ![racingbike image](https://graphhopper.com/maps/img/racingbike.png)\n\
  \nPlease note:\n\n * all motor vehicles (`car`, `small_truck`, `truck` and `scooter`)\
  \ support turn restrictions via `turn_costs=true`\n * the free package supports\
  \ only the vehicle profiles `car`, `bike` or `foot`\n * up to 2 different vehicle\
  \ profiles can be used in a single optimization request. The number of vehicles\
  \ is unaffected and depends on your subscription.\n * we offer custom vehicle profiles\
  \ with different properties, different speed profiles or different access options.\
  \ To find out more about custom profiles, please [contact us](https://www.graphhopper.com/contact-form/).\n\
  \ * a sophisticated `motorcycle` profile is available up on request. It is powered\
  \ by the [Kurviger](https://kurviger.de/en) Routing API and favors curves and slopes\
  \ while avoiding cities and highways.\n \n## TomTom\n\nIf you want to include traffic,\
  \ you can purchase the TomTom Add-on.\nThis Add-on only uses TomTom's road network\
  \ and historical traffic information.\nLive traffic is not yet considered. If you\
  \ are interested to learn how we consider traffic information, we recommend that\
  \ you read [this article](https://www.graphhopper.com/blog/2017/11/06/time-dependent-optimization/).\n\
  \nPlease note the following:\n\n * Currently we only offer this for our [Route Optimization\
  \ API](#tag/Route-Optimization-API).\n * In addition to our terms, you need to accept\
  \ TomTom's [End User License Aggreement](https://www.graphhopper.com/tomtom-end-user-license-agreement/).\n\
  \ * We do *not* use TomTom's web services. We only use their data with our software.\n\
  \ \n[Contact us](https://www.graphhopper.com/contact-form/) for more details.\n\n\
  #### Geographical Coverage\n\nWe offer\n\n- Europe including Russia\n- North, Central\
  \ and South America\n- Saudi Arabia\n- United Arab Emirates\n- South Africa\n- Australia\n\
  \n#### Supported Vehicle Profiles\n\nName       | Description           | Restrictions\
  \              | Icon\n-----------|:----------------------|:--------------------------|:---------------------------------------------------------\n\
  car        | Car mode              | car access                | ![car image](https://graphhopper.com/maps/img/car.png)\n\
  small_truck| Small truck like a Mercedes Sprinter, Ford Transit or Iveco Daily |\
  \ height=2.7m, width=2+0.4m, length=5.5m, weight=2080+1400 kg | ![small truck image](https://graphhopper.com/maps/img/small_truck.png)\n"
logo: "graphhopper.com-logo.png"
logoMediaType: "image/png"
tags:
- "location"
stubs: "graphhopper.com-stubs.json"
swagger: "graphhopper.com-swagger.json"
---