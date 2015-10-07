learning-docker
===============
Repository created in order to learn basics about Docker

Overview
--------

A *container* is a stripped-to-basics version of a Linux operating system. An *image* is software you load into a container. Docker lets people (or companies) create and share software through Docker images. Using Docker, you don't have to worry about whether your computer can run the software in a Docker image - a Docker container *can always run it*.

[docs.docker.com](http://docs.docker.com)

Contents
--------
- [Installation on Linux](#installation-on-linux)
- [Docker images](#docker-images)
- [Creating Docker image](#creating-docker-image)
- [Pushing image to Docker Hub](#pushing-image-to-docker-hub)
- [Pulling image from Docker Hub](#pulling-image-from-docker-hub)
- [References](#references)

Installation on Linux
---------------------

Install Docker with the following command:

```
$ wget -qO- https://get.docker.com/ | sh
```

to see if docker was installed type: 

```
$ docker
```

To see if the sample docker image was loaded and executed type:

```
$ sudo docker run hello-world
```

If everything works, you should see `Hello from Docker` message and some other stuff. It means Docker was installer properly.

Docker images
-------------

Docker images can be downloaded from [Docker Hub](https://hub.docker.com). We can search, download and run different images.

To run sample image type:

```
$ sudo docker run docker/whalesay cowsay boo
```

To see installed images type:

```
$ sudo docker images
```

Creating Docker image
---------------------

In a separate directory create file named `Dockerfile` with the following content:

```
FROM docker/whalesay:latest
RUN apt-get -y update && apt-get install -y fortunes
CMD /usr/games/fortune -a | cowsay
```

Build docker image with the following command:

```
$ sudo docker build -t docker-whale .
```

There's period **.** in the end and `docker-whale` is name of created docker image.

Short description of commands:
- `FROM` keyword tells Docker which image your image is based on
- `RUN` is used to install required software
- `CMD` is used to run the software

To verify is image is built, run:

```
$ sudo docker images
```

and check if `docker-whale` image is listed.

To run image, type:

```
$ sudo docker run docker-whale
```

Pushing image to Docker Hub
----------------------------

Create account on [Docker Hub](https://hub.docker.com) and Create new repository named `docker-whale`

List your images:

```
$ sudo docker images
```

You should see something like:

```
REPOSITORY          TAG                 IMAGE ID            CREATED             VIRTUAL SIZE
docker-whale        latest              30d13636f688        8 minutes ago       274 MB
hello-world         latest              af340544ed62        8 weeks ago         960 B
docker/whalesay     latest              fb434121fc77        4 months ago        247 MB
```

Copy `IMAGE_ID` of your image and type (use your own login here):

```
$ sudo docker tag 30d13636f688 pwittchen/docker-whale:latest
```

Type `sudo docker images` to see if your image is tagged.

```
REPOSITORY               TAG                 IMAGE ID            CREATED             VIRTUAL SIZE
docker-whale             latest              30d13636f688        9 minutes ago       274 MB
pwittchen/docker-whale   latest              30d13636f688        9 minutes ago       274 MB
hello-world              latest              af340544ed62        8 weeks ago         960 B
docker/whalesay          latest              fb434121fc77        4 months ago        247 MB
```

Login to Docker Hub with the following command:

```
$ sudo docker login --username=yourhubusername --password=yourpassword --email=youremail@company.com
```

Push your image to Docker Hub with the command (use your own login here):

```
$ sudo docker push pwittchen/docker-whale
```

Go to Docker Hub website and check if your image is there.

Pulling image from Docker Hub
------------------------------

Use docker rmi command to remove `docker-whale` and `pwittchen/docker-whale` iamges:

```
$ sudo docker rmi -f 30d13636f688
$ sudo docker rmi -f docker-whale
```

Pull your image:

```
$ sudo docker pull pwittchen/docker-whale
```

Run your image:

```
$ sudo docker run pwittchen/docker-whale
```

References
----------
- [Docker website](https://www.docker.com/)
- [Docker documentation](https://docs.docker.com/)
- [Getting started with Docker on Linux](http://docs.docker.com/linux/started/)
- [Docker Hub](https://hub.docker.com/)
