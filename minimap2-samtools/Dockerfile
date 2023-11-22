FROM ubuntu:20.04
MAINTAINER Miguel FB Abulencia "abulencia.miguel@gmail.com"
ENV DEBIAN_FRONTEND noninteractive

WORKDIR /tmp

### Install required packages

RUN apt-get clean all && \
    apt-get update --fix-missing && \
    apt-get install -y \
        libbz2-dev \
        liblzma-dev \
        libncurses5-dev \
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
    autoreconf -i && \
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
    autoconf -Wno-syntax && \
    ./configure && \
    make && \
    make install && \
    cp ./${NAMES} /usr/local/bin/ && \
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
    cp ./${NAMEB} /usr/local/bin/ && \
    cd .. && \
    strip /usr/local/bin/${NAMEB} && \
    rm -rf ./${NAMEB}/



### Installing minimap2
ENV VERSION 2.26-r1175
ENV NAME "minimap2"


RUN curl -L https://github.com/lh3/minimap2/releases/download/v2.26/minimap2-2.26_x64-linux.tar.bz2 | tar -jxvf - && \
    cp ./minimap2-2.26_x64-linux/minimap2 /bin/ && \
    rm -r minimap2-2.26_x64-linux/


RUN apt-get clean all && \
    apt-get update --fix-missing && \
    apt-get install -y \
        libhts-dev && \
    apt-get clean && \
    apt-get purge && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*
