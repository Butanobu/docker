FROM dockerreg:5000/software/apache

RUN \
	echo 'deb http://emon-repo.s3.amazonaws.com wheezy unstable' > /etc/apt/sources.list.d/emoncms.list && \
	apt-get update && \
	sudo apt-get install -y emoncms
