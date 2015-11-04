FROM localhost:5000/software/openjdk 

ENV CASSANDRA_MAJOR_VERSION 22
ENV CASSANDRA_MINOR_VERSION 2.2.3

ADD datastax.repo /etc/yum.repos.d/datastax.repo

RUN yum install -y cassandra"$CASSANDRA_MAJOR_VERSION"-"$CASSANDRA_MINOR_VERSION" \
	&& yum clean all 


ENV CASSANDRA_CONFIG /etc/cassandra/conf

# listen to all rpc
RUN sed -ri ' \
		s/^(rpc_address:).*/\1 0.0.0.0/; \
	' "$CASSANDRA_CONFIG/cassandra.yaml"


COPY docker-entrypoint.sh /docker-entrypoint.sh
RUN chmod +x /docker-entrypoint.sh
ENTRYPOINT ["/docker-entrypoint.sh"]


VOLUME /var/lib/cassandra

# 7000: intra-node communication
# 7001: TLS intra-node communication
# 7199: JMX
# 9042: CQL
# 9160: thrift service
EXPOSE 7000 7001 7199 9042 9160

CMD ["cassandra", "-f"]
