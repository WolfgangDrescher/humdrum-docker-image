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

WORKDIR /usr/local
RUN git clone https://github.com/humdrum-tools/humdrum-tools
WORKDIR /usr/local/humdrum-tools
RUN make update
RUN make
RUN make install

WORKDIR /usr/local
RUN git clone https://github.com/craigsapp/humlib
WORKDIR /usr/local/humlib
RUN make update
RUN make
RUN make install

WORKDIR /app

ENV PATH="/usr/local/humdrum-tools/humdrum/bin:/usr/local/humdrum-tools/humextra/bin:${PATH}"
