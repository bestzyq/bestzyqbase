---
title: Hexo + Butterfly主题 记录
date: 2024-07-26 19:24:59
tags: hexo
categories: 学习
---
# 背景
换新电脑，原有base安装全是warning，所以决定琢磨琢磨重新安装。

# 步骤
1. 安装Git，这个肯定是前提条件  
    - windows下安装git，直接下载安装即可：https://git-scm.com/download/
2. 安装nodejs，这个也是前提条件，这次试了一下[nvs](https://github.com/jasongin/nvs/)，有一些优点，比如可以指定版本，不用管全局安装的版本，可以切换版本，不用卸载再安装。  
    1. 安装nvs
        - 直接下载安装即可：https://github.com/jasongin/nvs/releases
        - 默认Windows无法启动脚本，因为安全问题，所以需要PowerShell 执行策略：[Powershell文档：about_Execution_Policies](https://learn.microsoft.com/zh-cn/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7.4&viewFallbackFrom=powershell-7.4%2C%E5%85%B3%E4%BA%8E%E6%89%A7%E8%A1%8C%E7%AD%96%E7%95%A5)。如果你不想看，直接执行下面这段就好啦
            ```powershell
            Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
            ```
    2. 安装nodejs
        > nvs文档：https://github.com/jasongin/nvs#windows-powershell-and-cmd-shells
        
        这里有个换源问题，否则难以下载。编辑 `settings.json` ，将内容替换如下：

        ```
        {
            "aliases": {},
            "remotes": {
                "default": "node",
                "node": "https://mirrors.cernet.edu.cn/nodejs-release/"
            }
        }
        ```

        - 要添加最新版本的节点，请执行以下操作：
            ```powershell
            nvs add latest
            ```
        - 或者添加节点的最新 LTS 版本：
            ```powershell
            nvs add lts
            ```
        - 然后运行命令，将节点版本添加到当前 shell 的 PATH 中：nvs use
            ```powershell
            nvs use lts
            PATH += ~/.nvs/node/6.9.1/x64
            ```
        - 要将其永久添加到 PATH，请使用：nvs link
            ```powershell
            nvs link lts
            ```
3. 安装hexo
    > hexo文档：https://hexo.io/zh-cn/docs/

    - hexo本身是非常简单的，按文档即可。
    - 主题：建议主题安装采用npm安装，例如 `npm install hexo-theme-butterfly`。具体看具体主题文档。之前采用其他两种安装方式，感觉主题随git一起上传仓库没有必要。
    另外需要注意如果想直接把纯网站推到gitee/github，需要安装 `hexo-deployer-git` ：
        ```powershell
        npm install hexo-deployer-git --save
        ```
        至于其他，看文档吧：https://hexo.io/zh-cn/docs/github-pages
    - 配置文件：butterfly的配置文件有cdn需求，不建议使用local，因为需要额外装hexo-butterfly-extjs，这个安装后会产生很多不必要的warnings。推荐使用又拍云支持的[Zstatic CDN](https://www.zstatic.net/)，输入 `https://s4.zstatic.net/ajax/libs/${cdnjs_name}/${version}/${min_cdnjs_file}` 即可。其他配置看这里：https://butterfly.js.org/posts/ceeb73f/?highlight=jsdelivr#CDN
4. Powershell中用不了 `hexo clean && deploy`，可以用 `hexo clean; hexo deploy` 。至于什么生成文章之类就不过多赘述了，文档都有。

# 附件
```json
# package.json
{
  "name": "hexo-site",
  "version": "0.0.0",
  "private": true,
  "scripts": {
    "build": "hexo generate",
    "clean": "hexo clean",
    "deploy": "hexo deploy",
    "server": "hexo server"
  },
  "hexo": {
    "version": "7.3.0"
  },
  "dependencies": {
    "hexo": "^7.0.0",
    "hexo-deployer-git": "^4.0.0",
    "hexo-generator-archive": "^2.0.0",
    "hexo-generator-category": "^2.0.0",
    "hexo-generator-index": "^3.0.0",
    "hexo-generator-tag": "^2.0.0",
    "hexo-renderer-ejs": "^2.0.0",
    "hexo-renderer-marked": "^6.0.0",
    "hexo-renderer-stylus": "^3.0.0",
    "hexo-server": "^3.0.0",
    "hexo-theme-butterfly": "^4.13.0"
  }
}
```