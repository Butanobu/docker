# This dockerfile prepsares and installs Domoticz
FROM dockerreg:5000/base/ubuntu:latest

RUN \
  apt-get update && \
  apt-get install -y cmake libboost-dev libboost-thread-dev libboost-system-dev libsqlite3-dev subversion libcurl4-openssl-dev libusb-dev zlib1g-dev && \
  apt-get clean && \
  rm -rf /var/lib/apt/lists/* && \
  adduser domoticz && \
  usermod -a -G dialout domoticz

USER domoticz
WORKDIR /home/domoticz

RUN \
  svn checkout svn://svn.code.sf.net/p/domoticz/code/trunk/ domoticz && \
  cd domoticz && \
  cmake -DCMAKE_BUILD_TYPE=Release . && \
  make
