FROM ubuntu:16.04
MAINTAINER Miguel FB Abulencia "abulencia.miguel@gmail.com"
ENV DEBIAN_FRONTEND noninteractive

WORKDIR /tmp

RUN apt-get update && \
  apt-get install -y \
  zlib1g-dev \
  build-essential \
  curl


### Install bwa

ENV VERSION v0.7.17
ENV NAME bwa
ENV URL "https://github.com/lh3/bwa/archive/refs/tags/${VERSION}.tar.gz"


RUN curl -SL $URL | tar -zxv && \
    cd ${NAME}-${VERSION} && \
    make -j 4 && \
    cd .. && \
    cp ./${NAME}-${VERSION}/${NAME} /usr/local/bin/ && \
    strip /usr/local/bin/${NAME}; true && \
    rm -rf ./${NAME}-${VERSION}/
