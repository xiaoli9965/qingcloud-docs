---
title: "集群使用"
description: 本小节主要介绍 什么是 RocketMQ 集群的使用，包括扩容集群、删除节点等。
keyword: 云计算,大数据,青云,QingCloud,消息队列,中间件,RocketMQ,rocketMQ,扩容集群,删除节点
weight: 8
draft: false
---

## 集群信息

在集群创建完毕后，可以在控制台`Appcenter -> 集群管理`标签下看到目前已经创建的集群信息：

**集群列表**：

![](../../_images/cluster_list.png)

## 配置参数

点击**集群 ID** 可以查看该集群的详细信息，点击右侧的**配置参数**，可以修改RocketMQ的相关参数。

![](../../_images/config_paras.png)

## 扩容集群

**纵向扩容**：点击集群**基本属性**右侧按钮里的**扩容集群**，可以在集群性能不足时提高节点的配置。

![](../../_images/resize_cluster.png)

**横向扩容**：点击集群右侧的**新增节点**， 可以在集群性能不足时添加新节点 。

![](../../_images/add_node.png)

## 删除节点

在集群利用率较低、服务能力过剩的情况下，可以通过删除一些主节点及其从节点来节省资源。

> **注意**
> 
> 删除主节点会导致未被消费的消息永久丢失，请谨慎操作。

