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

WORKDIR  /usr/local
RUN git clone https://github.com/humdrum-tools/humdrum-tools.git
RUN sed -i -e 's/git@github.com:/https:\/\/github.com\//g' humdrum-tools/.gitmodules
RUN (cd humdrum-tools && make update)
RUN (cd humdrum-tools && make)
RUN (cd humdrum-tools && make install)

RUN git clone https://github.com/craigsapp/humlib.git
RUN (cd humlib && make)
RUN (cd humlib && make install)

WORKDIR /app

ENV PATH="/usr/local/humdrum-tools/humdrum/bin:/usr/local/humdrum-tools/humextra/bin:${PATH}"
