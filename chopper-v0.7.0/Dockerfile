FROM ubuntu:20.04
MAINTAINER Miguel FB Abulencia "abulencia.miguel@gmail.com"
ENV DEBIAN_FRONTEND noninteractive

WORKDIR /tmp

### Install required packages

RUN apt-get clean all && \
    apt-get update --fix-missing && \
    apt-get install -y \
        unzip \
        wget && \
    apt-get clean && \
    apt-get purge && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*


### Installing chopper
ENV VERSION 0.7.0
ENV NAME "chopper"


RUN wget https://github.com/wdecoster/chopper/releases/download/v0.7.0/chopper-musl.zip && \
    unzip chopper-musl.zip && \
    chmod +x chopper && \
    cp chopper /bin/ && \
    rm chopper*
