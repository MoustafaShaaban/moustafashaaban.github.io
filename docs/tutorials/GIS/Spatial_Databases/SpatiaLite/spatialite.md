# Create a Spatialite Database and Insert Data to it

* In this tutorial we will learn how to create a spatialite database and how to insert data to it.


## Steps

* Download the required data
* Load the data to QGIS
* Create a table join between using (Join Attributes by Field Values) algorithm
* Create a Spatialite database and connect to it using QGIS DB Manager
* Insert data into the database
* Run basic SQL queries on the database


## Download the required data:

Data Sources:

  [GADM](https://gadm.org/download_country.html)

  [World Population Review](https://worldpopulationreview.com/states)

* First go to GADM website by clicking on the following link [GADM](https://gadm.org/download_country.html)
and from the Country drop down menu choose United States.
Then click on Shapefile to download it:

![GADM](./images/image1.jpg)

![GADM](./images/image2.jpg)

![GADM](./images/image3.jpg)

* Go to [World Population Review](https://worldpopulationreview.com/states) website and download the csv files containing the population data of us states.

![GADM](./images/worldpop2.PNG)

![GADM](./images/worldpop.PNG)

* We will need to download two files the 'US states - Ranked by Population 2022.csv' and the 'District of Columbia and Puerto Rico.csv'.

* After that we can open both files in microsoft excel or we can use a free software called [Only Office](https://www.onlyoffice.com/download-desktop.aspx) to copy the data of District of Columbia to the 'US states - Ranked by Population 2022.csv'.


## Load the data to QGIS

* Open a new project in QGIS software and add the 'gadm41_USA_1.shp' data file.

![GADM](./images/image4.jpg)

![GADM](./images/image5.jpg)

![GADM](./images/image6.jpg)

![GADM](./images/image7.jpg)

![GADM](./images/image8.jpg)

![GADM](./images/image9.jpg)

* Now, let's explore the attribute table of the new layer to see its content.

![GADM](./images/image10.jpg)

![GADM](./images/image11.jpg)

* As we can see from the picture above the us states are inside a field called 'Name_1'. We will use this name later in the tutorial.

* Now, let's add the second data file. Click on the Layer menu and choose 'Add Delimited Text Layer' option. A new window will appear, click on the icon nexxt to the File name to choose the 'US states - Ranked by Population 2022.csv' file:

![GADM](./images/image12.jpg)

![GADM](./images/image13.jpg)

![GADM](./images/image14.jpg)

![GADM](./images/image15.jpg)

![GADM](./images/image16.jpg)

* Also, In the Geometry Definition make sure to choose the 'No geometry (attribute only table)' option. Then click Add.

![GADM](./images/image17.jpg)

![GADM](./images/image18.jpg)

![GADM](./images/image19.jpg)

* A new layer is added to the Layers panel.


## Create a table join between using (Join Attributes by Field Values) algorithm

* From the QGIS toolbar click on Processing menu and choose Toolbox.

* In the Processing Toolbox search bar type 'table join' and double click on 'Join attributes by field value' under the Vector general tools to open it.

![GADM](./images/image20.jpg)

![GADM](./images/image21.jpg)

![GADM](./images/image22.jpg)

* The Join Attributes by Field Value window will appear. In the Input layer option choose the 'gadm41_USA_1' layer. And in the Table field option choose 'Name_1':

![GADM](./images/image23.jpg)

![GADM](./images/image24.jpg)

![GADM](./images/image25.jpg)

![GADM](./images/image26.jpg)

* In the Input layer 2 option make sure it has our second layer 'US states - Ranked by Population 2022' and then, click on the Table field 2 to choose the field that contains the US States 'State'

![GADM](./images/image27.jpg)

![GADM](./images/image28.jpg)

* Click on the button next to the 'Layer 2 fields to copy (leave empty to copy all fields) optional' to choose the fields we want to join in our case we need 3 fields (Pop, Pop2021, Pop2010) click on the checkboxes next to those fields. Then click on the blue back arrow to go back to the Join Attributes by Field Value window

![GADM](./images/image29.jpg)

![GADM](./images/image30.jpg)

* Scroll down to the Joined layer option and click on the button next to it and choose Save to File to save the new joined layer to a shape file. Choose a name to the new layer (like us_state_pop.shp) abd a location of the new file (like on the Desktop).

![GADM](./images/image31.jpg)

![GADM](./images/image32.jpg)

![GADM](./images/image33.jpg)

![GADM](./images/image34.jpg)

![GADM](./images/image35.jpg)

* Now, click on Run to run the algorithm.

![GADM](./images/image36.jpg)

![GADM](./images/image37.jpg)

![GADM](./images/image38.jpg)

* The new layer is added, let's see its attribute table to see the new fields

![GADM](./images/image39.jpg)

![GADM](./images/image40.jpg)

![GADM](./images/image41.jpg)

* As we can see in the screen above, there are 3 new fields (Pop, Pop2021m Pop2010) added to the main layer.


## Create a Spatialite database and connect to it using QGIS DB Manager

* In the QGIS Browser panel rigth click on SpatiaLite and choose Create Database, a new window will appear. Choose a location to save the database and database name (like us_states_pop) then click on save.

![GADM](./images/image42.jpg)

![GADM](./images/image43.jpg)

![GADM](./images/image44.jpg)

![GADM](./images/image45.jpg)

* Now, let's connect to our newly created database. In the QGIS toolbar open Database > DB Manager

![GADM](./images/image46.jpg)

![GADM](./images/image47.jpg)

* The Database Manager window will open. From the Providers panel expand SpatiaLite > us_states_pop to connect to the database.

![GADM](./images/image48.jpg)

![GADM](./images/image49.jpg)


## Insert data into the database

* From the Datebase Manager window click on the 'Import Layer File' button to insert a layer file to the database.

![GADM](./images/image50.jpg)

* A new window will appear, Make sure that 'us_state_pop' layer is selected in the Input option, and click on the checkboxes next to Primary Key and Create spatial index options to activate them. 

* The Primary Key option creates a new unique key to each record of the database, we can call the field whatever we like, but in this tutorial I will choose the default value 'id'.

* The Create spatial index option, is used with spatial data to imorive the queries time.

* Finally click Ok to load the data.

![GADM](./images/image51.jpg)

![GADM](./images/image52.jpg)

![GADM](./images/image53.jpg)

* A new table called us_state_pop is added to our database. Click on the Table tab to see its data.

![GADM](./images/image54.jpg)

![GADM](./images/image55.jpg)


## Run basic SQL queries on the database

* In the DB Manager window, click on the SQL Window, to open the SQL Query window

![GADM](./images/image56.jpg)

![GADM](./images/image57.jpg)

* Let's write a SQL query to retrive a record about New York city

  select * from us_state_pop where Name_1 = "New York";

* Next, click on Execute to run the query

![GADM](./images/image58.jpg)

* Here is the result:

![GADM](./images/image59.jpg)

* Another example, let's say we want to retrieve the name and population of all the states that have more than 10 million population.
  select Name_1, Pop from us_state_pop where Pop > 10000000;

![GADM](./images/image60.jpg)

* And that's it for today's tutorial. We can see how easy it is to create, manage and query spatial databases using QGIS.

* In a later tutorial, we will learn how to create a PostGIS database and query it's content.
