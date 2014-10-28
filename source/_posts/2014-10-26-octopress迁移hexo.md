title: octopress迁移Hexo
date: 2014-10-26 21:22:03
tags: [hexo,octopress]
keywords: octopress, hexo,迁移
categories: hexo
description: Octopress generate太慢，加之老机器太旧；趁着最近更新了机器，把博客迁移到Hexo，继续码博客吧。
comments: true
---
Octopress generate太慢，配置环境依赖得花费好长时间搞定，加之老机器太旧；趁着最近更新了机器，无奈把博客迁移到Hexo，继续码博客吧。
Hexo官网:[Link](http://hexo.io)

安装
---
1. Mac下首先安装Node.js，直接到[这里](http://nodejs.org/)下载安装即可，安装完毕后在.bash_profile中添加:
```
export PATH="/usr/local/bin/:$PATH"
```
<!--more-->
2. Mac自带git，不过得先安装好xCode才可以使用git
3. 新建文件夹hexo执行命令，安装hexo：
```
$ npm install -g hexo
```
4. 执行如下命令，初始化hexo
```
$ hexo init <folder>
$ cd <folder>
$ npm install
```
5. 如果是从octopress迁移的可以需要修改`_config.yml`
```
$ cp <octopress>/source/_post/* <hexo>/source/_post/
```
```
new_post_name: :year-:month-:day-:title.md
```
如果想要保留RSS，可以安装`hexo-migrator-rss`插件

主题和插件
---
Hexo提供了丰富的[插件](https://github.com/tommy351/hexo/wiki/Plugins)和[主题](https://github.com/tommy351/hexo/wiki/Themes):
安装方法：
1. 插件
```
$ npm install <plugin-name> --save
```
2. 主题
```
$ git clone <repository> themes/<theme-name>
```
注意需要在`_config.yml`中修改`plugins`和`theme`的值来启用。

调试
---
执行下面命令实时查看`http://localhost:4000`：
```
$ hexo server
```

部署git pages
---
修改`_config.yml`:
```
deploy:
  type: github
  repository: git@github.com:XXX/XXX.github.com.git
  branch: master
```
注意：为项目制作网页需要讲`branch`改为`gh-pages`,如果需要自定义域名需要添加CNAME文件，参考[Hexo](http://zespia.tw/hexo/docs/deployment.html)
之后deploy：
```
$ hexo clean
$ hexo generate
$ hexo deploy
```

