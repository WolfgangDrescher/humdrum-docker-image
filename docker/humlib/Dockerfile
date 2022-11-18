FROM ubuntu:latest

LABEL maintainer="drescher.wolfgang@gmail.com"

RUN apt-get update \
    && apt-get install -y \
        software-properties-common \
    && apt-get install -y \
        apt-utils \
        git \
        make \
        gcc \
        g++ \
        automake \
        libtool \
        curl \
        unzip \
        sudo \
    && rm -rf /var/lib/apt/lists/*

RUN git clone https://github.com/humdrum-tools/humdrum-tools.git
RUN sed -i -e 's/git@github.com:/https:\/\/github.com\//g' humdrum-tools/.gitmodules
RUN (cd /usr/local/humdrum-tools && make update)
RUN (cd /usr/local/humdrum-tools && make)
RUN (cd /usr/local/humdrum-tools && make install)

WORKDIR /usr/local
ADD humlib /usr/local/humlib
WORKDIR /usr/local/humlib
RUN (cd /usr/local/humlib && make)
RUN (cd /usr/local/humlib && make install)

WORKDIR /app

ENV PATH="/usr/local/humdrum-tools/humdrum/bin:/usr/local/humdrum-tools/humextra/bin:${PATH}"
