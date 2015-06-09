# Make sure you create a folder with the nodered installer in it, and
# modify this Dockerfile accordingly.

FROM dockerreg:5000/software/nodejs

ADD node-red-0.9.1.tar /
WORKDIR /node-red-0.9.1
RUN npm install --production && \
    npm install node-red-node-exif \
                node-red-node-twilio \
                node-red-node-geohash \
                node-red-node-web-nodes \
                node-red-node-geofence \
                node-red-contrib-neo4j \
                js2xmlparser \
                feedparser \
                redis \
                mongodb

VOLUME ["/node-red-0.9.1"]

EXPOSE 1880

CMD ["node", "red.js"]
