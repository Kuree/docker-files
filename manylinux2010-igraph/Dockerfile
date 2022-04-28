FROM keyiz/manylinux2010

LABEL description="A docker image for building portable Python linux binary wheels using modern GCC, with igraph installed"
LABEL maintainer="keyi@cs.stanford.edu"

RUN cd /tmp \
    && curl -L -o igraph.tar.gz https://github.com/igraph/igraph/releases/download/0.9.8/igraph-0.9.8.tar.gz \
    && tar -xzf igraph.tar.gz --strip-components=1 \
    && mkdir build && cd build && CFLAGS=-fPIC CXXFLAGS=-fPIC cmake .. -DCMAKE_BUILD_TYPE=Release \
    && make -j8 \
    && make install \
    && rm -rf /tmp/* 

