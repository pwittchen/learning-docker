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

`docker run hello-world`

If everything works, you should see `Hello from Docker` message and some other stuff. It means Docker was installer properly.

Docker images
-------------

Docker images can be downloaded from [Docker Hub](https://hub.docker.com). We can search, download and run different images.

To run sample image type:

`sudo docker run docker/whalesay cowsay boo`

To see installed images type:

`sudo docker images`

References
----------
- [Docker website](https://www.docker.com/)
- [Docker documentation](https://docs.docker.com/)
- [Getting started with Docker on Linux](http://docs.docker.com/linux/started/)
- [Docker Hub](https://hub.docker.com/)
