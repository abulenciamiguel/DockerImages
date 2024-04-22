FROM ubuntu:20.04
MAINTAINER Miguel FB Abulencia "abulencia.miguel@gmail.com"
ARG DEBIAN_FRONTEND noninteractive

WORKDIR /tmp

### Install required packages

RUN apt-get clean all && \
    apt-get update --fix-missing && \
    apt-get install -y \
        curl && \
    apt-get clean && \
    apt-get purge && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*


### Installing minimap2
ENV VERSION 2.26-r1175
ENV NAME "minimap2"


RUN curl -L https://github.com/lh3/minimap2/releases/download/v2.26/minimap2-2.26_x64-linux.tar.bz2 | tar -jxvf - && \
    cp ./minimap2-2.26_x64-linux/minimap2 /bin/ && \
    rm -r minimap2-2.26_x64-linux/

