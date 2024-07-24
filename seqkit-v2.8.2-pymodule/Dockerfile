FROM condaforge/mambaforge:23.11.0-0
MAINTAINER Miguel FB Abulencia "abulencia.miguel@gmail.com"
ARG DEBIAN_FRONTEND noninteractive

WORKDIR /tmp

### Install required packages
### Installing seqkit
ENV VERSION 2.8.2
ENV NAME "seqkit"

RUN apt-get clean all && \
    apt-get update --fix-missing && \
    apt-get install -y \
        gcc && \
    apt-get clean && \
    apt-get purge && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

RUN mamba install -c bioconda seqkit

RUN pip install jsonlib Jinja2 biopython jsonlib==1.2.1
