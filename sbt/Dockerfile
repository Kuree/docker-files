FROM openjdk:17-jdk-slim-buster

LABEL description="A docker image for running sbt"
LABEL maintainer="keyi@cs.stanford.edu"
LABEL url="https://github.com/Kuree/hgdb"

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        wget  && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN wget https://dl.bintray.com/sbt/debian/sbt-1.4.7.deb -O sbt.deb && \
    dpkg -i sbt.deb && \
    rm sbt.deb

