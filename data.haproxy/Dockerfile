FROM dockerreg:5000/software/haproxy

VOLUME ["/haproxy/"]

ADD config.tar /haproxy/

RUN chown haproxy:haproxy /haproxy/*
