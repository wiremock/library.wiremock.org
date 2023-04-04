---
slug: "taxrates-io"
title: "Taxrates.io API"
provider: "taxrates.io"
description: "<h3>Introduction</h3>\n<p>Taxrates.io is a global tax rate service that\
  \ automates the management of monitoring tax rates changes in 181 countries. We\
  \ monitor over 14,000 US sales tax, VAT, GST rates for you and make updates via\
  \ our API so you always have the most update tax rates.</p>\n<p>You can use Taxrates.io\
  \ as a virtual sandbox where we provide you with 30 days free trial.</p>\n<h3>Countries</h3>\n\
  <p>We currently support the following countries around the world. If you would like\
  \ to request the addition of a new country, please email us at\_<a href=\"mailto:support@taxrates.io\"\
  >support@taxrates.io</a></p>\n<table>\n  <tr><td>Afghanistan</td><td>Gambia</td><td>Nicaragua</td></tr>\n\
  \  <tr><td>Albania</td><td>Georgia</td><td>Niger</td></tr>\n  <tr><td>Andorra</td><td>Germany</td><td>Nigeria</td></tr>\n\
  \  <tr><td>Angola</td><td>Ghana</td><td>North Korea</td></tr>\n  <tr><td>Antigua\
  \ and Barbuda</td><td>Greece</td><td>Norway</td></tr>\n  <tr><td>Argentina</td><td>Grenada</td><td>Pakistan</td></tr>\n\
  \  <tr><td>Armenia</td><td>Guam</td><td>Palestine</td></tr>\n  <tr><td>Aruba</td><td>Guatemala</td><td>Panama</td></tr>\n\
  \  <tr><td>Australia</td><td>Guinea</td><td>Papua New Guinea</td></tr>\n  <tr><td>Austria</td><td>Guyana</td><td>Paraguay</td></tr>\n\
  \  <tr><td>Azerbaijan</td><td>Haiti</td><td>Peru</td></tr>\n  <tr><td>Bahamas</td><td>Honduras</td><td>Philippines</td></tr>\n\
  \  <tr><td>Bangladesh</td><td>Hungary</td><td>Poland</td></tr>\n  <tr><td>Barbados</td><td>Iceland</td><td>Portugal</td></tr>\n\
  \  <tr><td>Belarus</td><td>India</td><td>Puerto Rico</td></tr>\n  <tr><td>Belgium</td><td>Indonesia</td><td>Republic\
  \ of the Congo</td></tr>\n  <tr><td>Belize</td><td>Iran</td><td>Romania</td></tr>\n\
  \  <tr><td>Benin</td><td>Ireland</td><td>Russian Federation</td></tr>\n  <tr><td>Bhutan</td><td>Isle\
  \ of Man</td><td>Rwanda</td></tr>\n  <tr><td>Bolivia</td><td>Israel</td><td>Samoa</td></tr>\n\
  \  <tr><td>Bonaire</td><td>Italy</td><td>Senegal</td></tr>\n  <tr><td>Bosnia and\
  \ Herzegovina</td><td>Japan</td><td>Serbia</td></tr>\n  <tr><td>Botswana</td><td>Jersey</td><td>Seychelles</td></tr>\n\
  \  <tr><td>Brazil</td><td>Jordan</td><td>Sierra Leone</td></tr>\n  <tr><td>Bulgaria</td><td>Jordan</td><td>Singapore</td></tr>\n\
  \  <tr><td>Burkina Faso</td><td>Kazakhstan</td><td>Slovakia</td></tr>\n  <tr><td>Burundi</td><td>Kenya</td><td>Slovenia</td></tr>\n\
  \  <tr><td>Cambodia</td><td>Kiribati</td><td>Solomon Islands</td></tr>\n  <tr><td>Cameroon</td><td>Kosovo</td><td>Somalia</td></tr>\n\
  \  <tr><td>Cape Verde</td><td>Kyrgyzstan</td><td>South Africa</td></tr>\n  <tr><td>Central\
  \ African Republic</td><td>Laos</td><td>South Korea</td></tr>\n  <tr><td>Chad</td><td>Latvia</td><td>South\
  \ Sudan</td></tr>\n  <tr><td>Chile</td><td>Lebanon</td><td>Spain</td></tr>\n  <tr><td>China</td><td>Lesotho</td><td>Sri\
  \ Lanka</td></tr>\n  <tr><td>Columbia</td><td>Liberia</td><td>St Lucia</td></tr>\n\
  \  <tr><td>Comoros</td><td>Liechtenstein</td><td>Sudan</td></tr>\n  <tr><td>Cook\
  \ Islands</td><td>Lithuania</td><td>Suriname</td></tr>\n  <tr><td>Costa Rica</td><td>Luxembourg</td><td>Swaziland</td></tr>\n\
  \  <tr><td>Cote d'Ivoire</td><td>Macedonia</td><td>Sweden</td></tr>\n  <tr><td>Croatia</td><td>Madagascar</td><td>Switzerland</td></tr>\n\
  \  <tr><td>Cuba</td><td>Malawi</td><td>Tahiti</td></tr>\n  <tr><td>Curacao</td><td>Malaysia</td><td>Taiwan</td></tr>\n\
  \  <tr><td>Cyprus</td><td>Maldives</td><td>Tajikistan</td></tr>\n  <tr><td>Czech\
  \ Republic</td><td>Mali</td><td>Tanzania</td></tr>\n  <tr><td>Democratic Republic\
  \ of the Congo</td><td>Malta</td><td>Thailand</td></tr>\n  <tr><td>Denmark</td><td>Mauritania</td><td>Togo</td></tr>\n\
  \  <tr><td>Djbouti</td><td>Mauritius</td><td>Tonga</td></tr>\n  <tr><td>Dominica</td><td>Mexico</td><td>Trinidad\
  \ and Tobago</td></tr>\n  <tr><td>Dominican Republic</td><td>Micronesia</td><td>Tunisia</td></tr>\n\
  \  <tr><td>Ecuador</td><td>Moldova</td><td>Turkmenistan</td></tr>\n  <tr><td>Egypt</td><td>Monaco</td><td>Tuvalu</td></tr>\n\
  \  <tr><td>El Salvador</td><td>Mongolia</td><td>Uganda</td></tr>\n  <tr><td>Equatorial\
  \ Guinea</td><td>Montenegro</td><td>Ukraine</td></tr>\n  <tr><td>Eritrea</td><td>Morocco</td><td>United\
  \ Kingdom</td></tr>\n  <tr><td>Estonia</td><td>Mozambique</td><td>United States</td></tr>\n\
  \  <tr><td>Ethiopia</td><td>Myanmar</td><td>Uruguay</td></tr>\n  <tr><td>Fiji</td><td>Namibia</td><td>Vanuatu</td></tr>\n\
  \  <tr><td>Finland</td><td>Nepal</td><td>Venezuela</td></tr>\n  <tr><td>France</td><td>Netherlands</td><td>Vietnam</td></tr>\n\
  \  <tr><td>Gabon</td><td>New Zealand</td><td>Yemen</td></tr>\n</table>\n<h3>Products\
  \ codes</h3>\n<p>The Taxrates.io API’s provides product-level tax rates for a subset\
  \ of product codes. These codes are to be used for products that are either exempt\
  \ from tax in some jurisdictions or are taxed at reduced rates.</p>\n<p>We will\
  \ be expanding support for additional, less common categories over time. If you\
  \ would like to request the addition of a new product category, please email us\
  \ at\_<a href=\"mailto:support@taxrates.io\">support@taxrates.io</a></p>\n<p>Please\
  \ select a product code/s when making a request to the Taxrates.io API</p>\n<table>\n\
  \  <tr><th>Product code</th><th>Product Description</th></tr>\n  <tr><td>C010</td><td>Services\
  \ which are not subject to a service-specific tax</td></tr>\n  <tr><td>C011</td><td>Software\
  \ - Downloaded</td></tr>\n  <tr><td>C012</td><td>Books - Downloaded</td></tr>\n\
  \  <tr><td>C011</td><td>Music - Downloaded</td></tr>\n  <tr><td>C011</td><td>Movies/Digital\
  \ Video - Downloaded</td></tr>\n  <tr><td>C011</td><td>Other Electronic Goods -\
  \ Downloaded</td></tr>\n  <tr><td>C011</td><td>Streaming Music/Audio Services new</td></tr>\n\
  \  <tr><td>C011</td><td>Streaming Video Services new</td></tr>\n  <tr><td>C018</td><td>Software\
  \ as a Services, Generally (Remote Access to Hosted Software)</td></tr>\n  <tr><td>C018</td><td>Remote\
  \ Access to Hosted Software - Personal Use</td></tr>\n  <tr><td>C018</td><td>Remote\
  \ Access to Hosted Software - Business Use</td></tr>\n  <tr><td>C021</td><td>Remote\
  \ Access to Hosted Business Custom Applications</td></tr>\n  <tr><td>C021</td><td>Personal\
  \ Cloud Storage/Backup</td></tr>\n  <tr><td>C021</td><td>Business Cloud Storage/Backup</td></tr>\n\
  \  <tr><td>C021</td><td>Business Data Warehouses</td></tr>\n  <tr><td>C022</td><td>Infrastructure\
  \ as Service, Generally</td></tr>\n  <tr><td>C022</td><td>Ecommerce Site/Webserver\
  \ Hosting</td></tr>\n  <tr><td>C022</td><td>Provision of Virtual Computing Capacity</td></tr>\n\
  \  <tr><td>C022</td><td>Software - package or canned program</td></tr>\n  <tr><td>C022</td><td>Software\
  \ - modifications to canned program</td></tr>\n  <tr><td>C022</td><td>Software -\
  \ custom programs - material</td></tr>\n  <tr><td>C022</td><td>Software - custom\
  \ programs - professional serv.</td></tr>\n  <tr><td>C022</td><td>Information services</td></tr>\n\
  \  <tr><td>C022</td><td>Data processing services</td></tr>\n  <tr><td>C022</td><td>Mainframe\
  \ computer access and processing serv.</td></tr>\n  <tr><td>C022</td><td>Online\
  \ Data processing services</td></tr>\n</table>\n<h3>Filtering</h3>\n<p>When calling\
  \ the API endpoints you can use 'filter' parameters to get tax rate for the selected\
  \ type. You can get the following tax types (Each tax rate will always have one\
  \ of following types)</p>\n<h3>US Sales tax Rates</h3>\n<ol>\n  <li>CombinedRate</li>\n\
  \  <li>StateRate</li>\n  <li>CountyRate</li>\n  <li>CityRate</li>\n  <li>SpecialRate</li>\n\
  </ol>\n<p>We recommend using\_<a href=\"https://www.getpostman.com/\">Postman</a>\_\
  when discovering our API. Happy using!</p>\n<h3>Rate Limiting</h3>\n<p>We limit\
  \ API requests.</p>\n<p>If you’re exceeding this rate and encountering 429 errors,\
  \ review the following:</p>\n<ul>\n  <li>Only make requests in states / regions\
  \ where you have enabled.</li>\n  <li>Cache responses if the order details haven’\
  t changed since the last calculation at checkout.</li>\n</ul>\n<h3>Errors</h3>\n\
  <p>The Taxrates.io API uses the following error codes:<p/>\n<table>\n  <tr><th>Code</th><th>Error\
  \ Message</th></tr>\n  <tr><td>400</td><td>Bad Request – Your request format is\
  \ bad.</td></tr>\n  <tr><td>401</td><td>Unauthorized – Your API key is wrong.</td></tr>\n\
  \  <tr><td>404</td><td>Not Found – The specified resource could not be found.</td></tr>\n\
  \  <tr><td>405</td><td>Method Not Allowed – You tried to access a resource with\
  \ an invalid method.</td></tr>\n  <tr><td>429</td><td>Too Many Requests – You’re\
  \ requesting too many resources! Slow down!</td></tr>\n  <tr><td>500</td><td>Internal\
  \ Server Error – We had a problem with our server. Try again later.</td></tr>\n\
  \  <tr><td>503</td><td>Service Unavailable – We’re temporarily offline for maintenance.\
  \ Try again later.</td></tr>\n</table>\n<p>Verify your API token is correct and\
  \ make sure you’re correctly setting the\_<a href=\"#authentication\">Authorization\
  \ header</a>.</p>\n<p>If you’re still not sure what’s wrong,\_<a href=\"mailto:support@taxrates.io\"\
  >contact us</a>\_and we’ll investigate.</p>\n<h3>Changelog</h3>\n<p>Stay on top\
  \ of new developer-facing features, accuracy improvements, and bug fixes for our\
  \ API. Have a request? Encounter an issue?\_<a href=\"mailto:support@taxrates.io\"\
  >We’d love to hear your feedback.</a></p>\n\n\nContact Support:\n Name: apiteam@taxrates.io"
logo: "taxrates.io-logo.jpeg"
logoMediaType: "image/jpeg"
tags:
- "financial"
stubs: "taxrates.io-stubs.json"
swagger: "taxrates.io-swagger.json"
---