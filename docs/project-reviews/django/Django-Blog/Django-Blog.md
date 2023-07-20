---
title: Django Blog
slug: project-reviews/django/Django-Blog
---

# Advanced Django Blog with Rest API and GraphQL

### [Main Project Files on Github](https://github.com/MoustafaShaaban/Advanced_Django_Blog)

In this article I will review a project I created using the following frameworks:

* [Django Web Framework](https://www.djangoproject.com/).
* [Django REST Framework](https://www.django-rest-framework.org).
* [Graphene Django](https://docs.graphene-python.org/projects/django/en/latest/).
* [Cookiecutter Django](https://github.com/cookiecutter/cookiecutter-django).

-------------------------------------------------

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

* Make sure that [Docker](https://www.docker.com/) and [docker-compose](https://docs.docker.com/compose/) are installed in your system.

* Clone the repository: git clone https://github.com/MoustafaShaaban/Advanced_Django_Blog.git

* Change directory to blog_backend directory ``` cd blog_backend ```

* Build the docker image to develop the project locally using docker-compose:

``` docker-compose -f local.yml build ```

* Create the database by running the following commands:

` docker-compose -f local.yml run --rm django python manage.py makemigrations `

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

Currently, the project has the following GraphQL Queries and Mutations:

#### allTags 

Lists all the available tags in the website:

```gql

query ReturnAllTags {
  allTags {
    id
    name
    slug
  }
}

```

![type:video](./reviews/All-Tags.mp4)

---------------------------------------

#### createTag 

This mutation will do the following: 

1. Create a tag called Python, it takes only one input >> the tag name, then, Django will use slugify to create a slug for the tag before saving it to the database.

2. Return all the information about this tag (id, name, and slug):

```gql

mutation CreateTag {
  createTag(input: {name: "Python"}) {
    tag {
      id
      name
      slug
    }
  }

```

![type:video](./reviews/Create-Tag.mp4)

---------------------------------------

#### updateTag 

This mutation will do the following: 

1. Update the tag we need by its slug. so we first need to get the slug of the tag we need to update, then pass in the new name we want to.

2. Return all the information about this tag (id, name, and slug):

```gql

mutation UpdateTag {
  updateTag(slug: "python", name: "python") {
    tag {
      id
      name
      slug
    }
  }
}

```

![type:video](./reviews/Update-Tag.mp4)

---------------------------------------

#### deleteTag 

This mutation will do the following: 

1. Select the tag by its id then, deletes it.

2. Return a success Boolean, if its True, then the tag is deleted successfully:

```gql

mutation DeleteTag {
  deleteTag(id: 2) {
    success
  }
}

```

![type:video](./reviews/Delete-Tag.mp4)

---------------------------------------

#### createPost

This mutation will do the following: 

1. Create a new blog post, it takes the following inputs => title, content and tags.

2. Return an instance of the post and some of its information like post id, title, slug, author, tag, content and comments:

```gql

mutation createPost {
  createPost(input: {
    title: "Post 1",
    content: "Post 1 content",
    tags: [
        { slug: "python" },
    ]
  }) {
    post {
        id
        title
        slug
        author {
            username
        }
        tag {
            name
            slug
        }
        content
        comments {
            comment
            user {
                username
            }
        }
    }
  }
}

```

![type:video](./reviews/Create-Post.mp4)

---------------------------------------

#### updatePost

This mutation is protected, meaning that, only the post author who can update it, If another user tried to update the post, a GraphQL Error will be raised. and it does the following: 

1. Update a blog post, it selects the post by its id, then takes the following inputs => title, content and tags.

2. Return an instance of the post and some of its information like post id, title, slug, author, tag, content and comments:

```gql

mutation updatePost {
  updatePost(
    id: 1
    input: {title: "Post 1 updated", content: "Post 1 content updated", tags: [{slug: "python"}, {slug: "django"}]}
  ) {
    post {
      title
      tag {
        name
        slug
      }
      content
    }
  }
}

```

![type:video](./reviews/Update-Post.mp4)

---------------------------------------

#### deletePost

This mutation is protected, meaning that, only the post author who can delete it, If another user tried to delete the post, a GraphQL Error will be raised. and it does the following: 

1. Select the post by its id, then deletes it.

2. Return a success Boolean, if its True, then the post is deleted successfully:

```gql

mutation deletePost {
  deletePost(id: 1) {
    success
  }
}

```

![type:video](./reviews/Delete-Post.mp4)

---------------------------------------

#### createComment

This mutation will do the following: 

1. Adds a new comment to a blog post, it takes the following inputs => postSlug, email and comment.

2. Return an instance of comment and some of its information like comment id, user, email, comment and the post title which has this comment:

```gql

mutation createComment {
  createComment(
    inputs: {postSlug: "post-1", email: "admin@admin.com", comment: "Great post"}
  ) {
    comment {
      id
      user {
        username
      }
      email
      comment
      post {
        title
      }
    }
  }
}

```

![type:video](./reviews/Create-Comment.mp4)

---------------------------------------

#### updateComment

This mutation is protected, meaning that, only the user who added this comment can update it, If another user tried to update the comment, a GraphQL Error will be raised. and it does the following: 

1. Update a comment, it selects the comment by its id, then takes the following inputs => comment.

2. Return an instance of the comment and some of its information like comment id and comment:

```gql

mutation updateComment {
  updateComment(id: 1, comment: "Great post keep it up") {
    success
    comment {
        id
        comment
    }
  }
}

```

![type:video](./reviews/Update-Comment.mp4)

---------------------------------------

#### deleteComment

This mutation is protected, meaning that, only the user who added this comment can delete it, If another user tried to update the comment, a GraphQL Error will be raised. and it does the following: 

1. Select the comment by its id, then deletes it.

2. Return a success Boolean, if its True, then the comment is deleted successfully:

```gql

mutation deleteComment {
  deleteComment(id: 2) {
    success
  }
}

```

![type:video](./reviews/Delete-Comment.mp4)

---------------------------------------

#### allPosts

This Query returns all the blog posts:

```gql

query AllPosts {
    allPosts {
        id
        title
        author {
            username
        }
        tag {
            name
        }
        content
        comments {
            comment
            user {
                username
            }
        }
    }
}

```

![type:video](./reviews/All-Posts.mp4)

---------------------------------------

#### allPostsWithFilters

This is a GraphQL Relay Mutation which uses Django-Filter package to filter the posts. Here, we return the posts which its title contains the number 1:

```gql

query AllPostsWithFilters {
    allPostsWithFilters(title_Icontains: "1") {
        edges {
            node {
                id
                title
                author {
                    username
                }
            }
        }
    }
}

```

We can also filter the blog posts by content, and display specific number of posts. (Check the GraphQL Docs at the following project url: http://127.0.0.1:8000/graphql/  )

![type:video](./reviews/All-Posts-with-Filters.mp4)

---------------------------------------

#### postsByTag

This Query return all the posts which has the provided tag.

```gql

query PostsByTag {
    postsByTag(tag: "python") {
        id
        title
        author {
            username
        }
        tag {
            name
        }
        content
        comments {
            comment
            user {
                username
            }
        }
    }
}

```

![type:video](./reviews/Posts-By-Tag.mp4)

---------------------------------------

#### postsByTAuthor

This Query return all the posts which has the provided author username.

```gql

query PostsByAuthor {
    postsByAuthor(author: "admin") {
        id
        title
        author {
            username
        }
        tag {
            name
        }
        content
        comments {
            comment
            user {
                username
            }
        }
    }
}

```

![type:video](./reviews/Posts-By-Author.mp4)

---------------------------------------

#### postByTitle

This Query returns all the posts filtered by its title (This is not a GraphQL Relay Query like the one above)

```gql
query PostsByTitle {
    postByTitle(title: "Post") {
        id
        title
        author {
            username
        }
        tag {
            name
        }
        content
        comments {
            user {
                username
            }
            comment
        }
    }
}

```

![type:video](./reviews/Posts-By-Title.mp4)

---------------------------------------

#### commentsByPost

This Query return all the comments on a specific blog post.

```gql

query CommentsByPost {
    commentsByPost(postTitle: "Post") {
        id
        comment
        email
        user {
            username
        }
        post {
            title
            author {
                username
            }
        }
    }
}

```

![type:video](./reviews/Comments-by-Post.mp4)

-------------------------------------------------

### REST API Review

The REST API has the same functionality as the main website, It uses Django REST Framework Viewsets and Routers to allow users to perform Create, Read, Update and Delete (CURD) operations.

Also It uses Cookiecutter Django's REST API Documentation using Swagger API.

![type:video](./reviews/Rest-API-Docs.mp4)

I changed the default way to retrieve the blog post detail information, Instead of having to provide the post id, you can uses the post slug:

![type:video](./reviews/Rest-API-Root.mp4)