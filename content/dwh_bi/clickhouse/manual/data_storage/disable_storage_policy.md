---
title: "删除对象存储策略"
description: 本小节主要介绍如何删除 ClickHouse 对象存储策略。 
keyword: ClickHouse 删除对象存储策略，删除策略
weight: 40
collapsible: false
draft: false
---


当无需多磁盘存储和冷热存储时，为确保对象存储磁盘数据安全，您可以一键删除对象存储策略。

本小节主要介绍如何删除 ClickHouse 对象存储策略。

## 约束限制

- 仅策略关联表删除后，才能删除策略。
- 不支持删除 `default` 存储策略。
- 删除对象存储策略，将同时删除冷热存储策略。

## 前提条件

- 已获取管理控制台登录账号和密码，且已获取集群操作权限。
- 已创建 ClickHouse 集群，且集群状态为**活跃**。

## 删除策略

1. 登录 QingCloud 管理控制台。
2. 选择**产品与服务** > **数据仓库与 BI** > **ClickHouse**，进入集群管理页面。
3. 选择目标集群，点击目标集群 ID，进入集群详情页面。
4. 在**基本属性**模块，点击集群操作下拉菜单。
5. 展开下拉菜单，点击**删除冷热存储策略**，进入关闭确认窗口。

   <img src="../../../_images/off_bucket_policy.png" alt="关闭冷热存储" style="zoom:50%;" />

6. 输入策略名称，确认配置信息无误后，点击**提交**，返回集群详情页面。

   待集群状态切换为**活跃**，即删除对象存储策略完毕。

## 查询策略

执行如下命令，若只查询到 `default` 存储策略，则删除对象存储策略成功。

```bash
$ echo "select  *  from  system.storage_policies" | curl 'http://<ClickHouse 用户名>:<ClickHouse 密码>@<高可用 IP>:8123/' --data-binary @-
```
