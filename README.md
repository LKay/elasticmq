# Docker image for `elasticmq`

A docker container for [elasticmq](https://github.com/adamw/elasticmq) which is a nice message queue server with an SQS interface which makes it fantastic for SQS app developers.

It's on [docker-hub](https://hub.docker.com/r/lkay/elasticmq/) and [github](https://github.com/LKay/elasticmq)

## Tags and links

 * `latest` [(Dockerfile)](https://github.com/LKay/elasticmq/blob/master/images/latest/Dockerfile) [![](https://images.microbadger.com/badges/image/lkay/elasticmq.svg)](https://microbadger.com/images/lkay/elasticmq "Get your own image badge on microbadger.com")

 * `0.13.8` [(Dockerfile)](https://github.com/LKay/elasticmq/blob/master/images/0.13.8/Dockerfile) [![](https://images.microbadger.com/badges/image/lkay/elasticmq:0.13.8.svg)](https://microbadger.com/images/lkay/elasticmq:0.13.8 "Get your own image badge on microbadger.com")

## Running

To run just type:
```sh
docker run -P lkay/elasticmq
```
The elasticmq will run on `0.0.0.0:9324` by default.

Image by default uses configuration file located in `/etc/elasticmq/elasticmq.conf` and `/etc/elasticmq` is exposed ad a volume so you can easily replace that config file with your own by calling:
```sh
docker run -P -v /docker/host/elasticmq/my.conf:/etc/elasticmq/elasticmq.conf:ro  lkay/elasticmq
```

You can also provide all additional configurations using `ELASTICMQ_OPTS` environmental variable. You can pass your own configuration file by calling or any other configuration options. As an example:
```sh
docker run -P -e ELASTICMQ_OPTS="-Dnode-address.host=localsqs -Dnode-address.port=9999" lkay/elasticmq
```

For all configuration options refer to the [elasticmq repo](https://github.com/adamw/elasticmq#installation-stand-alone).
