---
title: 华理VPN的其他用法
date: 2024-06-21 00:08:53
tags:
- ECUST
- VPN
categories: 网络
---
> 可能大家平时使用华理VPN一般只从[网页](https://sslvpn.ecust.edu.cn/)或者客户端启动，其实还有一些有意思的用法

## 游戏加速器
华理VPN客户端？游戏加速器！
当在家中玩外服游戏丢包时，也许可以试试华理VPN**客户端**
例如，《War thunder》在家中直连情况下，约350ms且丢包严重；启动华理VPN客户端后，约100ms，没有丢包！
当然，效果肯定没有正常的游戏加速器好（毕竟是免费的嘛吗ヾ(≧▽≦*)o

## 访问其他地址
可能一般使用华理VPN时，只是访问标签导航界面给出的内容。
如果想模拟校园网下访问其他网页怎么办？
例如，信息办测速网站：http://172.20.17.6/
这个网页只能校园网下访问，且客户端访问不了，如果想在校外访问怎么办呢？（相信没人想要hhh
那么转换一下，访问这个就好了：https://172-20-17-6.sslvpn.ecust.edu.cn:8118/
可能有人想问，其他网页怎么办？原理不在此详述了，找找规律吧！

### 浏览器收藏夹法
编辑收藏夹中==>新建==>输入名称:SSLVPN==>输入URL:
```
javascript:location.href="https://"+location.hostname.replace(/\./g,'-')+(location.port?("-"+location.port+"-p"):"")+(location.protocol=="https:"?"-s":"")+".sslvpn.ecust.edu.cn:8118"+location.pathname+location.search;
```
在想访问的界面中，点击收藏夹中的SSLVPN即可

### 网页转换法
[华理VPN链接转换工具](https://www.ecustvr.top/vpn.html)

## 特别提醒
⚠特别提醒：不要滥用哦！！！

