EMODnet web service documentation
=================================
## R tutorial
Try out the EMODnet OGC web services in our R tutorial.
View the tutorial [here](./R-tutorial) or run it interactively with Binder:

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/EMODnet/Web-Service-Documentation/main?urlpath=lab/tree/R-tutorial/index.ipynb)

## Documentation

This document has links to all EMODnet web services that allow you to search, visualise and download EMODnet data and data products.

### Metadata services

The EMODnet catalogues and other partner catalogues (IFREMER,
etc.) offer the ability to search collections of metadata for data,
services and related information objects related to the EMODnet Marine
Data. The data catalogues offer a **CSW** endpoint to other client
applications to connect to the service and query the metadata held in
the catalogue.

  -------------------------- -------------------------------------------------------------------------------------------------------------------------
| Portal | CSW GetCapabilities |
|-|-|
| Central portal | https://www.emodnet.eu/geonetwork/emodnet/eng/csw?service=CSW&request=GetCapabilities&VERSION=2.0.2 |
| Bathymetry |  |
| Biology |  |
| Chemistry | https://sextant.ifremer.fr/geonetwork/srv/eng/csw-EMODNET_Chemistry?service=CSW&request=GetCapabilities&VERSION=2.0.2 |
| Geology | https://drive.emodnet-geology.eu/geonetwork/srv/eng/csw?service=CSW&request=GetCapabilities&VERSION=2.0.2 |
| Human activities |  |
| Physics | [https://catalogue.emodnet-physics.eu/geonetwork/srv/eng/csw?service=CSW&request=GetCapabilities&VERSION=2.0.2 |
| Seabed habitats |  |
  -------------------------- -------------------------------------------------------------------------------------------------------------------------

#### CSW GetCapabilities

The mandatory GetCapabilities operation allows CSW clients to retrieve
service metadata from a server. The response to a GetCapabilities
request shall be an XML document containing service metadata about the
server. This subclause specifies the XML document that a CSW server
shall return to describe its capabilities.

#### CSW GetRecords

GetRecords requests allows to query and filter the catalogue metadata records.

EMODnet central portal GetRecords example:

>   [https://www.emodnet.eu/geonetwork/emodnet/eng/csw?REQUEST=GetRecords&SERVICE=CSW&VERSION=2.0.2&ELEMENTSETNAME=summary&OUTPUTSCHEMA=http://www.opengis.net/cat/csw/2.0.2&CONSTRAINTLANGUAGE=FILTER&CONSTRAINT_LANGUAGE_VERSION=1.1.0&RESULTTYPE=results&TYPENAMES=csw:Record&CONSTRAINT=&lt;ogc:Filter xmlns:ogc="http://www.opengis.net/ogc"&gt;&lt;ogc:PropertyIsEqualTo&gt;&lt;ogc:PropertyName&gt;dc:type&lt;/ogc:PropertyName&gt;&lt;ogc:Literal&gt;dataset&lt;/ogc:Literal&gt;&lt;/ogc:PropertyIsEqualTo&gt;&lt;/ogc:Filter&gt;&maxRecords=1000](https://www.emodnet.eu/geonetwork/emodnet/eng/csw?REQUEST=GetRecords&SERVICE=CSW&VERSION=2.0.2&ELEMENTSETNAME=summary&OUTPUTSCHEMA=http://www.opengis.net/cat/csw/2.0.2&CONSTRAINTLANGUAGE=FILTER&CONSTRAINT_LANGUAGE_VERSION=1.1.0&RESULTTYPE=results&TYPENAMES=csw:Record&CONSTRAINT=%3Cogc:Filter%20xmlns:ogc=%22http://www.opengis.net/ogc%22%3E%3Cogc:PropertyIsEqualTo%3E%3Cogc:PropertyName%3Edc:type%3C/ogc:PropertyName%3E%3Cogc:Literal%3Edataset%3C/ogc:Literal%3E%3C/ogc:PropertyIsEqualTo%3E%3C/ogc:Filter%3E&maxRecords=1000)

EMODnet Physics GetRecords example:

>   [https://catalogue.emodnet-physics.eu/geonetwork/srv/eng/csw?REQUEST=GetRecords&SERVICE=CSW&VERSION=2.0.2&ELEMENTSETNAME=summary&OUTPUTSCHEMA=http://www.opengis.net/cat/csw/2.0.2&CONSTRAINTLANGUAGE=FILTER&CONSTRAINT_LANGUAGE_VERSION=1.1.0&RESULTTYPE=results&TYPENAMES=csw:Record&CONSTRAINT=&lt;ogc:Filter xmlns:ogc="http://www.opengis.net/ogc"&gt;&lt;ogc:PropertyIsEqualTo&gt;&lt;ogc:PropertyName&gt;dc:type&lt;/ogc:PropertyName&gt;&lt;ogc:Literal&gt;dataset&lt;/ogc:Literal&gt;&lt;/ogc:PropertyIsEqualTo&gt;&lt;/ogc:Filter&gt;&maxRecords=1000](http://catalog.emodnet-physics.eu/geonetwork/srv/eng/csw?REQUEST=GetRecords&SERVICE=CSW&VERSION=2.0.2&ELEMENTSETNAME=summary&OUTPUTSCHEMA=http://www.opengis.net/cat/csw/2.0.2&CONSTRAINTLANGUAGE=FILTER&CONSTRAINT_LANGUAGE_VERSION=1.1.0&RESULTTYPE=results&TYPENAMES=csw:Record&CONSTRAINT=%3Cogc:Filter%20xmlns:ogc=%22http://www.opengis.net/ogc%22%3E%3Cogc:PropertyIsEqualTo%3E%3Cogc:PropertyName%3Edc:type%3C/ogc:PropertyName%3E%3Cogc:Literal%3Edataset%3C/ogc:Literal%3E%3C/ogc:PropertyIsEqualTo%3E%3C/ogc:Filter%3E&maxRecords=1000)

#### CSW GetRecordById

GetRecordById requests retrieves catalogue metadata records using their
identifier.

EMODnet central portal GetRecordById example

>   https://www.emodnet.eu/geonetwork/emodnet/eng/csw?request=GetRecordById&service=CSW&version=2.0.2&elementSetName=full&id=5d4696dc-bac4-4dd4-82c5-258700553cb4

### Data visualisation services

The Web Map Service standard (**WMS**) provides a simple HTTP interface
for requesting geo-registered map images from one or more distributed
geospatial databases. A WMS request defines the geographic layer(s) and
area of interest to be processed. The response to the request is one or
more geo-registered map images (returned as JPEG, PNG, etc) that can be
displayed in a Geographic Information System (GIS) or in your own web
application (OpenLayers, Leaflet,\...).

The WMS supports the GetCapabilities, GetMap and GetFeatureInfo
operations as defined in the Open Geospatial Consortium (OGC) WMS
standard.

The EMODnet WMS services are accessible from 7 thematic portals at the
Pan-European scale or global scale for some specific data products.
Enter one of the following WMS endpoint URLs into your WMS client (QGIS,
ArcMap, MapInfo etc.):

  --------------------------------------------------------------------- -------------------------------------------------------------------------------------------------------------------------
  | Portal           | Description                                                                   | WMS GetCapabilities                                                                                                 |
  |:-----------------|:------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------|
  | Bathymetry       | Data Products                                                                 | https://ows.emodnet-bathymetry.eu/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0                             |
  | Biology          | Data Products                                                                 | https://geo.vliz.be/geoserver/Emodnetbio/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0                      |
  | Biology          | Occurrence data                                                               | https://geo.vliz.be/geoserver/Dataportal/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0                      |
  | Chemistry        | Eutrophication by sea region                                                  | https://ec.oceanbrowser.net/emodnet/Python/web/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0                |
  | Chemistry        | Eutrophication                                                                | https://ec.oceanbrowser.net/emodnet-projects/Python/web/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0       |
  | Chemistry        | Litter                                                                        | https://www.ifremer.fr/services/wms/emodnet_chemistry2?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0            |
  | Chemistry        | Contaminants                                                                  | https://nodc.ogs.trieste.it/geoserver/Contaminants/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0            |
  | Chemistry        | CDI Data Discovery and Access service                                         | https://geo-service.maris.nl/emodnet_chemistry/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0                |
  | Chemistry        | Distribution of CDI observations per data category (P36) and MSFD sea regions | https://geo-service.maris.nl/emodnet_chemistry_p36/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0            |
  | Geology          | Sea-floor (bedrock)                                                           | https://drive.emodnet-geology.eu/geoserver/bgr/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0                |
  | Geology          | Marine Minerals                                                               | https://drive.emodnet-geology.eu/geoserver/gsi/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0                |
  | Geology          | Seabed Substrate maps                                                         | https://drive.emodnet-geology.eu/geoserver/gtk/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0                |
  | Geology          | Events and Probabilities                                                      | https://drive.emodnet-geology.eu/geoserver/ispra/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0              |
  | Geology          | Coastal Behavior                                                              | https://drive.emodnet-geology.eu/geoserver/tno/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0                |
  | Geology          | Submerged Landscapes                                                          | https://drive.emodnet-geology.eu/geoserver/bgs/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0                |
  | Geology          | Index of borehole and geophysics data                                         | https://drive.emodnet-geology.eu/geoserver/geus/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0               |
  | Human Activities | Data and Data Products                                                        | https://ows.emodnet-humanactivities.eu/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0                        |
  | Physics          | Platforms                                                                     | http://geoserver.emodnet-physics.eu/geoserver/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0                 |
  | Seabed Habitats  | General datasets and products                                                 | https://ows.emodnet-seabedhabitats.eu/emodnet_view/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0            |
  | Seabed Habitats  | Individual habitat map and model datasets                                     | https://ows.emodnet-seabedhabitats.eu/emodnet_view_maplibrary/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0 |
  --------------------------------------------------------------------- -------------------------------------------------------------------------------------------------------------------------

#### WMS GetCapabilities

The mandatory GetCapabilities operation allows WMS clients to retrieve
service metadata from a server. The response to a GetCapabilities
request shall be an XML document containing metadata of the service
(proposed layers, associated projections, author \...).

The standard to construct a WMS GetCapabilities request, depending on
the version:

> {wms endpoint url}?SERVICE=WMS&VERSION=1.3.0&REQUEST=GetCapabilities

or

> {wms endpoint url}?SERVICE=WMS&VERSION=1.1.1&REQUEST=GetCapabilities

#### WMS GetMap

Using the information given in the GetCapabilities request, the GetMap
request returns a raster map containing the requested data layer
selected from all the available layers as defined in the XML document.
The elements such as the data layer, region, projection, size of the
returned image, image format, etc. are defined in the form of arguments.

Example of a GetMap request that returns an image of the EMODnet
Bathymetry Mean depth (DTM) based on source resolution of 1/8 arc minute
(\~250 meter) in multi colour style:

>   https://ows.emodnet-bathymetry.eu/wms?service=WMS&service=WMS&request=GetMap&version=1.1.1&layers=emodnet:mean_multicolour&styles=&format=image/png&transparent=true&info_format=text/html&tiled=false&width=400&height=628&srs=EPSG:3857&bbox=-2669794,2250306,4800533,14538934

Returns:

> <img src="https://ows.emodnet-bathymetry.eu/wms?service=WMS&service=WMS&request=GetMap&version=1.1.1&layers=emodnet:mean_multicolour&styles=&format=image/png&transparent=true&info_format=text/html&tiled=false&width=400&height=628&srs=EPSG:3857&bbox=-2669794,2250306,4800533,14538934" />

### Data download services

The EMODnet data layers are available as a Web Feature Service (WFS) or
Web Coverage Service (WCS) in accordance with the Open Geospatial
Consortium (OGC) specifications
([www.opengeospatial.org](http://www.opengeospatial.org)).

Note that some portals provide other, non-OGC, web services too. For example
EMODnet Bathymetry offers a REST service, EMODnet Biology allows
specific parameters in the WFS requests, EMODnet Chemistry has an
OPeNDAP service,\... See [section
1.3.9.](#other-web-services-by-thematic-portals)

#### Web Feature Service (WFS)

WFS defines a standard for exchanging vector data by querying both the
data structure and the source data. The basic operations are
GetCapabilities, DescribeFeatureType, and GetFeature. WFS supports a
variety of WFS output formats (Ex: GML, shapefile, json, geojson,
CSV,\...). The full list of output formats supported can be found by
performing a WFS GetCapabilities request.

The EMODnet WFS services are accessible from following endpoints:

  --------------------------------------------------------------------- -------------------------------------------------------------------------------
  | Portal           | Description                                                                   | WFS GetCapabilities                                                                                                 |
  |:-----------------|:------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------|
  | Bathymetry       | Data Products                                                                 | https://ows.emodnet-bathymetry.eu/wfs?SERVICE=WFS&REQUEST=GetCapabilities&VERSION=2.0.0                             |
  | Biology          | Data Products                                                                 | https://geo.vliz.be/geoserver/Emodnetbio/wfs?SERVICE=WFS&REQUEST=GetCapabilities&VERSION=2.0.0                      |
  | Biology          | Occurrence data                                                               | https://geo.vliz.be/geoserver/Dataportal/wfs?SERVICE=WFS&REQUEST=GetCapabilities&VERSION=2.0.0                      |
  | Chemistry        | Litter                                                                        | https://www.ifremer.fr/services/wfs/emodnet_chemistry2?SERVICE=WFS&REQUEST=GetCapabilities&VERSION=2.0.0            |
  | Chemistry        | Contaminants                                                                  | https://nodc.ogs.trieste.it/geoserver/Contaminants/wfs?SERVICE=WFS&REQUEST=GetCapabilities&VERSION=2.0.0            |
  | Chemistry        | CDI Data Discovery and Access service                                         | https://geo-service.maris.nl/emodnet_chemistry/wfs?SERVICE=WFS&REQUEST=GetCapabilities&VERSION=2.0.0                |
  | Chemistry        | Distribution of CDI observations per data category (P36) and MSFD sea regions | https://geo-service.maris.nl/emodnet_chemistry_p36/wfs?SERVICE=WFS&REQUEST=GetCapabilities&VERSION=2.0.0            |
  | Geology          | Sea-floor (bedrock)                                                           | https://drive.emodnet-geology.eu/geoserver/bgr/wfs?SERVICE=WFS&REQUEST=GetCapabilities&VERSION=2.0.0                |
  | Geology          | Marine Minerals                                                               | https://drive.emodnet-geology.eu/geoserver/gsi/wfs?SERVICE=WFS&REQUEST=GetCapabilities&VERSION=2.0.0                |
  | Geology          | Seabed Substrate maps                                                         | https://drive.emodnet-geology.eu/geoserver/gtk/wfs?SERVICE=WFS&REQUEST=GetCapabilities&VERSION=2.0.0                |
  | Geology          | Events and Probabilities                                                      | https://drive.emodnet-geology.eu/geoserver/ispra/wfs?SERVICE=WFS&REQUEST=GetCapabilities&VERSION=2.0.0              |
  | Geology          | Coastal Behavior                                                              | https://drive.emodnet-geology.eu/geoserver/tno/wfs?SERVICE=WFS&REQUEST=GetCapabilities&VERSION=2.0.0                |
  | Geology          | Submerged Landscapes                                                          | https://drive.emodnet-geology.eu/geoserver/bgs/wfs?SERVICE=WFS&REQUEST=GetCapabilities&VERSION=2.0.0                |
  | Geology          | Index of borehole and geophysics data                                         | https://drive.emodnet-geology.eu/geoserver/geus/wfs?SERVICE=WFS&REQUEST=GetCapabilities&VERSION=2.0.0               |
  | Human Activities | Data and Data Products                                                        | https://ows.emodnet-humanactivities.eu/wfs?SERVICE=WFS&REQUEST=GetCapabilities&VERSION=2.0.0                        |
  | Physics          | Platforms                                                                     | http://geoserver.emodnet-physics.eu/geoserver/wfs?SERVICE=WFS&REQUEST=GetCapabilities&VERSION=2.0.0                 |
  | Seabed Habitats  | General datasets and products                                                 | https://ows.emodnet-seabedhabitats.eu/emodnet_open/wfs?SERVICE=WFS&REQUEST=GetCapabilities&VERSION=2.0.0            |
  | Seabed Habitats  | Individual habitat map and model datasets                                     | https://ows.emodnet-seabedhabitats.eu/emodnet_open_maplibrary/wfs?SERVICE=WFS&REQUEST=GetCapabilities&VERSION=2.0.0 |
  --------------------------------------------------------------------- -------------------------------------------------------------------------------

##### WFS GetCapabilities

A GetCapabilities request generates a metadata document (xml) describing
a WFS service provided by server as well as valid WFS operations and
parameters.

##### WFS DescribeFeature

A DescribeFeature request returns a description of feature types
supported by a WFS service.

Example of a EMODnet Biology DescribeFeature request:

>   https://geo.vliz.be/geoserver/Dataportal/wfs?service=wfs&version=2.0.0&request=DescribeFeatureType&typeName=Dataportal:eurobis&outputFormat=application/json

Example of a EMODnet Human Activities DescribeFeature request:

>   https://ows.emodnet-humanactivities.eu/wfs?SERVICE=WFS&VERSION=1.1.0&request=describeFeatureType&typeName=shellfish&bbox=-1.3,0.3,49.2,49.9

##### WFS GetFeature

A GetFeature request returns a selection of features from a data source
including geometry and attribute values.

Example of a EMODnet Human Activities GetFeature request:

>   https://ows.emodnet-humanactivities.eu/wfs?SERVICE=WFS&VERSION=1.1.0&request=getFeature&typeName=shellfish&bbox=-1.3,0.3,49.2,49.9&outputFormat=application/json

#### Web Coverage Service (WCS)

The EMODnet portals provide Web Coverage Services (WCS) to support
requests for coverage data (rasters) or gridded data products. Enter one
of the following addresses into your WCS client:

  --------------------------------------------------------------------- ---------------------------------------------------------------------
  | Portal           | Description                               | WCS GetCapabilities                                                                                                 |
  |:-----------------|:------------------------------------------|:--------------------------------------------------------------------------------------------------------------------|
  | Bathymetry       | Data Products                             | https://ows.emodnet-bathymetry.eu/wcs?SERVICE=WCS&REQUEST=GetCapabilities&VERSION=2.0.1                             |
  | Biology          | Data Products                             | https://geo.vliz.be/geoserver/Emodnetbio/wcs?SERVICE=WCS&REQUEST=GetCapabilities&VERSION=2.0.1                      |
  | Human Activities | Data and Data Products                    | https://ows.emodnet-humanactivities.eu/wcs?SERVICE=WCS&REQUEST=GetCapabilities&VERSION=2.0.1                        |
  | Physics          | Platforms                                 | http://geoserver.emodnet-physics.eu/geoserver/wcs?SERVICE=WCS&REQUEST=GetCapabilities&VERSION=2.0.1                 |
  | Seabed Habitats  | Individual habitat map and model datasets | https://ows.emodnet-seabedhabitats.eu/emodnet_open_maplibrary/wcs?SERVICE=WCS&REQUEST=GetCapabilities&VERSION=2.0.1 |
  --------------------------------------------------------------------- ---------------------------------------------------------------------

##### WCS GetCapabilities

A WCS GetCapabilities request retrieves a list of the server's data, as
well as valid WCS operations and parameters.

##### WCS DescribeCoverage

A WCS DescribeCoverage request retrieves a metadata (XML) document that
fully describes the requested coverages.

Example of an EMODnet Bathymetry DescribeCoverage request:

>   [https://ows.emodnet-bathymetry.eu/wcs?service=wcs&version=1.0.0&request=DescribeCoverage&coverage=emodnet:mean](http://ows.emodnet-bathymetry.eu/wcs?service=wcs&version=1.0.0&request=DescribeCoverage&coverage=emodnet:mean)

##### WCS GetCoverage

A WCS GetCoverage request returns a coverage in a well known format.
Like a WMS GetMap request, but with several extensions to support the
retrieval of coverages.

Example of an EMODnet Bathymetry GetCoverage request:

>   <https://ows.emodnet-bathymetry.eu/wcs?service=wcs&version=1.0.0&request=getcoverage&coverage=emodnet:mean&crs=EPSG:4326&BBOX=-2.52,45.6,-1.08,46.40&format=image/tiff&interpolation=nearest&resx=0.00208333&resy=0.00208333>

### Non-OGC web services

  -------------------------- -------------------------------------------------------------------
  | Portal     | web service   | URL                                                        |
  |:-----------|:--------------|:-----------------------------------------------------------|
  | Bathymetry | REST API      | https://rest.emodnet-bathymetry.eu/                        |
  | Chemsitry  | OpenDap       | http://ec.oceanbrowser.net:8081/data/emodnet-domains/      |
  | Physics    | ERDDAP        | https://erddap.emodnet-physics.eu/                         |
  | Physics    | THREDDS       | http://thredds.emodnet-physics.eu/                         |
  | Physics    | SOAP API      | https://www.emodnet-physics.eu/Map/service/WSEmodnet2.aspx |
  -------------------------- -------------------------------------------------------------------

### Other useful links with documentation on EMODnet web services

* Bathymetry web Service documentation: https://www.emodnet-bathymetry.eu/data-products/web-services-and-standards
* Biology web Service documentation:  https://www.emodnet-biology.eu/emodnet-biology-api
* Chemistry web Service documentation: https://www.emodnet-chemistry.eu/products/api
* Chemistry GitHub: https://github.com/gher-ulg/EMODnet-Chemistry
* Geology web Service documentation: https://www.emodnet-geology.eu/services/
* Physics GitHub: https://github.com/EMODnet-Physics
* Seabed habitats Web service documentation: https://www.emodnet-seabedhabitats.eu/access-data/web-services/
* Seabed habitats GitHub: https://github.com/emodnetseabedhabitats
* Other repos in the main EMODnet GitHub: https://github.com/EMODnet

----------------------------------------------------------------------------------------------
<p align="center">
  Provided by EMODnet. See our <a href=https://emodnet.eu/en/terms-use> terms of use </a>
</p>
<p align="center">
  <a href="https://www.emodnet.eu">
    <img src="https://www.emodnet.eu/sites/emodnet.eu/files/public/logo_2x_1.png">
  </a>
</p>
