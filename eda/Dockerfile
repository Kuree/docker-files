FROM ubuntu:20.04
LABEL description="Docker image to run cad tools"
LABEL maintainer="keyi@cs.stanford.edu"

ENV DEBIAN_FRONTEND=noninteractive

RUN dpkg --add-architecture i386 && \
    apt-get update && \
    apt-get install -y --no-install-recommends \
            gcc g++ make cmake libelf-dev libtinfo-dev \
            libc6-i386 python3-dev python3-pip tcl time \
            libx11-6 && \
    dpkg-reconfigure --frontend noninteractive tzdata && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    ln -s /usr/lib/x86_64-linux-gnu/libtinfo.so.6 /usr/lib/x86_64-linux-gnu/libtinfo.so.5

# Switch shell to bash
RUN update-alternatives --install /bin/sh sh /bin/bash 100

ENV SHELL=/bin/bash
