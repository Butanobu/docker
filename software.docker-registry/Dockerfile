FROM dockerreg:5000/base/ubuntu:latest

RUN apt-get update && \
    apt-get -y install build-essential python-dev libevent-dev python-pip liblzma-dev && \
    pip install docker-registry && \
    mkdir -p /var/log/docker-registry && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

ADD config.yml /usr/local/lib/python2.7/dist-packages/config/config.yml
