FROM dockerreg:5000/base/ubuntu

RUN dpkg-divert --local --rename --add /sbin/initctl && \
    ln -s /bin/true /sbin/initctl && \
    apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10 && \
    echo 'deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen' | tee /etc/apt/sources.list.d/mongodb.list && \
    apt-get update && \
    apt-get install -y mongodb-org && \
    rm /sbin/initctl && \
    dpkg-divert --rename --remove /sbin/initctl && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    mkdir -p /data/db && \
    chown -R mongodb:mongodb /data

VOLUME ["/data/db"]

EXPOSE 27017 27018 27019 28017

USER mongodb

CMD ["/usr/bin/mongod"]
