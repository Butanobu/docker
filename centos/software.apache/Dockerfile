FROM centos

RUN\
    yum -y install httpd && \
    yum clean all  

EXPOSE 80 443

VOLUME /var/www /etc/apache2

CMD ["apachectl","-DFOREGROUND"]
