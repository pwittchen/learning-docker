learning-docker
===============
Repository created in order to learn basics about Docker

Overview
--------

A *container* is a stripped-to-basics version of a Linux operating system. An *image* is software you load into a container. Docker lets people (or companies) create and share software through Docker images. Using Docker, you don't have to worry about whether your computer can run the software in a Docker image - a Docker container *can always run it*.

[docs.docker.com](http://docs.docker.com)

Installation on Linux
---------------------

Install Docker with the following command:

```
wget -qO- https://get.docker.com/ | sh
```

to see if docker was installed type: 

`docker`

To see if the sample docker image was loaded and executed type:

`sudo docker run hello-world`

If everything works, you should see `Hello from Docker` message and some other stuff. It means Docker was installer properly.

Docker images on Docker Hub
---------------------------

Docker images can be downloaded from [Docker Hub](https://hub.docker.com). We can search, download and run different images.

To run sample image type:

`sudo docker run docker/whalesay cowsay boo`

To see installed images type:

`sudo docker images`

Creating Docker image
---------------------

In a separate directory create file named `Dockerfile` with the following content:

```
FROM docker/whalesay:latest
RUN apt-get -y update && apt-get install -y fortunes
CMD /usr/games/fortune -a | cowsay
```

Build docker image with the following command:

`sudo docker build -t docker-whale .`

There's period **.** in the end and `docker-whale` is name of created docker image.

Short description of commands:
- `FROM` keyword tells Docker which image your image is based on
- `RUN` is used to install required software
- `CMD` is used to run the software

To verify is image is built, run:

`sudo docker images`

and check if `docker-whale` image is listed.

References
----------
- [Docker website](https://www.docker.com/)
- [Docker documentation](https://docs.docker.com/)
- [Getting started with Docker on Linux](http://docs.docker.com/linux/started/)
- [Docker Hub](https://hub.docker.com/)
