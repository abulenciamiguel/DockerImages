FROM condaforge/mambaforge:23.11.0-0
MAINTAINER Miguel FB Abulencia "abulencia.miguel@gmail.com"
ARG DEBIAN_FRONTEND noninteractive

WORKDIR /tmp

### Install required packages


### Installing nanoq
ENV VERSION 0.10.0
ENV NAME "nanoq"


RUN mamba install -c bioconda nanoq
