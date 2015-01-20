How To Use AGRC Base Maps in QGIS
=================================

Most people know about AGRC's awesome [base maps](http://gis.utah.gov/data/sgid-base-map-services-arcmap/). They are [very popular](http://gis.utah.gov/basemaps-a-2014-day-in-the-life/) and provide high quality cartography using the latest and greatest data from the [Utah SGID](http://gis.utah.gov/data/). But did you know that they provide a [WMTS](http://en.wikipedia.org/wiki/Web_Map_Tile_Service) service that can be consumed in non-ESRI products?

Here's how to load our base maps in [QGIS 2.6.1](http://www.qgis.org/en/site/):

1. The first step is to find the URL to the service that you are interested in. Most of AGRC's base maps are within a folder called "[BaseMaps](http://mapserv.utah.gov/arcgis/rest/services/BaseMaps)" on our main ArcGIS Server instance. Once you find the specific layer that you are interested in, copy the URL for the WMTS link at the top of the services directory page:  
![link](http://i.imgur.com/4lXjFFl.jpg)
2. Open QGIS and click on the "Add WMS/WMST Layer" button to open the "Add Layer(s) from a WM(T)S Server".
3. Click on the "New" button to open the "Create a new WCS connection" dialog and add a name for the layer and the URL to the WMTS service and click "OK" to close the dialog.  
![dialog](http://i.imgur.com/zwN1Uag.jpg)
4. You should now see a new layer in the add layer dialog. Select the new layer and click on the "Add" button to add it to the map.  
![dialog](http://i.imgur.com/ZHvujIc.jpg)
5. You should now be able to view the base map as a layer in QGIS!  
![map](http://i.imgur.com/di10u7z.jpg)

## Bonus Tip
If you are having performance issues using our cached services through ArcMap, try loading them via these WMTS services. You can do this by double-clicking on the "Add WMTS Server" node in the ArcCatalog tree under "GIS Servers" and then pasting the same URL as above.
![arcmap](http://i.imgur.com/ydArdcM.jpg)
