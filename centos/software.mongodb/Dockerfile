#MongoDB for Centos
#Configuration File: /etc/mongod.conf
#Using official repository
#Version 3.0+
#Start with --rest --httpinterface to enable rest and web admin on PORT+1000
#PGP Key is imported by they have not started signing their packages. Set gpgcheck=1 when they do.

#Do we need to allow SELinux? 
#semange port -a -t mongod_port_t -p tcp 27017

#Ports
#27017: Default mongod port
#27018: Default port with shardsvr
#27019: Default Port with configsvr with clusterRole
#28017: Default web status page

FROM centos

RUN printf "[mongodb-org-3.0] \nname=MongoDB Repository \nbaseurl=https://repo.mongodb.org/yum/redhat/7/mongodb-org/3.0/x86_64/ \ngpgcheck=0 \nenabled=1" > /etc/yum.repos.d/mongodb-org-3.0.repo && \
ls /etc/yum.repos.d/ && \
cat /etc/yum.repos.d/mongodb-org-3.0.repo && \
curl -o mongokey.asc https://www.mongodb.org/static/pgp/server-3.0.asc && \
rpm --import mongokey.asc && \

yum install -y mongodb-org-server && \
yum clean all &&  \
mkdir -p /data/db && \
chown -R mongod:mongod /data


	
EXPOSE 27017 27018 27019 28017
USER mongod
ENTRYPOINT ["usr/bin/mongod"]
