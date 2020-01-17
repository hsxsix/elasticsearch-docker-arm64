# ElasticSearch-Docker-arm64

elasticsearch arm64设备的docker镜像

[English](https://github.com/hsxsix/elasticsearch-docker-rpi/blob/master/README.md) | [中文](https://github.com/hsxsix/elasticsearch-docker-rpi/blob/master/README_CN.md)

## 快速开始

参考官方文档: [Install Elasticsearch with Dockeredit](https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html),
仅需要把 "docker.elastic.co/elasticsearch/elasticsearch" 替换为 "hsxsix/elasticsearch-arm64"。

举个栗子:

使用docker命令在树莓派上(64位内核的系统)启动一个单点，

```shell
docker run -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" hsxsix/rpi-elasticsearch:7.5.1
```

## 特性

* 基于官方的Dockerfile，仅做很小的改动
* 适用于树莓派64位系统和其他arm64的设备
* 为了减小镜像体积和保证功能的完整性，使用了debian：latest作为基础镜像构建

## 对比官方Dockerfile的改动

* 基础镜像改为debian，减少镜像体积
* 删除官方elasticsearch软件包中JDK（此jdk仅适用于x86），替换为适用于arm64的AdoptOpenJDK-aarch64，jdk版本不变，依旧是13.0
* 构建时elasticsearch.yml配置文件中添加 xpack.ml.enabled: false， 树莓派等arm设备不支持此项功能，默认开启，elasticsearch会发生错误而退出
* 将apt 安装软件和新建用户、用户组授权等命令合并在一起，减少了一层

## FQA

* 基础镜像为什么不使用alpine，这样镜像体积不是更小吗？

alpine运行jdk需要依赖glic、默认没有bash、而且useradd   chroot等命令和标准命令相差较大，会有很大的变动，未经过充分的测试验证。
