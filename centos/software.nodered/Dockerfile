FROM localhost:5000/software/nodejs:V3

#Some modules need to be compiled from source. 

#Separated out npm install of extra moduels to make it readable

RUN yum install  --setopt=tsflags=nodocs  -y git gcc make  gcc-c++ && \
    yum clean all && \
    npm install -g --unsafe-perm node-red && \
    npm install -g node-gyp && \
    npm install -g \
        node-red-node-exif  \
        node-red-node-random \
        node-red-node-aws \
        node-red-node-dropbox \
        node-red-node-fitbit \
        node-red-node-google \
        node-red-node-badwords \
        node-red-node-rbe \
        node-red-node-base64 \
        node-red-node-daemon \
        node-red-node-jawboneup \
        node-red-node-openweathermap \
        node-red-node-strava \
        node-red-node-tfl \
        node-red-node-weather-underground \
        node-red-node-smooth \
        node-red-node-ping \
        node-red-node-pushover \
        node-red-node-suncalc \
        node-red-node-twilio \
        node-red-node-geohash \
        node-red-node-geofence \
        node-red-contrib-neo4j \
        node-red-node-wordpos \
        js2xmlparser \
        feedparser && \
    adduser -ms /bin/bash nodered && \
    mkdir -p  /home/nodered/.node-red && \
    chown nodered:nodered /home/nodered/.node-red

#removed mongodb and redis due to crypto requirements

USER  nodered

VOLUME ["/home/nodered/.node-red"]

EXPOSE 1880

CMD ["node-red"]

