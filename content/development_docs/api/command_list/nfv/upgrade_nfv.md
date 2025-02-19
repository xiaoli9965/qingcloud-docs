---
title: "UpgradeNFV"
description: 升级网络组件
draft: false
weight: 12
keyword: 青云, QingCloud, 云计算, API, NFV, NAT 网关, 网络组件, 升级版本
---

将一个或多个网络组件(NFV)版本从 1.0  升级到 2.0。

**Request Parameters**

| Parameter name | Type | Description | Required |
| --- | --- | --- | --- |
| nfvs.n | String | 网络组件的 ID | Yes |
| zone | String | 区域 ID，注意要小写 | Yes |

[_公共参数_](../../common/parameters.html#api-common-parameters)

**Response Elements**

| Name | Type | Description |
| --- | --- | --- |
| action | String | 响应动作 |
| job_id | String | 更新一个或多个网络组件(NFV)的 job ID 号 |
| ret_code | Integer | 执行成功与否，0 表示成功，其他值则为错误代码 |

**Example**

_Example Request_

```
https://api.qingcloud.com/iaas/?action=UpgradeNFV
&nfvs.1=nfv-1234abcd
&COMMON_PARAMS
```

_Example Response_:

```
{
  "action":"UpgradeNFVResponse",
  "ret_code":0,
  "job_id":"j-0om6hgcokm5"
}
```
