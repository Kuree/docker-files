FROM quay.io/pypa/manylinux1_x86_64

LABEL description="A docker image for building portable Python linux binary wheels using modern GCC"
LABEL maintainer="keyi@cs.stanford.edu"

ARG GCC_VERSION=8.3.0
ARG GCC_PATH=/usr/local/gcc-$GCC_VERSION

RUN yum -y update && yum -y install \
    curl \
    bison \
    flex \
    && yum clean all

RUN cd /tmp \
    && curl -L -o gcc.tar.gz "https://ftp.gnu.org/gnu/gcc/gcc-${GCC_VERSION}/gcc-${GCC_VERSION}.tar.gz" \
    && tar xf gcc.tar.gz \
    && cd /tmp/gcc-$GCC_VERSION \
    && contrib/download_prerequisites \
    && mkdir build \
    && cd build \
    && ../configure -v \
        --build=x86_64-linux-gnu \
        --host=x86_64-linux-gnu \
        --target=x86_64-linux-gnu \
        --prefix=/usr/local/gcc-$GCC_VERSION \
        --enable-checking=release \
        --enable-languages=c,c++ \
        --disable-multilib \
        --program-suffix=-$GCC_VERSION \
    && make -j12 \
    && make install-strip \
    && cd /tmp \
    && rm -rf /tmp/*

RUN cd /tmp \
    && curl -O ftp://sourceware.org/pub/binutils/snapshots/binutils-2.29.1.tar.gz \
    && tar -xf binutils-2.29.1.tar.gz \
    && cd binutils-2.29.1 \
    && ./configure \
    && make \
    && make install \
    && cd /tmp \
    && rm -rf /tmp/*

# env setup
ARG PYTHON_BIN=/opt/python/cp37-cp37m/bin/
ENV CC=/usr/local/gcc-8.3.0/bin/gcc-8.3.0
ENV CXX=/usr/local/gcc-8.3.0/bin/g++-8.3.0
ENV PATH="/usr/local/bin/:${PYTHON_BIN}:${PATH}"

RUN pip install cmake twine auditwheel
