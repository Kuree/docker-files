FROM ubuntu:20.04
LABEL description="Docker image to run Mininet with Python3"
LABEL maintainer="keyi@cs.stanford.edu"

ENV DEBIAN_FRONTEND=noninteractive

USER root
WORKDIR /root

COPY ENTRYPOINT.sh /

RUN apt-get update && apt-get install -y --no-install-recommends \
    python3 python3-dev python3-pip \
    cgroup-tools iperf iperf3 \
    libc6 net-tools python3-pkg-resources socat \
    telnet openvswitch-switch git openvswitch-testcontroller \
    make gcc iproute2 help2man \
    iputils-ping && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    chmod +x /ENTRYPOINT.sh

RUN update-alternatives --install /usr/bin/python python /usr/bin/python3 1

RUN git clone https://github.com/mininet/mininet /tmp/mininet && \
    cd /tmp/mininet && \
    make install && \
    rm -rf /tmp/mininet

# open flow
EXPOSE 6633 6653 6640

ENTRYPOINT ["/ENTRYPOINT.sh"]

