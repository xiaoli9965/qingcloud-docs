---
title: "常见问题"
description: 弹性容器实例 QCI 常见问题
keyword: 青云, QingCloud, 云计算, QCI, 容器, 弹性容器实例
draft: false
weight: 10
---

## 公有仓库镜像

鉴于国内网络限制，对于直接使用 Docker Hub 公有镜像仓库的用户，推荐优先选用青云云平台中的亚太 zone 或者雅加达 zone 。后续如果有较多用户有类似相关的诉求，青云云平台也将考虑搭建 Docker Hub 的镜像地址。目前遇到此类问题可以优先考虑先将公有镜像仓库推送到青云镜像仓库，并且在创建 QCI 实例的时候直接指定青云镜像仓库。

## VPC

若 QCI 实例位于 VPC 网络当中，并且需要访问外网(比如拉取公有仓库镜像)，需要提交给指定的 VPC 网络绑定 EIP，否则容器内部访问外网会失败。

## 端口

同一个 QCI 实例当中的容器共享同一个网络命名空间，因此在使用容器的时候请自行合理安排端口的分配，避免同一个 QCI 实例内不同容器之间的端口冲突。

## 镜像缓存

镜像缓存列表中的镜像大小不等于镜像所占硬盘空间的实际大小，比如大小为 7G 的镜像，导入缓存后显示大小为 4G 左右，而实际所占用空间在 14G 左右。估算单个缓存能够容纳的镜像个数应以实际占用空间为准。

## 配额

QCI 相关资源的配额如下：

| 资源类型 | 配额 |
|-------------|------------------------|
| 基础型 / 性能型容器组 | 10 |
| 企业型 e1/e2 以及超高性能型  | 10 |
| 镜像缓存 | 20 |

> 注意：如果配额不足请通过工单申请。

## 拉取容器镜像超时阈值

| 资源操作 | 超时时间 |
|-------------|------------------------|
| 创建容器组 | 30 分钟 |
| 创建镜像缓存 | 6 小时 |

> 注意：在创建镜像缓存和容器组的过程中，系统拉取镜像的时间取决于环境的网络情况。推荐将一些常用的镜像提前推送到诸如 [青云容器镜像仓库](https://docs.qingcloud.com/product/container/docker_hub.html) 或者阿里云镜像仓库，这样将显著缩短镜像拉取时间和容器组启动时间，加速效果视网络情况而定。

<span id = "diskmountstrategy"></span>

## 容器组机器类型与硬盘类型的匹配策略

| 云服务器类型 | 可挂载的硬盘类型 |
|-------------|------------------------|
| 基础型 | 基础型硬盘、性能型硬盘和容量型硬盘 |
| 性能型 | 性能型硬盘、容量型硬盘和基础型硬盘 |
| 超高性能型 | 超高性能型云服务器能够挂载超高性能型硬盘、容量型硬盘和企业级SSD硬盘 |
| 企业型 e1 |超高性能型、企业级SSD硬盘和容量型硬盘 |
| 企业型 e2	| 超高性能型、企业级SSD硬盘和容量型硬盘 |

## 限制

- 单个容器组最多创建 20 个容器
- 单个容器组最多创建 10 个 label
- 单个缓存最多存储 20 个镜像
- 目前调试终端只支持 sh shell

## 失败资源的删除

对于创建失败的资源，建议用户手动定期清理。或者系统将在稍后合适的时间 ( 一般一个小时左右 ) 自动删除失败的资源。特别的，对于创建过程中处于 pending 状态的容器组，在其加入网络并获取 IP 后，可以手动强制删除。对于大多数情形，推荐在系统离开 pending 状态以后，再进行删除操作。
