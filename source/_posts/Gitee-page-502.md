---
title: Gitee Page 502后的替代（GitHub Pages/Vercel）
date: 2024-05-06 16:18:22
tags:
- 网络
- CDN
- 服务器
categories: 网络
---
> Gitee Page 502了，确认是监管部门要求整改了，似乎无限期下架。在此诚挚感谢Gitee，感谢其为开源社区做出的贡献。

# Github Page
我之前采取的方法是Gitee->Github->Gitee Page（自动更新）。现在随着Gitee Page的关闭，Gitee->Github还是正常的，可以直接使用Github Page，绑定自定义域名即可，也是非常方便的。

不过，让我们看下Github Page的国内网络访问测试：

![](https://picx.zhimg.com/80/v2-cc6fcdacad3214cd65203a4af6a4aa9a_1440w.png)

总体看还是很不错的，但是一些地区会访问失败，这就很难受了：

![](https://pic6.zhimg.com/80/v2-85f8b2c9f48ab4d3d7ea97f51ea2010a_1440w.png)

# Vercel
Vercel的情况会好一点，只有一个无法访问，而且几乎是全国深绿
![](https://picx.zhimg.com/80/v2-1c1c7135ff575dd8ecf5e0e7aa44a535_1440w.png)

# 那如何使用Vercel呢？
其实非常简单，只需要进入[Vercel](https://vercel.com/)，绑定自己的Github，引入自己想要部署的仓库，创建并绑定自定义域名即可快速享用！
注意：一定要绑定自定义域名，其自带域名国内无法访问！！！

# 示例界面
[Vercel](https://mc.ecustvr.top/)

[Github Page](https://mc6.ecustvr.top/)