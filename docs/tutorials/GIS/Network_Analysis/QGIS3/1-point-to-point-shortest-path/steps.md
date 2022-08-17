# Point to Point Analysis (Shortest path):

* Point-to-point network analysis is one of the most used network analysis, 
we use it to calculate the shortest or fastest route between two points (Starting and Ending points).


#### Goal:

* Calculate the closest route between two points in the city of Dijon using OSM (Open Street Map) free data.


#### Download the required data:

Data Sources:

  [GADM](https://gadm.org/download_country36.html)

  [Geofabrik](https://download.geofabrik.de/europe/france/bourgogne.html)

* First go to GADM website by clicking on the following link [GADM](https://gadm.org/download_country36.html)
and from the Country drop down menu choose France.
Then click on Shapefile to download it:

![GADM](images/network_analysis_point-to-point/1-gadm_shapefile.png "GADM Website")

* Now go to Geofabrik website to download free OSM data exactly the Bourgogne region of France where Dijon city is located
by clicking on this link [Geofabrik](https://download.geofabrik.de/europe/france/bourgogne.html)

![Geofabrik](images/network_analysis_point-to-point/2-geofabrik_data.png "Geofabrik Website")

* Save the data files and extract the zip files in any location you want (you can leave it in the downloads folder for easy access to it).



### Step 1: Add the gadm36_FRA_4.shp layer:

![gadm36_FRA_4.shp](images/network_analysis_point-to-point/image1.jpeg)


### Step 2: In QGIS window open the Processing menu and click on Toolbox:

![Processing menu](images/network_analysis_point-to-point/image2.jpeg)


### Step 3: From the Processing Toolbox select Vector selection then Extract by expression option which allows us to extract data to a new layer by using an expression:

![Processing Toolbox](images/network_analysis_point-to-point/image3.jpeg)


### Step 4: The Extract by expression window will open, now click on the Expression icon:

![Extract by expression](images/network_analysis_point-to-point/image4.jpeg)


### Step 5: In the search box type name, then, double click on the NAME_4 from Fields and Values:

![Extract by expression](images/network_analysis_point-to-point/image5.jpeg)


### Step 6:  Now complete the expression as follow (“NAME_4” = ‘Dijon’) to extract the Dijon city boundaries and then click Ok:

![expression](images/network_analysis_point-to-point/image6.jpeg)

![expression](images/network_analysis_point-to-point/image7.jpeg)

![expression](images/network_analysis_point-to-point/image8.jpeg)


### Step 7: Click Run to run the algorithm, A new layer called Matching features will be created:

![Matching features](images/network_analysis_point-to-point/image9.jpeg)

![Matching features](images/network_analysis_point-to-point/image10.jpeg)


### Step 8: Turn off the gadm36_FRA_4.shp layer and right click on the Matching features layer then select Zoom to layers to see the result:

![Matching features](images/network_analysis_point-to-point/image11.jpeg)

![Matching features](images/network_analysis_point-to-point/image12.jpeg)

![Matching features](images/network_analysis_point-to-point/image13.jpeg)

![Matching features](images/network_analysis_point-to-point/image14.jpeg)


### Step 9: Open the Styling panel to style the newly created layer, then choose the outline blue style:

![Styling panel](images/network_analysis_point-to-point/image15.jpeg)

![Styling panel](images/network_analysis_point-to-point/image16.jpeg)

![Styling panel](images/network_analysis_point-to-point/image17.jpeg)


### Step 10: Now we can add the second data layer: gis_osm_roads_free_1.shp:

![gis_osm_roads_free_1.shp](images/network_analysis_point-to-point/image18.jpeg)


### Step 11: From the Processing Toolbox > Vector selection choose Extract by location tool:

![gis_osm_roads_free_1.shp](images/network_analysis_point-to-point/image19.jpeg)


### Step 12: The Extract by location window will appear. In the Extract features from choose the gis_osm_roads_free_1.shp layer. And in the Where the features (geometric predicate) check only (are within) option, and in By comparing to the features from choose the Matching features layer, then click Run:

![Extract by location window](images/network_analysis_point-to-point/image20.jpeg)

![Extract by location window](images/network_analysis_point-to-point/image21.jpeg)

![Extract by location window](images/network_analysis_point-to-point/image22.jpeg)


### Step 13: Turn off the gis_osm_roads_free_1.shp layer to see the results well:

![Extract by location](images/network_analysis_point-to-point/image23.jpeg)

![Extract by location](images/network_analysis_point-to-point/image24.jpeg)


### Step 14: Now we can choose a good style for our new layer, back to the styling panel choose the Topo road style for the Extracted (location layer) :

![Topo road style](images/network_analysis_point-to-point/image25.jpeg)

![Topo road style](images/network_analysis_point-to-point/image26.jpeg)


### Step 15: Now, It’s time for the Network analysis (Shortest path point to point), Back the Processing Toolbox > Network Analysis > Shortest path (point to point):

![Network analysis](images/network_analysis_point-to-point/image27.jpeg)


### Step 16: Make sure that the Extracted (location) layer is selected as the Vector layer representing network, and then click on the icon next to the Start point to pick a start point from the layer, then do the same for the End point:

![Network analysis](images/network_analysis_point-to-point/image28.jpeg)

![Network analysis](images/network_analysis_point-to-point/image29.jpeg)

![Network analysis](images/network_analysis_point-to-point/image30.jpeg)

![Network analysis](images/network_analysis_point-to-point/image31.jpeg)


### Step 17: In the Advanced parameter, choose the oneway field as the Direction field, and F for the Value for forward direction, T for Value for backward direction, and B for Value for both directions, Finally click Run to run the algorithm :

![Network analysis](images/network_analysis_point-to-point/image32.jpeg)


### Step 18: A new layer called Shortest path will be created, let’s choose a different style like (Topo main road) so we can see it:

![Network analysis](images/network_analysis_point-to-point/image33.jpeg)

![Network analysis](images/network_analysis_point-to-point/image34.jpeg)

![Network analysis](images/network_analysis_point-to-point/image35.jpeg)


### Step 19: That’s it, Here is the Shortest path between the start and end point that we picked!

![Network analysis](images/network_analysis_point-to-point/image36.jpeg)



## Further articles and blog posts to learn more:

[GIS Geography](https://gisgeography.com/network-analysis/)

[QGIS Tutorials](https://www.qgistutorials.com/en/docs/3/basic_network_analysis.html)