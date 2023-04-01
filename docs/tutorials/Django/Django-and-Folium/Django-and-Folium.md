---
title: Using Django with Folium
slug: tutorials/Django/Django-and-Folium
---


In this tutorial we will learn how to visualize data from Django database into an interactive web map using [Folium](https://python-visualization.github.io/folium/).

You can find the source code of this tutorial on my Github account [here](https://github.com/MoustafaShaaban/Django-and-Folium-Tutorial/tree/main)

# Table of contents

1. [Setting up the project](#project-setup)

2. [Setting up the maps app](#app-setup)


### Libraries and Packages used

* [Django Web Framework](https://www.djangoproject.com/)

* [django-crispy-forms](https://django-crispy-forms.readthedocs.io/en/latest/)

* [Folium](https://python-visualization.github.io/folium/)


According to [Folium's Docs](https://python-visualization.github.io/folium/) `folium` makes it easy to visualize data that's been manipulated in Python on an interactive leaflet map. It enables both the binding of data to a map for `choropleth` visualizations as well as passing rich vector/raster/HTML visualizations as markers on the map.

Let's get started.

## Project Setup <a name="project-setup"></a>

Create Django project (If you haven't used Django before you can check this [tutorial](https://moustafashaaban.github.io/tutorials/Django/Create_Django_project/django_project/) to learn how to create a Django project) called backend.


```bash
>>> cd Desktop/

>>> mkdir Django-and-Folium

>>> cd Django-and-Folium

>>> python -m venv venv

>>> source venv/bin/activate    *Linux or Git Bash on Windows*

>>> venv\Scripts\activate   *On Windows*

>>> python -m pip install django==4.1.3 django-crispy-forms folium==0.14.0

>>> django-admin startproject backend

>>> cd backend

>>> python manage.py startapp maps

>>> python manage.py migrate

>>> python manage.py createsuperuser
```

These commands will create a virtual environment and install the required libraries and packages for this project and create a new Django app called maps.

Register the newly created app and `crispy_forms` app inside the installed apps settings.


```python

# backend/settings.py

INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',

    # My Apps:
    'maps.apps.MapsConfig',

    # Other Apps
    'crispy_forms',
]

# Also choose a template pack for django-cripsy-forms settings in the bottom of the file:


CRISPY_TEMPLATE_PACK = 'bootstrap4'
```

In this tutorial we will use an app-level url configurations, so the last thing we need to do in this step is to create a urls/py file and map it in our main project urls.py

* Edit backend/urls.py to match the image below:

```python

# backend/urls.py

from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('maps.urls')),
]

```
* Create a new file called urls.py inside the app directory and type the following code inside it:

```python

# maps/urls.py

from django.urls import path

from . import views

urlpatterns = [

]

```

The `urlpatterns` is currently empty we will map the Django views to it later in the tutorial.


## App Setup <a name="app-setup"></a>

Let's start setting ip our app. I like to follow the following steps to setup my apps

* Create Django Model

* Create the View

* Map the View to `urls` configurations

* Create the template

So we will start by creating the Model, We will create a Feature model that has the following fields (name, description, latitude, longitude)

```python

# maps/models.py

from django.db import models


class Feature(models.Model):
    name = models.CharField(max_length=250, help_text='Feature Name')
    description = models.TextField(help_text='Feature Description')
    latitude = models.FloatField(help_text='Latitude')
    longitude = models.FloatField(help_text='Longitude')


    class Meta:
        verbose_name = ("feature")
        verbose_name_plural = ("features")

    def __str__(self):
        return f'{self.name}'

```


Register the model in Django admin site:

open `maps/admin.py` and add the following code:

```python

from django.contrib import admin

from .models import Feature


admin.site.register(Feature)
```


After creating a Model and registering it, we need to run the `makemigrations` command:

```console

>>> python manage.py makemigrations

>>> python manage.py migrate

```

Now let's move to the View.

We will split our code into two files here a new file we will create called `utils.py` and the main `views.py` file.

Inside the `maps` app directory create a new file called `utils.py` this file will contain a setup for Folium base map and we will loop through the data inside our database:

```python

# maps/utils.py

import folium
from folium.plugins import Fullscreen, LocateControl, Geocoder

from .models import Feature


def basemap(request):
    """
    Create a Folium base map
    """
    map = folium.Map(
        tiles='cartodbdark_matter',
        attr= 'Public Schools in Seattle'
    )

    features = Feature.objects.all()

    features_layer = folium.FeatureGroup(name='Features Layer').add_to(map)

    for feature in features:
        locations = [feature.latitude, feature.longitude]
        folium.Marker(
            locations,
            tooltip= str(feature.name),
            popup= feature.description
        ).add_to(features_layer)

    folium.TileLayer('cartodbpositron').add_to(map)

    folium.LayerControl(position='bottomright').add_to(map)
    Fullscreen().add_to(map)
    LocateControl().add_to(map)
    Geocoder().add_to(map)
    folium.LatLngPopup().add_to(map)

    

    map = map._repr_html_()

    context = {
        'map': map
    }

    return context
```

Now inside the `maps/views.py` add the following code:

```python

# maps/views.py

from django.shortcuts import render
from django.urls import reverse_lazy
from django.views import generic
from django.http import HttpResponse
from django.contrib import messages

from .models import Feature
from .utils import basemap


def index(request):
    map = basemap(request)
    return render(request, 'map.html', map)


class CreateFeature(generic.CreateView):
    model = Feature
    fields = ['name', 'type', 'description', 'latitude', 'longitude']
    template_name = 'create_feature.html'
    success_url = reverse_lazy('index')

    def get_context_data(self, **kwargs):
        map = folium.Map(
        tiles='cartodbdark_matter',
        attr= 'Django and Folium'
    )

        folium.TileLayer('cartodbpositron').add_to(map)

        folium.LayerControl(position='bottomright').add_to(map)
        Fullscreen().add_to(map)
        LocateControl().add_to(map)
        Geocoder().add_to(map)
        folium.LatLngPopup().add_to(map)

        map = map._repr_html_()
        context = super().get_context_data(**kwargs)
        context['map'] = map
        return context

```

This code creates two Django views:

* index: which is a Django Function-Based view that will be used to render the map page of our application which will contain the map.

* CreateFeature: A Django Class-Based view that will allow the users to create new features.


Now that our views are done, we will have to map the URLs configurations and create the templates.


Open the `maps/urls.py` file and add the following code:

```python

from django.urls import path

from . import views

urlpatterns = [
    path('', views.index, name='index'),
    path('create-feature/', views.CreateFeature.as_view(), name='create-feature'),
]

```

This will create two paths, One for displaying the map, and the other for creating new features.


Our final Step is to create the templates.

Create a new folder inside the maps app and call it templates.

Then create three HTML files inside it `base.html`, `map.html`, and `create_feature.html`

We will Django template inheritance so, both the `map.html` and `create_feature.html` will inherit its content from `base.html`.

`templates/base.html`

```html
<!-- maps/templates/base.html -->

{% load static %}
<!DOCTYPE html>
<html lang="en">

<head>
    <!-- Required meta tags -->
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />

    <!-- Bootstrap CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-rbsA2VBKQhggwzxH7pPCaAqO46MgnOM80zW1RWuH61DGLwZJEdK2Kadq2F9CUG65" crossorigin="anonymous">


    <title>{% block title %}{% endblock title %}</title>

    <style>
        li {
            list-style: none;
        }
    </style>
</head>

<body>
    <!-- Start Navbar -->

    <nav class="navbar navbar-expand-lg navbar-light bg-light">
        <div class="container">
            <a class="navbar-brand" href="{% url 'index' %}">Folium Map</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav"
                aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
        </div>
    </nav>

    <!-- End Navbar -->


    <!-- Start Main Container -->

    <div class="container mt-4">
        <!-- Start Folium Map -->
        {% block map %}{% endblock map %}
        <!-- End Folium Map -->

        <!-- Start Folium Map -->
        {% block content %}{% endblock content %}
        <!-- End Folium Map -->
    </div>

    <!-- End Main Container -->

    <!-- Optional JavaScript; choose one of the two! -->

    <!-- Option 1: Bootstrap and Popper -->
    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.11.6/dist/umd/popper.min.js" integrity="sha384-oBqDVmMz9ATKxIep9tiCxS/Z9fNfEXiDAYTujMAeBAsjFuCZSmKbSSUnQlmh/jp3" crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.2.3/dist/js/bootstrap.min.js" integrity="sha384-cuYeSxntonz0PPNlHhBs68uyIAVpIIOZZ5JqeqvYYIcEL727kskC66kF92t6Xl2V" crossorigin="anonymous"></script>

</body>

</html>

```

`maps/templates/map.html`

```html
<!-- maps/templates/map.html -->

{% extends 'base.html' %}
{% block title %}Django and Folium{% endblock title %}

{% block map %}
    {{ map|safe }}
{% endblock map %}

```


`maps/templates/create_feature.html`

```html
<!-- maps/templates/create_feature.html -->

{% extends "base.html" %}
{% load crispy_forms_tags %}

{% block content %}
    <div class="row">
        <div class="col-4">
            <form action="{% url 'create-feature' %}" method="post">
                {% csrf_token %}
                {{ form|crispy }}
                <button class="btn btn-primary mt-2" type="submit">Import</button>
            </form>
        </div>
        <div class="col-8">
            {{ map|safe }}
        </div>
    </div>
{% endblock content %}

```