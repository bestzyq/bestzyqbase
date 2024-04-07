---
title: 通过CNAME域名识别CDN厂商的方法
date: 2024-04-07 21:51:00
tags: 
- 网络
- CDN
categories: 网络
---
当您需要确定一个网站是否使用了CDN（内容分发网络）服务以及具体是由哪家CDN厂商提供的加速服务时，可以通过查询其静态资源域名的CNAME记录来实现。以下是详细步骤和相关知识：

## CNAME记录及其作用

**CNAME (Canonical Name)** 是DNS（域名系统）中的一种记录类型，用于将一个域名别名指向另一个真实的域名（即主域名）。在CDN场景中，用户通常会将自己的静态资源子域名（如`static.example.com`）设置为某个CDN厂商提供的CNAME值，使得对该子域名的请求会被透明地转发至CDN厂商的服务器，从而实现内容的快速分发和缓存。

## 各大CDN厂商的CNAME域名对照表

| CNAME厂商名字 | CNAME的域名                                     |
| -------------- | ----------------------------------------------- |
| 白山云科技     | qingcdn.com<br>bsclink.cn<br>trpcdn.net          |
| 网宿           | wsdvs.com<br>wsglb0.com<br>wscdns.com            |
| 蓝汛           | cggslb.com.cn                                   |
| 帝联           | fastcdn.com                                     |
| 阿里云         | kunlun\*.com                                    |
| 腾讯云         | dnsv1.com                                       |
| 百度云         | bdydns.com                                      |
| 七牛云         | qiniudns.com                                    |
| 又拍云         | aicdn.com                                       |
| 云端智度       | spdydns.com                                     |
| 网易云         | 163jiasu.com                                    |
| 360云         | 360cdn.cn<br>qihucdn.com                         |
| 亚马逊云       | cloudfront.net                                  |
| Microsoft Azure | mschcdn.com                                     |
| verycdn        | verycdn.net                                     |