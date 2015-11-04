# Adapted from https://github.com/docker-library/haproxy/blob/ba0dc92fc368edb8e1f4928662316435fe782348/1.5/Dockerfile
# How to Use
# 	Create your own hapoxy.cfg. And add these lines to your dockerfile:
# 	COPY haproxy.cfg /usr/local/etc/haproxy/haproxy.cfg
#	EXPOSE <Put the ports that you wish to be available here
#	Set Permissions:
#		RUN        chown  haproxy:haproxy /usr/local/etc/haproxy/haproxy.cfg  \
#		        && chmod -R 664 /usr/local/etc/haproxy/haproxy.cfg \
#	Set User:
#		USER haproxy
	

FROM centos

RUN yum install -y openssl pcre \
&& 	yum clean all

ENV HAPROXY_MAJOR 1.6
ENV HAPROXY_VERSION 1.6.0
ENV HAPROXY_MD5 2361c7dd0a709a1b235215225875f34c

# see http://sources.debian.net/src/haproxy/1.5.8-1/debian/rules/ for some helpful navigation of the possible "make" arguments
RUN buildDeps='gcc glibc-devel pcre-devel openssl-devel make' \
	&& set -x \
	&& yum install -y $buildDeps  \
	&& curl -SL "http://www.haproxy.org/download/${HAPROXY_MAJOR}/src/haproxy-${HAPROXY_VERSION}.tar.gz" -o haproxy.tar.gz \
	&& echo "${HAPROXY_MD5}  haproxy.tar.gz" | md5sum -c \
	&& mkdir -p /usr/src/haproxy \
	&& tar -xzf haproxy.tar.gz -C /usr/src/haproxy --strip-components=1 \
	&& rm haproxy.tar.gz \
	&& make -C /usr/src/haproxy \
		TARGET=linux2628 \
		USE_PCRE=1 PCREDIR= \
		USE_OPENSSL=1 \
		USE_ZLIB=1 \
		all \
		install-bin \
	&& mkdir -p /usr/local/etc/haproxy \
	&& cp -R /usr/src/haproxy/examples/errorfiles /usr/local/etc/haproxy/errors \
	&& rm -rf /usr/src/haproxy \
	&& yum remove -y  $buildDeps \
	&& yum clean all \
	&& groupadd --system haproxy \
	&& adduser -ms /bin/bash -g haproxy haproxy \
	&& mkdir /var/lib/haproxy \
	&& chown -R haproxy:haproxy  /var/lib/haproxy \
	&& chown -R haproxy:haproxy /usr/local/etc/haproxy/  \
	&& chmod -R 664 /usr/local/etc/haproxy


CMD ["haproxy", "-f", "/usr/local/etc/haproxy/haproxy.cfg"]
