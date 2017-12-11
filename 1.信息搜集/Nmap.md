Nmap 学习笔记
--------
nmap  [选项|多选项|协议|]  目标


* 全名扫描  nmap  -A   域名
* 扫描指定段   nmap  192.168.1.1-255



## 主机发现
|选项|解释|
|---|---|
|-sP|Ping 扫描|
|-P0|无Ping扫描|
|-PS|TCP SYN Ping扫描|
|-PU|UDP Ping扫描|
|-PE;-PP;-PM|ICMP Ping Types扫描|
|-PR|ARP Ping 扫描||
|-n | 禁止dns反向解析|
|-R |反向解析域名|
|--system-dns|使用系统域名解析器|
|-sL|列表扫描|
|-6|扫描ipv6地址|
|--traceroute|路由跟踪|
|-PY|SCTP INIT Ping 扫描|

* Ping扫描 -sP   默认Ping扫描使用TCP ACK 和 ICMP echo
* 无Ping扫描 用于防止防火墙禁止Ping  -P0
* -PS  目标主机禁止防火墙的时候使用该命令 SYN Ping

### 内网扫描 Arp
namp -PR ....

nmap -p0 --packet-trace


|协议 |端口|
|---|---|
|TCP |6|
|ICMP|1|
|IGMP|2|
|UDP|17|

```bash

nmap -p0,6,17,2 --packet-trace ..



```

##















## 内网
nmap --script  broadcast-dhcp-discover

## DNS
* dns信息扫描
nmap --script dns-nsid 8.8.8.8  -p 53 -sSU
* dns 服务发现，列表
nmap --script broadcast-dns-service-discovery 
* dns 递归查询是否可用
nmap -sU -p 53 --script  dns-recursion 8.8.8.8
* dns 域名暴力解析
nmap --script dns-brute  guangu100.yuncdndun.com
* dns 探测dns缓存记录
 nmap --script dns-cache-snoop  8.8.8.8
* dns 是否支持黑名单
nmap -sn --script dns-blacklist  8.8.8.8