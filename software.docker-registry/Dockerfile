FROM dockerreg:5000/base/ubuntu:latest

RUN apt-get update && \
    apt-get -y install build-essential python-dev libevent-dev python-pip liblzma-dev && \
    pip install docker-registry && \
    mkdir -p /var/log/docker-registry && \
    mkdir -p /docker-registry && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

ADD config.yml /usr/local/lib/python2.7/dist-packages/config/config.yml

VOLUME ["/docker-registry"]

EXPOSE 5000

CMD ["gunicorn","--access-logfile","/var/log/docker-registry/access.log","--error-logfile","/var/log/docker-registry/server.log","-k","gevent","--max-requests","100","--graceful-timeout","3600","-t","3600","-b","0.0.0.0:5000","-w","8","docker_registry.wsgi:application"]
