# Flask-on-docker
Fully working web service using modified instagram tech stack

In this project we containerize a Flask application with Postgres for development. We implement a Flask application using Docker, Postgres, Gunicorn, and Nginx. Docker was used as a container for both the development and production envrionemnets. Postgres is used for the database. Gunicorn aided in the production environment. Ngix act as a reverse proxy for Gunicorn to handle client requests as well as serve up static files. Nginx and Gunicorn help handle the static and media files. 

This repo is inspired by this tutorial: https://testdriven.io/blog/dockerizing-flask-with-postgres-gunicorn-and-nginx/

This application allows for users to upload images and view their uploaded images in their browers. See below for example:


# Build Instructions
To start you will need to check if docker-compose is installed. You can do that with:

`$ docker-compose --version`

to check if docker-compose is installed and if not, successfully run this command:

`$ pip3 install docker-compose`

# Development


# Production
