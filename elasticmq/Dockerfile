FROM java:8-jre-alpine

ENV ELASTICMQ_VERSION 0.13.8
ENV ELASTICMQ_SHA256 "41525fa141f36145e4bb54211bee0906a1901d1cfcbb0d86b8f4367b521e69e1"

ENV ELASTICMQ_PORT 9324
ENV ELASTICMQ_OPTS ""

COPY elasticmq.conf   /etc/elasticmq/elasticmq.conf
COPY elasticmq-server /usr/local/bin/elasticmq-server

WORKDIR /elasticmq

RUN apk add --no-cache --virtual .build-deps \
    wget \
    ca-certificates \
  && wget -q -O /elasticmq-server.jar http://s3-eu-west-1.amazonaws.com/softwaremill-public/elasticmq-server-${ELASTICMQ_VERSION}.jar \
  && echo "${ELASTICMQ_SHA256}  /elasticmq-server.jar" | sha256sum -c - \
  && mkdir -p /elasticmq \
  && chown nobody:nobody /elasticmq \
  && chmod 0750 /elasticmq \
  && chmod +x /usr/local/bin/elasticmq-server \
  && apk del .build-deps

VOLUME /etc/elasticmq

USER nobody

EXPOSE $ELASTICMQ_PORT

CMD elasticmq-server $ELASTICMQ_OPTS
