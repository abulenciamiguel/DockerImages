FROM ubuntu:20.04
MAINTAINER Miguel FB Abulencia "abulencia.miguel@gmail.com"
ENV DEBIAN_FRONTEND noninteractive

WORKDIR /tmp

### Install required packages

RUN apt-get clean all && \
    apt-get update --fix-missing && \
    apt-get install -y \
        libncurses5-dev \
        libbz2-dev \
        liblzma-dev \
        libgsl-dev \
        libcurl4-openssl-dev \
        autoconf \
        git \
        zlib1g-dev \
        build-essential \
        curl && \
    apt-get clean && \
    apt-get purge && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*



### Installing htslib/tabix/bgzip
ENV VERSIONH 1.18
ENV NAMEH "htslib"

RUN git clone https://github.com/samtools/htslib.git && \
    cd ${NAMEH} && \
    git submodule update --init --recursive && \
    autoheader && \
    autoconf && \
    ./configure && \
    make && \
    make install && \
    cd .. && \
    cp ./${NAMEH}/tabix /usr/local/bin/ && \
    cp ./${NAMEH}/bgzip /usr/local/bin/ && \
    cp ./${NAMEH}/htsfile /usr/local/bin/ && \
    rm -rf ./${NAMEH}/



### Installing samtools

ENV VERSIONS 1.18
ENV NAMES "samtools"


RUN git clone https://github.com/samtools/samtools.git && \
    cd ${NAMES} && \
    autoheader && \
    autoconf && \
    ./configure && \
    make && \
    make install && \
    cp ./${NAMES}/samtools /usr/local/bin/ && \
    cd .. && \
    rm -rf ./${NAMES}/



### Installing bcftools

ENV VERSIONH 1.18
ENV NAMEB "bcftools"

RUN git clone https://github.com/samtools/bcftools.git && \
    cd ${NAMEB} && \
    autoheader && \
    autoconf && \
    ./configure && \
    make && \
    make install && \
    cp ./${NAMEB}/bcftools /usr/local/bin/ && \
    cd .. && \
    strip /usr/local/bin/${NAMEB} && \
    rm -rf ./${NAMEB}/



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
