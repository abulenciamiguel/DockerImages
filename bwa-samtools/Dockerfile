FROM ubuntu:16.04
MAINTAINER Miguel FB Abulencia "abulencia.miguel@gmail.com"
ENV DEBIAN_FRONTEND noninteractive

WORKDIR /tmp

### Install required packages (samtools)

RUN apt-get clean all &&\
    apt-get update &&\
    apt-get install -y  \
        zlib1g-dev \
        build-essential \
        curl \
        libncurses5-dev \
        libbz2-dev \
        liblzma-dev \
        libgsl-dev \
        libcurl4-openssl-dev \
        autoconf \
        git && \
    apt-get clean && \
    apt-get purge && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

### Installing samtools/htslib/tabix/bgzip

ENV VERSIONH 1.18
ENV NAMEH "htslib"

ENV VERSIONS 1.18
ENV NAMES "samtools"

ENV VERSIONH 1.18
ENV NAMEB "bcftools"


RUN git clone https://github.com/samtools/htslib.git && \
    cd ${NAMEH} && \
    git submodule update --init --recursive && \
    autoconf && \
    autoheader && \
    ./configure && \
    make && \
    make install && \
    cd .. && \
    cp ./${NAMEH}/tabix /usr/local/bin/ && \
    cp ./${NAMEH}/bgzip /usr/local/bin/ && \
    cp ./${NAMEH}/htsfile /usr/local/bin/ && \
    strip /usr/local/bin/tabix; true && \
    strip /usr/local/bin/bgzip; true && \
    strip /usr/local/bin/htsfile; true && \

git clone https://github.com/samtools/samtools.git && \
    cd ${NAMES} && \
    autoconf && \
    autoheader && \
    ./configure && \
    make && \
    make install && \
    cp ./${NAMES} /usr/local/bin/ && \
    cd .. && \
    strip /usr/local/bin/${NAMES}; true && \

git clone https://github.com/samtools/bcftools.git && \
    cd ${NAMEB} && \
    autoconf && \
    autoheader && \
    ./configure && \
    make && \
    make install && \
    cp ./${NAMEB} /usr/local/bin/ && \
    cd .. && \
    strip /usr/local/bin/${NAMEB}; true && \
    rm -rf ./${NAMEH}/ && \
    rm -rf ./${NAMES}/ && \
    rm -rf ./${NAMEB}



### Install bwa

ENV VERSIONBWA 0.7.17
ENV NAMEBWA "bwa"
ENV URL "https://github.com/lh3/bwa/archive/refs/tags/v${VERSIONBWA}.tar.gz"


RUN curl -SL $URL | tar -zxv && \
    cd ${NAMEBWA}-${VERSIONBWA} && \
    make && \
    cd .. && \
    cp ./${NAMEBWA}-${VERSIONBWA}/${NAMEBWA} /usr/local/bin/ && \
    strip /usr/local/bin/${NAMEBWA}; true && \
    rm -rf ./${NAMEBWA}-${VERSIONBWA}/
