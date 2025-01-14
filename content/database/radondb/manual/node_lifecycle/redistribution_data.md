---
title: "数据重分布"
description: 本小节主要介绍如存储节点数据重分布。 
keyword: RadonDB 数据重分布
weight: 25
collapsible: false
draft: false
---


当几个存储节点的数据分布不均衡，或者新增存储节点后，可以通过在线数据重分布，快速迁移最新 SQL 节点数据至存储节点，重分布均衡存储节点数据。

> **注意**
> 
> 为了时数据完全均衡分布，建议选择业务低峰期执行数据重分布。

本小节主要介绍如何启动在线数据重分布。

## 前提条件

- 已获取 QingCloud 管理控制台登录账号和密码，且已获取集群操作权限。

## 操作步骤

1. 登录 QingCloud 管理控制台。
2. 选择**产品与服务** > **数据库与缓存** > **分布式数据库 RadonDB**，进入集群管理页面。
3. 选择目标集群，点击目标集群 ID，进入集群详情页面。
4. 在**基本属性**模块，展开下拉菜单。
5. 点击**数据重分布**。
6. 配置重分布信息。

   -**清理原数据**：迁移完成后是否清理原存储节点数据。默认为**true**；设置为**false** 时，迁移完成后需执行 `radon cleanup` 清理原数据。

   -**并发数**：迁移时的并发数。可选择32、64、128。

7. 确认配置信息无误后，点击**提交**，返回节点列表页面。

   待节点状态切换为**活跃**，即数据重分布完毕。

   <img src="../../../_images/redistribution.png" alt="数据重分布" style="zoom:50%;" />
