# ElasticSearch-Docker-arm64

elasticsearch docker for arm64, such as raspberr pi

[English](https://github.com/hsxsix/elasticsearch-docker-rpi/blob/master/README.md) | [中文](https://github.com/hsxsix/elasticsearch-docker-rpi/blob/master/README_CN.md)

## Quick Start

Look at this document: [Install Elasticsearch with Dockeredit](https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html),
just replace "docker.elastic.co/elasticsearch/elasticsearch" to "hsxsix/elasticsearch-arm64".
For example:

Starting a single node cluster with Dockeredit

To start a single-node Elasticsearch cluster for development or testing, specify single-node discovery to bypass the bootstrap checks:

```shell
docker run -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" hsxsix/elasticsearch-arm64:7.5.1
```

## Feature

* Base on official Dockerfile, only minor changes
* Adapted to Raspberry Pi 64 bit kernel and aarch64-based devices
* Debian is used as the base image in order to reduce the image size and guaranteed functionality

## Changes compared to the official docker image

* 
*
* 


