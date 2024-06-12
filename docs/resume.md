# Moustafa Shaaban Abdelaziz

* Year of Birth: 1996
* Address: Alexandria, Egypt
-----------------------------------------------------------------
## Contact
---------
* Email: Moustafa-Shaaban@outlook.com       
* Phone + Whatsapp Number: 0201018989702
* [Website](https://moustafashaaban.github.io/)
* [LinkedIn](https://www.linkedin.com/in/moustafashaaban)
* [Github](https://www.github.com/MoustafaShaaban)

-----------------------------------------------------------------

## Summary
---------
* Graduated from faculty of Arts department of Geography and Geographic Information Systems (GIS), Alexandria
University.

* I am a Junior Software Developer with GIS background with experience in building Web applications I am seeking to apply and expand my knowledge and skills towards working in a collaborative environment to develop quality software solutions that address and solve business problems.

Skills :  Python, JavaScript, HTML/CSS, SQL, PostgreSQL, Vue JS, Git/GitHub, Bootstrap, Django web framework, NodeJS

-----------------------------------------------------------------

## Experience
------------
#### Data Entry
  * Elsadek for Real estate valuation

#### Marine surveyor assistant
  * Misr Marine for Surveys and Services

#### Customer Service Representative
  * ECCO Outsourcing

------------

## Education
------------

#### Alexandria University:

* Bachelor's degree, from Faculty of Arts, Department of Geography and Geographic Information Systems, Division of Survey and Maps.

-----------------------------------------------------------------

## Projects
-----------

# Advanced Django Blog

A blog project built using 

  [Django Web Framework](https://www.djangoproject.com/), 
  [Django REST Framework](https://www.django-rest-framework.org), 
  [Graphene Django](https://docs.graphene-python.org/projects/django/en/latest/), 
  [Cookiecutter Django](https://github.com/cookiecutter/cookiecutter-django),
  [HTMX](https://htmx.org/),
  [Vue.js 3](https://vuejs.org/),
  [Quasar Framework](https://quasar.dev/),
  [Tanstack Vue Query](https://tanstack.com/query/latest/docs/vue/overview),
  [Vue Apollo](https://apollo.vuejs.org/),
  [Vue-multiselect](https://vue-multiselect.js.org/),


[Full Review](https://moustafashaaban.github.io/project-reviews/django/Django-Blog/Django-Blog/)

###  Project Goals

* Authenticated users can:

  * Access a GraphQL endpoint and run several Quries and CRUD Mutations.

  * Access a Rest API endpoint and run CRUD operations.

  * Create, Read, Update and Delete (CRUD) blog posts on the website.

  * Add comments on blog posts, but the comments will not be visiable until the website admin approves it.

  * Like Blog posts and Add them to their favorite list (using HTMX).

  * Access their profile which lists all their blog posts and their favorite posts.


* All users can read or search for the posts on the blog.

* Users can access separate frontend project built using Vue.js 3, Tanstack-Vue-Query, Vue-Apollo and Quasar Framework which connects with django through Django Rest Framework using Session Authentication.

* The frontend vue.js app also allows users to perform CRUD operations through connecting to a REST API and a GraphQL endpoints.

Currently in Vue frontend users can:

* Register for an account and log in to their account (users will be authenticated using Django Rest Framework Session Authentication).

* Add tags to blog using a Rest API endpoint and GraphQL endpoint.

* Perform CRUD operations to blog posts using both REST API and GraphQL.

* Perform CRUD operations to add comments to blog posts using both REST API and GraphQL.

* Add and remove posts to and form their favorite posts list.

* Access pages that show their added blog posts and their favorite posts.

* Search for blog posts by title and limiting the results using both REST API and GraphQL

* All users can read or search for the posts on the blog.


### Project files

* [Github](https://github.com/MoustafaShaaban/Advanced_Django_Blog)


### Project preview

* [Youtube](https://www.youtube.com/watch?v=mxe6Ca5yLOo)


###  Project Description:

This project is a Django project called `backend` and it has two registered apps and one third-party app.

* The `blog` app which contians an app-level templates and urls, used for most of the functionalities of our app, like, models, forms, views, urls, and custom template tags.

* The `users` app which uses `django.contrib.auth.urls` to allow users register and login to thier accounts.

* `crispy forms` third-party app which makes beautify django forms design.


### What could you learn from this project?

* Create Django models and define relationships between the database fields.

* Use both Django Class-based and Function-based views.

* Create custom Django template tags, (In this project I created a simple custom template tag that return the number of comments on each blog post).

* How to use page pagination on your website.

* How to associate each blog post to its author.

* How to protect your post so that only you who can modify or delete it.

* Throw a 403 forbidden page to any user who try to guss the URL to change something they are not authorized to do.

* Create a search form on your website.

* And many more.

-------------------------------------


# Django Geoapp + Vue.js 3

###  Project Goals

* Use Django admin site to import data from different sources (CSV, JSON, ...) into the database.

* Use the power of Folium to visualize data generated from Django Database on a Leaflet JS map.

* Visualize data using Folium's Simple Markers.

* Users can register for an account, login, and update their information (handled by Cookiecutter Django)

* Authenticated users can add, import, or export data using django forms.

* Use Vue.js 3 (using Vite ) and axios to fetch the data from the backend and display it in a Bootstrap Table.


### Project Files

* [Github](https://github.com/MoustafaShaaban/Django-Geoapp)

### Project Preview

* [Youtube](https://www.youtube.com/watch?v=dqDSYeppbGI)



### Libraries and Packages used

* [Django Web Framework](https://www.djangoproject.com/)

* [django-import-export](https://django-import-export.readthedocs.io/en/latest/) package

* [Folium](https://python-visualization.github.io/folium/)

* [Cookiecutter Django](https://cookiecutter-django.readthedocs.io/en/latest/index.html)

-------------------------------------
# Django Todo App

A project built with Django web framework and Bootstrap

###  Project Goals

* Users can register to our website to create todos.

* Users can Create, Read, Update and Delete the todos form the website.

* Once logged in, Users can access a REST API of the our website, which also allows them to use CRUD (Create, Read, Update and Delete) operations.

### Project Functionalities:

* Only logged in users can add todos from the website or the API.

* The list todo page of the website and the API will show only the todos which the logged in user created. Meaning, Only the author of the todo who can perform CRUD operations.

* If one user tried to test URLs to reach another user's todo a 403 Forbidden page is displayed.

* Once logged in Users can access a REST API which has a filtering framework built with django-filter package, which allows the user to filter the todos by their state (completed or not completed).

### Project Files

* [Github](https://github.com/MoustafaShaaban/Django_Todo_App_with_Authentication_and_Authorization)


### Project Preview

* [Youtube](https://www.youtube.com/watch?v=Ux8aDtOjBOY)

### Libraries and Packages used

* [Django Web Framework](https://www.djangoproject.com/)

* [Django Rest Framework](https://www.django-rest-framework.org/) package

* [django-filter](https://github.com/carltongibson/django-filter/tree/main)

* UI components from the official Bootstrap 4.6 website documentation.

----------------------------------------------------------------
# Django and folium

###  Project Goals

* Use the power of Folium package to visualize data generated from Django Database on a Leaflet JS map.

* Use Django Admin Site to Import and Export data into and from the database.

* Visualize data using Folium's Simple Markers and Marker Cluster.


### Project Files

* [Github](https://github.com/MoustafaShaaban/Django_and_Folium)

### Project Preview

* [Version 1 on Youtube](https://www.youtube.com/watch?v=r08MujfgjoM)

* [Version 2 on Youtube](https://www.youtube.com/watch?v=eU8r5l9-6JE)

* [Version 3 on Youtube](https://www.youtube.com/watch?v=ZdYvfzODhZg)


### Libraries and Packages used

* [Django Web Framework](https://www.djangoproject.com/)

* [django-import-export](https://django-import-export.readthedocs.io/en/latest/) package

* [Folium](https://python-visualization.github.io/folium/)


## Skills
---------

#### Languages:

* Arabic: Native Speaker
* English: Advanced


#### Computer Skills:

* Linux, Windows, Microsoft Office Suite, Git and Github.


#### Databases:

* SQL
* PostgreSQL and PostGIS
* Sqlite3 and Spatiallite


#### Web Development:

* HTML5
* CSS3
* JavaScript
* Backend development
* Django web framework
* Django rest framework
* Rest APIs
* GraphQL (Graphene Python)
* Vue JS
* Bootstrap 5
* Vite build tool
* Axios
* Apollo GraphQL Client
