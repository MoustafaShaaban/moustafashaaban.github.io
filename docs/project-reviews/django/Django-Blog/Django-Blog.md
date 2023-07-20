---
title: Django Blog
slug: project-reviews/django/Django-Blog
---

# Advanced Django Blog with Rest API and GraphQL

In this article I will talk about a project I created using the following frameworks:

* [Django Web Framework](https://www.djangoproject.com/).
* [Django REST Framework](https://www.django-rest-framework.org).
* [Graphene Django](https://docs.graphene-python.org/projects/django/en/latest/).
* [Cookiecutter Django](https://github.com/cookiecutter/cookiecutter-django).

-------------------------------------------------

### Table of Contents:

1. Project Description.
2. User Story.
3. Get started with the project
4. Main Project Review.
5. GraphQL Review.
6. REST API Review.

-------------------------------------------------

###  Project Description:

This project is called `blog_backend` and it has four registered apps and one third-party app.

* The `blog` app which contains an app-level templates and urls, used for most of the functionalities of our project, like, blog models, forms, views, urls, and custom template tags.

* The `api` app which contains the Django Rest Framework integration used to build a REST API.

* The `graphql_app` which contains the Graphene Django integration used to build a GraphQL endpoint.
    
* The `users` app which uses `django.contrib.auth.urls` to allow users to register and login to their accounts.

* `crispy forms` third-party app which beautify django forms UI design using Bootstrap.

-------------------------------------------------

### User Story

Users can register for a new account and login, once logged in users can confirm their email address (currently using Mail hog which is handled by Cookiecutter Django).

Once authenticated, users can do the following:

* Update their name or email address inside their profile page.

* Create, Read, Update and Delete (CRUD) blog posts on the website.

* Search for the blog posts.

* Mark posts as their favorite posts and access them in their profile dropdown menu .

* Access their profile which lists all their added blog posts and their favorite posts.

* Add comments on blog posts, but the comments will not be visible until the website admin approves it.

* Access a GraphQL endpoint and run several Queries and CRUD Mutations.

* Access a Rest API endpoint and run CRUD operations.

-------------------------------------------------

### To get started with this project

* Make sure that Docker and docker-compose are installed in your system.

* Clone the repository: git clone https://github.com/MoustafaShaaban/Advanced_Django_Blog.git

* Change directory to blog_backend directory ``` cd blog_backend ```

* Build the docker image to develop the project locally using docker-compose:

``` docker-compose -f local.yml build ```

* Create the database by running the following commands:

` docker-compose -f local.yml run --rm django python manage.py migrate `

* Create a super user:

` docker-compose -f local.yml run --rm django python manage.py createsuperuser `

* Now run the project:

``` docker-compose -f local.yml up ```

* Open the web browser and go to ` http://localhost:8000/ ` to see the results.

![type:video](./reviews/Start-Project.mp4)

Now, we can start reviewing our project.

-------------------------------------------------

### Main Project Review

* Adding a new blog post:

![type:video](./reviews/Add-Post.mp4)

* Updating a blog post:

![type:video](./reviews/Main-Update-Post.mp4)

* Delete a blog post:

![type:video](./reviews/Main-Delete-Post.mp4)

* Protect blog posts so that only the author of the post who can modify it:

![type:video](./reviews/Protect-Posts.mp4)

* Add blog posts to favorite posts:

![type:video](./reviews/Favorite-Posts.mp4)

* List all tags and its related posts: 

![type:video](./reviews/Tags.mp4).

* Search for blog posts:

![type:video](./reviews/Search.mp4)

-------------------------------------------------

### GraphQL Review