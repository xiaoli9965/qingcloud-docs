---
title: "DissociateEipsFromNFV"
description: 网络组件解绑一个或多个公网 IP
draft: false
weight: 3
keyword: 青云, QingCloud, 云计算, API, NFV, NAT 网关, 网络组件, 公网 IP
---



从一个网络组件解绑一个或多个公网 IP。

**Request Parameters**

| Parameter name | Type | Description | Required |
| --- | --- | --- | --- |
| nfv | String | 网络组件的 ID | Yes |
| zone | String | 区域 ID，注意要小写 | Yes |
| eips.n | String | 将要解绑的公网 IP 的 ID | Yes |

[_公共参数_](../../../parameters/)

**Response Elements**

| Name | Type | Description |
| --- | --- | --- |
| action | String | 响应动作 |
| job_id | String | 从一个网络组件解绑一个或多个公网IP job ID 号 |
| ret_code | Integer | 执行成功与否，0 表示成功，其他值则为错误代码 |

**Example**

_Example Request_

```
https://api.qingcloud.com/iaas/?action=DissociateEipsFromNFV
&nfv=nfv-1234abcd
&eips.1=eip-ek3scgap
&eips.2=eip-ek4scgam
&COMMON_PARAMS
```

_Example Response_:

```
{
  "action":"DissociateEipsFromNFVResponse",
  "ret_code":0,
  "job_id":"j-1234abcd"
}
```
