---
title: "通过 DNAT 功能实现提供公网服务"
descriptipn: 通过NAT网关的 DNAT 功能实现云服务器面向公网提供服务。
draft: false
weight: 20
keyword: QingCloud, 云计算, 青云, NAT网关, NAT, SNAT, DNAT
---

<!--VPC 网络内的一个或多个云服务器需要面向公网提供服务时，可以 NAT 网关的 DNAT 功能实现对公网提供服务。-->

NAT 网关支持 DNAT 功能，将 NAT 网关上的公网 IP 映射给云服务器使用，使云服务器能够对外提供公网访问服务。

## 前提条件

已创建 VPC 网络。具体操作，请参见[创建 VPC 网络](/network/vpc/manual/vpcnet/10_create_vpc/)。

## 配置流程

![](../../_images/dnat_qs.svg)

## 操作步骤

### 步骤1：创建 NAT 网关

1. 登录 [QingCloud 管理控制台](https://console.qingcloud.com/login)，在控制台导航栏中，选择**产品与服务** > **网络服务** > **NAT 网关**，进入 **NAT 网关**页面。

2. 点击**创建**，进入**创建 NAT 网关**页面。

   ![](../../_images/create_natgw.png)

3. 配置 NAT 网关信息。

   对于 NAT 网关的各项配置参数更详细的说明，可参见[创建 NAT 网关](../../manual/mge_nat/create_nat/)。

   - **区域**：选择需要创建 NAT 网关的区域。
   - **名称**：设置 NAT 网关的名称。名称长度为1~64个字符，须由中文、英文字母、数字、下划线（_）、中划线（-）和点（.）组成。
   - **VPC 网络**：选择 NAT 网关所属的 VPC。创建 NAT 网关后，不能修改 NAT 网关所属的 VPC。
   - **规格**：选择 NAT 网关的规格。不同规格的 NAT 网关会影响 SNAT 最大连接数和 流量转发能力，但不会影响 DNAT 性能。请您根据业务需求灵活选择规格。规格说明请参考 [NAT 网关规格](../../intro/specification/)。
   - **部署方式**：选择 NAT 网关集群节点部署方式。**多可用区部署**表示节点分散部署在不同可用区，可用性更高；**单可用区部署**表示节点部署在指定的同一可用区，网络延迟最低。
   - **可用区**：选择**单可用区部署**方式时，需要指定 NAT 网关所属的可用区。
   - **公网 IP**：NAT 网关需要绑定 EIP 才能正常工作。推荐选择**购买并绑定**。
   - **安全组**：选择 NAT 网关的安全组。
   - **集群模式**：选择**多可用区部署**方式时，需要选择 NAT 网关节点的集群模式。**低延时**表示网络流量会优先传输到距离最近的 NAT 网关节点上；**单高吞吐**表示网络流量会均衡地传输到所有的 NAT 网关节点上。

4. 点击**立即创建**。等待创建完成。

### 步骤2：配置指向 NAT 网关的路由

>**注意**
>
>- 若 NAT 网关所属的 VPC 是您在新版 NAT（ NATGW v2.0） 上线之后新建的，则系统会在创建 NAT 网关时自动在该 VPC 的默认路由表中下发指向 NAT 网关、目标网络为 0.0.0.0/0 的路由，无需您手动进行配置，请跳过本步骤，直接执行[步骤3](#步骤3添加-snat-规则)。
>- 若 NAT 网关所属的 VPC 是您在新版 NAT（ NATGW v2.0） 上线之前创建的，或者该 VPC 关联的默认路由表中已有目标网络为 0.0.0.0/0 的路由规则，则参照本步骤手动配置路由规则，将私有网络流量指向 NAT 网关。

1. 在左侧导航中，选择**网络** > **路由表**。

2. 在路由表列表中，单击需要访问 Internet 的私有网络所关联的路由表 ID，进入路由表详情页。

   > **说明**
   >
   > 若私有网络还未绑定路由表，请先创建并绑定。具体操作请参见[路由表使用指导](/network/vpc/manual/routing/02_route_function/)。

3. 在**规则**页签下，点击**添加路由**。

4. 在目标网络输入框中输入规则名称及目标网络地址段（如0.0.0.0/0，表示所有网络地址），下一跳选择 **NAT 网关**。

5. 点击**提交**。

6. 添加完成后，点击**应用修改**使配置生效。

### 步骤3：添加 DNAT 规则

1. 在 NAT 网关列表中，点击目标 NAT 网关的 ID 号，进入 NAT 网关详情页。

2. 在 **DNAT 规则**页签，点击**添加规则**，弹出**添加DNAT规则**窗口。

   ![](../../_images/create_dnat.png)

3. 配置 DNAT 规则。
   - **名称**：DNAT 规则的名称。

   - **协议**：选择`TCP`。

   - **公网 IP**：选择用来提供互联网通信的公网 IP。

   - **公网端口**：公网 IP 的端口。NAT 网关会将以指定协议和端口访问该公网 IP 的请求转发到指定内网 IP 的指定端口上。有效数值为0-65535。

     > **说明**
     >
     > 若您需要开放 80/443 端口，必须先进行 ICP 备案才可使用。在此之前，80/443 端口的服务将被禁用。更多备案详情请参见[备案常见问题](https://beian.qingcloud.com/icp)。

   - **内网 IP**：选择要通过 DNAT 规则进行互联网通信的云服务器内网 IP。

   - **内网端口**：内网 IP 的端口。有效数值为0-65535。

4. 点击**添加**。

5. 在 NAT 网关的基本信息区域右上方点击**应用修改**使配置生效。

### 步骤4：配置安全组规则

DNAT 规则配置成功后，需要放开对应的安全组规则，确保提供服务的端口能被互联网访问。安全组配置方法，请参见[安全组规则配置](/security/security_group/manual/sg_rules/)。

### 步骤5：结果验证

您可以使用互联网中的任意一台电脑访问云服务器上部署的服务，测试云服务器的连通性。

1. 打开本地电脑的浏览器。
2. 在浏览器地址栏输入 DNAT 规则中配置的`公网 IP:公网端口`来访问部署在云服务器上的应用服务。
   


