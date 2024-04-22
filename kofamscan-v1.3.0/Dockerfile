FROM condaforge/mambaforge:23.11.0-0
MAINTAINER Miguel FB Abulencia "abulencia.miguel@gmail.com"
ENV DEBIAN_FRONTEND noninteractive

WORKDIR /tmp

### Install required packages


### Installing kofamscan
ENV VERSION 1.3.0
ENV NAME "kofamscan"


RUN mamba install -c bioconda kofamscan==1.3.0
