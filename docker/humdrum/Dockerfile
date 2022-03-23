FROM alpine:latest

LABEL maintainer="drescher.wolfgang@gmail.com"

RUN apk add git
RUN apk add make
RUN apk add gcc
RUN apk add g++
RUN apk add libc-dev
RUN apk add automake
RUN apk add autoconf
RUN apk add libtool
WORKDIR /usr/local
RUN git clone https://github.com/humdrum-tools/humdrum-tools
WORKDIR /usr/local/humdrum-tools
RUN make update
RUN make
RUN make install

ENV PATH="/usr/local/humdrum-tools/humdrum/bin:/usr/local/humdrum-tools/humextra/bin:${PATH}"
