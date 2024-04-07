---
title: ECUST宿舍网络聚合（下）
date: 2024-04-04 22:57:30
tags:
- 网络
- ECUST
categories: 网络
---
## 前言
在上篇提到了有时需要访问校内网站的需要，而上篇只实现了同时使用运营商宽带和校园网ipv6的功能，这里我们谈谈如何实现同时使用运营商宽带和校园网ipv4&ipv6。**本篇内容需要软路由实现，比较复杂**

## 设备/资源
1. 软路由（Mi Router 3 Pro）
2. 固件：https://openwrt.ai/
3. Gitee: https://gitee.com/chinazyq/ECUST-openwrt

## 配置
### 前置准备
1. 刷Openwrt固件，推荐https://openwrt.ai/
2. 进入路由器管理界面，默认是10.0.0.1，密码: root。进入后进入网络-接口，建议修改lan里面IPv4地址，改成（例：192.168.2.1）
特别注意的是，新版本特性：配置时只能/不接LAN，不要接WAN，否则无法进入路由器管理界面
3. 进入网络-接口-设备，配置好你需要的两个wan口。
例如小米路由器R3P就是br-lan进入配置，网桥端口处只保留lan2和lan3
保存后，进入接口界面，删除原先的所有接口（也就是wan和wan6两个）
添加cmcc接口，选择设备，也就是你插入第一条网线的口（例如wan），配置pppoe，进行运营商拨号，分配防火墙区域wan
添加wan接口，选择设备，也就是你插入另一条网线的口（例如lan1），配置pppoe，进行运营商拨号，分配防火墙区域wan
建议在lan里面，使用“自定义的 DNS 服务器”处修改dns为2402:4e00::
DHCP/DNS里面可以选择关掉“DNS重定向”
4. 进入SSH，SSH用户名密码和登录相同
Windows:
Win+R cmd
```
ssh root@192.168.2.1
```
输入密码
如果一切顺利，分步输入相关指令吧

### 分步安装
1. 教育网cernet、校内地址走校园网，其它走宽带
```
# 更新软件包列表
opkg update
```
```
# 安装luci-app-mwan3
opkg install luci-app-mwan3
```
```
# 下载配置文件
wget -O /etc/config/mwan3 https://gitee.com/chinazyq/ECUST-openwrt/raw/master/mwan3
```
```
# 重新启动mwan3服务
/etc/init.d/mwan3 restart
```
2. 仅校内地址走校园网，其它走宽带
```
# 更新软件包列表
opkg update
```
```
# 安装luci-app-mwan3
opkg install luci-app-mwan3
```
```
# 下载配置文件
wget -O /etc/config/mwan3 https://gitee.com/chinazyq/ECUST-openwrt/raw/master/mwan3_onlyschool
```
```
# 重新启动mwan3服务
/etc/init.d/mwan3 restart
```

### 一键安装（新版本似乎已失效，还是手动分步安装吧）
1. 教育网cernet、校内地址走校园网，其它走宽带
```
#使用curl安装
export url='https://gitee.com/chinazyq/ECUST-openwrt/raw/master' && sh -c "$(curl -kfsSl $url/install.sh)" && source /etc/profile &> /dev/null
```
```
#使用wget安装
export url='https://gitee.com/chinazyq/ECUST-openwrt/raw/master' && wget -q --no-check-certificate -O /tmp/install.sh $url/install.sh  && sh /tmp/install.sh && source /etc/profile &> /dev/null
```
2. 仅校内地址走校园网，其它走宽带
```
#使用curl安装
export url='https://gitee.com/chinazyq/ECUST-openwrt/raw/master' && sh -c "$(curl -kfsSl $url/install_onlyschool.sh)" && source /etc/profile &> /dev/null
```
```
#使用wget安装
export url='https://gitee.com/chinazyq/ECUST-openwrt/raw/master' && wget -q --no-check-certificate -O /tmp/install_onlyschool.sh $url/install_onlyschool.sh  && sh /tmp/install_onlyschool.sh && source /etc/profile &> /dev/null
```

## 结语
通过配置，可以同时使用运营商宽带和校园网ipv4&ipv6，愉快使用吧！