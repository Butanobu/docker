FROM dockerreg:5000/software/openjdk7

RUN wget -O - http://debian.neo4j.org/neotechnology.gpg.key| apt-key add - && \
    echo 'deb http://debian.neo4j.org/repo stable/' > /etc/apt/sources.list.d/neo4j.list && \
    apt-get update && \
    apt-get install -d -y neo4j && \
    apt-get install -y neo4j && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*
