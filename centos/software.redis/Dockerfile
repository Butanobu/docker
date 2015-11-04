#Redis for Centos
#Configuration File: /etc/redis/redis.conf



#Ports
# 6379: Default Redis Port

FROM centos
ENV REDIS_DOWNLOAD_URL http://download.redis.io/redis-stable.tar.gz
RUN groupadd -r redis && useradd -r -g redis redis
RUN buildDeps='gcc make glibc-devel patch' \
  && set -x \
  && yum install -y $buildDeps \
  && cd /tmp \
  && mkdir -p /usr/src/redis \
  && curl -SL "$REDIS_DOWNLOAD_URL"  -o redis.tar.gz \
  && tar -xzf redis.tar.gz -C /usr/src/redis --strip-components=1 \
  && rm redis.tar.gz \
  && make -C /usr/src/redis \
  && make -C /usr/src/redis install \
  && rm -r /usr/src/redis \
  && yum remove -y $buildDeps \
  && yum clean -y all

RUN mkdir /data &&\
	chown -R redis:redis /data


VOLUME [ "/data", "/etc/redis" ]
WORKDIR /data

EXPOSE 6379
USER redis
#ENTRYPOINT ["/entrypoint.sh"]
CMD [ "redis-server" ]
