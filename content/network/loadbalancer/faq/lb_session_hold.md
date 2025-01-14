---
title: "负载均衡器会话保持"
description: 介绍负载均衡器会话保持的作用及相关原理、概念。
keyword: QingCloud, 青云, 云计算, 网络, 负载均衡器, 会话保持
draft: false
---

## LB 会话保持的作用

举例说明一下： 如果有一个用户在服务器甲登录了，访问请求被分配到服务器甲，在很短的时间，这个用户又发出了一个请求，如果没有会话保持功能的话，这个用户的请求很有可能会被分配到服务器乙去，这个时候在服务器乙上是没有登录的，所以你要重新登录，但是用户并不知道自己的请求被分配到了哪里，用户的感觉就是登录了，怎么又要登录，用户体验很不好。 如果配置了会话保持功能，所有这一系列的操作过程都由同一台服务器完成，而不能被负载均衡器分配到不同的服务器上。

## 支持的协议类型

四层协议：TCP，基于源地址的会话保持。数据传输快。适用场景：适用于注重可靠性，对数据准确性要求高的场景，如文件传输、发送或接收邮件、远程登录。对性能和并发规模有要求的 Web 应用。

七层协议：HTTP，基于 Cookie 的会话保持，使用 X-Forward-For 获取源地址。适用场景：需要对数据内容进行识别的应用，如 Web 应用、移动游戏等。

## 配置四层会话保持

四层协议的会话保持

支持基于源 IP 地址的简单会话保持，即来自同一 IP 地址的访问请求会转发到同一台后端服务器上进行处理。

说明：当创建四层协议监听器，负载方式设置为源地址来获得会话保持，理论上只要后端没有增删或者上下线，会话就不会过期 

## 配置七层会话保持

七层协议的会话保持

会话保持可以将来自同一个客户端的请求始终发给同一个后端服务器，是通过 Cookie 的方式来实现的，青云平台支持以下植入 Cookie 的方式。

植入 Cookie：由负载均衡器向客户端植入 Cookie，这时你需要指定 Cookie 的过期时间，不指定默认为不过期。

植入 Cookie 前缀：由你的后端业务来植入和管理，负载均衡器会通过在该 Cookie 前增加前缀来实现会话保持， 植入 Cookie 前缀对后端服务是透明的，不影响后端服务的正常运行；这时你需要指定需要植入前缀的 Cookie 名称。

重写 Cookie：Cookie 由你的后端业务来植入和管理，负载均衡器会通过完全重写该 Cookie 的值来实现会话保持， 重写 Cookie 对后端服务是透明的，不影响后端服务的正常运行；这时你需要指定需要重写的 Cookie 名称。

后端 Cookie：Cookie 由你的后端业务来植入和管理，这时你需要指定会话保持的 Cookie 名称和超时时间。