---
title: Spike-github-blog  
date: 2019-09-03 14:42:45  
categories: 实习  
comment: true  
---
# 三种方案：Jekyll VS Hexo VS Hugo
## Jekyll
**官网: https://jekyllrb.com  
使用语言: Ruby  
支持的文件格式: html/md** 

Pros:

- 把原文上传github，会自动帮你生成静态网站。
- Github Pages天然支持Jekyll.
- 基于GitHub，安全性能较高
- 相对hexo而言，可以直接在github网页版上编辑和发布博客，PC间切换和同步非常方便。

Cons:
- 不支持在titles或者YAML使用变量.
- 不内置支持livereload
- 不内置支持post pagination

## Hexo
**官网：https://hexo.io/  
使用语言: NodeJS  
支持的文件格式: md**

Pros:
- 快
- 操作简单，命令少，易于记忆
- 使用主体为中国社区

Cons:
- 更换电脑则需重新安装环境
- 本地生成 html 再上传GitHub，部署需：one deploy command

## Hugo
**官网：https://gohugo.io/  
使用语言: Golang  
支持的文件格式: md**

Pros：
- 最快
- 内置 dynamic API driven
- 内置 unlimited content types、i18n、multiple output format
- 预置模版

Cons：
- 支持的插件少、扩展性不够

# 吸引于Hexo的简洁操作，下面介绍基于hexo搭建博客的流程：
## 1. 环境准备
- Node.js (Should be at least nodejs 6.9）
- Git
## 2. Hello World
### 2.1 Github上新建名为username.github.io的仓库并初始化
### 2.2 安装Hexo
```
npm install -g hexo-cli   
hexo init  
hexo g  //生成  
hexo s  //启动服务  
```

[Hexo](./images/Hexo.png)

### 2.3 在github.io仓库中创建index.html
打开https://username.github.io/即可访问个人博客啦！
[HelloWorld](./images/HelloWorld.png)

## 3. 自定义主题
hexo官网自带主题库：https://hexo.io/themes/  
或GitHub自行查找主题，此处选用GitHub最火之next

### 3.1 下载主题
```
cd your-hexo-site
git clone https://github.com/theme-next/hexo-theme-next themes/next
```

### 3.2 启用主题
将Hexo文件夹下_config.yml 内的 theme 字段修改为next

### 3.3 选择Scheme
目前NexT支持三种Scheme
- Muse – 默认 Scheme，黑白主调，大量留白
- Mist – Muse 的紧凑版本，整洁有序的单栏外观
- Pisces – 双栏 Scheme  
更改NexT文件夹下_config.yml文件，搜索scheme，将需要启用的 scheme 前面的注释 # 去除即可

### 3.4 设置语言
更改NexT文件夹下_config.yml文件，搜索language，配置为：`language: en`

### 3.5 部署
- 修改_config.yml文件：
```
deploy:  
  type: git  
  repo: https://github.com/用户名/用户名.github.io.git  
  branch: master
```
- 安装 hexo-deployer-git：npm install hexo-deployer-git --save
- 生成站点文件并推送至远程库，执行hexo clean && hexo deploy
- 启动服务器hexo s
- 至此，你的个人博客就搭建好啦！！！

##4. 参考文献
https://www.techiediaries.com/jekyll-hugo-hexo/