---
title: "计费说明"
description: 本小节主要介绍 RabbitMQ 的计费说明。
keyword: 云计算,大数据,青云,QingCloud,消息队列,中间件,价格,计费,费用,RabbitMQ,rabbitmq,消息队列服务,消息中间件
weight: 10
draft: false
---

## 费用说明

RabbitMQ创建页面上的**费用预览**计费仅包括集群基础资源（CPU、RAM、磁盘、负载均衡器）费用，集群创建完成之后绑定的公网IP资源、VPC网络资源等费用将会另外计算。使用RabbitMQ时用户扩容后的资源费用也将另外计算。RabbitMQ基础资源费用的计算周期以RabbitMQ集群创建时间为起点，以RabbitMQ集群销毁时间为终点。

除了支持弹性计费，RabbitMQ也支持包年、包月等[合约方式](https://docsv3.qingcloud.com/services/bill_center/bill_guide/reserved/)。

## 价格影响因素

### 磁盘类型

不同的磁盘类型对应着不同的性能，会有相应的价格，详情请参考[磁盘价格文档](https://docsv3.qingcloud.com/storage/disk/billing/price/)。

| 磁盘类型  |                             指标                             |                  备注                  |
| :-------: | :----------------------------------------------------------: | :------------------------------------: |
|  基础型   |  IOPS范围参考：500 – 2500；IO吞吐范围参考：36MB/s - 100MB/s  |  节点类型为基础型时默认采用此类型磁盘  |
| SSD企业级 | IOPS范围参考：2000 – 30000；IO吞吐范围参考：12MB/s - 320MB/s | 节点类型为企业型e2时默认采用此类型磁盘 |


## 价格计算

可以通过 [价格计算器](https://www.qingcloud.com/pricing#/Kafka) 获取价格详情。
