# Flask-on-docker
Fully working web service using modified instagram tech stack

In this project we containerize a Flask application with Postgres for development. We implement a Flask application using Docker, Postgres, Gunicorn, and Nginx. Docker was used as a container for both the development and production envrionemnets. Postgres is used for the database. Gunicorn aided in the production environment. Ngix act as a reverse proxy for Gunicorn to handle client requests as well as serve up static files. Nginx and Gunicorn help handle the static and media files. 

This repo is inspired by this [tutorial](https://testdriven.io/blog/dockerizing-flask-with-postgres-gunicorn-and-nginx/)

This application allows for users to upload images and view their uploaded images in their browers. See below for example:
![](https://github.com/rachelHoman/flask-on-docker/blob/main/hw3-screen-recording.gif)


# Build Instructions
To start you will need to check if docker-compose is installed. You can do that with:

`$ docker-compose --version`

to check if docker-compose is installed and if not, successfully run this command:

`$ pip3 install docker-compose`

# Development
Build and run the Docker container with:

`$ docker-compose up -d --build`

Test the connetion by navigating to your local port such as: [http://localhost:1363](http://localhost:1363). You should see something like:

```
{
  "hello": "world"
}
```
To confirm that the data table was created you can follow these commands:

```
$ docker-compose exec db psql --username=hello_flask --dbname=hello_flask_dev

hello_flask_dev=# \l
```

You can check for the text script located in the static folder at [http://localhost:1363/static/hello.txt](http://localhost:1363/static/hello.txt). In your browser you should see:

`hi!`

Lastly, to upload an image, visit http://localhost:1363/upload.

To view the image uploaded, access: http://localhost:1363/media/IMAGE_FILE_NAME.

To end, bring down the development containers with:

`$ docker-compose down -v`

>[!NOTE]
>The -v flag brings down the associated volumes


# Production
>[!NOTE]
>This repository does not contain the .env.prod and .env.prod.db environment variable files. For secuirty purposes they are necessary for the services to run from the container.

Build and run the Docker contianer as follows:

`$ docker-compose -f docker-compose.prod.yml up -d --build`

Create the data table:

`$ docker-compose -f docker-compose.prod.yml exec web python manage.py create_db`

To test the connection, again check http://localhost:1363. You should see something like this in your browser:

```
{"hello": "world"}
```
Use the same process as [above](https://github.com/rachelHoman/flask-on-docker/blob/main/README.md#:~:text=hi!-,Lastly,-%2C%20to%20upload%20an) to upload and views photos.


To end, bring down the containers with:

`$ docker-compose -f docker-compose.prod.yml down -v`

