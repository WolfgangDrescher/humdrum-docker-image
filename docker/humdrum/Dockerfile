FROM ubuntu:latest

LABEL maintainer="drescher.wolfgang@gmail.com"

RUN apt-get install -y git
RUN apt-get install -y make
RUN apt-get install -y gcc
RUN apt-get install -y g++
RUN apt-get install -y libc-dev
RUN apt-get install -y automake
RUN apt-get install -y autoconf
RUN apt-get install -y libtool
WORKDIR /usr/local
RUN git clone https://github.com/humdrum-tools/humdrum-tools
WORKDIR /usr/local/humdrum-tools
RUN make update
RUN make
RUN make install

ENV PATH="/usr/local/humdrum-tools/humdrum/bin:/usr/local/humdrum-tools/humextra/bin:${PATH}"
