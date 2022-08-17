# Install PostgreSQL and PostGIS Databases:

* In this tutorial we will learn how to install PostgreSQL and PostGIS databases.


## Steps

* Download postgresql 14 windows x64 execution file
* Install PostgreSQL
* Install PostGIS


## Download postgresql 14 windows x64:

Official Website:

  [PostgreSQL](https://www.postgresql.org/download/windows/)


* Go to PostgreSQL website download page for windows by clicking on the following link [PostgreSQL](https://www.postgresql.org/download/windows/)

* Click on the download the installer:

![PostgreSQL](./images/image0.1.jpg)

* Click on the Windows x86-64 icon next to the PostgreSQL Version 14.4 to download the file:

![PostgreSQL](./images/image0.2.jpg)


## Install PostgreSQL

* After downloading go to your Downloads folder and double click on the 'postgresql-14.4-1-windows-x64.exe' to run the installer:


![PostgreSQL](./images/image1.jpg)

* Click Yes when the User Account Control window appear to run the file:

![PostgreSQL](./images/image2.jpg)

* Click next to start the installation:

![PostgreSQL](./images/image3.jpg)

* Choose the Installation Directory by clicking on the icon next to it, or click next to choose the default directory, here we will accept the default directory:

![PostgreSQL](./images/image4.jpg)

* Here we can choose what we want to install, Keep all the options selected and click next:

![PostgreSQL](./images/image5.jpg)

* Now we can choose where to save our data, We can also click next to choose the default directory:

![PostgreSQL](./images/image6.jpg)

* We need to choose a password for our postgre admin account, fill a password and retype it again then click Next:

![PostgreSQL](./images/image7.jpg)

![PostgreSQL](./images/image8.jpg)

* Here we choose the Port which PostgreSQL will run on, Click Next to keep the default port 5432:

![PostgreSQL](./images/image9.jpg)

* Click Next to keep the Default Locale:

![PostgreSQL](./images/image10.jpg)

* A Pre Installation Summary will appear to tell you what will be installed and where, Click Next to confirm:

![PostgreSQL](./images/image11.jpg)

* Click Next again to start the installation:

![PostgreSQL](./images/image12.jpg)

* Wait for the installation to finish:

![PostgreSQL](./images/image13.jpg)

* After the installation is completed make sure that the icon next to Stack Builder is checked to open it and install other options (PostGIS spatial database extension for our example):

![PostgreSQL](./images/image14.jpg)



## Install PostGIS

* Now that PostgreSQL database is installed we can use the Stack Builder to install PostGIS spatial database extension.

* The Stack Builder 4.2.1 window will open after we complete installing PostgreSQL database.

* Click on the down arrow to select the installed version of PostgreSQL then click Next:

![PostGIS](./images/image15.jpg)

![PostGIS](./images/image16.jpg)

![PostGIS](./images/image17.jpg)

* Click on the plus icon next to Spatial Extensions and choose "PostGIS 3.2 Bundle for PostgreSQL 14 (x64 bit: v3.2.1", then click Next:

![PostGIS](./images/image18.jpg)

![PostGIS](./images/image19.jpg)

![PostGIS](./images/image20.jpg)

![PostGIS](./images/image21.jpg)

![PostGIS](./images/image22.jpg)

* Click Next to choose the default download directory and wait for the download process to complete:

![GADM](./images/image23.jpg)

![GADM](./images/image24.jpg)

* Click Next to start installing PostGIS (make sure to leave the Skip Installation option unchecked):

![GADM](./images/image25.jpg)

![GADM](./images/image26.jpg)

* The PostGIS 3.2 Bundle for PostgreSQL 14 Setup window will open, Click on I Agree to start installing PostGIS:

![GADM](./images/image27.jpg)

* Click Next. (No need to check the checkbox to Create a spatial databse because we are going to use pgAdmin to create a PostGIS spatial database in the next tutorial)

![GADM](./images/image28.jpg)

* Click Next to keep the default Destination folder:

![GADM](./images/image29.jpg)

* Now, we need to click Yes to register the PROJ_LIB, GDAL_DATA, POSTGIS_ENABLED_DRIVERS and POSTGIS_ENABLED_OUTDB_RASTERS environment variables:

![GADM](./images/image30.jpg)

![GADM](./images/image31.jpg)

![GADM](./images/image32.jpg)

![GADM](./images/image33.jpg)

* Once the installation is complete, Click on Close then cilck on Finish to complete the installation process

![GADM](./images/image34.jpg)

![GADM](./images/image35.jpg)


* That's it for today's tutorial. We just installed PostgreSQL database and PostGIS spatial database extension.

* In the next tutorial, we will learn how to create a PostGIS spatial database using pgAdmin 4 and how to connect to it using QGIS and how to add data inside it and Query this data using SQL.
