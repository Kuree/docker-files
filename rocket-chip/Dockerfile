FROM keyiz/rocket-tools

LABEL description="Docker image for building rocket chip"
LABEL maintainer="keyi@cs.stanford.edu"

ARG SBT_VERSION=1.4.5

RUN mkdir /working/ && \
    cd /working/ && \
    curl -L -o sbt-$SBT_VERSION.deb https://dl.bintray.com/sbt/debian/sbt-$SBT_VERSION.deb && \
    dpkg -i sbt-$SBT_VERSION.deb && \
    rm sbt-$SBT_VERSION.deb && \
    apt-get update && \
    apt-get install --no-install-recommends -y python3 default-jre sbt wget && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    rm -rf /working/

RUN update-alternatives --install /bin/python python /bin/python3 100

