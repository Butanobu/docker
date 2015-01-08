FROM dockerreg:5000/base/ubuntu

RUN \
    apt-get update && \
    apt-get install -d -y couchdb

RUN dpkg-divert --local --rename --add /sbin/initctl && \
    ln -s /bin/true /sbin/initctl && \
    dpkg-divert --local --rename --add /usr/bin/ischroot && \
    ln -s /bin/true /usr/bin/ischroot && \
    apt-get install -y couchdb && \
    rm /sbin/initctl && \
    dpkg-divert --rename --remove /sbin/initctl && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    rm /usr/bin/ischroot && \
    dpkg-divert --rename --remove /usr/bin/ischroot
