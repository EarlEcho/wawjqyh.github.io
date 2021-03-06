# IP地址

## 简介

IP地址（Internet Protocol Address）是一种在Internet上的给主机编址的方式，也称为网络协议地址。常见的IP地址，分为IPv4与IPv6
两大类。2011年2月3日IPv4位地址分配完毕

IP地址编址方案：IP地址编址方案将IP地址空间划分为`A、B、C、D、E`五类，其中A、B、C是基本类，D、E类作为多播和保留使用

### IP地址转换

将IP地址分成了`网络号`和`主机号`两部分，设计者就必须决定每部分包含多少位。网络号的位数直接决定了可以分配的网络数（计算方法2^网络号位数-2）；
主机号的位数则决定了网络中最大的主机数（计算方法2^主机号位数-2）。然而，由于整个互联网所包含的网络规模可能比较大，也可能
比较小，最后选择了一种灵活的方案：将IP地址空间划分成不同的类别，每一类具有不同的网络号位数和主机号位数。

TCP/IP协议需要针对不同的网络进行不同的设置，且每个节点一般需要一个`IP地址`、一个`子网掩码`、一个`默认网关`。不过，
可以通过动态主机配置协议（DHCP），给客户端自动分配一个IP地址，避免了出错，也简化了TCP/IP协议的设置

## IP地址类型

### 公有地址

公有地址（Public address）由Inter NIC（Internet Network Information Center因特网信息中心）负责。这些IP地址分配给注册并向
Inter NIC提出申请的组织机构。通过它直接访问因特网。

### 私有地址

私有地址（Private address）属于非注册地址，专门为组织机构内部使用。

以下列出留用的内部私有地址

* A类 10.0.0.0--10.255.255.255
* B类 172.16.0.0--172.31.255.255
* C类 192.168.0.0--192.168.255.255

## IP地址分类

每个IP地址包括两个标识码（ID），即网络ID和主机ID。同一个物理网络上的所有主机都使用同一个网络ID，网络上的一个主机（包括网
络上工作站，服务器和路由器等）有一个主机ID与其对应

| 类别 | 最大网络数    | IP地址范围                | 最大主机数 | 私有IP地址范围              |
|:-----|:--------------|:--------------------------|:-----------|:----------------------------|
| A    | 126（2^7-2)   | 0.0.0.0-127.255.255.255   | 16777214   | 10.0.0.0-10.255.255.255     |
| B    | 16384(2^14)   | 128.0.0.0-191.255.255.255 | 65534      | 172.16.0.0-172.31.255.255   |
| C    | 2097152(2^21) | 192.0.0.0-223.255.255.255 | 254        | 192.168.0.0-192.168.255.255 |

## 特殊的网址

* 每一个字节都为0的地址（“0.0.0.0”）对应于当前主机
* IP地址中的每一个字节都为1的IP地址（“255．255．255．255”）是当前子网的广播地址
* IP地址中凡是以“11110”开头的E类IP地址都保留用于将来和实验使用
* IP地址中不能以十进制“127”作为开头，该类地址中数字127．0．0．1到127．255．255．255用于回路测试，如：127.0.0.1可以代表
本机IP地址，用`http://127.0.0.1`就可以测试本机中配置的Web服务器
* 网络ID的第一个8位组也不能全置为“0”，全“0”表示本地网络