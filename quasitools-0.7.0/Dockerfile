FROM condaforge/mambaforge:23.11.0-0
MAINTAINER Miguel FB Abulencia "abulencia.miguel@gmail.com"
ARG DEBIAN_FRONTEND noninteractive

WORKDIR /tmp

### Install required packages


### Installing quasitools
ENV VERSION 0.7.0
ENV NAME "quasitools"


RUN mamba install -c bioconda -c conda-forge -c defaults quasitools -y
