#Adapted from https://github.com/neo4j/docker-neo4j/blob/master/2.2.6/Dockerfile

#neo4j from github. Entrypoint file here: https://github.com/neo4j/docker-neo4j/raw/master/2.2.6/docker-entrypoint.sh
#Ports
# 7473: 
# 7474: Neo4j Server
FROM localhost:5000/software/openjdk

ENV NEO4J_VERSION 2.2.6
ENV NEO4J_EDITION community
ENV NEO4J_DOWNLOAD_ROOT http://dist.neo4j.org
ENV NEO4J_TARBALL neo4j-$NEO4J_EDITION-$NEO4J_VERSION-unix.tar.gz
ENV NEO4J_URI $NEO4J_DOWNLOAD_ROOT/$NEO4J_TARBALL
COPY docker-entrypoint.sh /docker-entrypoint.sh
RUN curl -SL $NEO4J_URI -o neo4j.tar.gz && \
	tar -xzf neo4j.tar.gz -C /var/lib && \
	mv /var/lib/neo4j-* /var/lib/neo4j && \
	rm neo4j.tar.gz && \
	chmod +x /docker-entrypoint.sh

WORKDIR /var/lib/neo4j
RUN mv data /data && \
	ln --symbolic /data



EXPOSE 7473 7474
ENTRYPOINT ["/docker-entrypoint.sh"]
CMD ["neo4j"]
