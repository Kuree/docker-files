FROM keyiz/manylinux

LABEL description="A docker image for building portable Python linux binary wheels using modern GCC, with igraph installed"
LABEL maintainer="keyi@cs.stanford.edu"

RUN cd /tmp \
    && curl -L -o igraph.tar.gz https://github.com/igraph/igraph/releases/download/0.8.2/igraph-0.8.2.tar.gz \
    && tar -xzf igraph.tar.gz --strip-components=1 \
    && ./configure CFLAGS=-fPIC CXXFLAGS=-fPIC \
    && make \
    && make check \
    && make install \
    && rm -rf /tmp/* 

