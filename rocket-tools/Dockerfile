FROM ubuntu:latest

LABEL description="Docker image contains latest rocket-tools"
LABEL maintainer="keyi@cs.stanford.edu"

ENV RISCV=/opt/riscv
ENV MAKEFLAGS=-j32

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
    apt-get install -y autoconf automake autotools-dev curl \
                       libmpc-dev libmpfr-dev libgmp-dev gawk \
                       build-essential bison flex texinfo gperf \
                       libtool patchutils bc zlib1g-dev libexpat-dev \
                       git pkg-config device-tree-compiler && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN git clone --depth 1 --recursive -j8 https://github.com/freechipsproject/rocket-tools && \
    cd rocket-tools && \
    ./build.sh
