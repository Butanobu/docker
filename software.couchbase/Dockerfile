FROM dockerreg:5000/base/ubuntu

ADD couchbase-server-community_3.0.1-ubuntu12.04_amd64.deb .

RUN \
  apt-get update && \
  apt-get install -y libssl1.0.0 && \
  dpkg -i couchbase-server-community_3.0.1-ubuntu12.04_amd64.deb && \
  rm couchbase-server-community_3.0.1-ubuntu12.04_amd64.deb && \
  apt-get clean && \
  rm -rf /var/lib/apt/lists/*
