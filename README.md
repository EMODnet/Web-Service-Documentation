EMODnet web service documentation
==================================
This document has links to all web services that allow you to search, visualise and download EMODnet data and data products.

# OGC web services
The majority of EMODnet web services are Open Geospatial Consortium (OGC) web services, following international standards for geospatial metadata retrieval, visualisation and data access. The image below provides an overview of the different OGC web services offered by EMODnet.

<figure>
<img src="https://emodnet.ec.europa.eu/sites/emodnet.ec.europa.eu/files/public/images/ogc_standards.jpg" align="centre" width="100%"></img>
<figcaption>Overview of the types of OGC web services offered by EMODnet. This image was adapted from the <a href="https://github.com/jwagemann/2017_pydata_tutorial">Pydata 2017 workshop of Julia Wagemann</a>.</figcaption>
</figure>

## Tutorials

Tuturials on using EMODnet's OGC services in following programming languages are available:

* [OGC web service tutorials in Python](https://github.com/EMODnet/OGC-Webservices-Python-Tutorial)
* [OGC web service tutorials in R](https://github.com/EMODnet/OGC-Webservices-R-Tutorial)

## Metadata services
### Catalogues Service for the Web (CSW)

The [EMODnet central catalogue](https://emodnet.ec.europa.eu/geonetwork) offers a Catalogues Service for the Web (**CSW**) endpoint (see table below), a widely used OGC standard to search collections of metadata for data, services and related information objects and export the metadata in a range of formats. It supports three main HTTP requests (operations), which are submitted in the form of a URL.


| Thematic           | CSW GetCapabilities                                                                                                               |
| ------------------ | --------------------------------------------------------------------------------------------------------------------------------- |
| Central Catalogue  | https://emodnet.ec.europa.eu/geonetwork/emodnet/eng/csw?service=CSW&request=GetCapabilities&VERSION=2.0.2                         |

#### CSW GetCapabilities

The ***GetCapabilities*** request allows CSW clients to retrieve service metadata from a server. The response to a GetCapabilities request shall be an XML document containing service metadata about the server. This subclause specifies the XML document that a CSW server shall return to describe its capabilities.

 > Example:<br>
[https://emodnet.ec.europa.eu/geonetwork/emodnet/eng/csw?<br>
service=CSW&<br>
request=GetCapabilities&<br>
version=2.0.2](	https://emodnet.ec.europa.eu/geonetwork/emodnet/eng/csw?service=CSW&request=GetCapabilities&VERSION=2.0.2)


#### CSW GetRecords

The ***GetRecords*** request allows to query and filter the catalogue metadata records.

> Example: Return a summary of the metadata records in the EMODnet catalogue that contain the word temperature in any of it's metadata fields as specified in the `constraints` parameter (differnt types of filter languages are available, see the [GetCapabilities](https://emodnet.ec.europa.eu/geonetwork/emodnet/eng/csw?service=CSW&request=GetCapabilities&VERSION=2.0.2) of the service for more information), and then limited to only 10 records for the purpose of this example using the `maxrecords` parameter:<br>
[https://emodnet.ec.europa.eu/geonetwork/emodnet/eng/csw?<br>
    request=GetRecords&<br>
    service=CSW&<br>
    version=2.0.2&<br>
    elementSetName=summary&<br>
    outputschema=http://www.opengis.net/cat/csw/2.0.2&<br>
    constraintlanguage=filter&<br> 
    constraint_language_version=1.1.0&<br>
    constraint=<ogc:Filter xmlns:ogc="http://www.opengis.net/ogc"><br>
                    &nbsp;&nbsp;&nbsp;\<ogc:PropertyIsEqualTo><br>
                        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<ogc:PropertyName>csw:Anytext</ogc:PropertyName><br>
                        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<ogc:Literal>temperature</ogc:Literal><br>
                    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\</ogc:PropertyIsEqualTo><br>
                &nbsp;&nbsp;&nbsp;\</ogc:Filter>&<br>
    resulttype=results&<br>
    typenames=csw:record&<br>
    maxrecords=10](https://emodnet.ec.europa.eu/geonetwork/emodnet/eng/csw?REQUEST=GetRecords&SERVICE=CSW&VERSION=2.0.2&ELEMENTSETNAME=summary&OUTPUTSCHEMA=http://www.opengis.net/cat/csw/2.0.2&CONSTRAINTLANGUAGE=FILTER&CONSTRAINT_LANGUAGE_VERSION=1.1.0&RESULTTYPE=results&TYPENAMES=csw:Record&&maxRecords=10&CONSTRAINT=<ogc:Filter%20xmlns:ogc="http://www.opengis.net/ogc"><ogc:PropertyIsEqualTo><ogc:PropertyName>csw:Anytext</ogc:PropertyName><ogc:Literal>temperature</ogc:Literal></ogc:PropertyIsEqualTo></ogc:Filter>)

#### CSW GetRecordById

The ***GetRecordById*** request retrieves catalogue metadata records using their
identifier.

> Example: return a record of Temperature in the Water Column (1960 - 2023) - CORA dataset<br>
[https://emodnet.ec.europa.eu/geonetwork/emodnet/eng/csw?<br>
service=CSW&<br>
version=2.0.2&<br>
request=GetRecordById&<br>
elementSetName=full&<br>
id=c5c97c694b6210454af2e3f92a8499fa411a0b46](https://emodnet.ec.europa.eu/geonetwork/emodnet/eng/csw?request=GetRecordById&service=CSW&version=2.0.2&elementSetName=full&id=c5c97c694b6210454af2e3f92a8499fa411a0b46)

## Data visualisation services
### Web Map Service (WMS) 
The Web Map Service standard (**WMS**) provides a simple HTTP interface
for requesting geo-registered map images from one or more distributed
geospatial databases. A WMS request defines the geographic layer(s) and
area of interest to be processed. The response to the request is one or
more geo-registered map images (returned as JPEG, PNG, etc) that can be
displayed in a Geographic Information System (GIS) or in your own web
application (OpenLayers, Leaflet,\...).

The WMS supports the ***GetCapabilities***, ***GetMap*** and ***GetFeatureInfo*** operations as defined in the Open Geospatial Consortium (OGC) WMS standard.

The EMODnet WMS services are accessible from 7 thematics at the
Pan-European scale or global scale for some specific data products.
Enter one of the following WMS endpoint URLs into your WMS client (QGIS,
ArcMap, MapInfo etc.):

| Thematic         | Description                                                                   | WMS GetCapabilities                                                                                                           |
|------------------|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|
| Bathymetry       | Data Products                                                                 | https://ows.emodnet-bathymetry.eu/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0                                       |
| Bathymetry       | CDI data discovery and access service                                         | https://geo-service.maris.nl/emodnet_bathymetry/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0                         |
| Biology          | Data Products                                                                 | https://geo.vliz.be/geoserver/Emodnetbio/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0                                |
| Biology          | New Data Products                                                             | https://ows.emodnet.eu/geoserver/biology/ows?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0                                |
| Biology          | Occurrence data                                                               | https://geo.vliz.be/geoserver/Dataportal/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0                                |
| Chemistry        | Eutrophication                                                                | https://ec.oceanbrowser.net/emodnet/Python/web/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0                          |
| Chemistry        | Litter                                                                        | https://sextant.ifremer.fr/services/wms/emodnet_chemistry2?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0                  |
| Chemistry        | Contaminants                                                                  | https://geoserver.hcmr.gr/geoserver/EMODNET_SHARED/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0                              |
| Chemistry        | CDI data discovery and access service                                         | https://geo-service.maris.nl/emodnet_chemistry/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0                          |
| Chemistry        | Distribution of CDI observations per data category (P36) and MSFD sea regions | https://geo-service.maris.nl/emodnet_chemistry_p36/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0                      |
| Geology          | Sea-floor (bedrock)                                                           | https://drive.emodnet-geology.eu/geoserver/bgr/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0                          |
| Geology          | Marine Minerals                                                               | https://drive.emodnet-geology.eu/geoserver/gsi/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0                          |
| Geology          | Seabed substrate maps                                                         | https://drive.emodnet-geology.eu/geoserver/gtk/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0                          |
| Geology          | Events and Probabilities                                                      | https://drive.emodnet-geology.eu/geoserver/ispra/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0                        |
| Geology          | Coastal Behaviour                                                             | https://drive.emodnet-geology.eu/geoserver/tno/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0                          |
| Geology          | Submerged Landscapes                                                          | https://drive.emodnet-geology.eu/geoserver/bgs/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0                          |
| Geology          | Index of borehole and geophysics data                                         | https://drive.emodnet-geology.eu/geoserver/geus/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0                         |
| Human Activities | Data and Data Products                                                        | https://ows.emodnet-humanactivities.eu/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0                                  |
| Physics          | Data and Data Products                                                        | https://prod-geoserver.emodnet-physics.eu/geoserver/ows?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0                     |
| Physics          | Gridded Products                                                              | https://prod-erddap.emodnet-physics.eu/ncWMS/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0   
| Seabed Habitats  | General datasets and products                                                 | https://ows.emodnet-seabedhabitats.eu/geoserver/emodnet_view/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0            |
| Seabed Habitats  | Individual habitat map and model datasets                                     | https://ows.emodnet-seabedhabitats.eu/geoserver/emodnet_view_maplibrary/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0 |

#### WMS GetCapabilities

The ***GetCapabilities*** request allows WMS clients to retrieve service metadata from a server. The response to a GetCapabilities request shall be an XML document containing metadata of the service (available layers, associated projections, styles, author ...).  

> The standard to construct a WMS ***GetCapabilities*** request is as follows: <br>
>[https://ows.emodnet-bathymetry.eu/wms?<br>
            service=WMS&<br>
            version=1.3.0&<br>
            request=GetCapabilities](https://ows.emodnet-bathymetry.eu/wms?SERVICE=WMS&REQUEST=GetCapabilities&VERSION=1.3.0)

#### WMS GetMap

Using the information given in the ***GetCapabilities*** request, the ***GetMap*** request returns a raster map containing the requested data layer selected from all the available layers as defined in the XML document. The elements such as the data layer, region, projection, size of the returned image, image format, etc. are defined in the form of arguments.


>Example of a GetMap request that returns an image of the EMODnet Bathymetry Mean depth (DTM) based on source resolution of 1/8 arc minute (~250 meter) in multi colour style:<br>
[https://ows.emodnet-bathymetry.eu/wms?<br>
            service=WMS&<br>
            request=GetMap&<br>
            version=1.1.1&<br>
            layers=emodnet:mean_multicolour&<br>
            styles=&<br>
            format=image/png&<br>
            transparent=true&<br>
            info_format=text/html&<br>
            tiled=false&<br>
            width=400&<br>
            height=628&<br>
            srs=EPSG:3857&<br>
            bbox=-2669794,2250306,4800533,14538934](https://ows.emodnet-bathymetry.eu/wms?service=WMS&request=GetMap&version=1.1.1&layers=emodnet:mean_multicolour&styles=&format=image/png&transparent=true&info_format=text/html&tiled=false&width=400&height=628&srs=EPSG:3857&bbox=-2669794,2250306,4800533,14538934) <br>
            <br>
Which returns:<br>
<img src="https://ows.emodnet-bathymetry.eu/wms?service=WMS&service=WMS&request=GetMap&version=1.1.1&layers=emodnet:mean_multicolour&styles=&format=image/png&transparent=true&info_format=text/html&tiled=false&width=400&height=628&srs=EPSG:3857&bbox=-2669794,2250306,4800533,14538934" />

### Web Map Tile Service (WMTS)

In contrast to a WMS service, which offers real time rendered georeferenced images for a custom geographic extent, a Web Map Tile Service (**WMTS**) serves pre-rendered georeferenced map tiles with a fixed geographic extent for different zoom levels. As images are pre-rendered and can be cached (locally or remotely), WMTS offers a superior performance for web map viewer applications. 

The EMODnet WMTS service are accessible from following endpoints:

| Thematic         | Description                               | WMTS GetCapabilities                                                                                                                        |
|------------------|-------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| Bathymetry       | Data Products                             | https://tiles.emodnet-bathymetry.eu/wmts/1.0.0/WMTSCapabilities.xml                                                                         |
| Biology          | Data Products                             | https://geo.vliz.be/geoserver/Dataportal/gwc/service/wmts?REQUEST=GetCapabilities&SERVICE=WMTS&VERSION=1.0.0                                |
| Biology          | New Data Products                         | https://ows.emodnet.eu/geoserver/biology/gwc/service/wmts?REQUEST=GetCapabilities&SERVICE=WMTS&VERSION=1.0.0                                |
| Biology          | Occurrence data                           | https://geo.vliz.be/geoserver/Emodnetbio/gwc/service/wmts?REQUEST=GetCapabilities&SERVICE=WMTS&VERSION=1.0.0                                |
| Chemistry        | Contaminants                              | https://geoserver.hcmr.gr/geoserver/EMODNET_SHARED/gwc/service/wmts?REQUEST=GetCapabilities&SERVICE=WMTS&VERSION=1.0.0                      |
| Geology          | Sea-floor (bedrock)                       | https://drive.emodnet-geology.eu/geoserver/bgr/gwc/service/wmts?REQUEST=GetCapabilities&SERVICE=WMTS&VERSION=1.0.0                          |
| Geology          | Marine Minerals                           | https://drive.emodnet-geology.eu/geoserver/gsi/gwc/service/wmts?REQUEST=GetCapabilities&SERVICE=WMTS&VERSION=1.0.0                          |
| Geology          | Seabed substrate maps                     | https://drive.emodnet-geology.eu/geoserver/gtk/gwc/service/wmts?REQUEST=GetCapabilities&SERVICE=WMTS&VERSION=1.0.0                          |
| Geology          | Events and Probabilities                  | https://drive.emodnet-geology.eu/geoserver/ispra/gwc/service/wmts?REQUEST=GetCapabilities&SERVICE=WMTS&VERSION=1.0.0                        |
| Geology          | Coastal Behaviour                         | https://drive.emodnet-geology.eu/geoserver/tno/gwc/service/wmts?REQUEST=GetCapabilities&SERVICE=WMTS&VERSION=1.0.0                          |
| Geology          | Submerged Landscapes                      | https://drive.emodnet-geology.eu/geoserver/bgs/gwc/service/wmts?REQUEST=GetCapabilities&SERVICE=WMTS&VERSION=1.0.0                          |
| Geology          | Index of borehole and geophysics data     | https://drive.emodnet-geology.eu/geoserver/geus/gwc/service/wmts?REQUEST=GetCapabilities&SERVICE=WMTS&VERSION=1.0.0                         |
| Human Activities | Data and Data Products                    | https://ows.emodnet-humanactivities.eu/geoserver/gwc/service/wmts?REQUEST=GetCapabilities&SERVICE=WMTS&VERSION=1.0.0                         |
| Physics          | Data and Data Products                    | https://prod-geoserver.emodnet-physics.eu/geoserver/gwc/service/wmts?REQUEST=GetCapabilities&SERVICE=WMTS&VERSION=1.0.0                     |
| Seabed Habitats  | General datasets and products             | https://ows.emodnet-seabedhabitats.eu/geoserver/emodnet_view/gwc/service/wmts?REQUEST=GetCapabilities&SERVICE=WMTS&VERSION=1.0.0            |
| Seabed Habitats  | Individual habitat map and model datasets | https://ows.emodnet-seabedhabitats.eu/geoserver/emodnet_view_maplibrary/gwc/service/wmts?REQUEST=GetCapabilities&SERVICE=WMTS&VERSION=1.0.0 |

## Data download services

The EMODnet data layers are available as a Web Feature Service (**WFS**) or
Web Coverage Service (**WCS**) in accordance with the Open Geospatial
Consortium (OGC) specifications
([www.opengeospatial.org](http://www.opengeospatial.org)).

### Web Feature Service (WFS)
Web Feature Service (**WFS**) defines a standard for exchanging vector data by querying both the data structure and the source data. The basic operations are
***GetCapabilities***, ***DescribeFeatureType***, and ***GetFeature***.

The EMODnet WFS services are accessible from following endpoints:

| Thematic         | Description                                                                   | WFS GetCapabilities                                                                                                           |
|------------------|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|
| Bathymetry       | Data Products                                                                 | https://ows.emodnet-bathymetry.eu/wfs?SERVICE=WFS&REQUEST=GetCapabilities&VERSION=2.0.0                                       |
| Biology          | Data Products                                                                 | https://geo.vliz.be/geoserver/Emodnetbio/wfs?SERVICE=WFS&REQUEST=GetCapabilities&VERSION=2.0.0                                |
| Biology          | Occurrence data                                                               | https://geo.vliz.be/geoserver/Dataportal/wfs?SERVICE=WFS&REQUEST=GetCapabilities&VERSION=2.0.0                                |
| Chemistry        | Litter                                                                        | https://sextant.ifremer.fr/services/wfs/emodnet_chemistry2?SERVICE=WFS&REQUEST=GetCapabilities&VERSION=2.0.0                  |
| Chemistry        | Contaminants                                                                  | https://geoserver.hcmr.gr/geoserver/EMODNET_SHARED/wfs?SERVICE=WFS&REQUEST=GetCapabilities&VERSION=2.0.0                              |
| Chemistry        | CDI data discovery and access service                                         | https://geo-service.maris.nl/emodnet_chemistry/wfs?SERVICE=WFS&REQUEST=GetCapabilities&VERSION=2.0.0                          |
| Chemistry        | Distribution of CDI observations per data category (P36) and MSFD sea regions | https://geo-service.maris.nl/emodnet_chemistry_p36/wfs?SERVICE=WFS&REQUEST=GetCapabilities&VERSION=2.0.0                      |
| Geology          | Sea-floor (bedrock)                                                           | https://drive.emodnet-geology.eu/geoserver/bgr/wfs?SERVICE=WFS&REQUEST=GetCapabilities&VERSION=2.0.0                          |
| Geology          | Marine Minerals                                                               | https://drive.emodnet-geology.eu/geoserver/gsi/wfs?SERVICE=WFS&REQUEST=GetCapabilities&VERSION=2.0.0                          |
| Geology          | Seabed substrate maps                                                         | https://drive.emodnet-geology.eu/geoserver/gtk/wfs?SERVICE=WFS&REQUEST=GetCapabilities&VERSION=2.0.0                          |
| Geology          | Events and Probabilities                                                      | https://drive.emodnet-geology.eu/geoserver/ispra/wfs?SERVICE=WFS&REQUEST=GetCapabilities&VERSION=2.0.0                        |
| Geology          | Coastal Behaviour                                                             | https://drive.emodnet-geology.eu/geoserver/tno/wfs?SERVICE=WFS&REQUEST=GetCapabilities&VERSION=2.0.0                          |
| Geology          | Submerged Landscapes                                                          | https://drive.emodnet-geology.eu/geoserver/bgs/wfs?SERVICE=WFS&REQUEST=GetCapabilities&VERSION=2.0.0                          |
| Geology          | Index of borehole and geophysics data                                         | https://drive.emodnet-geology.eu/geoserver/geus/wfs?SERVICE=WFS&REQUEST=GetCapabilities&VERSION=2.0.0                         |
| Human Activities | Data and Data Products                                                        | https://ows.emodnet-humanactivities.eu/wfs?SERVICE=WFS&REQUEST=GetCapabilities&VERSION=2.0.0                                  |
| Physics          | Data and Data Products                                                        | https://prod-geoserver.emodnet-physics.eu/geoserver/ows?SERVICE=WFS&REQUEST=GetCapabilities&VERSION=2.0.0                     |
| Seabed Habitats  | General datasets and products                                                 | https://ows.emodnet-seabedhabitats.eu/geoserver/emodnet_open/wfs?SERVICE=WFS&REQUEST=GetCapabilities&VERSION=2.0.0            |
| Seabed Habitats  | Individual habitat map and model datasets                                     | https://ows.emodnet-seabedhabitats.eu/geoserver/emodnet_open_maplibrary/wfs?SERVICE=WFS&REQUEST=GetCapabilities&VERSION=2.0.0 |

#### WFS GetCapabilities

The ***GetCapabilities*** request generates a metadata document (xml) describing a WFS service provided by server as well as valid WFS operations and parameters (available features, supported file formats, etc.).

>The standard to construct a WFS ***GetCapabilities*** request is as follows: <br>
 [ https://ows.emodnet-bathymetry.eu/wfs?<br>
SERVICE=WFS&<br>
REQUEST=GetCapabilities&<br>
VERSION=2.0](https://ows.emodnet-bathymetry.eu/wfs?SERVICE=WFS&REQUEST=GetCapabilities&VERSION=2.0.)

#### WFS DescribeFeature

A ***DescribeFeature*** request returns a description of a feature type (including available attribute fields).

> Example of a EMODnet Biology ***DescribeFeature*** request:<br>
[https://geo.vliz.be/geoserver/Dataportal/wfs?<br>
            service=wfs&<br>
            version=2.0.0&<br>
            request=DescribeFeatureType&<br>
            typeName=Dataportal:eurobis&<br>
            outputFormat=application/json](https://geo.vliz.be/geoserver/Dataportal/wfs?service=wfs&version=2.0.0&request=DescribeFeatureType&typeName=Dataportal:eurobis&outputFormat=application/json)

>Example of a EMODnet Human Activities ***DescribeFeature*** request:<br>
[https://ows.emodnet-humanactivities.eu/wfs?<br>
            service=WFS&<br>
            version=1.1.0&<br>
            request=describeFeatureType&<br>
            typeName=shellfish&<br>
            bbox=-1.3,0.3,49.2,49.9](https://ows.emodnet-humanactivities.eu/wfs?SERVICE=WFS&VERSION=1.1.0&request=describeFeatureType&typeName=shellfish&bbox=-1.3,0.3,49.2,49.9)

#### WFS GetFeature

The ***GetFeature*** request returns a selection of features from a data source including geometry and attribute values.

>Example of a EMODnet Human Activities ***GetFeature*** request:<br>
[https://ows.emodnet-humanactivities.eu/wfs?<br>
            service=WFS&<br>
            version=1.1.0&<br>
            request=getFeature&<br>
            typeName=shellfish&<br>
            bbox=-1.3,0.3,49.2,49.9&<br>
            outputFormat=application/json](https://ows.emodnet-humanactivities.eu/wfs?SERVICE=WFS&VERSION=1.1.0&request=getFeature&typeName=shellfish&bbox=-1.3,0.3,49.2,49.9&outputFormat=application/json)

#### EMODnetWFS: An R Client of EMODnet Web Feature Service data

[EMODnetWFS](https://emodnet.github.io/EMODnetWFS/) is an R package developed to access WFS data from EMODnet. You can install with:

```r
remotes::install_github("EMODnet/EMODnetWFS")
```

### Web Coverage Service (WCS)
Web Coverage Service (**WCS**) is a data-access protocol that defines and enables the web-based retrieval of multi-dimensional raster type geospatial datasets.  The basic operations (HTTP requests) are
***GetCapabilities***, ***DescribeCoverage***, and ***GetCoverage***.

The EMODnet thematics provide Web Coverage Services (WCS) to support
requests for coverage data (rasters) or gridded data products. Enter one
of the following addresses into your WCS client:

| Thematic         | Description                               | WCS GetCapabilities                                                                                                           |
|------------------|-------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|
| Bathymetry       | Data Products                             | https://ows.emodnet-bathymetry.eu/wcs?SERVICE=WCS&REQUEST=GetCapabilities&VERSION=2.0.1                                       |
| Biology          | Data Products                             | https://geo.vliz.be/geoserver/Emodnetbio/wcs?SERVICE=WCS&REQUEST=GetCapabilities&VERSION=2.0.1                                |
| Biology          | New Data Products                         | https://ows.emodnet.eu/geoserver/biology/ows?SERVICE=WCS&REQUEST=GetCapabilities&VERSION=2.0.1                                |
| Human Activities | Data and Data Products                    | https://ows.emodnet-humanactivities.eu/wcs?SERVICE=WCS&REQUEST=GetCapabilities&VERSION=2.0.1                                  |
| Seabed Habitats  | Individual habitat map and model datasets | https://ows.emodnet-seabedhabitats.eu/geoserver/emodnet_open_maplibrary/wcs?SERVICE=WCS&REQUEST=GetCapabilities&VERSION=2.0.1 |

#### WCS GetCapabilities

A WCS ***GetCapabilities*** request returns an XML document with information to the service and data provider and an overview of all the coverages (raster dataset) available on the web serveras well as valid WCS operations and parameters.

> The standard to construct a WFS ***GetCapabilities*** request is as follows: <br>[https://ows.emodnet-bathymetry.eu/wcs?<br>
service=WCS&<br>
request=GetCapabilities&<br>
version=2.0.1](https://ows.emodnet-bathymetry.eu/wcs?SERVICE=WCS&REQUEST=GetCapabilities&VERSION=2.0.1)

#### WCS DescribeCoverage

A WCS ***DescribeCoverage*** request returns an XML document with metadata information fully describing one specific coverage
>Example of an EMODnet Bathymetry ***DescribeCoverage*** request:<br>
[https://ows.emodnet-bathymetry.eu/wcs?<br>
            service=wcs&<br>
            version=1.0.0&<br>
            request=DescribeCoverage&<br>
            coverage=emodnet:mean](https://ows.emodnet-bathymetry.eu/wcs?service=wcs&version=1.0.0&request=DescribeCoverage&coverage=emodnet:mean)

#### WCS GetCoverage

A WCS GetCoverage request returns a coverage encoded in a specified format (e.g GeoTiff, ESRI ASCII or netCDF), resampling algorithm, projection, etc.


>Example of an EMODnet Bathymetry ***GetCoverage*** request:<br>
[https://ows.emodnet-bathymetry.eu/wcs?<br>
            service=wcs&version=1.0.0&<br>
            request=getcoverage&<br>
            coverage=emodnet:mean&<br>
            crs=EPSG:4326&<br>
            BBOX=-2.52,45.6,-1.08,46.40&<br>
            format=image/tiff&<br>
            interpolation=nearest&<br>
            resx=0.00208333&<br>
            resy=0.00208333](https://ows.emodnet-bathymetry.eu/wcs?service=wcs&version=1.0.0&request=getcoverage&coverage=emodnet:mean&crs=EPSG:4326&BBOX=-2.52,45.6,-1.08,46.40&format=image/tiff&interpolation=nearest&resx=0.00208333&resy=0.00208333)

# Non-OGC web services

Some thematics provide other, non-OGC, download services that are more suited for the types of data they offer. This includes ERDDAP & THREDDS services for the retrieval of multidimensional raster data using the OPeNDAP standard and a custom REST API service to extract retrieve water depth at locations and along profiles from the EMODnet Bathymetry DTM .

| Thematic   | web service | URL                                                                                                                                                                                    |
| ---------- | ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| EMDOnet    | ERDDAP      | https://erddap.emodnet.eu/erddap/index.html                                                                                                                                            |
| Bathymetry | REST API    | https://rest.emodnet-bathymetry.eu/                                                                                                                                                    |
| Chemistry  | THREDDS     | http://opendap.oceanbrowser.net/thredds/catalog/data/emodnet-domains/catalog.html <br /> XML version: http://opendap.oceanbrowser.net/thredds/catalog/data/emodnet-domains/catalog.xml |
| Chemistry  | ERDDAP     |  https://erddap.emodnet-chemistry.eu/erddap/index.html |
| Physics    | ERDDAP      | https://prod-erddap.emodnet-physics.eu/erddap/index.html                                                                                                                        |
# Other useful links with documentation on EMODnet web services

* Biology Github: https://github.com/EMODnet/EMODnet-Biology-Guidance
* Chemistry GitHub: https://github.com/gher-ulg/EMODnet-Chemistry
* Physics GitHub: https://github.com/EMODnet-Physics
* Seabed habitats GitHub: https://github.com/emodnetseabedhabitats
* Other repos in the main EMODnet GitHub: https://github.com/EMODnet

# Web service status

Having trouble? Verify the status of the EMODnet web services at https://monitor.emodnet.eu.

-----------------------------------------------------------------------------------------------------------
<center> Provided by EMODnet. See our <a href=https://emodnet.ec.europa.eu/en/terms-use-emodnet-online-services-data-and-data-products> terms of use </a></center>
<center><a href="https://emodnet.ec.europa.eu/"><img style="float: None" style="border-width:0" src="https://emodnet.ec.europa.eu/sites/emodnet.ec.europa.eu/files/public/emodnet_logos/web/EMODnet_standard_colour.png" /></a>
</center>
