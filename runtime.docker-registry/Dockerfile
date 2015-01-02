# IMPORTANT: when you run this image, you need a host directory data volume for the DB and image files:

# docker run -d -p <hostport>:5000 -v <host directory>:/docker-registry <this image>

FROM dockerreg:5000/software/docker-registry

ENTRYPOINT ["gunicorn","--access-logfile","/var/log/docker-registry/access.log","--error-logfile","/var/log/docker-registry/server.log","-k","gevent","--max-requests","100","--graceful-timeout","3600","-t","3600","-b","0.0.0.0:5000","-w","8","docker_registry.wsgi:application"]
