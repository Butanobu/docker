FROM dockerreg:5000/base/ubuntu

RUN \
    dpkg-divert --local --rename --add /sbin/initctl && \
    ln -s /bin/true /sbin/initctl && \
    apt-get update && \
    apt-get install -y software-properties-common && \
    apt-add-repository ppa:mosquitto-dev/mosquitto-ppa && \
    apt-get update && \
    apt-get install -y mosquitto && \
    rm /sbin/initctl && \
    dpkg-divert --rename --remove /sbin/initctl
