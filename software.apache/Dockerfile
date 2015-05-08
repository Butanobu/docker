FROM dockerreg:5000/base/ubuntu:latest

RUN apt-get update && \
    apt-get -y install apache2 && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*
