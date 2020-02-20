FROM arm32v7/node:slim as base

LABEL maintainer = Wago <Helmut.Saal@wago.com>
LABEL maintainer = Wago <dirk.meihoefer@wago.com>
LABEL maintainer = Wago <sergei.ikkert@wago.com>
LABEL maintainer = Wago <Jens.Sparmann@wago.com>

COPY resources / 

RUN set -x 
RUN apt -y update
RUN apt -y install --no-install-recommends build-essential python

# Home directory for Node-RED application source code.
RUN mkdir -p /usr/src/node-red
# package.json contains Node-RED NPM module and node dependencies
COPY package.json /usr/src/node-red/

# User data directory, contains flows, config and nodes.
RUN mkdir /data

WORKDIR /usr/src/node-red

# Add node-red user so we aren't running as root.
RUN adduser --home /usr/src/node-red/ --disabled-password node-red \
    && chown -R node-red:node-red /data \
    && chown -R node-red:node-red /usr/src/node-red

#USER node-red

RUN npm install
RUN npm install node-red-contrib-iiot-opcua
RUN npm install node-red-contrib-modbustcp
RUN npm install node-red-dashboard
RUN npm install node-red-contrib-telegrambot

RUN apt -y purge build-essential
RUN apt -y purge python 
RUN apt-get -y autoremove
RUN apt-get clean && rm -fr /var/lib/apt/lists/* /tmp/* /var/tmp/*

FROM scratch as final
COPY --from=base / /

WORKDIR /usr/src/node-red
# User configuration directory volume
EXPOSE 1880

# Environment variable holding file path for flows configuration
ENV FLOWS=flows.json
ENV NODE_PATH=/usr/src/node-red/node_modules:/data/node_modules

CMD ["npm", "start", "--", "--userDir", "/data"]