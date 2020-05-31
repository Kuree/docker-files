FROM multiarch/ubuntu-core:arm64-bionic

LABEL description="A docker image for build cad related python packages"
LABEL maintainer="keyi@cs.stanford.edu"

RUN apt update && apt install -y --no-install-recommends gcc-8 g++-8 \
        zip unzip patchelf make cmake python3-dev python3-pip \
        python3-wheel verilator && \
    apt-get clean

RUN rm -rf /usr/bin/gcc && rm -rf /usr/bin/g++ && \
    ln -s /usr/bin/gcc-8 /usr/bin/gcc && \
    ln -s /usr/bin/g++-8 /usr/bin/g++ && \
    ln -s /usr/bin/python3 /usr/bin/python && \
    ln -s /usr/bin/pip3 /usr/bin/pip
