# Django Protfolio
---------------

This section of the website contians my Django projects.

Currently it has some projects under the name of:
* [Advanced Django Blog](https://github.com/MoustafaShaaban/Advanced_Django_Blog)

* [Django Todo App with Authentication and Authorization with REST API](https://github.com/MoustafaShaaban/Django_Todo_App_with_Authentication_and_Authorization)

* [Django and folium](https://github.com/MoustafaShaaban/Django_and_Folium)

-------------------------------------------------------------
## Advanced Django Blog

A project built with Django web framework and Bootstrap.

###  Project Goals

* All users can read or search for the posts on the blog.

* Authenticated users can:

    * Create, Read, Update and Delete (CRUD) blog posts on the website.

    * Add comments on blog posts, but the comments will not be shown until the website admin approves it.

    * Access their profile which lists all their added blog posts.


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


### Libraries and Packages used

* [Django Web Framework](https://www.djangoproject.com/)

* [django-crispy-forms](https://django-crispy-forms.readthedocs.io/en/latest/) package

* UI components from the official [Bootstrap 5.2](https://getbootstrap.com/docs/5.2/getting-started/introduction/) website documentation.
-------------------------------------------------------------

## Django Todo App

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
## Django and folium

###  Project Goals

* Use the power of Folium package to visualize data generated from Django Database on a Leaflet JS map.

* Use Django Admin Site to Import and Export data into and from the database.

* Visualize data using Folium's Simple Markers and Marker Cluster.


### Project Files

* [Github](https://github.com/MoustafaShaaban/Django_and_Folium)

### Project Preview

* [Version 1 on Youtube](https://www.youtube.com/watch?v=r08MujfgjoM)

* [Version 2 on Youtube](https://www.youtube.com/watch?v=eU8r5l9-6JE)


### Libraries and Packages used

* [Django Web Framework](https://www.djangoproject.com/)

* [django-import-export](https://django-import-export.readthedocs.io/en/latest/) package

* [Folium](https://python-visualization.github.io/folium/)