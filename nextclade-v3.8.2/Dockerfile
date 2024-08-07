FROM condaforge/mambaforge:23.11.0-0
MAINTAINER Miguel FB Abulencia "abulencia.miguel@gmail.com"
ARG DEBIAN_FRONTEND noninteractive

WORKDIR /tmp

### Install required packages


### Installing nextclade
ENV VERSION 3.8.2
ENV NAME "nextclade"


RUN mamba install -c bioconda nextclade
