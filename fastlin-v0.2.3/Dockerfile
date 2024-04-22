FROM condaforge/mambaforge:23.11.0-0
MAINTAINER Miguel FB Abulencia "abulencia.miguel@gmail.com"
ARG DEBIAN_FRONTEND noninteractive

WORKDIR /tmp

### Install required packages


### Installing fastlin
ENV VERSION 0.2.3
ENV NAME "fastlin"


RUN mamba install -c bioconda fastlin
