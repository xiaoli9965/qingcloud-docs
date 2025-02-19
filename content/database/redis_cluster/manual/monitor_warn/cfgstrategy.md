---
title: "配置指标告警策略"
description: 本小节介绍如何查配置指标告警。 
weight: 5
draft: false
keyword: QingCloud，Redis Cluster，监控，告警，指标
---

Redis Cluster 监控告警是通过云监控服务 CloudSat 为集群服务器的资源和服务提供监控告警管理。当绑定的监控项超过阈值时将触发告警，并通过短信、邮件等形式发送告警通知。

本小节介绍如何创建及绑定指标告警策略。配置告警通知策略请参见[配置告警通知策略](../cfgnotice/)。

## 背景信息

- 支持的告警监控项：**CPU利用率**、**内存使用率**、**磁盘使用量**、**节点服务状态**、**是否指向预期主节点**、**被拒绝的Key个数**、**Keyspace未命中数**、**Client连接数最大值**、**Redis内存使用率最大值**、**命中率最大值**、**节点角色**。
- 支持的监控周期：**1分钟**、**5分钟**。

## 操作步骤

1. 登录 [QingCloud 管理控制台](https://console.qingcloud.com/login)。

2. 在控制台顶部的导航菜单中，选择**产品与服务** > **数据库与缓存** > **键值数据库 Redis**，进入 Redis Cluster 管理页面。

3. 点击目标集群 **ID** 号，进入集群详情页面。

4. 点击**告警**页签，进入告警配置页面。

   <img src="/database/redis_cluster/_images/warning.png" alt="告警页面" />

### 绑定指标告警策略

1. 在**告警**页签，勾选需要配置的节点，点击**绑定指标告警策略**。

   <img src="/database/redis_cluster/_images/select_warning_policy.png" alt="选择要绑定的告警策略" style="zoom:45%;" />

2. 选择已创建的告警策略，点击**提交**。

   若还未创建有告警策略或已有告警策略不合适，请参见[创建指标告警策略](#创建指标告警策略)进行新建。

   >**说明**
   >
   >每个节点只能绑定一个指标告警和一个事件告警。

### 创建指标告警策略

1. 在**告警**页签，勾选节点，点击**绑定指标告警策略** > **创建指标告警策略**。

2. 在**创建告警策略**页面，配置告警基本参数。

   <img src="/database/redis_cluster/_images/create_warning_policy_1.png" style="zoom:45%;" />

   **名称** ：输入告警策略名称。

   **对象范围** ：默认为**平台监控**。

   **告警类型** ：默认为**指标告警**，即对集群指标进行监控告警。

   **资源类型** ：默认为**集群节点**。

   **监控周期** ：可选择**1分钟**或**5分钟**。**5分钟**粒度为免费使用，**1分钟**粒度将收取费用。

3. 点击**下一步**，配置告警规则。

   <img src="/database/redis_cluster/_images/create_warning_policy_2.png" style="zoom:45%;" />

   点击**添加规则**，并可配置指标规则阈值和告警级别，一个策略可添加多条指标规则。

   > **说明**
   >
   > 有多条指标规则时，任何一条规则满足条件都会触发告警。

4. 点击**下一步**，配置告警行为。

   <img src="/database/redis_cluster/_images/create_warning_policy_3.png" style="zoom:45%;" />

   **发送通知** ：选择是否发送告警通知。

   **触发条件** ：选择告警触发条件，可选择**资源变为告警时**和**资源恢复正常时**。

   **告警次数** ：当资源持续处于**告警**状态时，连续发送告警通知的次数。最多为100次。

   **通知列表** ：选择告警通知列表。可点击**新列表**创建新的通知列表。

5. 确认配置无误后，点击**提交**，返回指标告警策略配置窗口，即可选择新创建的告警策略。

   > **说明**
   >
   > 若需要删除或修改告警策略，请点击**管理告警策略**进入云监控 CloudSat 的**平台告警策略**页面进行操作，具体说明请参见**云监控 CloudSat** [告警服务](https://docsv3.qingcloud.com/monitor_service/cloudsat/manual/alarm_service/)。
