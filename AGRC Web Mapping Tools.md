AGRC Web Mapping Services
=========================

AGRC offers a variety of web mapping services that make it easy to add authoritative web maps to your web applications. The two most popular are our [base maps](http://gis.utah.gov/developer/base-maps/) and [geocoding service](http://api.mapserv.utah.gov/#geocoding). These services together with a custom service that shows your application-specific data can add geographic context to your web applications.

This post will show you how simple it is to leverage AGRC's services with JavaScript. We will develop a simple web app contains a dynamic map and simple address finding controls.

## ESRI JavaScript API
The first thing to do is create a simple `.html` page and import [ESRI's ArcGIS API for JavaScript](https://developers.arcgis.com/en/javascript/). You can load their API by a CSS file:

    <link rel="stylesheet" href="http://serverapi.arcgisonline.com/jsapi/arcgis/3.5/js/esri/css/esri.css">

and a script file: 

    <script src="http://serverapi.arcgisonline.com/jsapi/arcgis/3.5/"></script>

This will load all necessary dependencies including [Dojo](https://developers.arcgis.com/en/javascript/jshelp/inside_dojo.html) into your application. Because ESRI's API is built on top of Dojo, it is following their convention and switching to [AMD](http://en.wikipedia.org/wiki/Asynchronous_module_definition) for their module loading. Therefore, it is highly recommended that any new development use the AMD syntax for importing modules to ensure that the code will work in the future. All code examples in this post will be using the new syntax. If you are unfamiliar with AMD you may want to check out [Dojo's excellent tutorial](http://dojotoolkit.org/documentation/tutorials/1.9/modules/) on the subject.

## Base Maps
AGRC provides [seven high-quality, pre-rendered base map services](http://gis.utah.gov/developer/base-maps/). These services are published through ESRI's [ArcGIS Server software](http://www.esri.com/software/arcgis/arcgisserver). The service directory end points can be found here: 

[http://mapserv.utah.gov/arcgis/rest/services/BaseMaps](http://mapserv.utah.gov/arcgis/rest/services/BaseMaps)

Adding one of these services to a map is relatively easy. First, we need to import a few ESRI modules. Then create a new map and tiled layer. Finally, we add the newly created layer to the map. Here's what the code looks like:

<script src="https://gist.github.com/stdavis/5979421.js"></script>

And here's the result; a fully interactive base map that shows off a lot of the great GIS data that is housed in the [State Geographic Information Database (SGID)](http://gis.utah.gov/data/) that AGRC maintains.

<a class="jsbin-embed" href="http://jsbin.com/elenab/8/embed?live">JS Bin</a><script src="http://static.jsbin.com/js/embed.js"></script>

## Geocoding (Address Matching)
To [geocode](http://en.wikipedia.org/wiki/Geocoding) an address means to find it's corresponding geographic coordinates (think latitude and longitude). AGRC provides a highly authoritative service for geocoding addresses which is built off of the best [transportation](http://gis.utah.gov/data/sgid-transportation/) and [address data](http://gis.utah.gov/data/address-overview/) available. It's also optimized for the State of Utah's unique addressing systems.

Before you can use any of AGRC's web API services you will need to create an account and an API key for your domain. Check out the [Getting Started Guide](http://developer.mapserv.utah.gov/StartupGuide) for more information. Once you have a key you can start using services such as [Geocoding](http://api.mapserv.utah.gov/#geocoding). Here's an example of a typical geocoding request that finds coordinates for 123 S Main St, SLC:

[http://api.mapserv.utah.gov/api/v1/geocode/123%20S%20Main%20St/Salt%20Lake%20City?spatialReference=4326&apiKey=AGRC-151FF757622085](http://api.mapserv.utah.gov/api/v1/geocode/123%20S%20Main%20St/Salt%20Lake%20City?spatialReference=4326&apiKey=AGRC-151FF757622085)

There are samples of how to use this service in several popular languages in our [GeocodingSample GitHub repository](https://github.com/agrc/GeocodingSample).

Perhaps the easiest way for you to use this service is to use the `FindAddress` widget in our [AGRC Dojo Widget Library](https://github.com/agrc/agrc.widgets). You can do this by adding a config object to your `require` call that defines an `agrc` package and it's location. Here I have it pointing at the 'agrc' package on our cdn:

<script src="https://gist.github.com/stdavis/5985759.js"></script>

Once we have defined our `agrc` package, we can import modules just like any other package. This example shows how to import the `FindAddress` widget and initializing it with our `map` object and our [AGRC Web API](http://api.mapserv.utah.gov/) key:

<a class="jsbin-embed" href="http://jsbin.com/elenab/11/embed?live,javascript">JS Bin</a><script src="http://static.jsbin.com/js/embed.js"></script>

## Custom Data Overlays
The last step in our demo will be to add a data overlay on top of the base map. To do this you need to have access to a map service that is pointed at your data. This is usually done using ESRI's [ArcGIS Server software](http://www.esri.com/software/arcgis/arcgisserver). If you do not have access to this software, you may want to [contact](http://gis.utah.gov/about/contact/) us about getting a service set up on our servers for you. For this demo we will use a service that we host that shows the Utah DFO fuel sites within the state. The endpoint for this service is here: [http://mapserv.utah.gov/arcgis/rest/services/UtahDFOFuelSites/MapServer](http://mapserv.utah.gov/arcgis/rest/services/UtahDFOFuelSites/MapServer).

To add this service to our map we need to import the `esri/layers/ArcGISDynamicMapServiceLayer` module and create a new layer using the url to our service. Then we can add it to the map. Here's what it looks like:

<a class="jsbin-embed" href="http://jsbin.com/elenab/12/embed?live,javascript">JS Bin</a><script src="http://static.jsbin.com/js/embed.js"></script>

## Wrap-up
This is just a small sampling of what AGRC has to offer in terms of web mapping services. If you are interested in an advanced example of one of our web applications you can check out our [AGRCJavaScriptBoilerPlate](https://github.com/agrc/AGRCJavaScriptProjectBoilerPlate). I did a [presentation](http://video.esri.com/watch/2326/how-i-work-utah-agrc-javascript-boilerplate-project-tour) on it at the ESRI Dev Summit in March 2013.

## Glossary
**Dojo**: This is a bunch of JavaScript code written by really smart people that ESRI used to build their API.  
**AMD**: The new standard for loading JavaScript which is organized into separate files. Dojo and ESRI have adopted it as their new standard.  
**Map Service**: A map that is drawn on a server and then sent to a web browser.
**ArcGIS Server**: Software that allows GIS data to be served up over the web via web services such as map services.  



<style>
/* override wordpress yellow background */
.highlight {
   background-color: transparent !important;
}
code {
    display: inline-block;
    margin-bottom: 0;
}
iframe.jsbin-embed {
    height: 378px !important;
    border: none !important;
}
</style>