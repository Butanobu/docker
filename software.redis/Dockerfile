# Create data container from this image
# Add /home/redis/conf/<port>/redis.conf to data container for all servers
# run container with -p <port>:<port> and -w="/home/redis/conf/<port>"

FROM kvmhost:5000/base/ubuntu

RUN \
    cd / && \
    wget http://download.redis.io/redis-stable.tar.gz && \
    tar xvzf redis-stable.tar.gz && \
    cd redis-stable && \
    make && \
    cp src/redis-benchmark src/redis-sentinel src/redis-server src/redis-trib.rb src/redis-check-aof src/redis-check-dump src/redis-cli /usr/local/bin && \
    cd / && \
    rm -rf redis-stable && \
    rm redis-stable.tar.gz && \
    adduser redis && \
    mkdir -p /home/redis/conf && \
    chown redis:redis /home/redis/conf && \
    apt-get update && \
    apt-get install -y ruby && \
    gem install redis && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

VOLUME ["/home/redis/conf"]

USER redis

CMD ["redis-server","redis.conf"]
