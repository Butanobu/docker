# Make sure you create a folder with the nodered installer in it, and
# modify this Dockerfile accordingly.

FROM localhost:5000/software/nodejs:V1

RUN  \
yum install -y git python make gcc && \ 
npm install node-red \
                node-red-node-wordpos \
                node-red-node-smooth \
                node-red-node-blink1 \
                node-red-node-wol \
                node-red-node-ping \
                node-red-node-pushover \
                node-red-node-suncalc \
                node-red-node-exif \
                node-red-node-twilio \
                node-red-node-geohash \
                node-red-node-web-nodes \
                node-red-node-geofence \
                node-red-contrib-neo4j \
                js2xmlparser \
                feedparser \
                redis \
                mongodb && \
    mkdir /home/nodered/.node-red && \
    chown nodered:nodered /home/nodered/.node-red

USER nodered

VOLUME ["/home/nodered/.node-red"]

EXPOSE 1880

CMD ["node-red"]
