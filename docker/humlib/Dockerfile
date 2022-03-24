FROM alpine:latest

LABEL maintainer="drescher.wolfgang@gmail.com"

RUN apt-get install git
RUN apt-get install make
RUN apt-get install gcc
RUN apt-get install g++
RUN apt-get install libc-dev
RUN apt-get install automake
RUN apt-get install autoconf
RUN apt-get install libtool
WORKDIR /usr/local
RUN git clone https://github.com/humdrum-tools/humdrum-tools
WORKDIR /usr/local/humdrum-tools
RUN make update
RUN make
RUN make install

# https://github.com/craigsapp/humlib/issues/49
RUN apt-get install sudo
WORKDIR /usr/local
RUN git clone https://github.com/craigsapp/humlib
WORKDIR /usr/local/humlib
RUN make update
RUN make
RUN make install

ENV PATH="/usr/local/humdrum-tools/humdrum/bin:/usr/local/humdrum-tools/humextra/bin:${PATH}"
