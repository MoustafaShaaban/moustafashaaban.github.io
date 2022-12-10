# Installing VS Code and some Popular Extensions:

* This is the final tutorial in setting a Python development enviroment and tools in our system. You can find the previous parts here:

* [Install Python 3.9.0](../1-Installing_Python/python.md)

* [Install Anaconda Distribution](../2-Installing_Anaconda/anaconda.md)

* [Creating Anaconda Environment and Installing ArcGIS Python API](../3-Creating_Anaconda_Environment/anaconda_environment.md):

* In this tutorial we will learn how to install Microsoft VS Code and some of its recommended extensions.


## Steps

* Download VS Code.
* Install VS Code.
* Install recommended extensions.
* Create a Jupyter Notebook file and choose the conda environment kernel to use.


## Download VS Code:

* Open your web browser (here i am using Microsoft Edge) search bar type download VS Code and click enter to search.

* Click on the first search result 'Download Visual Studio Code - Mac, Linux, Windows':

![VS Code](./images/image1.jpg)

![VS Code](./images/image2.jpg)

![VS Code](./images/image3.jpg)

* Under the Windows logo click on 64 bit button next to User Installer:

![VS Code](./images/image4.jpg)

* Wait until the download is completed.

![VS Code](./images/image5.jpg)

![VS Code](./images/image6.jpg)



## Install VS Code:

* After you finish downloading the VSCode file go to your downloads folder and double click on the file to open it:

![VS Code](./images/image7.jpg)

* Click on the I accept the agreement radio button then click next:

![VS Code](./images/image8.jpg)

![VS Code](./images/image9.jpg)

* Choose the install location by clicking on Browse and choose a folder, or click Next to accept the default installation location:

![VS Code](./images/image10.jpg)

* Click Next to create a shorcut to VS Code in Start Menu Folder:

![VS Code](./images/image11.jpg)

* Make sure to check the Other options because these will help us later.

* These options adds shortcuts to VS Code in context menus (when you right-click on something like Desktop, folder or a file) and register VS Code as the default program to open supported file types (.py, .html, .ipynb, .md and others). The last option adds VS Code to windows Path (this is used for example, if you want to open a file called test.py from the CMD or terminal you can type code test.py this will open the file in VS Code)

* Click Next:

![VS Code](./images/image12.jpg)

* Click Install:

![VS Code](./images/image13.jpg)

* Wait until the installation is finished then click Finish to open VS Code:

![VS Code](./images/image14.jpg)

## Install Recommended Extensions:

* When you open VS Code you will see a Get Started page which will help you to setup the application like choosing a color theme, Sync to other devices and others.

* Do whatever you like to customize your application then close this page:

![VS Code](./images/image15.jpg)

* In the left toolbar click on the last Icon to open the Extensions window:

![VS Code](./images/image16.jpg)

* From the Popular section Install Python extension, This will install tools for Python, Jupyter Notebook and others:

![VS Code](./images/image17.jpg)

![VS Code](./images/image18.jpg)

* Close the Get Started pages as we are not going to use them:

![VS Code](./images/image19.jpg)

![VS Code](./images/image20.jpg)

* Install another two extensions called Live Server and Prettier as you will be using these extensions alot in the future:

    * Live Server extension allows you to run a local server on your computer which helps you to auto reload the web page with each change in your code (we will be using this extension in ArcGIS JavaScript API and Web Development Tutorials).

    * Prettier is a code formatter extension which help us in organizing our code files.

![VS Code](./images/image21.jpg)

![VS Code](./images/image22.jpg)

![VS Code](./images/image23.jpg)

![VS Code](./images/image24.jpg)

![VS Code](./images/image25.jpg)

![VS Code](./images/image26.jpg)

![VS Code](./images/image27.jpg)

* Now we are ready for the final step.


## Create a Jupyter Notebook file and choose the conda environment kernel to use:

* Now we are going to create a Jupyter Notebook in VS Code.

* Click on the File menu from the toolbar and choose New File...

![VS Code](./images/image28.jpg)

![VS Code](./images/image29.jpg)

* Click on Jupyter Notebook .ipynb support

![VS Code](./images/image30.jpg)

* A new file called Untitled-1.ipynb will be created.

* Now, let's learn how to change between conda environments in VS Code.

* On the top right of the file you will see a Kernel icon called Python 3.9.9 64-bit which means that the currently used environment is the global Python Environment.

![VS Code](./images/image31.jpg)

* Click on the name and you will see all the available conda environments in our system.

* Click on ArcGIS_Python_API Conda Env to choose it:

![VS Code](./images/image32.jpg)

* You will notice that the kernel name is changed to ArcGIS_Python_API (Python 3.9.13) which means that we are inside the conda environment we created on the previous tutorial [here](../3-Creating_Anaconda_Environment/anaconda_environment.md)


* And that's it. We reached the end of our tutorial sections where we learned how to download and install development tools we are going to use in our coding and analysis journey



## External Links in this Tutorial:

[Microsoft VS Code](https://code.visualstudio.com/Download)