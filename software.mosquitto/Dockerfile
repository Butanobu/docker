FROM dockerreg:5000/base/ubuntu

RUN \
    apt-get update && \
    apt-get install -y software-properties-common && \
    apt-add-repository ppa:mosquitto-dev/mosquitto-ppa && \
    apt-get update && \
    apt-get install -y mosquitto && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

USER mosquitto
CMD ["/usr/sbin/mosquitto"]
