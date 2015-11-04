FROM centos

RUN \
    curl -SL http://download.opensuse.org/repositories/home:/oojah:/mqtt/CentOS_CentOS-7/home:oojah:mqtt.repo && \
    mv home:oojah:mqtt.repo /etc/yum.repos.d/mqtt.repo && \
    yum -y install mosquitto && \
    yum -y clean all

EXPOSE 1883
USER mosquitto
CMD ["/usr/sbin/mosquitto"]
