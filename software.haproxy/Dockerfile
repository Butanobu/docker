FROM dockerreg:5000/base/ubuntu:latest

RUN apt-get update && \
    apt-get -y install haproxy && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    mkdir /haproxy && \
    chown haproxy:haproxy /haproxy
