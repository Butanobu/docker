FROM kvmhost:5000/base/ubuntu

RUN \
    apt-get update && \
    apt-get -y install erlang-base-hipe erlang-dev erlang-manpages erlang-eunit erlang-nox libicu-dev libmozjs185-dev libcurl4-openssl-dev && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    wget http://www.mirrorservice.org/sites/ftp.apache.org/couchdb/source/1.6.1/apache-couchdb-1.6.1.tar.gz && \
    tar -zxvf apache-couchdb-*.tar.gz && \
    cd apache* && \
    ./configure && \
    make && make install && \
    adduser --disabled-login --disabled-password --no-create-home --gecos "" couchdb && \
    chown -R couchdb:couchdb /usr/local/var/lib/couchdb /usr/local/var/log/couchdb /usr/local/var/run/couchdb /usr/local/etc/couchdb && \
    chmod 0770 /usr/local/var/lib/couchdb/ /usr/local/var/log/couchdb/ /usr/local/var/run/couchdb/ /usr/local/etc/couchdb/*.ini /usr/local/etc/couchdb/*.d && \
    ln -s /usr/local/etc/logrotate.d/couchdb /etc/logrotate.d/couchdb && \
    ln -s /usr/local/etc/init.d/couchdb /etc/init.d && \
    update-rc.d couchdb defaults && \
    sed -i s/127.0.0.1/0.0.0.0/g /usr/local/etc/couchdb/default.ini

EXPOSE 5984

VOLUME ["/usr/local/var/lib/couchdb"]

USER couchdb

CMD ["couchdb"]
