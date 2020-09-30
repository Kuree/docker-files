FROM quay.io/pypa/manylinux2010_x86_64

LABEL description="Manylinux2010 image with Java installed"
LABEL maintainer="keyi@cs.stanford.edu"


RUN yum -y install \
    java-1.8.0-openjdk.x86_64 \
    gmp-devel \
    && yum clean all

# env setup
ARG PYTHON_BIN=/opt/python/cp37-cp37m/bin/
ENV PATH="/usr/local/bin/:${PYTHON_BIN}:${PATH}"

RUN pip install cmake twine auditwheel

