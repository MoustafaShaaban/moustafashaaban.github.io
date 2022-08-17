# Service Area Analysis (From layer):

* In this tutorial we will learn how to use the Service Area Network Analysis () in Dijon city.

* We will continue from where we left of in the second tutorial you can find it [point-to-point-fastest-path](../2-point-to-point-fastest-path/steps.md)


#### Goal:

* Download free OSM data using the QuickOSM Plugin for QGIS

* Show all the roads that the hospitals in Dijon can cover in 10 minutes.


#### Required data:

Data Sources:

  * [GADM](https://gadm.org/download_country36.html)

  * [Geofabrik](https://download.geofabrik.de/europe/france/bourgogne.html)

We will use the same data we extracted on the last tutorial:

  * Matching features layer which is extracted from a shapefile containing the cantons of France which is the boundaries of Dijon canton.
  * Extracted (location) layer which contains the roads inside Dijon canton.


#### Step by Step Tutorial:

#### Step 1 Download and style the data: 

* Click on the Plugins menu from QGIS toolbar and then click on Manage and Install Plugins:

![Plugins](./images/image1.jpg)

![Plugins](./images/image2.jpg)


* In the search bar type QuickOSM and then click on Install Plugin:

![QuickOSM](./images/image3.jpg)

![QuickOSM](./images/image4.jpg)

* Open the QuickOSM plugin by clicking on its icon:

![QuickOSM](./images/image5.jpg)

* The plugin menu will appear, In the Preset search bar type hospital and click on Facilities/Health/Hospital, A new Query will appear which for all the hospitals. Then in the location type Dijon, To search for Hospitals that are located in Dijon only. Finally click on Run query:

![QuickOSM](./images/image6.jpg)

![QuickOSM](./images/image7.jpg)

![QuickOSM](./images/image8.jpg)

![QuickOSM](./images/image9.jpg)

![QuickOSM](./images/image10.jpg)

![QuickOSM](./images/image11.jpg)


* Two new layers are added by the query, a point and a polygon layer, let's turn off the polygon layer as we will not use it.

![QuickOSM](./images/image12.jpg)

* Let's choose a new style for the "amenity hospital healthcare hospital Dijon" layer:

![QuickOSM](./images/image13.jpg)

![QuickOSM](./images/image14.jpg)

![QuickOSM](./images/image15.jpg)

![QuickOSM](./images/image16.jpg)

![QuickOSM](./images/image17.jpg)

![QuickOSM](./images/image18.jpg)

* We can have a look at the Attribute table to see its content:

![QuickOSM](./images/image19.jpg)

![QuickOSM](./images/image20.jpg)

![QuickOSM](./images/image21.jpg)

![QuickOSM](./images/image22.jpg)



#### Step 2 Network Analysis Service Area: 

* Click on the Processing menu from QGIS toolbar then open the Toolbox.

![QuickOSM](./images/image23.jpg)

![QuickOSM](./images/image24.jpg)

![QuickOSM](./images/image25.jpg)

* From the Processing Toolbox go to Network analysis > Service area (from layer).

![QuickOSM](./images/image26.jpg)

* The Service Area (from layer) algorithm window will open, Choose the "Extracted (location)" layer as the Vector layer representing network. Then, choose "Fastest" as the Path type to calculate, this type takes the Travel cost as time, In our case we will make it as 10 minutes:

![QuickOSM](./images/image27.jpg)

![QuickOSM](./images/image28.jpg)

![QuickOSM](./images/image29.jpg)

![QuickOSM](./images/image30.jpg)

![QuickOSM](./images/image31.jpg)

* In the Advanced parameter, choose the oneway field as the Direction field, and F for the Value for forward direction, T for Value for backward direction, B for Value for both directions, and maxspeed as the Speed field,  Finally click Run to run the algorithm:

![QuickOSM](./images/image32.jpg)

![QuickOSM](./images/image33.jpg)

![QuickOSM](./images/image34.jpg)

![QuickOSM](./images/image35.jpg)

![QuickOSM](./images/image36.jpg)





























## Further articles and blog posts to learn more:

[GIS Geography](https://gisgeography.com/network-analysis/)
