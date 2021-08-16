ARG BASE_IMAGE=nodered/node-red
FROM ${BASE_IMAGE} as base
USER root
RUN apk add curl
COPY /resources /
RUN chmod +x /docker-entrypoint.sh
USER node-red
WORKDIR /usr/src/node-red/.node-red
RUN source /install-certificates \
    && source /requirements.txt
RUN rm /tmp/wago.crt 2>/dev/null || :

FROM scratch as final
LABEL maintainer = Wago <dirk.meihoefer@wago.com, sergei.ikkert@wago.com>
LABEL description="node-red with preinstalled modules"
COPY --from=base / /
USER node-red
WORKDIR /usr/src/node-red
ENTRYPOINT [ "/docker-entrypoint.sh" ]
CMD [ "npm start", "--cache /data/.npm", "--userDir", "/data" ]

