---
title: githubPages从hexo迁移至Jekyll  
date: 2019-09-03 17:15:45  
categories:   
comment: true  
top: 10
---

生命在于折腾，作者在实习结束后，由于hexo的特性，更换电脑需要重新配置，突发奇想抛掉所有的备份，只带上md文件重新搭建一个基于Jekyll的博客系统，是否能成功呢？
# 1. 重新配置pc与GitHub的SSH连接
# 2. 安装Jekyll(win10系统下)
## 2.2 安装Ruby环境
- 首先点击下载[Ruby Installer](https://rubyinstaller.org/downloads/)  
- 通过命令行安装Jekyll and bundler gems  
```
gem install jekyll bundler
```
- 切换到你想要作为站点的地址  
```
cd 站点地址
jekyll new 站点名
```
- 建立站点与服务器的连接
```
bundle exec jekyll serve
```
若连接成功，则会如下图显示。[Jekyll本地连接成功](./images/Jekyll本地连接成功.png)
