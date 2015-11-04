FROM dockerreg:5000/base/ubuntu:14.04_v2

RUN apt-get update && \
    apt-get install -y curl libusb-1.0-0.dev && \
    curl -sL https://deb.nodesource.com/setup | bash - && \
    apt-get update && \
    apt-get install -y nodejs && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*
