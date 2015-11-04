#Links to more info:
#	Official Dockerfile based on Debian
#		https://github.com/docker-library/mysql/blob/e892e8c52485535cce5dbadaba2c579fcc805f21/5.6/Dockerfile
#How to Use: 
# docker run --name some-mysql -e MYSQL_ROOT_PASSWORD=my-secret-pw -d <image name>
# Root password has to be set
# Other options are: 
#	-e MYSQL_DATABASE=databasename creates database with name
#	-e MYSQL_USER and -e MYSQL_PASSWORD creates a user that has super user access to the created database
#	These are for the 'docker run' command. Use ENV to set these variables in your dockerfile
#	On Centos the configuration file location is /etc/my.cnf
#	Copy your customisations to it
FROM centos

# add our user and group first to make sure their IDs get assigned consistently, regardless of whatever dependencies get added
RUN groupadd -r mysql && useradd -r -g mysql mysql && set -x

RUN mkdir /docker-entrypoint-initdb.d

# FATAL ERROR: please install the following Perl modules before executing /usr/local/mysql/scripts/mysql_install_db:
# File::Basename
# File::Copy
# Sys::Hostname
# Data::Dumper

ENV MYSQL_MAJOR 5.6
ENV MYSQL_VERSION 5.6.27
ENV RPM_NAME mysql-community-release-el7-5.noarch.rpm

RUN		curl -sSL http://repo.mysql.com/"$RPM_NAME" -o mysql.rpm \
	&&	yum localinstall -y mysql.rpm \
	&&	yum install -y mysql-community-server \
	&&	yum clean all \
	&&	rm -rf /var/lib/mysql \
	&&	mkdir -p /var/lib/mysql




# comment out a few problematic configuration values
# don't reverse lookup hostnames, they are usually another container
RUN sed -Ei 's/^(bind-address|log)/#&/' /etc/my.cnf \
	&& echo 'skip-host-cache\nskip-name-resolve' | awk '{ print } $1 == "[mysqld]" && c == 0 { c = 1; system("cat") }' /etc//my.cnf > /tmp/my.cnf \
	&& mv /tmp/my.cnf /etc/my.cnf

VOLUME /var/lib/mysql

COPY docker-entrypoint.sh /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]

EXPOSE 3306
CMD ["mysqld"]
