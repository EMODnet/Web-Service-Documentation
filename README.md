EMODnet web service documentation
=================================
### Metadata services

The EMODnet catalogues and other partner catalogues (IFREMER,
etc.) offer the ability to search collections of metadata for data,
services and related information objects related to the EMODnet Marine
Data. The data catalogues offer a **CSW** endpoint to other client
applications to connect to the service and query the metadata held in
the catalogue.

  -------------------------- -------------------------------------------------------------------------------------------------------------------------
| Portal | URL |
|-|-|
| EMODnet Central portal | [https://www.emodnet.eu/geonetwork/emodnet/eng/csw](https://www.emodnet.eu/geonetwork/emodnet/eng/csw?service=CSW&request=GetCapabilities) |
| EMODnet Bathymetry |  |
| EMODnet Biology |  |
| EMODNET Chemistry | [https://sextant.ifremer.fr/geonetwork/srv/eng/csw-EMODNET_Chemistry](https://sextant.ifremer.fr/geonetwork/srv/eng/csw-EMODNET_Chemistry?service=CSW&request=GetCapabilities) |
| EMODnet Geology | [https://drive.emodnet-geology.eu/geonetwork/srv/eng/csw](https://drive.emodnet-geology.eu/geonetwork/srv/eng/csw?service=CSW&request=GetCapabilities) |
| EMODnet Human activities |  |
| EMODnet Physics | [https://catalog.emodnet-physics.eu/geonetwork/srv/eng/csw](https://catalog.emodnet-physics.eu/geonetwork/srv/eng/csw?service=CSW&request=GetCapabilities) |
| EMODnet Seabed habitats |  |
  -------------------------- -------------------------------------------------------------------------------------------------------------------------

#### CSW GetCapabilities

The mandatory GetCapabilities operation allows CSW clients to retrieve
service metadata from a server. The response to a GetCapabilities
request shall be an XML document containing service metadata about the
server. This subclause specifies the XML document that a CSW server
shall return to describe its capabilities.

Examples of EMODnet CSW GetCapabilities:

> <http://www.emodnet.eu/geonetwork/emodnet/eng/csw?service=CSW&request=GetCapabilities&version=2.0.2>

> <https://sextant.ifremer.fr/geonetwork/srv/eng/csw?service=CSW&request=GetCapabilities&version=2.0.2>

#### CSW GetRecords

GetRecords requests allows to query the catalogue metadata records.

EMODnet central portal GetRecords example:

>   <http://www.emodnet.eu/geonetwork/emodnet/eng/csw?REQUEST=GetRecords&SERVICE=CSW&VERSION=2.0.2&ELEMENTSETNAME=summary&OUTPUTSCHEMA=http://www.opengis.net/cat/csw/2.0.2&CONSTRAINTLANGUAGE=FILTER&CONSTRAINT_LANGUAGE_VERSION=1.1.0&RESULTTYPE=results&TYPENAMES=csw:Record&CONSTRAINT=%3Cogc:Filter%20xmlns:ogc=%22http://www.opengis.net/ogc%22%3E%3Cogc:PropertyIsEqualTo%3E%3Cogc:PropertyName%3Edc:type%3C/ogc:PropertyName%3E%3Cogc:Literal%3Edataset%3C/ogc:Literal%3E%3C/ogc:PropertyIsEqualTo%3E%3C/ogc:Filter%3E&maxRecords=1000>

EMODnet Physics GetRecords example:

>   <http://catalog.emodnet-physics.eu/geonetwork/srv/eng/csw?REQUEST=GetRecords&SERVICE=CSW&VERSION=2.0.2&ELEMENTSETNAME=summary&OUTPUTSCHEMA=http://www.opengis.net/cat/csw/2.0.2&CONSTRAINTLANGUAGE=FILTER&CONSTRAINT_LANGUAGE_VERSION=1.1.0&RESULTTYPE=results&TYPENAMES=csw:Record&CONSTRAINT=%3Cogc:Filter%20xmlns:ogc=%22http://www.opengis.net/ogc%22%3E%3Cogc:PropertyIsEqualTo%3E%3Cogc:PropertyName%3Edc:type%3C/ogc:PropertyName%3E%3Cogc:Literal%3Edataset%3C/ogc:Literal%3E%3C/ogc:PropertyIsEqualTo%3E%3C/ogc:Filter%3E&maxRecords=1000>

#### CSW GetRecordById

GetRecordById requests retrieves catalogue metadata records using their
identifier.

EMODnet central portal GetRecordById example

>   <http://www.emodnet.eu/geonetwork/emodnet/eng/csw?request=GetRecordById&service=CSW&version=2.0.2&elementSetName=full&id=5d4696dc-bac4-4dd4-82c5-258700553cb4>

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
| Portal | URL |
|-|-|
| EMODnet Bathymetry | https://ows.emodnet-bathymetry.eu/wms |
| EMODnet Biology - data products | http://geo.vliz.be/geoserver/Emodnetbio/wms |
| EMODnet Biology - Occurrence data | http://geo.vliz.be/geoserver/Dataportal/wms |
| EMODnet Chemistry - Concentration maps by sea region | http://ec.oceanbrowser.net/emodnet/Python/web/wms |
| EMODnet Chemistry - Concentration maps by parameter | http://ec.oceanbrowser.net/emodnet-combined/Python/web/wms |
| EMODnet Chemistry - Plots | http://ec.oceanbrowser.net/emodnet/Python/web/wpswms |
| EMODnet Chemistry - Marine litter | https://www.ifremer.fr/services/wms/emodnet_chemistry2 |
| EMODnet Chemistry - CDI Data Discovery and Access service | https://geoservice.maris.nl/wms/seadatanet/EMODnet_chemistry |
| EMODnet Chemistry – CDI per parameter | http://geoservice.maris2.nl/wms/project/emodnet_chemistry_service/wms |
| EMODnet Geology – Sea-floor (bedrock) | https://drive.emodnet-geology.eu/geoserver/bgr/wms |
| EMODnet Geology – Marine Minerals | https://drive.emodnet-geology.eu/geoserver/gsi/wms |
| EMODnet Geology – Seabed Substrate maps | https://drive.emodnet-geology.eu/geoserver/gtk/wms |
| EMODnet Geology – Events and Probabilities | https://drive.emodnet-geology.eu/geoserver/ispra/wms |
| EMODnet Geology – Coastal Behavior | https://drive.emodnet-geology.eu/geoserver/tno/wms |
| EMODnet Geology – Submerged Landscapes | https://drive.emodnet-geology.eu/geoserver/bgs/wms |
| EMODnet Human activities | https://ows.emodnet-humanactivities.eu/wms |
| EMODnet Physics | https://geoserver.emodnet-physics.eu/geoserver/emodnet/wms |
| EMODnet Seabed Habitats – General datasets and products | https://ows.emodnet-seabedhabitats.eu/emodnet_view/wms |
| EMODnet Seabed Habitats - individual habitat map and model datasets | https://ows.emodnet-seabedhabitats.eu/emodnet_view_maplibrary/wms |
  --------------------------------------------------------------------- -------------------------------------------------------------------------------------------------------------------------

#### WMS GetCapabilities

The mandatory GetCapabilities operation allows WMS clients to retrieve
service metadata from a server. The response to a GetCapabilities
request shall be an XML document containing metadata of the service
(proposed layers, associated projections, author \...).

The standard to construct a WMS GetCapabilities request, depending on
the version:

(wms endpoint url)?SERVICE=WMS&VERSION=1.3.0&REQUEST=GetCapabilities or
(wms endpoint url)?SERVICE=WMS&VERSION=1.1.1&REQUEST=GetCapabilities

Example of a GetCapabilities request addressed to the EMODnet Physics
view service:

>   [https://geoserver.emodnet-physics.eu/geoserver/emodnet/wms?SERVICE=WMS&VERSION=1.3.0&REQUEST=GetCapabilities](http://geoserver.emodnet-physics.eu/geoserver/emodnet/wms?SERVICE=WMS&VERSION=1.3.0&REQUEST=GetCapabilities)

#### WMS GetMap

Using the information given in the GetCapabilities request, the GetMap
request returns a raster map containing the requested data layer
selected from all the available layers as defined in the XML document.
The elements such as the data layer, region, projection, size of the
returned image, image format, etc. are defined in the form of arguments.

Example of a GetMap request that returns an image of the EMODnet
Bathymetry Mean depth (DTM) based on source resolution of 1/8 arc minute
(\~250 meter) in multi colour style:

>   [https://ows.emodnet-bathymetry.eu/wms?service=WMS&service=WMS&request=GetMap&version=1.1.1&layers=emodnet%3Amean\_multicolour&styles=&format=image%2Fpng&transparent=true&info\_format=text%2Fhtml&tiled=false&width=400&height=628&srs=EPSG%3A3857&bbox=-2669794.954627626%2C2250306.11271559%2C4800533.188102208%2C14538934.276066802](http://ows.emodnet-bathymetry.eu/wms?service=WMS&service=WMS&request=GetMap&version=1.1.1&layers=emodnet%3Amean_multicolour&styles=&format=image%2Fpng&transparent=true&info_format=text%2Fhtml&tiled=false&width=400&height=628&srs=EPSG%3A3857&bbox=-2669794.954627626%2C2250306.11271559%2C4800533.188102208%2C14538934.276066802)

Returns:

> <img src="http://ows.emodnet-bathymetry.eu/wms?service=WMS&service=WMS&request=GetMap&version=1.1.1&layers=emodnet%3Amean_multicolour&styles=&format=image%2Fpng&transparent=true&info_format=text%2Fhtml&tiled=false&width=400&height=628&srs=EPSG%3A3857&bbox=-2669794.954627626%2C2250306.11271559%2C4800533.188102208%2C14538934.276066802" />

### Data download services

The EMODnet data layers are available as a Web Feature Service (WFS) or
Web Coverage Service (WCS) in accordance with the Open Geospatial
Consortium (OGC) specifications
([www.opengeospatial.org](http://www.opengeospatial.org)).

Note that some portals provide other download services too. For example
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
  | Portal | URL |
|-|-|
| EMODnet Bathymetry | https://ows.emodnet-bathymetry.eu/wfs |
| EMODnet Biology | http://geo.vliz.be/geoserver/Emodnetbio/wfs |
| EMODnet Biology - Occurrence data | http://geo.vliz.be/geoserver/Dataportal/wfs |
| EMODnet Chemistry - Marine litter | https://www.ifremer.fr/services/wfs/emodnet_chemistry2 |
| EMODnet Chemistry – Time series location | http://emodnet02.cineca.it/geoserver/wfs |
| EMODnet Geology – Sea-floor (bedrock) | https://drive.emodnet-geology.eu/geoserver/bgr/wfs |
| EMODnet Geology – Marine Minerals | https://drive.emodnet-geology.eu/geoserver/gsi/wfs |
| EMODnet Geology – Seabed Substrate maps | https://drive.emodnet-geology.eu/geoserver/gtk/wfs |
| EMODnet Geology – Events and Probabilities | https://drive.emodnet-geology.eu/geoserver/ispra/wfs |
| EMODnet Geology – Coastal Behavior | https://drive.emodnet-geology.eu/geoserver/tno/wfs |
| EMODnet Geology – Submerged Landscapes | https://drive.emodnet-geology.eu/geoserver/bgs/wfs |
| EMODnet Human activities | https://ows.emodnet-humanactivities.eu/wfs |
| EMODnet Physics | https://geoserver.emodnet-physics.eu/geoserver/emodnet/wfs |
| EMODnet Seabed Habitats – General datasets and products | https://ows.emodnet-seabedhabitats.eu/emodnet_open/wfs |
| EMODnet Seabed Habitats - individual habitat map and model datasets | https://ows.emodnet-seabedhabitats.eu/emodnet_open_maplibrary/wfs |
  --------------------------------------------------------------------- -------------------------------------------------------------------------------

##### WFS GetCapabilities

A GetCapabilities request generates a metadata document (xml) describing
a WFS service provided by server as well as valid WFS operations and
parameters.

Example of a EMODnet human activities GetCapabilities request:

>   <https://ows.emodnet-humanactivities.eu/wfs?SERVICE=WFS&VERSION=1.1.0&request=GetCapabilities>

##### WFS DescribeFeature

A DescribeFeature request returns a description of feature types
supported by a WFS service.

Example of a EMODnet Biology DescribeFeature request:

>   <http://geo.vliz.be/geoserver/Dataportal/wfs?service=wfs&version=2.0.0&request=DescribeFeatureType&typeName=Dataportal:eurobis&outputFormat=application/json>

Example of a EMODnet Human Activities DescribeFeature request:

>   <https://ows.emodnet-humanactivities.eu/wfs?SERVICE=WFS&VERSION=1.1.0&request=describeFeatureType&typeName=shellfish&bbox=-1.3,0.3,49.2,49.9>

##### WFS GetFeature

A GetFeature request returns a selection of features from a data source
including geometry and attribute values.

Example of a EMODnet Human Activities GetFeature request:

>   <https://ows.emodnet-humanactivities.eu/wfs?SERVICE=WFS&VERSION=1.1.0&request=getFeature&typeName=shellfish&bbox=-1.3,0.3,49.2,49.9&outputFormat=application/json>

#### Web Coverage Service (WCS)

The EMODnet portals provide Web Coverage Services (WCS) to support
requests for coverage data (rasters) or gridded data products. Enter one
of the following addresses into your WCS client:

  --------------------------------------------------------------------- ---------------------------------------------------------------------
| Portal | URL |
|-|-|
| EMODnet Bathymetry | https://ows.emodnet-bathymetry.eu/wcs |
| EMODnet Biology | http://geo.vliz.be/geoserver/Emodnetbio/wcs |
| EMODnet Human activities | https://ows.emodnet-humanactivities.eu/wcs |
| EMODnet Seabed Habitats - individual habitat map and model datasets | https://ows.emodnet-seabedhabitats.eu/emodnet_open_maplibrary/wcs |
  --------------------------------------------------------------------- ---------------------------------------------------------------------

##### WCS GetCapabilities

A WCS GetCapabilities request retrieves a list of the server's data, as
well as valid WCS operations and parameters.

Example of an EMODnet Bathymetry WCS GetCapabilities request:

>   <https://ows.emodnet-bathymetry.eu/wcs?service=wcs&version=1.0.0&request=GetCapabilities>

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

>   <https://ows.emodnet-bathymetry.eu/wcs?service=wcs&version=1.0.0&request=getcoverage&coverage=emodnet:mean&crs=EPSG:4326&BBOX=-2.08542634499992,45.656434726,-1.08908527599993,46.4319841780001&format=image/tiff&interpolation=nearest&resx=0.00208333&resy=0.00208333>

### Other web services by thematic portals

  -------------------------- -------------------------------------------------------------------
 | Portal | URL |
|-|-|
| EMODnet Bathymetry | https://portal.emodnet-bathymetry.eu/services/ |
| EMODnet Biology | http://www.emodnet-biology.eu/emodnet-biology-api |
| EMODNET Chemistry | https://www.emodnet-chemistry.eu/products/api |
| EMODnet Geology | https://www.emodnet-geology.eu/services/ |
| EMODnet Human activities |  |
| EMODnet Physics |  |
| EMODnet Seabed habitats | https://www.emodnet-seabedhabitats.eu/access-data/web-services/ |
  -------------------------- -------------------------------------------------------------------
