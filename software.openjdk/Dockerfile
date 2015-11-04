FROM dockerreg:5000/base/ubuntu:latest

RUN apt-get update && \
    apt-get -y install openjdk-7-jre && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*
