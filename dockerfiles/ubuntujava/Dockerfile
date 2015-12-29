# it's simple docker container with ubuntu, java
# and tools required for development and deployment of jvm projects

FROM ubuntu:14.04
MAINTAINER pwittchen
USER root

# install java
RUN apt-get update
RUN apt-get install software-properties-common -y
RUN add-apt-repository ppa:webupd8team/java -y
RUN apt-get update
RUN echo debconf shared/accepted-oracle-license-v1-1 select true | debconf-set-selections
RUN apt-get install oracle-java8-installer -y
RUN apt-get install oracle-java8-set-default

# install tools
RUN apt-get install -y wget sed git ant maven gradle
