# ElasticSearch-Docker-arm64

elasticsearch docker for arm64, such as raspberr pi

[English](https://github.com/hsxsix/elasticsearch-docker-rpi/blob/master/README.md) | [中文](https://github.com/hsxsix/elasticsearch-docker-rpi/blob/master/README_CN.md)

## Quick Start

Look at this document: [Install Elasticsearch with Dockeredit](https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html),
just replace "docker.elastic.co/elasticsearch/elasticsearch" to "hsxsix/elasticsearch-arm64".
For example:

Starting a single node cluster at Raspberry Pi 4 (64bit kernel) with Dockeredit

To start a single-node Elasticsearch cluster for development or testing, specify single-node discovery to bypass the bootstrap checks:

```shell
docker run -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" hsxsix/elasticsearch-arm64:7.5.1
```

## Feature

* Base on official Dockerfile, only minor changes
* Adapted to Raspberry Pi 64 bit kernel and aarch64-based devices
* Debian is used as the base image in order to reduce the image size and guaranteed functionality

## Changes compared to the official docker image

* Base image changed to debian, reducing image size 
* Delete the JDK in the official elasticsearch package (this jdk is only applicable to x86) and replace it with AdoptOpenJDK-aarch64. The jdk version is unchanged, and it is still 13.0
* Add "xpack.ml.enabled: false"" to the elasticsearch.yml during build image. Raspberry Pi and other arm devices do not support this feature. It is enabled by default and elasticsearch will exit with an error
* RUN command merge to reduced docker image's layers

## FQA

* Why don't use alpine for the base image, so the image volume is smaller?
Alpine runs jdk relying on glic、no bash by default, useradd、chroot and other commands are quite different from standard commands, the Dockerfile will be great changes, which have not been fully tested and verified.

