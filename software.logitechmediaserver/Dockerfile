FROM dockerreg:5000/base/ubuntu:12.04_v1

ADD logitechsources.list /etc/apt/sources.list.d/

RUN apt-get update && \
    apt-get install --allow-unauthenticated -y logitechmediaserver && \
    locale-gen en_GB.UTF-8 ja_JP.UTF-8 && \
    update-locale LANG=ja_JP.UTF-8 && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

VOLUME ["/var/lib/squeezeboxserver"]
VOLUME ["/var/log/squeezeboxserver"]

ENV LANG ja_JP.UTF-8
