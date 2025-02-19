---
title: "创建集群"
description: 本小节主要介绍如何快速创建 PostgreSQL 集群实例。 
keyword: PostgreSQL 实例, 创建集群,创建实例
weight: 10
collapsible: false
draft: false
---

通过 AppCenter 集群管理控制台，您可以快速创建 PostgreSQL 集群。

本小节主要介绍如何快速创建 PostgreSQL 集群。

## 前提条件

- 已获取 QingCloud 管理工作台登录账号和密码，且账号已实名认证。
- 已获取 PostgreSQL 集群操作权限。

## 操作步骤

1. 登录 QingCloud 管理工作台。
2. 选择**产品与服务** > **数据库与缓存** > **关系型数据库 PostgreSQL**，进入 PostgreSQL 集群管理页面。
3. 点击**立即部署**，进入应用部署页面。
4. 选择**区域**。
   根据就近原则，选择实例所在区域。
5. 配置实例基本属性、应用版本、网络信息、环境参数等信息。
   
   a. [基本设置](#基本设置)

   b. （可选）节点设置，包括[主实例设置](#主实例设置自定义)、[只读实例设置](#只读实例设置自定义)、[proxy 实例设置](#proxy-实例设置自定义)

   c. [网络设置](#网络设置)

   d. [服务环境参数设置](#服务环境参数设置)

   e. [用户协议](#用户协议)

6. 确认配置和费用信息无误后，点击**提交**，创建集群。
   
   集群创建成功后，可在**集群管理**页面，查看和管理 PostgreSQL 集群。

   ![集群列表](../../_images/cluster_list.png)

### 基本设置

集群名称、网络、版本、计费方式等基本信息配置。

|<span style="display:inline-block;width:140px">参数</span> |<span style="display:inline-block;width:520px">参数说明</span>|
|:----|:----|
|   UUID     |  系统默认分配的全局唯一标识码，不可修改。  |
|   应用名称     |  （可选）输入当前集群的名称。<li>默认为`PostgreSQL x Cluster`。  |
|   描述  |  （可选）对集群的简要描述。   |
|   版本  |  选择集群版本。   |
|   资源配置类型 |  选择资源配置类型。<li>可选择**基础型**、**增强型**、**专业型**。<li>可选择**自定义**可展开**主实例设置**、**只读实例设置**、**proxy实例设置**，自定义节点参数。| 
|   计费方式 |  选择集群计费方式，可选择按**小时**、**月**、**年**计费。| 
|   自动备份时间 |  选择自动备份时间，可选择在每天指定时间段创建备份。<li>默认自动备份为`关闭`。| 
|   可用区 |  选择区域内可用区。| 

![基本设置](../../_images/base_step_1.png)

### 主实例设置（自定义）

集群主实例的资源配置，包括云服务器规格、磁盘大小等。

|<span style="display:inline-block;width:140px">参数</span> |<span style="display:inline-block;width:520px">参数说明</span>|
|:----|:----|
|   CPU     |  选择集群节点云服务器 CPU 规格。  |
|   内存     |  选择集群节点云服务器内存规格。  |
|   节点类型  |  选择集群节点云服务器类型。可选择`基础型`和`企业型  e2`。<li>不同类型可选 CPU 和内存不同。   |
|   磁盘大小 |  配置集群数据和日志存储磁盘大小。磁盘大小决定了数据库最大容量以及 IOPS 能力，请根据业务量，可滑动设置或输入数字配置集群磁盘大小。<li>最小可配置为 20GB。| 

![主实例节点设置](../../_images/base_step_2.png)

### 只读实例设置（自定义）

集群只读实例的资源配置，包括云服务器规格、磁盘大小等。

|<span style="display:inline-block;width:140px">参数</span> |<span style="display:inline-block;width:520px">参数说明</span>|
|:----|:----|
|   CPU     |  选择集群节点云服务器 CPU 规格。  |
|   内存     |  选择集群节点云服务器内存规格。  |
|   节点类型  |  选择集群节点云服务器类型。可选择`基础型`和`企业型  e2`。<li>不同类型可选 CPU 和内存不同。   |
|   节点数量     |  选择节点数量。 <li>默认为0，最多可选择5个。 |
|   磁盘大小 |  配置集群数据和日志存储磁盘大小。磁盘大小决定了数据库最大容量以及 IOPS 能力，请根据业务量，可滑动设置或输入数字配置集群磁盘大小。<li>最小可配置为 20GB。| 

![节点设置](../../_images/base_step_3.png)

### proxy 实例设置（自定义）

集群 proxy 实例的资源配置，包括云服务器规格、磁盘大小等。

|<span style="display:inline-block;width:140px">参数</span> |<span style="display:inline-block;width:520px">参数说明</span>|
|:----|:----|
|   CPU     |  选择集群节点云服务器 CPU 规格。  |
|   内存     |  选择集群节点云服务器内存规格。  |
|   节点类型  |  选择集群节点云服务器类型。可选择`基础型`和`企业型  e2`。<li>不同类型可选 CPU 和内存不同。   |
|   节点数量     |  选择节点数量。 <li>默认为0，最多可选择2个。 |
|   磁盘大小 |  配置集群数据和日志存储磁盘大小。磁盘大小决定了数据库最大容量以及 IOPS 能力，请根据业务量，可滑动设置或输入数字配置集群磁盘大小。<li>最小可配置为 20GB。| 

![节点设置](../../_images/base_step_4.png)

### 网络设置

通过为集群设置独享私有网络，便于网络**过滤控制**，且不影响其它私有网络的设置，可确保数据库的对不同业务进行网络隔离。数据库集群仅可加入已连接路由器的私有网络，且需确保私有网络的 DHCP 处于**打开**状态。 

出于安全考虑，所有的集群都需要部署在私有网络中，选择已创建的网络。

|<span style="display:inline-block;width:140px">参数</span> |<span style="display:inline-block;width:520px">参数说明</span>|
|:----|:----|
|   私有网络     |  选择私有网络。<li>默认适配同区域已有私有网络。可在下拉框选择已有私有网络。<li>若无可选网络，可点击**创建**，创建依赖网络资源。  |
|   节点 IP   |  配置节点 IP。<li>默认为`自动分配`。<li> 选择`手动配置`需为各节点配置 IP。  |
|   预留 IP      |   配置集群预留高可用 IP 地址。<li>默认为`自动分配`。<li>选择`手动配置`需为集群配置高可用写、高可用读、高可用Proxy IP。   |

![网络设置](../../_images/base_step_5.png)

### 服务环境参数设置

数据库的环境参数配置。需创建初始的数据库账号，并设置数据库服务的配置参数。

|<span style="display:inline-block;width:140px">参数</span> |<span style="display:inline-block;width:520px">参数说明</span>|
|:----|:----|
|   数据库名称     |  输入初始数据库名称。<li>默认为 `qingcloud`。  |
|   数据库用户名     |  输入数据库初始用户账号名。<li>默认为 `pguser`。  |
|   密码   |  输入数据库初始用户账号密码。<li>默认为 `qingcloud1234`。   |
|   更多服务环境参数     |   点击展开参数列，可配置更多数据库参数。<li> 可配置参数与数据库性能相关，部分参数修改会导致 PostgreSQL 服务重启，具体可见参数说明。<li> 高可用版可配置**是否同步流复制**参数，该参数用于设置`同步流复制`或`异步流复制`的主从复制模式。默认配置为`是`，即同步流复制。 |

 >注意：
 >
 >PostgreSQL 创建初始化过程中，会根据服务器参数信息呢创建数据库账户。同时，为了方便用户维护，会自动创建数据库超级用户 `root`，密码与自定义初始密码相同。

![参数设置](../../_images/base_step_6.png)

### 用户协议

阅读**云平台 AppCenter 用户协议**，并勾选用户协议。

![用户协议](../../_images/base_step_7.png)
